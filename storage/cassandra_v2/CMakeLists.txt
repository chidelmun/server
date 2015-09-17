# Include Datastax C++ Driver


int main() {
  boost::shared_ptr<char> p(new char(10));
  return 0;
}
" CASSANDRAV2SE_OK)
ENDIF()

SET(cassandra_sources
    ha_cassandra_v2.cc
    ha_cassandra_v2.h
    )

LINK_DIRECTORIES(${LINK_DIR})

IF(CASSANDRAV2SE_OK)
  MYSQL_ADD_PLUGIN(cassandra ${cassandra_sources} STORAGE_ENGINE
    MODULE_ONLY LINK_LIBRARIES thrift COMPONENT cassandrav2-engine)
ENDIF(CASSANDRAV2SE_OK)
