add_library(Benchmark
  Benchmark.swift
  BenchmarkClock.swift
  BenchmarkCommand.swift
  BenchmarkFilter.swift
  BenchmarkMain.swift
  BenchmarkReporter.swift
  BenchmarkResult.swift
  BenchmarkRunner.swift
  BenchmarkSetting.swift
  BenchmarkSuite.swift
  MakeTests.swift
  Stats.swift)
# NOTE: workaround for CMake <3.17 which does not propagate the property
set_target_properties(Benchmark PROPERTIES
  INTERFACE_INCLUDE_DIRECTORIES ${CMAKE_Swift_MODULE_DIRECTORY})
target_compile_options(Benchmark PRIVATE
  $<$<BOOL:${BUILD_TESTING}>:-enable-testing>)
target_link_libraries(Benchmark PUBLIC
  dispatch
  swiftDispatch
  ArgumentParser
  Foundation)

_install_target(Benchmark)
set_property(GLOBAL APPEND PROPERTY Benchmark_EXPORTS Benchmark)
