INCLUDE_DIRECTORIES (
	${CMAKE_BINARY_DIR}
	${TBB_INCLUDE_DIR}
)

LINK_DIRECTORIES(
	${PROJECT_BINARY_DIR}/opencog/cogserver/server
	${TBB_INCLUDE_DIR}
	${TBB_LIBRARY_DIRS}
)

LINK_LIBRARIES(
	server
	${ATOMSPACE_LIBRARIES}
	zmq
	tbb
)

ADD_CXXTEST(AtomSpacePublisherModuleUTest)

TARGET_LINK_LIBRARIES(AtomSpacePublisherModuleUTest
	atomspacepublishermodule
)

SET_TESTS_PROPERTIES(AtomSpacePublisherModuleUTest
	PROPERTIES ENVIRONMENT
	"PYTHONPATH=/usr/local/share/opencog/python"
)
