CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

set(CMAKE_CXX_VISIBILITY_PRESET hidden)

ADD_LIBRARY(otp otp.cc)

ADD_EXECUTABLE(otp_test otp_test.cc otp.cc)
ADD_TEST(otp_test otp_test)
TARGET_LINK_LIBRARIES(otp_test
    ${GTEST_LIBS_DIR}/libgtest.a
    ${GTEST_LIBS_DIR}/libgtest_main.a
    pthread
)
ADD_DEPENDENCIES(otp_test googletest)

ADD_EXECUTABLE(otp_bench otp_bench.cc otp.cc)
TARGET_LINK_LIBRARIES(otp_bench
    ${GBENCH_LIBS_DIR}/libbenchmark.a
    pthread
)
ADD_DEPENDENCIES(otp_bench googlebenchmark)
