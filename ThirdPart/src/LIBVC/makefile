lib=../../../lib/src/LIBVC/lib/libVc.a
Vc=Vc-1.4.2

all:$(lib)

$(lib): makefile Install test_VC.cpp
	make clean;
	./Install $(Vc);
	#make test;

clean:
	rm -r -f $(Vc) ../../../lib/src/LIBVC


OPT=_opt
include $(TRUST_ENV)/make.$(TRUST_ARCH_CC)$(OPT)
include $(TRUST_ENV)/make.all_Includes.TRUST

test: test_VC.cpp
	cp test_VC.cpp $(TRUST_TMP)/build/lib/Vc_build; cd $(TRUST_TMP)/build/lib/Vc_build; \
	$(TRUST_CC) -o $@ $< $(CppFlags) -Wno-error -L$(TRUST_ROOT)/lib/src/LIBVC/lib -lVc -I$(TRUST_ROOT)/lib/src/LIBVC/include || exit -1; pwd; \
	./test && echo "VC Library OK" && rm -rf $(TRUST_TMP)/build/lib/Vc_build && exit 0 || (echo "VC Library KO, we remove .a"; rm $(TRUST_ROOT)/lib/src/LIBVC/lib/libVc.a; exit -1)


