# C# Code


``` C#
using System;
using System.Text;

/*
 *  ## Dezimal zu Binärconverter ##
 *  
 *       Sebastian Welscher
 * 
 *       16.04.2018
 *  
 */

namespace BinaryConvert
{
    public class Dec2Bin
    {
        private static int[] bin = new int[8];
        StringBuilder sb;

        public Dec2Bin()
        {
            sb = new StringBuilder();
        }

        public string Convert2Binary(string dec_number)
        {
            int calc, mod;
            int i = 0;
            if (dec_number.Equals (""))
            {
                return "Bitte Nummer eingeben";
            }
            else
            {
                calc = Convert.ToInt32(dec_number);
            }
            
            string ausgabe;
            Array.Clear(bin, 0, bin.Length);
            sb.Clear();

            if (calc < 0 || calc > 255)
            {
                return "Zahl zu groß";
            }
            else
            {
                do
                {
                    mod = calc % 2;  // prüfe auf Rest
                    calc = calc / 2; // teile durch 2
                    bin[i] = mod;    // schreibe Ergebnis ins Array

                    i++;  // Zähler erhöhen

                } while (calc != 0);

                for (int j = bin.Length - 1; j >= 0; j--)
                {
                    sb.Append(Convert.ToString(bin[j])); // Stringeinzelteile an Stringbuilder übergeben 
                }
                i = 0;
                ausgabe = sb.ToString();  // String aufbauen

                return ausgabe;
            }
        }
    }

 /*
 *  ## Binär zu Dezimalconverter ##
 *  
 *       Sebastian Welscher
 * 
 *       12.05.2018
 *  
 */

    public class Bin2Dec
    {
        private char[] chardata = new char[8];
        private int[] intdata = new int[8];

        public Bin2Dec()
        {
            //Konstruktor
        }

        public string Convert2Dec(string input)
        {
            string output;
            ClearArray(chardata);             //Arrayinhalt löschen
            ClearArray(intdata);
            FillCharArray(input);     //CharArray füllen
            IntoIntArray();           //CharArrayinhalte in IntArrayinhalte konvertieren
            output = ParseArray();             //IntArrayInhalt auf 0 und 1 abfragen
            return output;
        }

        private void ClearArray(Array arr)
        {
            Array.Clear(arr, 0, arr.Length);
        }

        private void FillCharArray(string data)
        {
            chardata = data.ToCharArray();   // String in einzelne Chars aufspalten und in Array speichern
        }

        private void IntoIntArray()
        {
            int dat;
            for(int i = 0;i<chardata.Length; i++)
            {
                dat = (int)char.GetNumericValue(chardata[i]);   // Numerischen Inhalt aus Char abrufen und in int umwandeln
                intdata[i] = dat;                               // Daten in IntArray speichern
            }
        }

        private string ParseArray()
        {
            // To-Do: Größere Zahlen abfangen

            string dat;
            int[] convnumbers = { 128, 64, 32, 16, 8, 4, 2, 1};  // Konvertierungsnummern
            int sum = 0, calc = 0;                           // Hilfsvariablen
            for(int i = 0; i<intdata.Length;i++)
            {
                if (intdata[i] == 1)           // wenn IntArrayeintrag == 1, dann calc die jeweilige Konvertierungsnummer zuweisen
                {
                    calc = convnumbers[i];
                }
                else
                {
                    calc = 0;                   // ansonsten 0 setzten
                }
                sum = sum + calc;  // Konvertierungsmummern zusammenrechnen
            }

            dat = sum.ToString();  // int zu string konvertieren
            return dat;
        }
    }

    /*
     *  ## Dezimal zu Hexadezimalconverter ##
     *  
     *       Sebastian Welscher
     * 
     *       13.05.2018
     *  
     */

    public class Dez2Hexa
    { 
       private int[] hexval;
        public Dez2Hexa()
        {
            //Konstruktor
            hexval = new int[2];
        }
        
        public string Convert2Hex(string input)
        {
            string output;

            output = Calculate(input);  // Funktion Calculate aufrufen

            return output;
        }

        private void ClearArray(Array arr)
        {
            Array.Clear(arr, 0, arr.Length);     
        }

        private string Calculate(string data)
        {
            string dat;
            ClearArray(hexval);
            int calc = 0, mod = 0;  // Hilfsvariablen
            if (data.Equals (""))        
            {
                dat = "Bitte Nummer eingeben";
            }
            else
            {
                calc = Convert.ToInt32(data);
            }
            if(calc < 0 || calc > 255)   // Testen ob Zahl kleiner 0 oder größer 255
            {
                dat = "Zahl zu groß";
            }
            else
            {
                mod = calc % 16;  // Modulo Operation, prüfen auf Rest
                calc = calc / 16;
                hexval[0] = calc;
                hexval[1] = mod;
                dat = Convert.ToString(hexval[0] + hexval[1]);
            }
            return dat;
        }
        private string ParseNumber(int number)  // Nummer überprüfen ob größer 9 und dann jeweils den passenden Buchstaben zuweisen
        {
            string output = "";
            if (number < 10)
            {
                output = Convert.ToString(number);
            }
            else
            {
                switch (number)
                {
                    case 10:
                        {
                            output = "A";
                        }
                        break;
                    case 11:
                        {
                            output = "B";
                        }
                        break;
                    case 12:
                        {
                            output = "C";
                        }
                        break;
                    case 13:
                        {
                            output = "D";
                        }
                        break;
                    case 14:
                        {
                            output = "E";
                        }
                        break;
                    case 15:
                        {
                            output = "F";
                        }
                        break;
                }
            }
            return output;
        }
    }

}
```
