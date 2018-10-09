# C-BinaryConverter-dll


A little library for C# Programms to convert from decimal to binary, binary to decimal & decimal to hexadecimal.

To use the library in Visual Studio download the BinaryConverter.dll file, than open your project and go to References > Add Reference in the Project-Explorer and search for the dll file on your computer. 

Then include the library at the start of your xxx.cs file with **using BinaryConvert**;

After that, you can use the classes as usual


      public partial class Form1 : Form
    {
        Dec2Bin dec2Bin;
        Bin2Dec bin2dec;
        Dez2Hexa dez2hexa;

        public Form1()
        {
            InitializeComponent();
            dec2Bin = new Dec2Bin();
            bin2dec = new Bin2Dec();
            dez2hexa = new Dez2Hexa();
        }

        private void TestButton_Click(object sender, EventArgs e)
        {
            ergBox.Text = dec2Bin.Convert2Binary(inputText.Text);
            testBox.Text = bin2dec.Convert2Dec(ergBox.Text);
            hexaBox.Text = dez2hexa.Convert2Hex(inputText.Text);
           
        }

       
    }
