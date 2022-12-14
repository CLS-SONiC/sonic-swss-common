INCLUDES = -I $(top_srcdir)

lib_LTLIBRARIES = libswsscommon.la

EXTRA_DIST = \
    consumer_state_table_pops.lua \
    consumer_table_pops.lua \
    producer_state_table_apply_view.lua \
    table_dump.lua \
    portcounter.lua \
    fdb_flush.lua \
    fdb_flush.v2.lua

EXTRA_CONF_DIST = database_config.json

swssdir = $(datadir)/swss
swsscommondir = /var/run/redis/sonic-db

dist_swss_DATA = $(EXTRA_DIST)
dist_swsscommon_DATA = $(EXTRA_CONF_DIST)

bin_PROGRAMS = swssloglevel

if DEBUG
DBGFLAGS = -ggdb -DDEBUG
else
DBGFLAGS = -g -DNDEBUG
endif

libswsscommon_la_SOURCES = \
    events_common.cpp         \
    events_service.cpp        \
    events.cpp                \
    logger.cpp                \
    redisreply.cpp            \
    configdb.cpp              \
    dbconnector.cpp           \
    dbinterface.cpp           \
    defaultvalueprovider.cpp  \
    sonicv2connector.cpp      \
    table.cpp                 \
    json.cpp                  \
    producertable.cpp         \
    producerstatetable.cpp    \
    rediscommand.cpp          \
    redistran.cpp             \
    redisselect.cpp           \
    select.cpp                \
    selectableevent.cpp       \
    selectabletimer.cpp       \
    consumertable.cpp         \
    consumertablebase.cpp     \
    consumerstatetable.cpp    \
    ipaddress.cpp             \
    ipprefix.cpp              \
    ipaddresses.cpp           \
    macaddress.cpp            \
    netdispatcher.cpp         \
    netlink.cpp               \
    nfnetlink.cpp             \
    notificationconsumer.cpp  \
    notificationproducer.cpp  \
    linkcache.cpp             \
    portmap.cpp               \
    pubsub.cpp                \
    tokenize.cpp              \
    exec.cpp                  \
    saiaclschema.cpp          \
    subscriberstatetable.cpp  \
    timestamp.cpp             \
    warm_restart.cpp          \
    luatable.cpp              \
    countertable.cpp          \
    redisutility.cpp          \
    restart_waiter.cpp        \
    redis_table_waiter.cpp

libswsscommon_la_CXXFLAGS = $(DBGFLAGS) $(AM_CFLAGS) $(CFLAGS_COMMON) $(LIBNL_CFLAGS) $(CODE_COVERAGE_CXXFLAGS)
libswsscommon_la_CPPFLAGS = $(DBGFLAGS) $(AM_CFLAGS) $(CFLAGS_COMMON) $(LIBNL_CPPFLAGS) $(CODE_COVERAGE_CPPFLAGS)
libswsscommon_la_LIBADD = -lpthread $(LIBNL_LIBS) $(CODE_COVERAGE_LIBS) -lzmq -lboost_serialization -luuid -lyang

swssloglevel_SOURCES =  \
	loglevel.cpp        \
	loglevel_util.cpp	

swssloglevel_CXXFLAGS = $(DBGFLAGS) $(AM_CFLAGS) $(CFLAGS_COMMON) $(CODE_COVERAGE_CXXFLAGS)
swssloglevel_CPPFLAGS = $(DBGFLAGS) $(AM_CFLAGS) $(CFLAGS_COMMON) $(CODE_COVERAGE_CPPFLAGS)
swssloglevel_LDADD = libswsscommon.la $(CODE_COVERAGE_LIBS)
