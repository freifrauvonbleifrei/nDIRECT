#PREFIX = Specify the install path

objects= Trans_filter_1x1.o NDIRECT_conv_exe.o  NDIRECT_direct_1x1s1.o \
		NDIRECT_direct_1x1s2.o NDIRECT_conv_thread.o Direct_3x3s1.o Direct_3x3s2.o \
		Direct_7x7s2.o verify.o
		 

all:$(objects)
	$(CXX)  -march=native $(objects) -shared -fPIC -fopenmp -O3 -o libnd.so
	ar rcs libnd.a $(objects)

Trans_filter_1x1.o:Trans_filter_1x1.c 
	$(CXX)  -march=native -c -fPIC Trans_filter_1x1.c -O3 -o Trans_filter_1x1.o
NDIRECT_conv_exe.o:NDIRECT_conv_exe.c 
	$(CXX)  -march=native -c -fPIC NDIRECT_conv_exe.c -O3 -o NDIRECT_conv_exe.o
NDIRECT_direct_1x1s1.o:NDIRECT_direct_1x1s1.c
	$(CXX)  -march=native -c -fPIC -fopenmp NDIRECT_direct_1x1s1.c -O3 -o NDIRECT_direct_1x1s1.o
NDIRECT_direct_1x1s2.o:NDIRECT_direct_1x1s2.c 
	$(CXX)  -march=native -c -fPIC -fopenmp NDIRECT_direct_1x1s2.c -O3 -o NDIRECT_direct_1x1s2.o
NDIRECT_conv_thread.o:NDIRECT_conv_thread.c 
	$(CXX)  -march=native -c -fPIC -fopenmp NDIRECT_conv_thread.c -O3 -o NDIRECT_conv_thread.o
Direct_3x3s1.o:Direct_3x3s1.c 
	$(CXX)  -march=native -c -fPIC -fopenmp Direct_3x3s1.c -O3 -o Direct_3x3s1.o
Direct_3x3s2.o:Direct_3x3s2.c
	$(CXX)  -march=native -c -fPIC -fopenmp Direct_3x3s2.c -O3 -o Direct_3x3s2.o
Direct_7x7s2.o:Direct_7x7s2.c
	$(CXX)  -march=native -c -fPIC -fopenmp Direct_7x7s2.c -O3 -o Direct_7x7s2.o
#Direct_3x3_exe.o:Direct_3x3_exe.c 
#	$(CXX)  -march=native -c -fPIC Direct_3x3_exe.c -O3 -o Direct_3x3_exe.o
verify.o:verify.c 
	$(CXX)  -march=native -c -fPIC verify.c -O3 -o verify.o

install:
		mkdir -p $(PREFIX)/ND
		mkdir -p $(PREFIX)/ND/lib
		cp -f ./libnd.so $(PREFIX)/ND/lib/
		cp -f ./libnd.a $(PREFIX)/ND/lib/
		mkdir -p $(PREFIX)/ND/include
		cp -f ./*.h $(PREFIX)/ND/include/

.PHONY:clean
clean:
	rm -rf $(PREFIX)/ND *.o *.a *.so
