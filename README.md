# using System;
using System.IO;
using System.Linq.Expressions;
using System.Text;

bool checkEqual(char[] caracteres, string mot)
{
    int i = 0;
    foreach (char caractere in caracteres)
    {
        if (mot.Contains(caractere))
            i++;
        else
            break;
    }
    return ( i == caracteres.Length);
}
try
{
    //je recupere le texte de mon fichier dans un tableau de chaine
    string[] dictionnaire = File.ReadAllLines(@"C:\Users\NAVIRE\Desktop\progdotnet\monFichier.txt");
    Console.WriteLine("************CHERCHONS LE MOT************\n\n");
    Console.WriteLine("les mots entres doivent utiliser la virgule comme separateur :\n");
    var mot ="";
    mot = Console.ReadLine();
    string[] mots = mot.Split(","); //insere les differents mots de l'utilisateur separer par la virgule dans un tableau
    
    for (int i = 0; i < mots.Length; i++)
    {
        char[] letters = mots[i].ToCharArray(); //convertir chaque chaine d'entree en tableau de caractere puis comparer aux elements du dictionnaire
        if (checkEqual(letters, dictionnaire[i]))
            Console.WriteLine(mots[i] + " correspond a =>" + dictionnaire[i]);
        else Console.WriteLine(mots[i] + " n'a pas de correspondance");
    }
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}