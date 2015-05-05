# libs Makefile
include ../Makefile.common
LIBS+=libstm32.a
CFLAGSlib+=-c

all: libs

libs: $(LIBS)

libstm32.a:
	@echo -n "Building $@ ..."
	@cd $(STMLIB)/CMSIS/Device/ST/STM32F2xx/Source/Templates && \
		$(CC) $(CFLAGSlib) \
			system_stm32f2xx.c
	@cd $(STMLIB)/STM32F2xx_StdPeriph_Driver/src && \
		$(CC) $(CFLAGSlib) \
			-D"assert_param(expr)=((void)0)" \
			-I../../CMSIS/Include \
			-I../../CMSIS/Device/ST/STM32F2xx/Include \
			-I../inc \
			*.c
#	@cd $(STMLIB)/STM32_USB-FS-Device_Driver/src && \
#	$(CC) $(CFLAGSlib) \
#	-D"assert_param(expr)=((void)0)" \
#	-I../../CMSIS/Include \
#	-I../../CMSIS/Device/ST/STM32F10x/Include \
#	-I../inc \
#	*.c
	@$(AR) cr $(LIBDIR)/$@ \
		$(STMLIB)/CMSIS/Device/ST/STM32F2xx/Source/Templates/system_stm32f2xx.o \
		$(STMLIB)/STM32F2xx_StdPeriph_Driver/src/*.o 
	@echo "done."
.PHONY: libs clean tshow

clean:
	rm -f $(STMLIB)/CMSIS/Device/ST/STM32F2xx/Source/Templates/system_stm32f2xx.o
	rm -f $(STMLIB)/STM32F2xx_StdPeriph_Driver/src/*.o
	rm -f $(LIBS)
tshow:
	@echo "######################################################################################################"
	@echo "################# optimize settings: $(InfoTextLib), $(InfoTextSrc)"
	@echo "######################################################################################################"
