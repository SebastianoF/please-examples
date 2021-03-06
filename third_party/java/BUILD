# This says that all targets in this package that don't specify otherwise
# will be visible to the whole repo.
# This is often useful for third-party packages like this where we expect
# anyone to use them.
package(default_visibility = ['PUBLIC'])

# maven_jar fetches a single .jar file from Maven.
# Note that it doesn't fetch dependencies, we have to specify them explicitly.
maven_jar(
    name = 'protobuf',
    id = 'com.google.protobuf:protobuf-java:3.4.0',
    # Please can hash-verify downloaded artifacts so you're sure you get
    # what you're expecting. This is particularly useful when fetching things
    # from external repositories.
    hash = 'ea1115a7983c2c23b7d90ccef4a83675f4e3df9c',
    sources = False,  # Not available
)

maven_jar(
    name = 'protobuf-java-util',
    id = 'com.google.protobuf:protobuf-java-util:3.4.0',
    hash = '65e518040d4f932b6dbd7a255f74509cac50066e',
    sources = False,
    deps = [
        ':protobuf',
    ],
)

maven_jar(
    name = 'protoc-gen-grpc-java',
    id = 'io.grpc:protoc-gen-grpc-java:1.6.1',
    binary = True,
    hash = 'c1da85124ac0f72659614a9789f42c63f8e5a8fe',
)

# maven_jars fetches a library and its transitive dependencies from Maven.
# A little fiddling is needed here to handle dependencies that have no
# sources available.
# TODO(pebers): Revisit this once issue #120 is resolved.
maven_jars(
    name = 'grpc-all',
    id = 'io.grpc:grpc-all:1.6.1',
    exclude = [
        'protobuf-java',
        'protobuf-java-util',
    ],
    deps = [
        ':protobuf-java-util',
    ],
)

maven_jar(
    name = 'junit',
    id = 'junit:junit:4.12',
    hash = 'sha1: a791201ac8a3d2a251045a52e264de01343ad2df',
    # This means that this library will only be able to be used by tests
    # (go_test rules and so forth). Obviously we'd be unlikely to use
    # junit in production code, but it can be useful to enforce these
    # things so nobody introduces such a dependency by accident.
    test_only = True,
)

maven_jar(
    name = 'mockito',
    id = 'org.mockito:mockito-all:1.10.19',
    hash = 'e93ceaea4cf704350fbb2a450ddbb7b4e3e062e3',
    test_only = True,
)

maven_jar(
    name = 'args4j',
    id = 'args4j:args4j:2.32',
    hash = 'a08fb9a7217df438872f27936058f594eab29396',
)
