---
title: "İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: efdf4694c1a1b6df2e9531a2bb4c813b536a330e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a>İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma
Tasarım zamanında varsayılan değerlere nesnenin özellikleri belirlenebiliyor olsa da, çalışma zamanında girdiğiniz değerleri nesne bozulduğunda kaybolur. Bir nesnenin veri değerlerini depolamak ve nesne örneği bir sonraki başlatılışında almak sağlar örnekleri arasında kalıcı hale getirmek için seri hale getirme kullanabilirsiniz.  
  
 Bu kılavuzda, basit bir oluşturacak `Loan` nesne ve verileri bir dosyaya kalır. Nesne yeniden oluşturduğunuzda, ardından dosyadan verileri alır.  
  
> [!IMPORTANT]
>  Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulama gerekir `Create` klasörü için izni. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha az izni. Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` (yerine bir klasör izinlerini Oluştur) tek bir dosya izni. Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.  
  
> [!IMPORTANT]
>  Bu örnek verileri bir ikili biçimi dosyasında depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas verileri için kullanılmamalıdır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklatın. **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma  
 İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir test uygulaması.  
  
### <a name="to-create-the-loan-class"></a>Kredi sınıfı oluşturmak için  
  
1.  Yeni bir sınıf kitaplığı projesi oluşturun ve "LoanClass" olarak adlandırın. Daha fazla bilgi için bkz: [oluşturma çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).  
  
2.  İçinde **Çözüm Gezgini**, Class1 dosya için kısayol menüsünü açın ve seçin **yeniden adlandırma**. Dosyayı Yeniden Adlandır `Loan` ve ENTER tuşuna basın. Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `Loan`.  
  
3.  Aşağıdaki genel üyeler sınıfına ekleyin:  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 Ayrıca kullanan basit bir uygulama oluşturmanız gerekir `Loan` sınıfı.  
  
### <a name="to-create-a-test-application"></a>Bir test uygulaması oluşturmak için  
  
1.  Çözümünüz için bir Windows Forms uygulaması projesi eklemek için **dosya** menüsünde seçin **Ekle**, **yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda, seçin **Windows Forms uygulaması**ve girin `LoanApp` proje ve ardından adı olarak **Tamam** iletişim kutusunu kapatmak için .  
  
3.  İçinde **Çözüm Gezgini**, LoanApp projesini seçin.  
  
4.  Üzerinde **proje** menüsünde seçin **başlangıç projesi olarak ayarla**.  
  
5.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.  
  
6.  İçinde **Başvuru Ekle** iletişim kutusunda, seçin **projeleri** sekmesini ve ardından LoanClass projesini seçin.  
  
7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
8.  Tasarımcıda dört eklemek <xref:System.Windows.Forms.TextBox> formu denetimleri.  
  
9. Kod Düzenleyicisi'ne şu kodu ekleyin:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. Bir olay işleyicisi ekleme `PropertyChanged` aşağıdaki kodu kullanarak formuna olay:  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 Bu noktada, derleme ve uygulamayı çalıştırın. Gelen varsayılan değerleri Not `Loan` sınıfı metin kutularında görünür. Faiz oranını değeri, 7.1 için 7.5 değiştirin ve sonra uygulamayı kapatın ve yeniden çalıştırın çalıştığınızda — değer 7.5 varsayılan olarak döner.  
  
 Gerçek Hayatta, faiz oranları uygulama her çalıştırıldığında düzenli aralıklarla, ancak mutlaka değiştirin. Kullanıcının uygulamanın çalıştığı her zaman faiz oranını güncelleştirme yapmak yerine, uygulama örnekleri arasında en son faiz oranını korumak daha iyi olur. Sonraki adımda, yalnızca serileştirme kredisi sınıfına ekleyerek bunu.  
  
## <a name="using-serialization-to-persist-the-object"></a>Nesne kalıcı hale getirmek için seri hale getirme kullanma  
 Kredi sınıfı için değerleri kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.  
  
### <a name="to-mark-a-class-as-serializable"></a>Bir sınıf seri hale getirilebilir olarak işaretlemek için  
  
-   Kredi sınıfı için sınıf bildirimi aşağıdaki gibi değiştirin:  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 `Serializable` Özniteliği derleyici sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir. Çünkü `PropertyChanged` olayı, bir Windows Form nesnesi tarafından işlenir, seri hale getirilemez. `NonSerialized` Özniteliği, kalıcı sınıf üyeleri işaretlemek için kullanılabilir.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Seri hale üyesi engellemek için  
  
-   Bildirimi değiştirme `PropertyChanged` şekilde olay:  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 Sonraki adım, LoanApp uygulamaya serileştirme kod eklemektir. Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanacağınız <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanları. Tam olarak nitelenmiş adlar yazma zorunluluğunu ortadan kaldırmak için gerekli sınıf kitaplıkları başvurular ekleyebilirsiniz.  
  
### <a name="to-add-references-to-namespaces"></a>Ad alanlarına başvurular eklemek için  
  
-   Aşağıdaki deyimleri en üst kısmına ekleyin `Form1` sınıfı:  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     Bu durumda, nesneyi bir ikili dosya biçiminde kaydetmek için bir ikili biçimlendirici kullanıyor.  
  
 Sonraki adım, nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1.  Bir sabit serileştirilmiş verilerinin dosya adı için sınıfına ekleyin.  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  Kodda değişiklik `Form1_Load` olay yordamı şekilde:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     Dosyanın var olduğunu ilk denetlemelisiniz unutmayın. Varsa oluşturma bir <xref:System.IO.Stream> ikili dosya okuma için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirmek için sınıf. Ayrıca akış türünden kredisi nesne türüne dönüştürmeniz gerekir.  
  
 Metin kutuları için girilen verileri kaydetmek için kod sonraki eklemelisiniz `Loan` ve ardından, bir dosyaya sınıfı seri gerekir.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Verileri Kaydet ve sınıf seri hale getirmek için  
  
-   Aşağıdaki kodu ekleyin `Form1_FormClosing` olay yordamı:  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 Bu noktada, yeniden yapılandırabilir ve uygulamayı çalıştırın. Başlangıçta, varsayılan değerleri metin kutularında görünür. Dördüncü metin kutusuna bir ad girin ve değerleri değiştirmek deneyin. Uygulamayı kapatın ve yeniden çalıştırın. Yeni değerler şimdi metin kutularına göründüğüne dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seri hale getirme (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)
