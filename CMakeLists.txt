CMAKE_MINIMUM_REQUIRED (VERSION 2.8.7)
PROJECT (cryptopp)

#STATIC | SHARED
OPTION(COMPILE_CRYPTOPP_LIB_SHARED    "Build cryptopp as a shared lib (setting this to OFF will compile statically)" ON)
#OPTION(CRYPTOPP_BUILD_TESTS  "Build cryptopp tests" ON)
OPTION(CRYPTOPP_DISABLE_ASM  "Disable ASM" ON)
OPTION(CRYPTOPP_DISABLE_SSSE3 "Disable SSSE3" ON)
OPTION(CRYPTOPP_DISABLE_AESNI "Disable AES-NI" ON)

SET (cryptopp_SOURCES
	src/3way.cpp
	src/adler32.cpp
	src/algebra.cpp
	src/algparam.cpp
	src/arc4.cpp
	src/asn.cpp
	src/authenc.cpp
	src/base32.cpp
	src/base64.cpp
	src/basecode.cpp
	src/bfinit.cpp
	src/blowfish.cpp
	src/blumshub.cpp
	src/camellia.cpp
	src/cast.cpp
	src/casts.cpp
	src/cbcmac.cpp
	src/ccm.cpp
	src/channels.cpp
	src/cmac.cpp
	src/cpu.cpp
	src/crc.cpp
	src/cryptlib_bds.cpp
	src/cryptlib.cpp
	src/default.cpp
	src/des.cpp
	src/dessp.cpp
	src/dh2.cpp
	src/dh.cpp
	src/dll.cpp
	src/dsa.cpp
	src/eax.cpp
	src/ec2n.cpp
	src/eccrypto.cpp
	src/ecp.cpp
	src/elgamal.cpp
	src/emsa2.cpp
	src/eprecomp.cpp
	src/esign.cpp
	src/files.cpp
	src/filters.cpp
	src/fips140.cpp
	src/fipstest.cpp
	src/gcm.cpp
	src/gf2_32.cpp
	src/gf256.cpp
	src/gf2n.cpp
	src/gfpcrypt.cpp
	src/gost.cpp
	src/gzip.cpp
	src/hex.cpp
	src/hmac.cpp
	src/hrtimer.cpp
	src/ida.cpp
	src/idea.cpp
	src/integer.cpp
	src/iterhash.cpp
	src/luc.cpp
	src/mars.cpp
	src/marss.cpp
	src/md2.cpp
	src/md4.cpp
	src/md5.cpp
	src/misc.cpp
	src/modes.cpp
	src/mqueue.cpp
	src/mqv.cpp
	src/nbtheory.cpp
	src/network.cpp
	src/oaep.cpp
	src/osrng.cpp
	src/panama.cpp
	src/pch.cpp
	src/pkcspad.cpp
	src/polynomi.cpp
	src/pssr.cpp
	src/pubkey.cpp
	src/queue.cpp
	src/rabin.cpp
	src/randpool.cpp
	src/rc2.cpp
	src/rc5.cpp
	src/rc6.cpp
	src/rdtables.cpp
	src/rijndael.cpp
	src/ripemd.cpp
	src/rng.cpp
	src/rsa.cpp
	src/rw.cpp
	src/safer.cpp
	src/salsa.cpp
	src/seal.cpp
	src/seed.cpp
	src/serpent.cpp
	src/sha3.cpp
	src/shacal2.cpp
	src/sha.cpp
	src/sharkbox.cpp
	src/shark.cpp
	src/simple.cpp
	src/skipjack.cpp
	src/socketft.cpp
	src/sosemanuk.cpp
	src/square.cpp
	src/squaretb.cpp
	src/strciphr.cpp
	src/tea.cpp
	src/tftables.cpp
	src/tiger.cpp
	src/tigertab.cpp
	src/trdlocal.cpp
	src/ttmac.cpp
	src/twofish.cpp
	src/vmac.cpp
	src/wait.cpp
	src/wake.cpp
	src/whrlpool.cpp
	src/winpipes.cpp
	src/xtr.cpp
	src/xtrcrypt.cpp
	src/zdeflate.cpp
	src/zinflate.cpp
	src/zlib.cpp
)

SET (cryptopp_HEADERS
	include/3way.h
	include/adler32.h
	include/aes.h
	include/algebra.h
	include/algparam.h
	include/arc4.h
	include/argnames.h
	include/asn.h
	include/authenc.h
	include/base32.h
	include/base64.h
	include/basecode.h
	include/bench.h
	include/blowfish.h
	include/blumshub.h
	include/camellia.h
	include/cast.h
	include/cbcmac.h
	include/ccm.h
	include/channels.h
	include/cmac.h
	include/config.h
	include/cpu.h
	include/crc.h
	include/cryptlib.h
	include/default.h
	include/des.h
	include/dh2.h
	include/dh.h
	include/dll.h
	include/dmac.h
	include/dsa.h
	include/eax.h
	include/ec2n.h
	include/eccrypto.h
	include/ecp.h
	include/elgamal.h
	include/emsa2.h
	include/eprecomp.h
	include/esign.h
	include/factory.h
	include/files.h
	include/filters.h
	include/fips140.h
	include/fltrimpl.h
	include/gcm.h
	include/gf2_32.h
	include/gf256.h
	include/gf2n.h
	include/gfpcrypt.h
	include/gost.h
	include/gzip.h
	include/hex.h
	include/hmac.h
	include/hrtimer.h
	include/ida.h
	include/idea.h
	include/integer.h
	include/iterhash.h
	include/lubyrack.h
	include/luc.h
	include/mars.h
	include/md2.h
	include/md4.h
	include/md5.h
	include/mdc.h
	include/misc.h
	include/modarith.h
	include/modes.h
	include/modexppc.h
	include/mqueue.h
	include/mqv.h
	include/nbtheory.h
	include/network.h
	include/nr.h
	include/oaep.h
	include/oids.h
	include/osrng.h
	include/panama.h
	include/pch.h
	include/pkcspad.h
	include/polynomi.h
	include/pssr.h
	include/pubkey.h
	include/pwdbased.h
	include/queue.h
	include/rabin.h
	include/randpool.h
	include/rc2.h
	include/rc5.h
	include/rc6.h
	include/resource.h
	include/rijndael.h
	include/ripemd.h
	include/rng.h
	include/rsa.h
	include/rw.h
	include/safer.h
	include/salsa.h
	include/seal.h
	include/secblock.h
	include/seckey.h
	include/seed.h
	include/serpent.h
	include/serpentp.h
	include/sha3.h
	include/shacal2.h
	include/sha.h
	include/shark.h
	include/simple.h
	include/skipjack.h
	include/smartptr.h
	include/socketft.h
	include/sosemanuk.h
	include/square.h
	include/stdcpp.h
	include/strciphr.h
	include/tea.h
	include/tiger.h
	include/trdlocal.h
	include/trunhash.h
	include/ttmac.h
	include/twofish.h
	include/validate.h
	include/vmac.h
	include/wait.h
	include/wake.h
	include/whrlpool.h
	include/winpipes.h
	include/words.h
	include/xtrcrypt.h
	include/xtr.h
	include/zdeflate.h
	include/zinflate.h
	include/zlib.h
)

INCLUDE_DIRECTORIES (${CMAKE_CURRENT_SOURCE_DIR}/include/)
INCLUDE_DIRECTORIES (${CMAKE_CURRENT_SOURCE_DIR}/src/)

# Set flags
IF (CRYPTOPP_DISABLE_ASM)
	ADD_DEFINITIONS (-DCRYPTOPP_DISABLE_ASM)
ENDIF ()
IF (CRYPTOPP_DISABLE_SSSE3)
	ADD_DEFINITIONS (-DCRYPTOPP_DISABLE_SSSE3)
ENDIF ()
IF (CRYPTOPP_DISABLE_AESNI)
	ADD_DEFINITIONS (-DCRYPTOPP_DISABLE_AESNI)
ENDIF ()

IF(COMPILE_LIB_SHARED)
	ADD_LIBRARY (cryptopp
    	SHARED
    	${cryptopp_SOURCES}
    	${cryptopp_HEADERS}
    )
ELSE(COMPILE_LIB_SHARED)
	ADD_LIBRARY (cryptopp
    	STATIC
    	${cryptopp_SOURCES}
    	${cryptopp_HEADERS}
    )
ENDIF(COMPILE_LIB_SHARED)


set_target_properties(cryptopp
    PROPERTIES
    ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/"
    LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/"
    RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/")


IF (MSVC)
	target_link_libraries(cryptopp ws2_32)
ENDIF ()

#Disabled testing because I dont need it
#You can re-enable it but some file paths will be broken
#IF (CRYPTOPP_BUILD_TESTS)
#	ENABLE_TESTING ()
#	# Generate your adhoc.cpp.proto
#	SET (cryptopp_TEST_SOURCES
#		bench.cpp
#		bench2.cpp
#		test.cpp
#		validat1.cpp
#		validat2.cpp
#		validat3.cpp
#		datatest.cpp
#		regtest.cpp
#		fipsalgt.cpp
#		dlltest.cpp)
#	ADD_CUSTOM_COMMAND (
#		OUTPUT adhoc.cpp
#		COMMAND ${CMAKE_COMMAND} -E copy ${CMAKE_CURRENT_SOURCE_DIR}/adhoc.cpp.proto ${CMAKE_CURRENT_BINARY_DIR}/adhoc.cpp
#	)
#	LIST (APPEND cryptopp_TEST_SOURCES
#		adhoc.cpp
#	)
#	ADD_EXECUTABLE (cryptest
#		${cryptopp_TEST_SOURCES}
#	)
#	TARGET_LINK_LIBRARIES (cryptest
#		cryptopp)
#
#	set_target_properties(cryptopp
#            PROPERTIES
#            ARCHIVE_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/"
#            LIBRARY_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/"
#            RUNTIME_OUTPUT_DIRECTORY "${CMAKE_SOURCE_DIR}/build/")
#
#	# Run validation tests
#	ADD_TEST (NAME cryptopp_validation_tests
#		COMMAND ${CMAKE_COMMAND} -E chdir ${CMAKE_CURRENT_SOURCE_DIR} $<TARGET_FILE:cryptest> v)
#	# Run test scripts
#	ADD_TEST (NAME cryptopp_test_scripts
#		COMMAND ${CMAKE_COMMAND} -E chdir ${CMAKE_CURRENT_SOURCE_DIR} $<TARGET_FILE:cryptest> tv TestVectors/all.txt)
#ENDIF ()

