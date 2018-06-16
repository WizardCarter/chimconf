# chimconf
A fast, lightweight, header-only C++11 library for reading and writing from human-readable configuration files.

https://github.com/WizardCarter/chimconf

With chimconf, you can read/write from configuration files like example.config (provided) using simple code like the following:

```c++
//read from a file

//open the file
chim::config_file file("example.config", chim::config_file::READ);
file.open();
//load the file into the internal buffer
file.load();
//retrieve values
bool potatoes_are_good = file.get_bool("potatoes_are_good");
int num_potatoes = file.get_int("num_potatoes");
std::string fav_actor = file.get_string("favorite actor");
//close the file
file.close();
  
//write to a file
using namespace chim;
//open the file
config_file file("example.config", config_file::WRITE);
file.open();
//add some values to the buffer
file.put_bool("potatoes_are_good", true);
file.put_int("num_potatoes", 15);
file.put_comment("Note: Sweet Potatoes are also good");
file.put_string("favorite actor", "Danny Devito");
//write changes
file.write_changes();
//close the file
file.close();
```  

Note that this is a C++11 library. For it to compile correctly, you MUST enable C++ support on your compiler.

You may use chimconf for any project, as long as you do not claim that you created it and any copies you distribute include the license and this file. Though it's not required, a link back to the github page for this project in your credits would be appretiated. Additionally, if you do something cool with chimconf, please let me know. I'd love to see what you do with it.

FUTURE FEATURES:
- Write empty lines in WRITE mode for readability
- Read/Write vectors to a single variable
