Знайомство з основними механізмами реалізації технології "клієнт-сервер" в ОС Unix, робота з неіменованими каналами

Мета Ознайомити з основними механізмами реалізації новітніх технологій ("клієнт-сервер"), розбір програми роботи з неіменованими каналами.

Завдання Розробити програму що зчитує файл та передає його вміст іншій команді, за допомогою неіменованого каналу.

<a href="https://imgbb.com/"><img src="https://image.ibb.co/nDUj0d/2018_05_18_15_15_26.png" alt="2018_05_18_15_15_26" border="0"></a>

<a href="https://imgbb.com/"><img src="https://image.ibb.co/eDvwDy/2018_05_18_14_49_58.png" alt="2018_05_18_14_49_58" border="0"></a>




#include <stdio.h>
#include <stdlib.h>
        int main(int argc, char *argv[])
        {
        char str[20];
        FILE *file, *pipe_fp;
        file == fopen("file.txt", "r");
        if (file == NULL) {
          perror("fopen");
          exit(1);
        }
        pipe_fp = popen("cat","w");
        if (pipe_fp == NULL) {
          perror("popen");
          exit(1);
        }
        do {
          fgets(str,20,file);
          if (feof(file)) break;
          fputs(str, pipe_fp);
        }
        while (!feof(file));
        fclose(file);
        pclose(pipe_fp);
        return 0;
        }
 
