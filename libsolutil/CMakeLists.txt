set(sources
	Algorithms.h
	AnsiColorized.h
	Assertions.h
	Common.h
	CommonData.cpp
	CommonData.h
	CommonIO.cpp
	CommonIO.h
	cxx20.h
	DisjointSet.cpp
	DisjointSet.h
	DominatorFinder.h
	Exceptions.cpp
	Exceptions.h
	ErrorCodes.h
	FixedHash.h
	FunctionSelector.h
	IpfsHash.cpp
	IpfsHash.h
	JSON.cpp
	JSON.h
	Keccak256.cpp
	Keccak256.h
	LazyInit.h
	LEB128.h
	Numeric.cpp
	Numeric.h
	picosha2.h
	Profiler.cpp
	Profiler.h
	Result.h
	SetOnce.h
	StackTooDeepString.h
	StringUtils.cpp
	StringUtils.h
	SwarmHash.cpp
	SwarmHash.h
	TemporaryDirectory.cpp
	TemporaryDirectory.h
	UTF8.cpp
	UTF8.h
	vector_ref.h
	Views.h
	Visitor.h
	Whiskers.cpp
	Whiskers.h
)

add_library(solutil ${sources})
target_link_libraries(solutil PUBLIC Boost::boost Boost::filesystem Boost::system range-v3 fmt::fmt-header-only nlohmann_json::nlohmann_json)
target_include_directories(solutil PUBLIC "${PROJECT_SOURCE_DIR}")
add_dependencies(solutil solidity_BuildInfo.h)

if(SOLC_LINK_STATIC)
	target_link_libraries(solutil PUBLIC Threads::Threads)
endif()
