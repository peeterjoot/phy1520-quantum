THISDIR := phy1520-quantum
THISBOOK := phy1520

BIBLIOGRAPHY_PATH := classicthesis_mine
HAVE_OWN_CONTENTS := 1
#HAVE_OWN_TITLEPAGE := 1
HAVE_CUSTOM_DEDICATION := 1
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/Index.tex
MY_CLASSICTHESIS_FRONTBACK_FILES += ../latex/classicthesis_mine/FrontBackmatter/ContentsAndFigures.tex
BOOKTEMPLATE := ../latex/classicthesis_mine/ClassicThesis2.tex
include make.revision
include ../latex/make.bookvars

#ONCEFLAGS := -justonce

# comment this out for online pdf version (uncomment for KDP)
PRINT_VERSION := 1

ifndef PRINT_VERSION
PARAMS += --no-print
endif
ifdef PRINT_VERSION
DISTEXTRA := kdp
endif

SOURCE_DIRS += appendix
FIGURES := ../figures/$(THISBOOK)
SOURCE_DIRS += $(FIGURES)

#GENERATED_SOURCES += matlab.tex 
GENERATED_SOURCES += mathematica.tex 
GENERATED_SOURCES += julia.tex 
GENERATED_SOURCES += backmatter.tex
 
EPS_FILES := $(wildcard $(FIGURES)/*.eps)
PDFS_FROM_EPS := $(subst eps,pdf,$(EPS_FILES))

THISBOOK_DEPS += $(PDFS_FROM_EPS)
#THISBOOK_DEPS += macros_mathematica.sty

DO_SPELL_CHECK := $(shell cat spellcheckem.txt)

include ../latex/make.rules

.PHONY: spellcheck
spellcheck: $(patsubst %.tex,%.sp,$(filter-out $(DONT_SPELL_CHECK),$(DO_SPELL_CHECK)))

%.sp : %.tex
	spellcheck $^
	touch $@

julia.tex : ../julia/METADATA
mathematica.tex : ../mathematica/METADATA

problemSets :: gradQuantumProblemSet1.pdf
problemSets :: gradQuantumProblemSet2.pdf
problemSets :: gradQuantumProblemSet3.pdf
problemSets :: gradQuantumProblemSet4.pdf
problemSets :: gradQuantumProblemSet5.pdf
problemSets :: gradQuantumProblemSet6.pdf

gradQuantumProblemSet1.pdf : gradQuantumProblemSet1Problem1.tex
gradQuantumProblemSet1.pdf : gradQuantumProblemSet1Problem2.tex
gradQuantumProblemSet1.pdf : moreBraKetProblemsP12.tex

gradQuantumProblemSet2.pdf : ../phy1520/gradQuantumProblemSet2Problem1.tex
gradQuantumProblemSet2.pdf : ../phy1520/gradQuantumProblemSet2Problem2.tex
gradQuantumProblemSet2.pdf : ../phy1520/gradQuantumProblemSet2Problem3.tex

gradQuantumProblemSet3.pdf : ../phy1520/gradQuantumProblemSet3Problem1.tex
gradQuantumProblemSet3.pdf : ../phy1520/gradQuantumProblemSet3Problem2.tex
gradQuantumProblemSet3.pdf : ../phy1520/gradQuantumProblemSet3Problem3.tex

gradQuantumProblemSet4.pdf : ../phy1520/gradQuantumProblemSet4Problem1.tex
gradQuantumProblemSet4.pdf : ../phy1520/gradQuantumProblemSet4Problem2.tex
gradQuantumProblemSet4.pdf : ../phy1520/gradQuantumProblemSet4Problem3.tex

gradQuantumProblemSet5.pdf : ../phy1520/gradQuantumProblemSet5Problem1.tex
gradQuantumProblemSet5.pdf : ../phy1520/gradQuantumProblemSet5Problem2.tex
gradQuantumProblemSet5.pdf : ../phy1520/gradQuantumProblemSet5Problem3.tex
gradQuantumProblemSet5.pdf : ../phy1520/gradQuantumProblemSet5Problem4.tex

gradQuantumProblemSet6.pdf : ../phy1520/gradQuantumProblemSet6Problem1.tex
gradQuantumProblemSet6.pdf : ../phy1520/gradQuantumProblemSet6Problem2.tex
gradQuantumProblemSet6.pdf : ../phy1520/gradQuantumProblemSet6Problem3.tex

gradQuantumProblemSet7.pdf : ../phy1520/gradQuantumProblemSet7Problem1.tex
gradQuantumProblemSet7.pdf : ../phy1520/gradQuantumProblemSet7Problem2.tex
gradQuantumProblemSet7.pdf : ../phy1520/gradQuantumProblemSet7Problem3.tex
gradQuantumProblemSet7.pdf : ps7mathematica.tex

gradQuantumProblemSet8.pdf : ../phy1520/gradQuantumProblemSet8Problem1.tex
gradQuantumProblemSet8.pdf : ../phy1520/gradQuantumProblemSet8Problem2.tex
gradQuantumProblemSet8.pdf : ../phy1520/gradQuantumProblemSet8Problem3.tex
gradQuantumProblemSet8.pdf : ../phy1520/gradQuantumProblemSet8Problem4.tex
gradQuantumProblemSet8.pdf : ps8mathematica.tex

ps7mathematica.tex : ../METADATA ../mathematica/METADATA
	(cd .. ; ./METADATA -mathematica -latex -phy1520 -filter phy1520/ps7/ ) > $@

ps8mathematica.tex : ../METADATA ../mathematica/METADATA
	(cd .. ; ./METADATA -mathematica -latex -phy1520 -filter phy1520/ps8/ ) > $@

parameters.sty : ../latex/bin/mkparams
	../latex/bin/mkparams $(PARAMS) > $@

backmatter.tex: ../latex/classicthesis_mine/backmatter2.tex
	rm -f $@
	#ln -s ../latex/classicthesis_mine/backmatter_with_parts.tex backmatter.tex
	ln -s ../latex/classicthesis_mine/backmatter2.tex backmatter.tex

