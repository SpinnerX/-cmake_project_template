# Cpp CMake Project
This is a C++ CMake template project. This project will contain starting up code and file structures and cmake modules.


## File Structure

** TemplateProject **
- Contains a file called "Precompiled headers" that you can change the name
- This is used so that we are not constantly recompiling the same headers throughout our project.
- Contains Core.h and Core.cpp in the include and src directories that have startup code.
- Splitting the project into two directories, the "include" and the "src".
- Include directory contains all headers files, and src directory contains all of the implementation files such as *.cpp or .cc, etc.

** Sandbox **
- Will be the client-side folder
- This is will a lot of the client-side programming will be done.
- Such as to involve

** cmake **
- Cmake directory contain other cmake modules.
- These cmake modules will help find specific dependencies and are easier ways to know \
    which third party libraries to utilize. (depending on the project)

