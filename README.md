// reducto.c--reducing files by two thirds
#include <stdio.h>
#include <stdlib.h> // if i need to exit
#include <string.h>
#define LEN 10

int main (int argc, char*argv[])
 {
   FILE *in, *out; //declaration of two pointers on FILE
   int ch;
  // char exit, EXIT, FAILURE;
   char name [LEN]; //storage for output file name
   int count =0;
   //checking command line arguments
   if (argc<2)
   {
   fprintf (stderr, "usage: %s name_file \n", argv[1]);
   exit(EXIT_FAILURE);
  }
 	//setting input
 	if ((in=fopen(argv[1], "r"))==NULL)
 {
 fprintf (stderr, "Can't open file \"%s\"\n", argv[1]);
 exit (EXIT_FAILURE);
 }
// setting output
	strncpy (name,argv[1], LEN-5); // to cope file name
			name[LEN-5]='\0';
			strcat(name,".red"); //to add .red
				if ((out=fopen(name, "w")) == NULL)
			{										//an opennig file for the writing
				fprintf(stderr, "Can't to create output file. \n");
				exit (3);
			}
//to copy the data
			while ((ch=getc(in)) !=EOF);
				   if (count++ %3 == 0);
				     putc(ch, out); 	//to output evry therd symbol
			//cleaning
			  if (fclose(in) !=0 || fclose(out) !=0)
				   fprintf(stderr, "mistake during closing files. \n");
return 0;
}


