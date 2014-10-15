lua-static
==========

Lua and lua socket with modifications to be statically compiled. Necessary for executing in ns-3-dce.

For compiling lua (in Ubuntu box):

- Install lua and liblua:
  - sudo apt-get install lua5.1
  - sudo apt-get install liblua5.1-0-dev

- Install loop using luarocks:
  - sudo apt-get install luarocks
  - sudo luarocks install loop

- Generate the pre-load library:
  - In luasocket-2.0.2/src do:
    - precompiler.lua -o luasocketscripts -l "?.lua" socket.lua socket/ftp.lua socket/http.lua socket/smtp.lua socket/tp.lua socket/url.lua mime.lua ltn12.lua

    - preloader.lua -o fullluasocket luasocket.h mime.h luasocketscripts.h
- Compile lua socket:
  - In luasocket-2.0.2/src do:
    - make static
    - cp fullluasocket.h ../../lua-5.1.5/src
    
- Compile lua:
  - In lua-5.1.5/src do:
    - make ns3
    
The executable "lua" obtained has luasocket included
  
  

