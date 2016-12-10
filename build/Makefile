# 

CXX = g++
# -Wall -Wextra
CXXFLAGS = -fPIC  -O3 -g -fno-strict-aliasing -arch x86_64 -DNDEBUG -DUSING_MM_COMMAND_API=1
LDFLAGS = -shared
RM = rm -f
TARGET_LIB = mmapi.so

SRCS = StoredCommands.cpp LiveMesh.cpp 
OBJS = $(SRCS:.cpp=.o)

.PHONY: all
all: ${TARGET_LIB}

$(TARGET_LIB): $(OBJS)
	$(CXX) ${LDFLAGS} -o $@ $^

$(SRCS:.cpp=.d): %.d:%.cpp
	$(CXX) $(CXXFLAGS) -MM $< >$@

include $(SRCS:.cpp=.d)

.PHONY: clean
clean:
	-${RM} ${TARGET_LIB} ${OBJS} $(SRCS:.cpp=.d)

