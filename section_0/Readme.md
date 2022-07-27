# Resources
download and install [Visual Studio](https://visualstudio.microsoft.com/downloads/)

download [SFML](https://www.sfml-dev.org/download.php) and unpack the SFML archive wherever you like but preferably unpack to C:\

# Create a new project
Open Open Visual Studio and click on Create new project, choose Empty project (C++) 

![](https://i.imgur.com/o2HQIQt.jpeg)

Give the name you want, for instance SFML_example

![](https://i.imgur.com/tSN9m83.jpeg)

Now the project is empty, with Ctrl+Shit+A we can make a new file and name it main.cpp

![](https://i.imgur.com/T0FPSzN.jpeg)


# Setup VS
The compiler needs to know where to find the SFML headers (.hpp files), and the linker where to find the SFML libraries (.lib files).
Alt+Enter to enter in the properties
add:
 - The path to the SFML headers (<sfml-install-path>/include) to C/C++ » General » Additional Include Directories

 - The path to the SFML libraries (<sfml-install-path>/lib) to Linker » General » Additional Library Directories

![](https://i.imgur.com/zwu0tff.jpeg)

![](https://i.imgur.com/t0Xnz4M.jpeg)

The next step is to link the application to the SFML libraries (.lib files) that code will need. SFML is made of 5 modules (system, window, graphics, network and audio), and there's one library for each of them.
Libraries must be added in the project's properties, in Linker » Input » Additional Dependencies.

For the moment "sfml-graphics.lib", "sfml-window.lib" and "sfml-system.lib" And add the right Dependencies "freetype.lib", "winmm.lib" and "opengl32.lib"
It is important to link to the libraries that match the configuration: "sfml-xxx-d.lib" for Debug, and "sfml-xxx.lib" for Release.

![Debug](https://i.imgur.com/7TIPYPD.jpeg)

![Release](https://i.imgur.com/2DzxYgL.jpeg)

for last to define the SFML_STATIC macro in the preprocessor options of the project.
![](https://i.imgur.com/dWyNryS.jpeg)

Now VS should be ready to use SFML, you can try with the follow code :
```
#include <SFML/Graphics.hpp>

int main()
{
    sf::RenderWindow window(sf::VideoMode(800, 600), "My window");

    while (window.isOpen()) {
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // clear the window with black color
        window.clear();
        // end the current frame
        window.display();
    }
    return 0;
}
```

in the next sectionyou will understand exactly what this code does.