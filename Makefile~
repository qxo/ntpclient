# A long time ago, far, far away, under Solaris, you needed to
#    CFLAGS += -xO2 -Xc
#    LDLIBS += -lnsl -lsocket
# To cross-compile
#    CC = arm-linux-gcc
# To check for lint
#    CFLAGS += -Wpointer-arith -Wcast-align -Wcast-qual -Wshadow -Wundef \
#     -Waggregate-return -Wnested-externs -Winline -Wwrite-strings -Wstrict-prototypes

# This is old-school networking code, making the traditional cast between
# struct sockaddr* and struct sockaddr_in*.  Thus a modern gcc needs:
CFLAGS += -fno-strict-aliasing
CC = /usr/local/opt/crosstool/arm-linux/gcc-3.3.4-glibc-2.3.2/arm-linux/bin/gcc
CFLAGS += -std=c89
CFLAGS += -W -Wall
CFLAGS += -O2
# CFLAGS += -DPRECISION_SIOCGSTAMP
CFLAGS += -DENABLE_DEBUG
CFLAGS += -DENABLE_REPLAY
# CFLAGS += -DUSE_OBSOLETE_GETTIMEOFDAY

LDFLAGS += -static 

all: ntpclient

test: ntpclient
	./ntpclient -d -r <test.dat

ntpclient: ntpclient.o phaselock.o /usr/local/opt/crosstool/arm-linux/gcc-3.3.4-glibc-2.3.2/arm-linux/lib/libpthread.a /usr/local/opt/crosstool/arm-linux/gcc-3.3.4-glibc-2.3.2/arm-linux/lib/librt.a

ntpclient.o phaselock.o: ntpclient.h

adjtimex: adjtimex.o

clean:
	rm -f ntpclient adjtimex *.o



