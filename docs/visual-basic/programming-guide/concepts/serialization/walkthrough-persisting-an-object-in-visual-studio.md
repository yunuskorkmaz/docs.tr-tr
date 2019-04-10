---
title: (Visual Basic) Visual Studio'da bir nesneyi kalıcı kılma
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 55ad2049003baaed26f4db909ae466aefdd161e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303355"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="cb18f-102">İzlenecek yol: (Visual Basic) Visual Studio'da bir nesneyi kalıcı kılma</span><span class="sxs-lookup"><span data-stu-id="cb18f-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="cb18f-103">Nesnesi yok edildiğinde, bir nesnenin özellikler varsayılan değerlere tasarım zamanında olsa da, çalışma zamanında girilen değerleri kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="cb18f-104">Seri hale getirme, bir nesnenin veri değerleri depolamak ve bunları nesnesi örneği başlatıldığında almanıza imkan tanıyan örnekler arasında kalıcı hale getirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb18f-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb18f-105">Visual Basic'te, bir ad veya sayı gibi basit verilerini depolamak için kullanabileceğiniz `My.Settings` nesne.</span><span class="sxs-lookup"><span data-stu-id="cb18f-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="cb18f-106">Daha fazla bilgi için [My.Settings nesnesi](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="cb18f-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="cb18f-107">Bu kılavuzda, basit bir oluşturacağınız `Loan` nesne ve verileri bir dosyaya kalıcı.</span><span class="sxs-lookup"><span data-stu-id="cb18f-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="cb18f-108">Nesne yeniden oluşturduğunuzda dosyadan verileri ardından alır.</span><span class="sxs-lookup"><span data-stu-id="cb18f-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb18f-109">Bu örnek, bir dosya zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb18f-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="cb18f-110">Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulama gerekir `Create` klasörüne izni.</span><span class="sxs-lookup"><span data-stu-id="cb18f-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="cb18f-111">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="cb18f-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="cb18f-112">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha düşük bir izni.</span><span class="sxs-lookup"><span data-stu-id="cb18f-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="cb18f-113">Mümkün olan yerlerde, dosyayı dağıtım sırasında oluşturmak ve yalnızca vermek için daha güvenli olan `Read` izinleri tek bir dosya (yerine bir klasörün izinlerini oluşturma).</span><span class="sxs-lookup"><span data-stu-id="cb18f-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="cb18f-114">Ayrıca, kök klasöre veya Program dosyaları klasörüne kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb18f-115">Bu örnek, bir ikili verileri depolar.</span><span class="sxs-lookup"><span data-stu-id="cb18f-115">This example stores data in a binary.</span></span> <span data-ttu-id="cb18f-116">Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="cb18f-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb18f-117">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cb18f-118">Ayarlarınızı değiştirmek için tıklayın **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="cb18f-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cb18f-119">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="cb18f-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="cb18f-120">Kredi nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb18f-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="cb18f-121">İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir test uygulaması.</span><span class="sxs-lookup"><span data-stu-id="cb18f-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="cb18f-122">Kredi sınıfı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cb18f-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="cb18f-123">Yeni bir sınıf kitaplığı projesi oluşturun ve "LoanClass" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="cb18f-124">Daha fazla bilgi için [projeler ve çözümler oluşturma](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="cb18f-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="cb18f-125">İçinde **Çözüm Gezgini**Class1 dosyası için kısayol menüsünü açın ve seçin **Yeniden Adlandır**.</span><span class="sxs-lookup"><span data-stu-id="cb18f-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="cb18f-126">Dosyayı Yeniden Adlandır `Loan` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="cb18f-127">Dosya yeniden adlandırılırken da yeniden adlandırmak sınıfa `Loan`.</span><span class="sxs-lookup"><span data-stu-id="cb18f-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="cb18f-128">Sınıfına aşağıdaki genel üyeleri Ekle:</span><span class="sxs-lookup"><span data-stu-id="cb18f-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="cb18f-129">Ayrıca kullanan basit bir uygulama oluşturmanız gerekir `Loan` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="cb18f-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="cb18f-130">Bir test uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="cb18f-130">To create a test application</span></span>  
  
1. <span data-ttu-id="cb18f-131">Çözümünüz için bir Windows Forms uygulaması projesi eklemek için **dosya** menüsünde seçin **Ekle**,**yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="cb18f-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="cb18f-132">İçinde **Yeni Proje Ekle** iletişim kutusunda **Windows Forms uygulaması**girin `LoanApp` 'a tıklayın ve proje adı olarak **Tamam** iletişim kutusunu kapatmak için .</span><span class="sxs-lookup"><span data-stu-id="cb18f-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="cb18f-133">İçinde **Çözüm Gezgini**, LoanApp projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="cb18f-134">Üzerinde **proje** menüsünde seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="cb18f-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="cb18f-135">Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="cb18f-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="cb18f-136">İçinde **Başvuru Ekle** iletişim kutusunda **projeleri** sekmesini ve ardından LoanClass projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="cb18f-137">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="cb18f-138">Tasarımcıda dört ekleme <xref:System.Windows.Forms.TextBox> formu için denetimler.</span><span class="sxs-lookup"><span data-stu-id="cb18f-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="cb18f-139">Kod Düzenleyicisi'ne şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="cb18f-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="cb18f-140">İçin bir olay işleyicisi ekleme `PropertyChanged` olay formuna aşağıdaki kodu kullanarak:</span><span class="sxs-lookup"><span data-stu-id="cb18f-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="cb18f-141">Bu noktada, oluşturun ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="cb18f-142">Varsayılan değerlerini Not `Loan` sınıfı metin kutularında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="cb18f-143">Faiz oranını değeri, 7.1 için 7.5 değiştirin ve ardından uygulamayı kapatın ve yeniden çalıştırın deneyin — değeri 7.5 varsayılana.</span><span class="sxs-lookup"><span data-stu-id="cb18f-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="cb18f-144">Gerçek dünyada, uygulama her çalıştırıldığında düzenli aralıklarla ancak bu şart değildir faiz oranları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="cb18f-145">Kullanıcının uygulamanın çalıştığı her saat faiz oranını güncelleştirme yapmak yerine, uygulama örnekleri arasında en son faiz oranını korumak iyidir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="cb18f-146">Sonraki adımda, yalnızca kredi sınıfı seri hale getirme ekleyerek bunu.</span><span class="sxs-lookup"><span data-stu-id="cb18f-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="cb18f-147">Nesne kalıcı hale getirmek için serileştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="cb18f-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="cb18f-148">Kredi sınıfı değerlerini kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="cb18f-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="cb18f-149">Bir sınıf seri hale getirilebilir olarak işaretlemek için</span><span class="sxs-lookup"><span data-stu-id="cb18f-149">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="cb18f-150">Kredi sınıfı için sınıf bildirimi aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="cb18f-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="cb18f-151">`Serializable` Öznitelik derleyiciye sınıftaki her şeyi bir dosyaya kalıcı olmasını.</span><span class="sxs-lookup"><span data-stu-id="cb18f-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="cb18f-152">Çünkü `PropertyChanged` olayı, bir Windows Form nesnesi tarafından işlenir, seri hale getirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="cb18f-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="cb18f-153">`NonSerialized` Özniteliği, kalıcı sınıf üyeleri işaretlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="cb18f-154">Serileştirilmekte olan bir üye önlemek için</span><span class="sxs-lookup"><span data-stu-id="cb18f-154">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="cb18f-155">Değişiklik bildirimi `PropertyChanged` aşağıdaki gibi olay:</span><span class="sxs-lookup"><span data-stu-id="cb18f-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="cb18f-156">Sonraki adım, LoanApp uygulamaya serileştirme kodu eklemektir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="cb18f-157">Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanacağınız <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="cb18f-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="cb18f-158">Tam nitelikli adlarını yazarak önlemek için gerekli sınıf kitaplıklarına başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb18f-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="cb18f-159">Ad alanlarına başvurular eklemek için</span><span class="sxs-lookup"><span data-stu-id="cb18f-159">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="cb18f-160">Üstüne aşağıdaki deyimleri ekleyin `Form1` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="cb18f-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="cb18f-161">Bu durumda, ikili biçimde nesneyi kaydetmek için bir ikili biçimlendirici kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="cb18f-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="cb18f-162">Sonraki adım, bir nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="cb18f-163">Bir nesnenin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="cb18f-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="cb18f-164">Bir sabit seri hale getirilmiş veri dosya adı için bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="cb18f-165">Kodda değişiklik `Form1_Load` aşağıdaki gibi olay yordam:</span><span class="sxs-lookup"><span data-stu-id="cb18f-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="cb18f-166">Dosyanın var olduğundan ilk denetlemelidir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="cb18f-167">Yoksa, oluşturun bir <xref:System.IO.Stream> ikili dosyayı okumak için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosya çevirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="cb18f-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="cb18f-168">Ayrıca akış türünden kredi nesne türüne dönüştürmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="cb18f-169">Ardından metin kutusuna girilen verileri kaydetmek için kod ekleyin `Loan` sınıfı ve ardından sınıfı bir dosyaya serileştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="cb18f-170">Verileri Kaydet ve sınıfı serileştirmek için</span><span class="sxs-lookup"><span data-stu-id="cb18f-170">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="cb18f-171">Aşağıdaki kodu ekleyin `Form1_FormClosing` olay yordam:</span><span class="sxs-lookup"><span data-stu-id="cb18f-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="cb18f-172">Bu noktada, yeniden derleyebilir ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="cb18f-173">Başlangıçta, varsayılan değerleri metin kutularında görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="cb18f-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="cb18f-174">Deneyin değerleri değiştirmek ve dördüncü metin kutusuna bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="cb18f-175">Uygulamayı kapatın ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb18f-175">Close the application and then run it again.</span></span> <span data-ttu-id="cb18f-176">Yeni değerler artık metin kutularına göründüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cb18f-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb18f-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb18f-177">See also</span></span>

- [<span data-ttu-id="cb18f-178">Seri hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb18f-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="cb18f-179">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cb18f-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
