add_library(template_lib SHARED 
            source1.cpp)

target_link_libraries(template_lib ${THIRD_PARTY_LIBS})