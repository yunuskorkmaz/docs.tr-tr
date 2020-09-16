---
title: Visual Studio’da Bir Nesneyi Kalıcı Kılma
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 3febd3f74510d11a7103edbd52bcae8043a5edc0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558608"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>İzlenecek yol: Visual Studio 'da bir nesneyi kalıcı hale getirme (Visual Basic)
Tasarım zamanında bir nesnenin özelliklerini varsayılan değerlere ayarlayabilseniz de, nesne yok edildiğinde çalışma zamanında girilen tüm değerler kaybedilir. Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.  
  
> [!NOTE]
> Visual Basic, bir ad veya sayı gibi basit verileri depolamak için `My.Settings` nesnesini kullanabilirsiniz. Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).  
  
 Bu izlenecek yolda basit bir `Loan` nesne oluşturacak ve verilerini bir dosyaya sürdürmeye devam edersiniz. Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.  
  
> [!IMPORTANT]
> Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur. Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasör için izni olması gerekir. İzinler, erişim denetim listeleri kullanılarak ayarlanır. Dosya zaten varsa, uygulamanın daha az izne sahip yalnızca `Write` izne ihtiyacı vardır. Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve yalnızca `Read` tek bir dosyaya (bir klasör için Izin oluşturmak yerine) izin verilmesi daha güvenlidir. Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.  
  
> [!IMPORTANT]
> Bu örnek, verileri bir ikili dosya halinde depolar. Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.  
  
> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın. Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Kredi nesnesi oluşturma  
 İlk adım, sınıfını `Loan` kullanan bir sınıf ve test uygulaması oluşturmaktır.  
  
### <a name="to-create-the-loan-class"></a>Kredi sınıfı oluşturmak için  
  
1. Yeni bir sınıf kitaplığı projesi oluşturun ve "Kreclass" olarak adlandırın. Daha fazla bilgi için bkz. [çözüm ve proje oluşturma](/visualstudio/ide/creating-solutions-and-projects).  
  
2. **Çözüm Gezgini**, Class1 dosyası için kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin. Dosyayı olarak yeniden adlandırın `Loan` ve ENTER 'a basın. Dosyanın yeniden adlandırılması de sınıfı olarak yeniden adlandırılacaktır `Loan` .  
  
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
  
 Ayrıca, sınıfını kullanan basit bir uygulama da oluşturmanız gerekecektir `Loan` .  
  
### <a name="to-create-a-test-application"></a>Test uygulaması oluşturmak için  
  
1. Çözümünüze Windows Forms bir uygulama projesi eklemek için **Dosya** menüsünde **Ekle**,**Yeni proje**' yi seçin.  
  
2. **Yeni Proje Ekle** Iletişim kutusunda **uygulama Windows Forms**seçin ve `LoanApp` projenin adı olarak girin ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
3. **Çözüm Gezgini**, kremi uygulama projesini seçin.  
  
4. **Proje** menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.  
  
5. **Proje** menüsünde, **Başvuru Ekle**' yi seçin.  
  
6. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin ve sonra ödünç sınıfı projesini seçin.  
  
7. **Tamam**’a tıklayarak iletişim kutusunu kapatın.  
  
8. Tasarımcıda, forma dört denetim ekleyin <xref:System.Windows.Forms.TextBox> .  
  
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
  
10. `PropertyChanged`Aşağıdaki kodu kullanarak forma olay işleyicisi ekleyin:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 Bu noktada, uygulamayı derleyip çalıştırabilirsiniz. Sınıfın varsayılan değerlerinin `Loan` metin kutularında göründüğünü unutmayın. 7,5 olan faiz oranı değerini 7,1 olarak değiştirmeyi deneyin ve sonra uygulamayı kapatıp yeniden çalıştırın. değer varsayılan olarak 7,5 ' ye döner.  
  
 Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir. Uygulamanın her çalıştığında, kullanıcının faiz oranını güncelleştirmesini sağlamak yerine, uygulamanın örnekleri arasındaki en son faiz oranını korumak daha iyidir. Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.  
  
## <a name="using-serialization-to-persist-the-object"></a>Nesneyi kalıcı hale getirmek için serileştirme kullanma  
 Kredi sınıfının değerlerini kalıcı hale getirmek için, önce sınıfı özniteliğiyle işaretlemeniz gerekir `Serializable` .  
  
### <a name="to-mark-a-class-as-serializable"></a>Bir sınıfı seri hale getirilebilir olarak işaretlemek için  
  
- Kredi sınıfının sınıf bildirimini aşağıdaki gibi değiştirin:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable`Özniteliği derleyiciye sınıftaki her şeyin bir dosyaya kalıcı olarak devam edebilir olduğunu söyler. `PropertyChanged`Olay bir Windows form nesnesi tarafından işlendiği için serileştirilemiyor. `NonSerialized`Özniteliği kalıcı olmaması gereken sınıf üyelerini işaretlemek için kullanılabilir.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Bir üyenin serileştirilmesine engel olmak için  
  
- `PropertyChanged`Olay bildirimini aşağıdaki gibi değiştirin:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir. Sınıfını seri hale getirmek ve bir dosyaya yazmak için, <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanlarını kullanırsınız. Tam nitelikli adları yazmadan kaçınmak için, gerekli sınıf kitaplıklarına başvurular ekleyebilirsiniz.  
  
### <a name="to-add-references-to-namespaces"></a>Ad alanlarına başvurular eklemek için  
  
- Aşağıdaki deyimlerini sınıfının üst kısmına ekleyin `Form1` :  
  
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
  
2. `Form1_Load`Olay yordamındaki kodu aşağıdaki gibi değiştirin:  
  
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
  
     Önce dosyanın var olduğunu denetlemeniz gerektiğini unutmayın. Varsa, <xref:System.IO.Stream> ikili dosyayı okumak için bir sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirecek bir sınıf oluşturun. Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.  
  
 Sonra, metin kutularına girilen verileri sınıfa kaydetmek için kod eklemeniz gerekir `Loan` ve ardından sınıfı bir dosyaya serileştirilmelidir.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Verileri kaydetmek ve sınıfı seri hale getirmek için  
  
- Olay yordamına aşağıdaki kodu ekleyin `Form1_FormClosing` :  
  
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

- [Serileştirme (Visual Basic)](index.md)
- [Visual Basic Programlama Kılavuzu](../../index.md)
