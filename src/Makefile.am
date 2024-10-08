## Note: starting comments with ## means they don't end up in Makefile

SUFFIXES = .h .c .o .l .check

# Check files before compiling; requires splint!
CHECK = 1

# Some preferences
### We use the no-lines option to prevent confusion with splint flag settings.
### Should fix splint to avoid this...
YFLAGS = -v -t -d --debug --no-lines
LFLAGS = -L
LEXLIB = -lfl

## We only build Splint
bin_PROGRAMS = splint

AM_CPPFLAGS = -I$(srcdir)/Headers -I$(builddir)

## Grammar sources

FLEX_SRC = cscanner.l
BISON_SRC = cgrammar.y  llgrammar.y  mtgrammar.y  signature.y

## The main sources

SETSRC = globSet.c intSet.c typeIdSet.c guardSet.c usymIdSet.c sRefSet.c

LISTSRC = clauseStack.c filelocStack.c \
          cstringList.c cstringSList.c sRefSetList.c ctypeList.c \
          enumNameList.c enumNameSList.c exprNodeList.c exprNodeSList.c \
          uentryList.c fileIdList.c filelocList.c qualList.c sRefList.c \
          flagMarkerList.c idDeclList.c flagSpec.c

CPPSRC = cppmain.c cpplib.c cppexp.c cpphash.c cpperror.c

CSRC = context.c uentry.c cprim.c macrocache.c qual.c qtype.c stateClause.c \
       stateClauseList.c ctype.c cvar.c clabstract.c idDecl.c clause.c \
       globalsClause.c modifiesClause.c warnClause.c functionClause.c \
       functionClauseList.c metaStateConstraint.c metaStateConstraintList.c \
       metaStateExpression.c metaStateSpecifier.c functionConstraint.c \
       pointers.c cscannerHelp.c

SPLINTSRC = exprNode.c exprChecks.c llmain.c help.c rcfiles.c
CHECKSRC = structNames.c transferChecks.c varKinds.c nameChecks.c

GLOBSRC = globals.c flags.c general.c osd.c reader.c mtreader.c

GRAMSRC = cscanner.c cgrammar.c mtgrammar.c llgrammar.c signature.c

OVERFLOWCHSRC = constraintList.c constraintResolve.c \
                constraintGeneration.c constraintTerm.c \
                constraintExprData.c constraintExpr.c constraint.c \
                loopHeuristics.c 

GENERALSRC = exprData.c cstring.c fileloc.c message.c inputStream.c \
             fileTable.c cstringTable.c valueTable.c stateValue.c \
             llerror.c messageLog.c flagMarker.c aliasTable.c ynm.c \
             sRefTable.c genericTable.c ekind.c usymtab.c multiVal.c \
             lltok.c sRef.c lcllib.c randomNumbers.c fileLib.c

METASTATESRC = mtscanner.c stateInfo.c stateCombinationTable.c metaStateTable.c \
               metaStateInfo.c annotationTable.c annotationInfo.c mttok.c \
               mtDeclarationNode.c mtDeclarationPieces.c mtDeclarationPiece.c \
               mtContextNode.c mtValuesNode.c mtDefaultsNode.c \
               mtAnnotationsNode.c mtMergeNode.c mtAnnotationList.c \
               mtAnnotationDecl.c mtTransferClauseList.c mtTransferClause.c \
               mtTransferAction.c mtLoseReferenceList.c mtLoseReference.c \
               mtDefaultsDeclList.c mtDefaultsDecl.c mtMergeItem.c \
               mtMergeClause.c mtMergeClauseList.c

## These are only used if LCL is enabled

LCLONLYSRC = usymtab_interface.c abstract.c ltoken.c lclscanline.c \
             lclsyntable.c lcltokentable.c sort.c symtable.c lclinit.c \
             shift.c lclscan.c lsymbol.c mapping.c

LSLSRC = tokentable.c scan.c scanline.c lslparse.c \
         lh.c checking.c lclctypes.c imports.c lslinit.c syntable.c 

LCLSETSRC  = lsymbolSet.c sigNodeSet.c lslOpSet.c sortSet.c

LCLLISTSRC = initDeclNodeList.c sortList.c declaratorInvNodeList.c \
             interfaceNodeList.c sortSetList.c declaratorNodeList.c \
             letDeclNodeList.c stDeclNodeList.c storeRefNodeList.c \
             lslOpList.c lsymbolList.c termNodeList.c ltokenList.c \
             traitRefNodeList.c pairNodeList.c typeNameNodeList.c \
             fcnNodeList.c paramNodeList.c programNodeList.c \
             varDeclarationNodeList.c varNodeList.c quantifierNodeList.c \
             replaceNodeList.c importNodeList.c

GRAMHEADERSRC = signature_gen.h cgrammar_tokens.h \
                llgrammar_gen.h mtgrammar_tokens.h

HEADERSRC = Headers/abstBodyNode.h         Headers/ltokenList.h \
          Headers/abstract.h               Headers/macrocache.h \
          Headers/abstractNode.h           Headers/mapping.h \
          Headers/message.h                \
          Headers/aliasStack.h             Headers/messageLog.h \
          Headers/aliasTable.h             Headers/metaStateConstraint.h \
          Headers/annotationInfo.h         Headers/metaStateConstraintList.h \
          Headers/annotationTable.h        Headers/metaStateExpression.h \
          Headers/arrayQualNode.h          Headers/metaStateInfo.h \
          Headers/basic.h                  Headers/metaStateSpecifier.h \
          Headers/bool.h                   Headers/metaStateTable.h \
          Headers/boolStack.h              Headers/misc.h \
          Headers/cgrammar.h               Headers/modifiesClause.h \
          Headers/modifyNode.h             \
          Headers/checking.h               Headers/mtAnnotationDecl.h \
          Headers/clabstract.h             Headers/mtAnnotationList.h \
          Headers/claimNode.h              Headers/mtAnnotationsNode.h \
          Headers/clause.h                 Headers/mtContextNode.h \
          Headers/clauseStack.h            Headers/mtDeclarationNode.h \
          Headers/code.h                   Headers/mtDeclarationPiece.h \
          Headers/constants.h              Headers/mtDeclarationPieces.h \
          Headers/constDeclarationNode.h   Headers/mtDefaultsDecl.h \
          Headers/constraintExprData.h     Headers/mtDefaultsDeclList.h \
          Headers/constraintExpr.h         Headers/mtDefaultsNode.h \
          Headers/constraint.h             Headers/mtgrammar.h \
          Headers/constraintList2.h        \
          Headers/constraintList.h         \
          Headers/constraintOutput.h       Headers/mtincludes.h \
          Headers/constraintResolve.h      Headers/mtLoseReference.h \
          Headers/constraintTerm.h         Headers/mtLoseReferenceList.h \
          Headers/context.h                Headers/mtMergeClause.h \
          Headers/cpperror.h               Headers/mtMergeClauseList.h \
          Headers/cppexp.h                 Headers/mtMergeItem.h \
          Headers/cpp.h                    Headers/mtMergeNode.h \
          Headers/cpphash.h                Headers/mtreader.h \
          Headers/cpplib.h                 Headers/mtscanner.h \
          Headers/cprim.h                  Headers/mttok.h \
          Headers/cscanner.h               Headers/mtTransferAction.h \
          Headers/cstring.h                Headers/mtTransferClause.h \
          Headers/cstringList.h            Headers/mtTransferClauseList.h \
          Headers/cstringSList.h           Headers/mtValuesNode.h \
          Headers/cstringTable.h           Headers/multiVal.h \
          Headers/ctokens.h                Headers/nameChecks.h \
          Headers/ctypeList.h              Headers/nameNode.h \
          Headers/CTypesNode.h             Headers/opFormNode.h \
          Headers/cvar.h                   Headers/osd.h \
          Headers/declaratorInvNode.h      Headers/pairNode.h \
          Headers/declaratorInvNodeList.h  Headers/pairNodeList.h \
          Headers/declaratorNode.h         Headers/paramNode.h \
          Headers/declaratorNodeList.h     Headers/paramNodeList.h \
          Headers/dmalloc.h                Headers/osd.h \
          Headers/ekind.h                  Headers/pp.h \
          Headers/enumNameList.h           Headers/privateNode.h \
          Headers/enumNameSList.h          Headers/programNode.h \
          Headers/enumSpecNode.h           Headers/programNodeList.h \
          Headers/exportNode.h             Headers/qtype.h \
          Headers/exposedNode.h            Headers/qual.h \
          Headers/exprChecks.h             Headers/qualList.h \
          Headers/exprData.h               Headers/quantifiedTermNode.h \
          Headers/exprNode.h               Headers/quantifierNode.h \
          Headers/exprNodeList.h           Headers/quantifierNodeList.h \
          Headers/exprNodeSList.h          Headers/randomNumbers.h \
          Headers/fcnNode.h                Headers/rcfiles.h \
          Headers/fcnNodeList.h            Headers/reader.h \
          Headers/fileId.h                 Headers/refTable-branch.h \
          Headers/fileIdList.h             Headers/renamingNode.h \
          Headers/fileLib.h                Headers/replaceNode.h \
          Headers/fileloc.h                Headers/replaceNodeList.h \
          Headers/filelocList.h            Headers/scan.h \
          Headers/filelocStack.h           Headers/scanline.h \
          Headers/fileTable.h              Headers/sgrammar_tokens.h \
          Headers/flag_codes.h             Headers/sHerald.h \
          Headers/flagMarker.h             Headers/shift.h \
          Headers/flagMarkerList.h         Headers/signature2.h \
          Headers/flags.h                  \
          Headers/flagSpec.h               Headers/signature.h \
          Headers/forwardTypes.h           Headers/signNode.h \
          Headers/functionClause.h         Headers/sigNode.h \
          Headers/functionClauseList.h     Headers/sigNodeSet.h \
          Headers/functionConstraint.h     Headers/sort.h \
          Headers/general.h                Headers/sortList.h \
          Headers/genericTable.h           Headers/sortSet.h \
          Headers/globalList.h             Headers/sortSetList.h \
          Headers/globalsClause.h          \
          Headers/globals.h                \
          Headers/globSet.h                Headers/sRef.h \
          Headers/gram.h                   Headers/sRefList.h \
          Headers/guardSet.h               Headers/sRefSet.h \
          Headers/handle.h                 Headers/sRefSetList.h \
          Headers/sRefSetStack.h           \
          Headers/idDecl.h                 Headers/sRefTable.h \
          Headers/idDeclList.h             Headers/stateClause.h \
          Headers/importNode.h             Headers/stateClauseList.h \
          Headers/importNodeList.h         Headers/stateCombinationTable.h \
          Headers/imports.h                Headers/stateInfo.h \
          Headers/initDeclNode.h           Headers/stateValue.h \
          Headers/initDeclNodeList.h       Headers/stDeclNode.h \
          Headers/inputStream.h            Headers/stDeclNodeList.h \
          Headers/interfaceNode.h          Headers/stmtNode.h \
          Headers/interfaceNodeList.h      Headers/storeRefNode.h \
          Headers/intSet.h                 Headers/storeRefNodeList.h \
          Headers/intTable.h               Headers/strOrUnionNode.h \
          Headers/iterNode.h               Headers/structNames.h \
          Headers/lcl_constants.h          Headers/symtable.h \
          Headers/lclctypes.h              Headers/syntable.h \
          Headers/lclForwardTypes.h        Headers/system_constants.h \
          Headers/lclinit.h                Headers/taggedUnionNode.h \
          Headers/lcllib.h                 Headers/termNode.h \
          Headers/lclMisc.h                Headers/termNodeList.h \
          Headers/lclPredicateNode.h       Headers/tmpname.h \
          Headers/lclscan.h                Headers/tokentable.h \
          Headers/lclscanline.h            Headers/traitRefNode.h \
          Headers/lclsyntable.h            Headers/traitRefNodeList.h \
          Headers/lcltokentable.h          Headers/transferChecks.h \
          Headers/lclTypeSpecNode.h        Headers/typeExpr.h \
          Headers/lctype.h                 Headers/typeIdSet.h \
          Headers/letDeclNode.h            Headers/typeNameNode.h \
          Headers/letDeclNodeList.h        Headers/typeNameNodeList.h \
          Headers/lh.h                     Headers/typeNamePack.h \
          Headers/limwr.h                  Headers/typeNode.h \
          Headers/uentry.h                 Headers/usymtab.h \
          Headers/llerror.h                Headers/uentryList.h \
          Headers/llglobals.h              Headers/usymId.h \
          Headers/usymIdSet.h              \
          Headers/llgrammar.h              Headers/usymtab_interface.h \
          Headers/llmain.h                 Headers/valueMatrix.h \
          Headers/lltok.h                  Headers/valueTable.h \
          Headers/lslinit.h                Headers/varDeclarationNode.h \
          Headers/lslOp.h                  Headers/varDeclarationNodeList.h \
          Headers/lslOpList.h              Headers/varKinds.h \
          Headers/lslOpSet.h               Headers/varNode.h \
          Headers/lslparse.h               Headers/varNodeList.h \
          Headers/lsymbol.h                Headers/version.h \
          Headers/lsymbolList.h            Headers/warnClause.h \
          Headers/lsymbolSet.h             Headers/ynm.h \
          Headers/ltoken.h                 Headers/splintMacros.nf  \
          Headers/typeId.h \
          Headers/pointers.h   Headers/mstring.h   Headers/help.h


IFILES =  ctbase.i  cttable.i  exprDataQuite.i

## Non-built files we need to distribute
EXTRA_DIST = $(BISON_SRC) $(FLEX_SRC) bison.head bison.reset \
            flags.def flex.head flex.reset $(IFILES) \
            .splintrc LICENSE \
            Headers/cscannerHelp.h \
 Headers/256_random_numbers.nf  Headers/splintMacros.nf	Headers/reservedNames.nf

COMMONSRC =  $(CPPSRC) $(CSRC) $(CHECKSRC) $(GENERALSRC) \
            $(GLOBSRC) $(IFACESRC) $(LISTSRC) $(SETSRC) $(METASTATESRC)

LCLSRC = $(LCLSETSRC) $(LCLLISTSRC) $(LSLSRC) $(CMNSRC) $(LCLONLYSRC) 

ALLSRC = $(GRAMSRC) $(COMMONSRC) $(SPLINTSRC) $(OVERFLOWCHSRC) $(HEADERSRC) $(LCLSRC)

#files to run Splint on
LINTSRC = $(COMMONSRC) $(SPLINTSRC) 

splint_SOURCES = $(ALLSRC)
splint_LDADD = $(LEXLIB)

## Sources that need to be built
BUILT_SOURCES = $(GRAMHEADERSRC) $(GRAMSRC) flag_codes.gen

## Grammars

# Signature
signature.tab.c: signature.y
	$(BISON) $(YFLAGS) -p lsl $<

signature.tab.h: signature.tab.c
	@echo $@ generated

signature_gen.h: bison.head signature.tab.h bison.reset
	cat $^ >$@

signature.c: bison.head signature.tab.c bison.reset
	cat $^ | $(SED) 's/signature\.tab\.h/signature_gen.h/g' >$@

# CGrammar
cgrammar.tab.c: cgrammar.y
	$(BISON) $(YFLAGS) $<
	@echo '*      Note: Expect 159 shift/reduce conflicts and 123 reduce/reduce conflicts. (see cgrammar.y for explanation)'

cgrammar.tab.h: cgrammar.tab.c
	@echo $@ generated

cgrammar_tokens.h: bison.head cgrammar.tab.h bison.reset
	cat $^ | $(SED) -e 's/YYSTYPE/cgrammar_YYSTYPE/g' -e 's/lsllex/cgrammar_lsllex/g' >$@

cgrammar.c: bison.head cgrammar.tab.c bison.reset
	cat $^ | $(SED) -e 's/YYSTYPE/cgrammar_YYSTYPE/g' -e 's/lsllex/cgrammar_lsllex/g' -e 's/cgrammar\.tab\.h/cgrammar_tokens.h/g' >$@

# MTGrammar
mtgrammar.tab.c: mtgrammar.y
	$(BISON) $(YFLAGS) -p mt $<
	@echo '*       Note: Expect 11 shift/reduce conflicts.'

mtgrammar.tab.h: mtgrammar.tab.c
	@echo $@ generated

mtgrammar_tokens.h: bison.head mtgrammar.tab.h bison.reset
	cat $^ >$@

mtgrammar.c: bison.head mtgrammar.tab.c bison.reset
	cat $^ | $(SED) 's/mtgrammar\.tab\.h/mtgrammar_tokens.h/g' >$@

# LLGrammar

llgrammar.tab.c: llgrammar.y
	$(BISON) $(YFLAGS) -p yl $<
	@echo '*       Note: Expect 2 shift/reduce conflicts'

llgrammar.tab.h: llgrammar.tab.c
	@echo $@ generated

llgrammar_gen.h: bison.head llgrammar.tab.h bison.reset
	cat $^ >$@

llgrammar.c: bison.head llgrammar.tab.c bison.reset
	cat $^ | $(SED) 's/llgrammar\.tab\.h/llgrammar_gen.h/g' >$@

# CScanner

cscanner.lex.c: cscanner.l cgrammar_tokens.h
	$(FLEX) $(LFLAGS) -o $@ $<

cscanner.c: flex.head cscanner.lex.c flex.reset
	cat $^ | $(SED) -e 's/YYSTYPE/cgrammar_YYSTYPE/g' -e 's/lsllex/cgrammar_lsllex/g' >$@

## Flag codes

flag_codes.gen: flags.def
	$(GREP) "FLG_" $< >$@

## Checking rules

CHECKS = $(subst .c,.check,$(splint_SOURCES))

## Other rules

.PHONY: nocheck
nocheck:
	$(MAKE) CHECK=0

.PHONY: test
test: splint
	$(MAKE) -C ../test

.PHONY: libs
libs: splint
	$(MAKE) -C ../lib

splintme: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude  $(OVERFLOWCHSRC) $(LINTSRC) $(LCLSRC) -dump lclint +forcehints -misplacedsharequal +showsourceloc -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw -mts tainted

splintmebounds: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude  $(OVERFLOWCHSRC) $(LINTSRC) $(LCLSRC) -dump lclint +forcehints -misplacedsharequal +showsourceloc -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw -mts tainted +bounds +impboundsconstraints

splintmesupcounts: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude  $(OVERFLOWCHSRC) $(LINTSRC) $(LCLSRC) -dump lclint +forcehints -misplacedsharequal +showsourceloc -unrecogcomments  -fcnuse -incondefs -exportlocal -supcounts -constuse -mts file -mts filerw 

lintbuffercheck: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude $(LINTSRC) $(OVERFLOWCHSRC) $(LCLSRC) -dump lclint +forcehints -misplacedsharequal +showsourceloc -unrecogcomments -supcounts -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw +bounds -DLINTBUFFERCHECK

valsplint:
	valgrind -v --leak-resolution=high --num-callers=20 --show-reachable=no --leak-check=yes ./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude $(LINTSRC) $(OVERFLOWCHSRC) $(LCLSRC) -dump lclint +forcehints -misplacedsharequal +showsourceloc -unrecogcomments -supcounts -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw 


splintsome: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude lcllib.c  -dump lclint +forcehints -misplacedsharequal +showsourceloc -unrecogcomments -supcounts -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw +partial

splinttest: 
	./splint $(DEFAULT_INCLUDES) $(DEFS) $(INCLUDES) $(AM_CPPFLAGS) $(CPPFLAGS) +singleinclude test.c +forcehints -misplacedsharequal +showsourceloc -unrecogcomments -fcnuse -incondefs -exportlocal -constuse -mts file -mts filerw +keep +supcounts +partial -null

CLEANFILES = splint$(EXEEXT) *.output *.tab.h *.tab.c *.lex.c $(BUILT_SOURCES)
