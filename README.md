# CMake-Demo-Build

Сваляте и инсталирате [CMake](https://cmake.org/download/).
Разархивирате репото в папка по избор.
Отваряте файла `CMakeLists.txt` и четете внимателно коментарите.
При променливите `set(...)` си слагате пътя до вашите папки.
Останалите команди са готови да работят с файловете от репото.

**Build без Visual Studio:**
В папката със source файловете отваряте терминал/конзола/powershell. Пишете командата `cmake -B out/build -S .`
Ако горната команда е успешна пишете `cmake --build out/build`
 
`out/build` в първата команда създава директория `out` в която слага директория `build` в която ще се build-ва проекта.
`out/build` във втората команда посочва директорията в която да се build-не.
Ако всичко мине успешно, в `out/build/Debug` трябва да имате `.exe` файл, `.dll` файлове и `assets` папка.
Ако пуснете `.exe` файла ще се пуснете програмата.

**Build с Visual Studio:**
Папката със source файловете я отваряте с Visual Studio. Изчаквате Visual Studio да се усети какво се случва.  От dropdown-a на зелената стрелка (с която обикновено run-вате проектите) избирате `.exe` файла и след това го run-вате. 
Ако всичко мине успешно, в `out/build/Debug` трябва да имате `.exe` файл, `.dll` файлове и `assets` папка.
Ако пуснете `.exe` файла ще се пуснете програмата.
