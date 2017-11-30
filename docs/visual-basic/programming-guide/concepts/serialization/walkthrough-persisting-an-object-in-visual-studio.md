---
title: "Visual Studio (Visual Basic) bir nesneyi kalıcı kılma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 838038fd873c3a841fd83d30df1c7b3e27fe697f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio (Visual Basic) bir nesneyi kalıcı kılma
Tasarım zamanında varsayılan değerlere nesnenin özellikleri belirlenebiliyor olsa da, çalışma zamanında girdiğiniz değerleri nesne bozulduğunda kaybolur. Bir nesnenin veri değerlerini depolamak ve nesne örneği bir sonraki başlatılışında almak sağlar örnekleri arasında kalıcı hale getirmek için seri hale getirme kullanabilirsiniz.  
  
> [!NOTE]
>  Visual Basic'te bir adı veya numarası gibi basit veri depolamak için kullanabileceğiniz `My.Settings` nesnesi. Daha fazla bilgi için bkz: [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 Bu kılavuzda, basit bir oluşturacak `Loan` nesne ve verileri bir dosyaya kalır. Nesne yeniden oluşturduğunuzda, ardından dosyadan verileri alır.  
  
> [!IMPORTANT]
>  Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur. Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulama gerekir `Create` klasörü için izni. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha az izni. Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` (yerine bir klasör izinlerini Oluştur) tek bir dosya izni. Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.  
  
> [!IMPORTANT]
>  Bu örnek, bir ikili verileri depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas verileri için kullanılmamalıdır.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tıklatın. **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma  
 İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir test uygulaması.  
  
### <a name="to-create-the-loan-class"></a>Kredi sınıfı oluşturmak için  
  
1.  Yeni bir sınıf kitaplığı projesi oluşturun ve "LoanClass" olarak adlandırın. Daha fazla bilgi için bkz: [oluşturma çözümler ve projeler](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2.  İçinde **Çözüm Gezgini**, Class1 dosya için kısayol menüsünü açın ve seçin **yeniden adlandırma**. Dosyayı Yeniden Adlandır `Loan` ve ENTER tuşuna basın. Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `Loan`.  
  
3.  Aşağıdaki genel üyeler sınıfına ekleyin:  
  
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
  
2.  İçinde **Yeni Proje Ekle** iletişim kutusunda, seçin **Windows Forms uygulaması**ve girin `LoanApp` proje ve ardından adı olarak **Tamam** iletişim kutusunu kapatmak için .  
  
3.  İçinde **Çözüm Gezgini**, LoanApp projesini seçin.  
  
4.  Üzerinde **proje** menüsünde seçin **başlangıç projesi olarak ayarla**.  
  
5.  Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.  
  
6.  İçinde **Başvuru Ekle** iletişim kutusunda, seçin **projeleri** sekmesini ve ardından LoanClass projesini seçin.  
  
7.  İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
8.  Tasarımcıda dört eklemek <xref:System.Windows.Forms.TextBox> formu denetimleri.  
  
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
  
10. Bir olay işleyicisi ekleme `PropertyChanged` aşağıdaki kodu kullanarak formuna olay:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 Bu noktada, derleme ve uygulamayı çalıştırın. Gelen varsayılan değerleri Not `Loan` sınıfı metin kutularında görünür. Faiz oranını değeri, 7.1 için 7.5 değiştirin ve sonra uygulamayı kapatın ve yeniden çalıştırın çalıştığınızda — değer 7.5 varsayılan olarak döner.  
  
 Gerçek Hayatta, faiz oranları uygulama her çalıştırıldığında düzenli aralıklarla, ancak mutlaka değiştirin. Kullanıcının uygulamanın çalıştığı her zaman faiz oranını güncelleştirme yapmak yerine, uygulama örnekleri arasında en son faiz oranını korumak daha iyi olur. Sonraki adımda, yalnızca serileştirme kredisi sınıfına ekleyerek bunu.  
  
## <a name="using-serialization-to-persist-the-object"></a>Nesne kalıcı hale getirmek için seri hale getirme kullanma  
 Kredi sınıfı için değerleri kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.  
  
### <a name="to-mark-a-class-as-serializable"></a>Bir sınıf seri hale getirilebilir olarak işaretlemek için  
  
-   Kredi sınıfı için sınıf bildirimi aşağıdaki gibi değiştirin:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Özniteliği derleyici sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir. Çünkü `PropertyChanged` olayı, bir Windows Form nesnesi tarafından işlenir, seri hale getirilemez. `NonSerialized` Özniteliği, kalıcı sınıf üyeleri işaretlemek için kullanılabilir.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Seri hale üyesi engellemek için  
  
-   Bildirimi değiştirme `PropertyChanged` şekilde olay:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Sonraki adım, LoanApp uygulamaya serileştirme kod eklemektir. Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanacağınız <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanları. Tam olarak nitelenmiş adlar yazma zorunluluğunu ortadan kaldırmak için gerekli sınıf kitaplıkları başvurular ekleyebilirsiniz.  
  
### <a name="to-add-references-to-namespaces"></a>Ad alanlarına başvurular eklemek için  
  
-   Aşağıdaki deyimleri en üst kısmına ekleyin `Form1` sınıfı:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Bu durumda, nesneyi bir ikili dosya biçiminde kaydetmek için bir ikili biçimlendirici kullanıyor.  
  
 Sonraki adım, nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1.  Bir sabit serileştirilmiş verilerinin dosya adı için sınıfına ekleyin.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Kodda değişiklik `Form1_Load` olay yordamı şekilde:  
  
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
  
     Dosyanın var olduğunu ilk denetlemelisiniz unutmayın. Varsa oluşturma bir <xref:System.IO.Stream> ikili dosya okuma için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirmek için sınıf. Ayrıca akış türünden kredisi nesne türüne dönüştürmeniz gerekir.  
  
 Metin kutuları için girilen verileri kaydetmek için kod sonraki eklemelisiniz `Loan` ve ardından, bir dosyaya sınıfı seri gerekir.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Verileri Kaydet ve sınıf seri hale getirmek için  
  
-   Aşağıdaki kodu ekleyin `Form1_FormClosing` olay yordamı:  
  
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
  
 Bu noktada, yeniden yapılandırabilir ve uygulamayı çalıştırın. Başlangıçta, varsayılan değerleri metin kutularında görünür. Dördüncü metin kutusuna bir ad girin ve değerleri değiştirmek deneyin. Uygulamayı kapatın ve yeniden çalıştırın. Yeni değerler şimdi metin kutularına göründüğüne dikkat edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Seri hale getirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
