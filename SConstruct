import os, subprocess, platform, sys

libs_path = ['/home/sven/coden/cpp/godot/bin']
libs = ['libgodot-cpp.linux.debug.64.a', 'libgodot-cpp.linux.release.64.a']

include_path = [
                '/home/sven/coden/cpp/godot/godot-headers',
                '/home/sven/coden/cpp/godot/include/godot_cpp',
                '/home/sven/coden/cpp/godot/include/godot_cpp/core',
                '/home/sven/coden/cpp/godot/include/godot_cpp/classes',
                '/home/sven/coden/cpp/godot/include/godot_cpp/variant'
]

env = Environment(CPPPATH = include_path)

opts = Variables([],ARGUMENTS)
opts.Add(EnumVariable
            (
                'target','Compilation target', 'release', 
                allowed_values=('debug','release'),
                ignorecase = 2
            )                     
        )

opts.Update(env)

if env['target'] == 'debug':
    env.Append(CCFLAGS = '/W3')
    env.Append(CCFLAGS = '/MDd')
    env.Append(CCFLAGS = '/Zi')
    env.Append(CCFLAGS = '/EHsc')
    env.Append(CCFLAGS = '/D_EBUG')
    env.Append(CCFLAGS = '/FS')

    Mkdir('godot/native')
    env.SharedLibrary(target='godot/native/gdns_lib-D', source=Glob('src/*.cpp'), INCLUDE = include_path, LIBS = libs[0], LIBPATH = libs_path)
    
else:
    env.Append(CCFLAGS = '/W3')
    env.Append(CCFLAGS = '/MD')
    env.Append(CCFLAGS = '/Zi')
    env.Append(CCFLAGS = '/Ox')
    env.Append(CCFLAGS = '/EHsc')
    env.Append(CCFLAGS = '/DNDEBUG')
    env.Append(CCFLAGS = '/FS')

    Mkdir('godot/native')
    env.SharedLibrary(target='godot/native/gdns_lib-R', source=Glob('src/*.cpp'), INCLUDE = include_path, LIBS = libs[1], LIBPATH = libs_path)

