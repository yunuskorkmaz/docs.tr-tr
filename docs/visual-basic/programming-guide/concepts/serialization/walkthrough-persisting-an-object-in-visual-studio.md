---
title: Visual Studio’da Bir Nesneyi Kalıcı Kılma
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: fbd342c929e8519571c0f6bb76d4091efcfe4476
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350390"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio 'da bir nesneyi kalıcı hale getirme (Visual Basic)
Tasarım zamanında bir nesnenin özelliklerini varsayılan değerlere ayarlayabilseniz de, nesne yok edildiğinde çalışma zamanında girilen tüm değerler kaybedilir. Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.  
  
> [!NOTE]
> Visual Basic, ad veya sayı gibi basit verileri depolamak için `My.Settings` nesnesini kullanabilirsiniz. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 Bu izlenecek yolda basit bir `Loan` nesnesi oluşturacak ve verilerini bir dosyaya sürdürmeye devam edersiniz. Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.  
  
> [!IMPORTANT]
> Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın klasör için `Create` izni olması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten mevcutsa, uygulamanın daha az bir izin `Write` izni olması gerekir. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve yalnızca tek bir dosyaya `Read` izinleri verilmesi (bir klasör için izin oluşturmak yerine) daha güvenlidir. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.  
  
> [!IMPORTANT]
> Bu örnek, verileri bir ikili dosya halinde depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma  
 İlk adım, sınıfı kullanan bir `Loan` sınıfı ve test uygulaması oluşturmaktır.  
  
### <a name="to-create-the-loan-class"></a>Kredi sınıfı oluşturmak için  
  
1. Yeni bir sınıf kitaplığı projesi oluşturun ve "Kreclass" olarak adlandırın. Daha fazla bilgi için bkz. [çözüm ve proje oluşturma](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2. **Çözüm Gezgini**, Class1 dosyası için kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin. Dosyayı `Loan` olarak yeniden adlandırın ve ENTER 'a basın. Dosyanın yeniden adlandırılması de `Loan`sınıfı olarak yeniden adlandırılacaktır.  
  
3. Sınıfına aşağıdaki ortak üyeleri ekleyin:  
  
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
  
 Ayrıca, `Loan` sınıfını kullanan basit bir uygulama da oluşturmanız gerekecektir.  
  
### <a name="to-create-a-test-application"></a>Test uygulaması oluşturmak için  
  
1. Çözümünüze Windows Forms bir uygulama projesi eklemek için **Dosya** menüsünde **Ekle**,**Yeni proje**' yi seçin.  
  
2. **Yeni Proje Ekle** iletişim kutusunda, **Windows Forms uygulama**' yı seçin ve projenin adı olarak `LoanApp` girin ve ardından Iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
3. **Çözüm Gezgini**, kremi uygulama projesini seçin.  
  
4. **Proje** menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.  
  
5. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.  
  
6. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin ve sonra ödünç sınıfı projesini seçin.  
  
7. İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.  
  
8. Tasarımcıda, forma dört <xref:System.Windows.Forms.TextBox> denetimi ekleyin.  
  
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
  
10. Aşağıdaki kodu kullanarak forma `PropertyChanged` olayı için bir olay işleyicisi ekleyin:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 Bu noktada, uygulamayı derleyip çalıştırabilirsiniz. `Loan` sınıfından varsayılan değerlerin metin kutularında göründüğünü unutmayın. 7,5 olan faiz oranı değerini 7,1 olarak değiştirmeyi deneyin ve sonra uygulamayı kapatıp yeniden çalıştırın. değer varsayılan olarak 7,5 ' ye döner.  
  
 Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir. Uygulamanın her çalıştığında, kullanıcının faiz oranını güncelleştirmesini sağlamak yerine, uygulamanın örnekleri arasındaki en son faiz oranını korumak daha iyidir. Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.  
  
## <a name="using-serialization-to-persist-the-object"></a>Nesneyi kalıcı hale getirmek için serileştirme kullanma  
 Kredi sınıfının değerlerini kalıcı hale getirmek için önce sınıfı `Serializable` özniteliğiyle işaretlemeniz gerekir.  
  
### <a name="to-mark-a-class-as-serializable"></a>Bir sınıfı seri hale getirilebilir olarak işaretlemek için  
  
- Kredi sınıfının sınıf bildirimini aşağıdaki gibi değiştirin:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` özniteliği derleyiciye sınıftaki her şeyin bir dosyaya kalıcı olarak devam edebilir olduğunu söyler. `PropertyChanged` olayı bir Windows form nesnesi tarafından işlendiği için serileştirilemiyor. `NonSerialized` özniteliği, kalıcı olmaması gereken sınıf üyelerini işaretlemek için kullanılabilir.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Bir üyenin serileştirilmesine engel olmak için  
  
- `PropertyChanged` olayının bildirimini aşağıdaki gibi değiştirin:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir. Sınıfını seri hale getirmek ve bir dosyaya yazmak için <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanlarını kullanırsınız. Tam nitelikli adları yazmadan kaçınmak için, gerekli sınıf kitaplıklarına başvurular ekleyebilirsiniz.  
  
### <a name="to-add-references-to-namespaces"></a>Ad alanlarına başvurular eklemek için  
  
- Aşağıdaki deyimlerini `Form1` sınıfının üst kısmına ekleyin:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     Bu durumda, nesneyi ikili bir biçimde kaydetmek için ikili bir biçimlendirici kullanıyorsunuz.  
  
 Sonraki adım, nesne oluşturulduğunda nesnenin serisini kaldırmak için kod eklemektir.  
  
### <a name="to-deserialize-an-object"></a>Bir nesnenin serisini kaldırmak için  
  
1. Seri hale getirilen verilerin dosya adı için sınıfa bir sabit ekleyin.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. `Form1_Load` olay yordamındaki kodu aşağıdaki gibi değiştirin:  
  
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
  
     Önce dosyanın var olduğunu denetlemeniz gerektiğini unutmayın. Varsa, dosyayı çevirmek için ikili dosyayı ve bir <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> sınıfını okumak üzere bir <xref:System.IO.Stream> sınıfı oluşturun. Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.  
  
 Sonra, metin kutularına girilen verileri `Loan` sınıfına kaydetmek için kod eklemeniz gerekir ve ardından sınıfı bir dosyaya serileştirilmelidir.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Verileri kaydetmek ve sınıfı seri hale getirmek için  
  
- `Form1_FormClosing` olay yordamına aşağıdaki kodu ekleyin:  
  
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
  
 Bu noktada, uygulamayı derleyip çalıştırabilirsiniz. Başlangıçta, varsayılan değerler metin kutularında görünür. Değerleri değiştirmeyi deneyin ve dördüncü metin kutusuna bir ad girin. Uygulamayı kapatın ve sonra yeniden çalıştırın. Yeni değerlerin artık metin kutularında göründüğünü unutmayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Serileştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
