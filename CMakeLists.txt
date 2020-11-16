# Find zephyr. This also loads Zephyr's build system. 
cmake_minimum_required(VERSION 3.13.1)

# Set Enironment Variables
find_package(Zephyr REQUIRED HINTS $ENV{ZEPHYR_BASE})
project(my_zephyr_app)

# Add your source file to the "app" target. This must come after
# find_package(Zephyr) which defines the target.
target_sources(app PRIVATE src/main.c)
