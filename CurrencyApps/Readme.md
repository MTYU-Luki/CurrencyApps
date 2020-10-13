# Currency Apps
This application includes the function of calculating currency exchange rates from dollars to rupiah. One dollar is considered to be worth Rp. 15,000.

## Scope & Functionalities
- Users can enter numbers
- User can touch the calculate button
- Users get "INVALID" info if what is entered is in text

## How Does it works?
Diawali dari method MainWindows pada class `MainWindows.Xaml.cs`, Lengkapnya sebagai berikut;

```csharp
public MainWindow()
        {
            InitializeComponent();
            currency = new CurrencyController();
        }
```


pada private void Button_Hitung_Click yang berapa pada class `MainWindow.xaml.cs` terdapat coding untuk mengatasi human error jika users melakukan kesalahan input. Jadi users jika memasukkan selain angka maka akan mendapatkan hasil **INVALID**, tapi jika users memasukkan angka maka akan diteruskan ke `CurrencyController.cs`.  

```csharp
 private void Button_Hitung_Click(object sender, RoutedEventArgs e)
        {
            var nominalInput = InputTextBox.Text;
            var result = "invalid";
            if (currencyController.isAllowed(nominalInput))
            {
                result = currencyController.usdToIdr(nominalInput);
            }
            resultLabel.Content = result;

        }
```

logika perhitungan terdapat pada class `CurencyController.cs` sebagai berikut cara kerjanya;

```csharp
public string usdToIdr(string nominal)
        {
            var nominalDouble = Convert.ToDouble(nominal);
            var result = nominalDouble * 15000;
            return Convert.ToString(result);
        }
```
# Latihan
1. Review kembali percobaan 1 sampai dengan 3 dengan menjawab pertanyaan-pertanyaan pada latihan tersebut.
2. Mengapa perlu membuat class CurrencyController.cs pada percobaan 4 ?
3. Jelaskan kegunaan method isAllowed pada percobaan 4!
4. Jelaskan secara singkat mengenai Regex pada percobaan 4!
5. Buatlah class diagramnya pada percobaan 4! 


## Jawaban No 1
- **Percobaan 1**
  - jika kita memasukan angka berapapun pada textbox kemudian kita klik button Calculate, maka yang akan keluar adalah sama seperti angka yang kita masukan
- **Percobaan 2**
  - jika kita memasukan sebarang angka pada textbox dan kita klik button Calculate maka angka tersebut akan dikalikan 15000 `(var result = nominalDouble * 15000;)`.
  - jika kita  memasukan sembarang huruf pada textbox maka akan terjadi carsh, karena kita baru membuat fugsi yang bisa meghitung angka.
- **Percobaan 3**
  - jika kita memasukan sebarang angka pada textbox dan kita klik button Calculate maka angka tersebut akan dikalikan 15000 `(var result = nominalDouble * 15000;)`.
  - jika kita memasukan huruf ke text box akan menampilkan kalimat "INVALID".

## Jawaban No 2
- Untuk memisahkan fungsi logika perhitungan dari `CurencyController.cs` dengan logika untuk mengontrol tampilan `Mainwindows.xaml.cs`

## Jawaban No 3
- Untuk megizinkan dari inputtextbox, jika yang diinputkan angka maka akan menjalankan fungsi matematic dan jika yang diinputkan huruf maka akan mengembalikan "INVALID" karena tidak diizinkan.

## Jawaban No 4
- Fungsi Regex adalah mencari suatu pola spesifik dari fungsi `Regex("[^0-9,-]+");`

## Jawaban No 5
