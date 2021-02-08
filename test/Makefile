SRC_FILES = $(wildcard *.cas)
COM_FILES = $(patsubst %.cas,%.com,$(SRC_FILES))

%.com : %.cas
	base=`basename $@ .com`; \
	casl -a $< >$$base.out

test:	$(COM_FILES)
	for i in $(COM_FILES); \
	do \
	  base=`basename $$i .com`; \
	  echo $$base:; \
	  ./test-comet $$base; \
	  echo; \
	done | tee log

	@npass=`grep ' ok ' log | wc -l`; \
	nfail=`grep ' ng ' log | wc -l`; \
	echo "$$npass passed, $$nfail failed"

clean:
	rm -f *.com *.out log

# sla, sra, sll, srl, jumps, call, ret
