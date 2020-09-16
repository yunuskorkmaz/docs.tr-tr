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
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="a5571-102">İzlenecek yol: Visual Studio 'da bir nesneyi kalıcı hale getirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5571-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="a5571-103">Tasarım zamanında bir nesnenin özelliklerini varsayılan değerlere ayarlayabilseniz de, nesne yok edildiğinde çalışma zamanında girilen tüm değerler kaybedilir.</span><span class="sxs-lookup"><span data-stu-id="a5571-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="a5571-104">Nesneleri, değerleri depolamanızı ve nesnenin bir sonraki açılışında bunları almanızı sağlayan örnekler arasında bir nesnenin verilerini kalıcı hale getirmek için serileştirme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5571-105">Visual Basic, bir ad veya sayı gibi basit verileri depolamak için `My.Settings` nesnesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="a5571-106">Daha fazla bilgi için bkz [. My. Settings nesnesi](../../../language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="a5571-106">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="a5571-107">Bu izlenecek yolda basit bir `Loan` nesne oluşturacak ve verilerini bir dosyaya sürdürmeye devam edersiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="a5571-108">Daha sonra nesneyi yeniden oluşturduğunuzda dosyadaki verileri buradan alırsınız.</span><span class="sxs-lookup"><span data-stu-id="a5571-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5571-109">Bu örnek, dosya zaten yoksa yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5571-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="a5571-110">Bir uygulamanın bir dosya oluşturması gerekiyorsa, bu uygulamanın `Create` klasör için izni olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5571-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="a5571-111">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a5571-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="a5571-112">Dosya zaten varsa, uygulamanın daha az izne sahip yalnızca `Write` izne ihtiyacı vardır.</span><span class="sxs-lookup"><span data-stu-id="a5571-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="a5571-113">Mümkün olduğunda, dağıtım sırasında dosyanın oluşturulması ve yalnızca `Read` tek bir dosyaya (bir klasör için Izin oluşturmak yerine) izin verilmesi daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="a5571-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="a5571-114">Ayrıca, Kullanıcı klasörlerine veri yazmak, kök klasör veya Program Files klasöründen daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="a5571-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a5571-115">Bu örnek, verileri bir ikili dosya halinde depolar.</span><span class="sxs-lookup"><span data-stu-id="a5571-115">This example stores data in a binary.</span></span> <span data-ttu-id="a5571-116">Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas veriler için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a5571-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a5571-117">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="a5571-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="a5571-118">Ayarlarınızı değiştirmek için **Araçlar** menüsünden **Içeri ve dışarı aktarma ayarları** ' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a5571-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="a5571-119">Daha fazla bilgi için bkz. [Visual STUDIO IDE 'Yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="a5571-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="a5571-120">Kredi nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5571-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="a5571-121">İlk adım, sınıfını `Loan` kullanan bir sınıf ve test uygulaması oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="a5571-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="a5571-122">Kredi sınıfı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5571-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="a5571-123">Yeni bir sınıf kitaplığı projesi oluşturun ve "Kreclass" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="a5571-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="a5571-124">Daha fazla bilgi için bkz. [çözüm ve proje oluşturma](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="a5571-124">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="a5571-125">**Çözüm Gezgini**, Class1 dosyası için kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="a5571-126">Dosyayı olarak yeniden adlandırın `Loan` ve ENTER 'a basın.</span><span class="sxs-lookup"><span data-stu-id="a5571-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="a5571-127">Dosyanın yeniden adlandırılması de sınıfı olarak yeniden adlandırılacaktır `Loan` .</span><span class="sxs-lookup"><span data-stu-id="a5571-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="a5571-128">Sınıfına aşağıdaki ortak üyeleri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5571-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="a5571-129">Ayrıca, sınıfını kullanan basit bir uygulama da oluşturmanız gerekecektir `Loan` .</span><span class="sxs-lookup"><span data-stu-id="a5571-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="a5571-130">Test uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a5571-130">To create a test application</span></span>  
  
1. <span data-ttu-id="a5571-131">Çözümünüze Windows Forms bir uygulama projesi eklemek için **Dosya** menüsünde **Ekle**,**Yeni proje**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="a5571-132">**Yeni Proje Ekle** Iletişim kutusunda **uygulama Windows Forms**seçin ve `LoanApp` projenin adı olarak girin ve ardından iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a5571-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="a5571-133">**Çözüm Gezgini**, kremi uygulama projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="a5571-134">**Proje** menüsünde **Başlangıç projesi olarak ayarla**' yı seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="a5571-135">**Proje** menüsünde, **Başvuru Ekle**' yi seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="a5571-136">**Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin ve sonra ödünç sınıfı projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="a5571-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="a5571-137">**Tamam**’a tıklayarak iletişim kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="a5571-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="a5571-138">Tasarımcıda, forma dört denetim ekleyin <xref:System.Windows.Forms.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="a5571-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="a5571-139">Kod Düzenleyicisi'ne şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5571-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="a5571-140">`PropertyChanged`Aşağıdaki kodu kullanarak forma olay işleyicisi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a5571-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="a5571-141">Bu noktada, uygulamayı derleyip çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="a5571-142">Sınıfın varsayılan değerlerinin `Loan` metin kutularında göründüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5571-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="a5571-143">7,5 olan faiz oranı değerini 7,1 olarak değiştirmeyi deneyin ve sonra uygulamayı kapatıp yeniden çalıştırın. değer varsayılan olarak 7,5 ' ye döner.</span><span class="sxs-lookup"><span data-stu-id="a5571-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="a5571-144">Gerçek dünyada, faiz oranları düzenli aralıklarla değişir, ancak uygulama her çalıştırıldığında her zaman gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a5571-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="a5571-145">Uygulamanın her çalıştığında, kullanıcının faiz oranını güncelleştirmesini sağlamak yerine, uygulamanın örnekleri arasındaki en son faiz oranını korumak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="a5571-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="a5571-146">Bir sonraki adımda, yalnızca kredi sınıfına serileştirme ekleyerek bunu yapacaksınız.</span><span class="sxs-lookup"><span data-stu-id="a5571-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="a5571-147">Nesneyi kalıcı hale getirmek için serileştirme kullanma</span><span class="sxs-lookup"><span data-stu-id="a5571-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="a5571-148">Kredi sınıfının değerlerini kalıcı hale getirmek için, önce sınıfı özniteliğiyle işaretlemeniz gerekir `Serializable` .</span><span class="sxs-lookup"><span data-stu-id="a5571-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="a5571-149">Bir sınıfı seri hale getirilebilir olarak işaretlemek için</span><span class="sxs-lookup"><span data-stu-id="a5571-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="a5571-150">Kredi sınıfının sınıf bildirimini aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a5571-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="a5571-151">`Serializable`Özniteliği derleyiciye sınıftaki her şeyin bir dosyaya kalıcı olarak devam edebilir olduğunu söyler.</span><span class="sxs-lookup"><span data-stu-id="a5571-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="a5571-152">`PropertyChanged`Olay bir Windows form nesnesi tarafından işlendiği için serileştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="a5571-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="a5571-153">`NonSerialized`Özniteliği kalıcı olmaması gereken sınıf üyelerini işaretlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a5571-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="a5571-154">Bir üyenin serileştirilmesine engel olmak için</span><span class="sxs-lookup"><span data-stu-id="a5571-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="a5571-155">`PropertyChanged`Olay bildirimini aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a5571-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="a5571-156">Sonraki adım, ödünç uygulama uygulamasına serileştirme kodu eklemektir.</span><span class="sxs-lookup"><span data-stu-id="a5571-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="a5571-157">Sınıfını seri hale getirmek ve bir dosyaya yazmak için, <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanlarını kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a5571-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="a5571-158">Tam nitelikli adları yazmadan kaçınmak için, gerekli sınıf kitaplıklarına başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="a5571-159">Ad alanlarına başvurular eklemek için</span><span class="sxs-lookup"><span data-stu-id="a5571-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="a5571-160">Aşağıdaki deyimlerini sınıfının üst kısmına ekleyin `Form1` :</span><span class="sxs-lookup"><span data-stu-id="a5571-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="a5571-161">Bu durumda, nesneyi ikili bir biçimde kaydetmek için ikili bir biçimlendirici kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="a5571-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="a5571-162">Sonraki adım, nesne oluşturulduğunda nesnenin serisini kaldırmak için kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="a5571-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="a5571-163">Bir nesnenin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="a5571-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="a5571-164">Seri hale getirilen verilerin dosya adı için sınıfa bir sabit ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a5571-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="a5571-165">`Form1_Load`Olay yordamındaki kodu aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a5571-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="a5571-166">Önce dosyanın var olduğunu denetlemeniz gerektiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5571-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="a5571-167">Varsa, <xref:System.IO.Stream> ikili dosyayı okumak için bir sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirecek bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a5571-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="a5571-168">Akış türünden kredi nesne türüne de dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5571-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="a5571-169">Sonra, metin kutularına girilen verileri sınıfa kaydetmek için kod eklemeniz gerekir `Loan` ve ardından sınıfı bir dosyaya serileştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a5571-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="a5571-170">Verileri kaydetmek ve sınıfı seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="a5571-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="a5571-171">Olay yordamına aşağıdaki kodu ekleyin `Form1_FormClosing` :</span><span class="sxs-lookup"><span data-stu-id="a5571-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="a5571-172">Bu noktada, uygulamayı derleyip çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5571-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="a5571-173">Başlangıçta, varsayılan değerler metin kutularında görünür.</span><span class="sxs-lookup"><span data-stu-id="a5571-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="a5571-174">Değerleri değiştirmeyi deneyin ve dördüncü metin kutusuna bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="a5571-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="a5571-175">Uygulamayı kapatın ve sonra yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a5571-175">Close the application and then run it again.</span></span> <span data-ttu-id="a5571-176">Yeni değerlerin artık metin kutularında göründüğünü unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5571-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5571-177">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5571-177">See also</span></span>

- [<span data-ttu-id="a5571-178">Serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5571-178">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="a5571-179">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a5571-179">Visual Basic Programming Guide</span></span>](../../index.md)
