---
title: (Visual Basic) Visual Studio'da bir nesneyi kalıcı kılma
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 25951327028b9b8ced8506b3ba6395e8c9e6abed
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483690"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio'da (Visual Basic) nesneyi kalıcı kılma
Nesnesi yok edildiğinde, bir nesnenin özellikler varsayılan değerlere tasarım zamanında olsa da, çalışma zamanında girilen değerleri kaybedilir. Seri hale getirme, bir nesnenin veri değerleri depolamak ve bunları nesnesi örneği başlatıldığında almanıza imkan tanıyan örnekler arasında kalıcı hale getirmek için kullanabilirsiniz.  
  
> [!NOTE]
>  Visual Basic'te, bir ad veya sayı gibi basit verilerini depolamak için kullanabileceğiniz `My.Settings` nesne. Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 Bu kılavuzda, basit bir oluşturacağınız `Loan` nesne ve verileri bir dosyaya kalıcı. Nesne yeniden oluşturduğunuzda dosyadan verileri ardından alır.  
  
> [!IMPORTANT]
>  Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulama gerekir `Create` klasörüne izni. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha düşük bir izni. Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` izinleri tek bir dosya (yerine bir klasörün izinlerini oluşturma). Ayrıca, kök klasöre veya Program dosyaları klasörüne kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.  
  
> [!IMPORTANT]
>  Bu örnek, bir ikili verileri depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma  
 İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir test uygulaması.  
  
### <a name="to-create-the-loan-class"></a>Kredi sınıfı oluşturmak için  
  
1.  Yeni bir sınıf kitaplığı projesi oluşturun ve "LoanClass" olarak adlandırın. Daha fazla bilgi için [projeler ve çözümler oluşturma](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2.  İçinde **Çözüm Gezgini**Class1 dosyası için kısayol menüsünü açın ve seçin **Yeniden Adlandır**. Dosyayı Yeniden Adlandır `Loan` ve ENTER tuşuna basın. Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `Loan`.  
  
3.  Sınıfına aşağıdaki genel üyeleri Ekle:  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 Ayrıca kullanan basit bir uygulama oluşturmanız gerekir `Loan` sınıfı.  
  
### <a name="to-create-a-test-application"></a>Bir test uygulaması oluşturmak için  
  
1.  Çözümünüz için bir Windows Forms uygulaması projesi eklemek için **dosya** menüsünde seçin **Ekle**,**yeni proje**.  
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda **Windows Forms uygulaması**girin `LoanApp` 'a tıklayın ve proje adı olarak **Tamam** iletişim kutusunu kapatmak için .  
  
3.  İçinde **Çözüm Gezgini**, LoanApp projesini seçin.  
  
4.  Üzerinde **proje** menüsünde seçin **başlangıç projesi olarak ayarla**.  
  
5.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.  
  
6.  İçinde **Başvuru Ekle** iletişim kutusunda **projeleri** sekmesini ve ardından LoanClass projesini seçin.  
  
7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
8.  Tasarımcıda dört ekleme <xref:System.Windows.Forms.TextBox> formu için denetimler.  
  
9. Kod Düzenleyicisi'ne şu kodu ekleyin:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. İçin bir olay işleyicisi ekleme `PropertyChanged` olay formuna aşağıdaki kodu kullanarak:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 Bu noktada, oluşturun ve uygulamayı çalıştırın. Varsayılan değerlerini Not `Loan` sınıfı metin kutularında görüntülenir. Faiz oranını değeri, 7.1 için 7.5 değiştirin ve ardından uygulamayı kapatın ve yeniden çalıştırın deneyin — değeri 7.5 varsayılana.  
  
 Gerçek dünyada, uygulama her çalıştırıldığında düzenli aralıklarla ancak bu şart değildir faiz oranları değiştirin. Kullanıcının uygulamanın çalıştığı her saat faiz oranını güncelleştirme yapmak yerine, uygulama örnekleri arasında en son faiz oranını korumak iyidir. Sonraki adımda, yalnızca kredi sınıfı seri hale getirme ekleyerek bunu.  
  
## <a name="using-serialization-to-persist-the-object"></a>Nesne kalıcı hale getirmek için serileştirme kullanma  
 Kredi sınıfı değerlerini kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.  
  
### <a name="to-mark-a-class-as-serializable"></a>Bir sınıf seri hale getirilebilir olarak işaretlemek için  
  
-   Kredi sınıfı için sınıf bildirimi aşağıdaki gibi değiştirin:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Öznitelik derleyiciye sınıftaki her şeyi bir dosyaya kalıcı olmasını. Çünkü `PropertyChanged` olayı, bir Windows Form nesnesi tarafından işlenir, seri hale getirilemiyor. `NonSerialized` Özniteliği, kalıcı sınıf üyeleri işaretlemek için kullanılabilir.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Serileştirilmekte olan bir üye önlemek için  
  
-   Değişiklik bildirimi `PropertyChanged` aşağıdaki gibi olay:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Sonraki adım, LoanApp uygulamaya serileştirme kodu eklemektir. Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanacağınız <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanları. Tam nitelikli adlarını yazarak önlemek için gerekli sınıf kitaplıklarına başvurular ekleyebilirsiniz.  
  
### <a name="to-add-references-to-namespaces"></a>Ad alanlarına başvurular eklemek için  
  
-   Üstüne aşağıdaki deyimleri ekleyin `Form1` sınıfı:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Bu durumda, ikili biçimde nesneyi kaydetmek için bir ikili biçimlendirici kullanıyor.  
  
 Sonraki adım, bir nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1.  Bir sabit seri hale getirilmiş veri dosya adı için bir sınıf ekleyin.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Kodda değişiklik `Form1_Load` aşağıdaki gibi olay yordam:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     Dosyanın var olduğundan ilk denetlemelidir unutmayın. Yoksa, oluşturun bir <xref:System.IO.Stream> ikili dosyayı okumak için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosya çevirmek için sınıf. Ayrıca akış türünden kredi nesne türüne dönüştürmek gerekir.  
  
 Ardından metin kutusuna girilen verileri kaydetmek için kod ekleyin `Loan` sınıfı ve ardından sınıfı bir dosyaya serileştirmek gerekir.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Verileri Kaydet ve sınıfı serileştirmek için  
  
-   Aşağıdaki kodu ekleyin `Form1_FormClosing` olay yordam:  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 Bu noktada, yeniden derleyebilir ve uygulamayı çalıştırın. Başlangıçta, varsayılan değerleri metin kutularında görüntülenir. Deneyin değerleri değiştirmek ve dördüncü metin kutusuna bir ad girin. Uygulamayı kapatın ve yeniden çalıştırın. Yeni değerler artık metin kutularına göründüğüne dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seri hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
