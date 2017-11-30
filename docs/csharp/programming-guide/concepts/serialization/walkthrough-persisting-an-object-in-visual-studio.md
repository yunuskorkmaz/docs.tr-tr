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
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="c6404-102">İzlenecek yol: Visual Studio'da (C#) bir nesneyi kalıcı kılma</span><span class="sxs-lookup"><span data-stu-id="c6404-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="c6404-103">Tasarım zamanında varsayılan değerlere nesnenin özellikleri belirlenebiliyor olsa da, çalışma zamanında girdiğiniz değerleri nesne bozulduğunda kaybolur.</span><span class="sxs-lookup"><span data-stu-id="c6404-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="c6404-104">Bir nesnenin veri değerlerini depolamak ve nesne örneği bir sonraki başlatılışında almak sağlar örnekleri arasında kalıcı hale getirmek için seri hale getirme kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6404-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="c6404-105">Bu kılavuzda, basit bir oluşturacak `Loan` nesne ve verileri bir dosyaya kalır.</span><span class="sxs-lookup"><span data-stu-id="c6404-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="c6404-106">Nesne yeniden oluşturduğunuzda, ardından dosyadan verileri alır.</span><span class="sxs-lookup"><span data-stu-id="c6404-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6404-107">Bu örnek, dosyanın zaten mevcut değilse yeni bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c6404-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="c6404-108">Bir uygulama bir dosya oluşturmanız gerekiyorsa, bu uygulama gerekir `Create` klasörü için izni.</span><span class="sxs-lookup"><span data-stu-id="c6404-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="c6404-109">İzinler, erişim denetim listeleri kullanılarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c6404-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="c6404-110">Dosya zaten varsa, uygulamanın yalnızca ihtiyacı `Write` izin, daha az izni.</span><span class="sxs-lookup"><span data-stu-id="c6404-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="c6404-111">Mümkünse, dağıtım sırasında dosyası oluşturun ve yalnızca izni için daha güvenli olan `Read` (yerine bir klasör izinlerini Oluştur) tek bir dosya izni.</span><span class="sxs-lookup"><span data-stu-id="c6404-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="c6404-112">Ayrıca, kök klasöre veya Program dosyaları klasörü kullanıcı klasörleri verileri yazmak amacıyla daha güvenlidir.</span><span class="sxs-lookup"><span data-stu-id="c6404-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c6404-113">Bu örnek verileri bir ikili biçimi dosyasında depolar.</span><span class="sxs-lookup"><span data-stu-id="c6404-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="c6404-114">Bu biçimler, parolalar veya kredi kartı bilgileri gibi hassas verileri için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="c6404-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6404-115">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="c6404-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c6404-116">Ayarlarınızı değiştirmek için tıklatın. **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c6404-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c6404-117">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c6404-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="c6404-118">Kredi nesnesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6404-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="c6404-119">İlk adım oluşturmaktır bir `Loan` sınıfı ve sınıfını kullanan bir test uygulaması.</span><span class="sxs-lookup"><span data-stu-id="c6404-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="c6404-120">Kredi sınıfı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6404-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="c6404-121">Yeni bir sınıf kitaplığı projesi oluşturun ve "LoanClass" olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="c6404-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="c6404-122">Daha fazla bilgi için bkz: [oluşturma çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="c6404-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="c6404-123">İçinde **Çözüm Gezgini**, Class1 dosya için kısayol menüsünü açın ve seçin **yeniden adlandırma**.</span><span class="sxs-lookup"><span data-stu-id="c6404-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="c6404-124">Dosyayı Yeniden Adlandır `Loan` ve ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6404-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="c6404-125">Dosyayı yeniden adlandırmak da yeniden adlandırın sınıfına `Loan`.</span><span class="sxs-lookup"><span data-stu-id="c6404-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="c6404-126">Aşağıdaki genel üyeler sınıfına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6404-126">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="c6404-127">Ayrıca kullanan basit bir uygulama oluşturmanız gerekir `Loan` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c6404-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="c6404-128">Bir test uygulaması oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6404-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="c6404-129">Çözümünüz için bir Windows Forms uygulaması projesi eklemek için **dosya** menüsünde seçin **Ekle**, **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="c6404-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="c6404-130">İçinde **Yeni Proje Ekle** iletişim kutusunda, seçin **Windows Forms uygulaması**ve girin `LoanApp` proje ve ardından adı olarak **Tamam** iletişim kutusunu kapatmak için .</span><span class="sxs-lookup"><span data-stu-id="c6404-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="c6404-131">İçinde **Çözüm Gezgini**, LoanApp projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6404-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="c6404-132">Üzerinde **proje** menüsünde seçin **başlangıç projesi olarak ayarla**.</span><span class="sxs-lookup"><span data-stu-id="c6404-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="c6404-133">Üzerinde **proje** menüsünde seçin **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c6404-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="c6404-134">İçinde **Başvuru Ekle** iletişim kutusunda, seçin **projeleri** sekmesini ve ardından LoanClass projesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c6404-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="c6404-135">İletişim kutusunu kapatmak için **Tamam** 'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c6404-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="c6404-136">Tasarımcıda dört eklemek <xref:System.Windows.Forms.TextBox> formu denetimleri.</span><span class="sxs-lookup"><span data-stu-id="c6404-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="c6404-137">Kod Düzenleyicisi'ne şu kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6404-137">In the Code Editor, add the following code:</span></span>  
  
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
  
10. <span data-ttu-id="c6404-138">Bir olay işleyicisi ekleme `PropertyChanged` aşağıdaki kodu kullanarak formuna olay:</span><span class="sxs-lookup"><span data-stu-id="c6404-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="c6404-139">Bu noktada, derleme ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6404-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="c6404-140">Gelen varsayılan değerleri Not `Loan` sınıfı metin kutularında görünür.</span><span class="sxs-lookup"><span data-stu-id="c6404-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="c6404-141">Faiz oranını değeri, 7.1 için 7.5 değiştirin ve sonra uygulamayı kapatın ve yeniden çalıştırın çalıştığınızda — değer 7.5 varsayılan olarak döner.</span><span class="sxs-lookup"><span data-stu-id="c6404-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="c6404-142">Gerçek Hayatta, faiz oranları uygulama her çalıştırıldığında düzenli aralıklarla, ancak mutlaka değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6404-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="c6404-143">Kullanıcının uygulamanın çalıştığı her zaman faiz oranını güncelleştirme yapmak yerine, uygulama örnekleri arasında en son faiz oranını korumak daha iyi olur.</span><span class="sxs-lookup"><span data-stu-id="c6404-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="c6404-144">Sonraki adımda, yalnızca serileştirme kredisi sınıfına ekleyerek bunu.</span><span class="sxs-lookup"><span data-stu-id="c6404-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="c6404-145">Nesne kalıcı hale getirmek için seri hale getirme kullanma</span><span class="sxs-lookup"><span data-stu-id="c6404-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="c6404-146">Kredi sınıfı için değerleri kalıcı hale getirmek için önce sınıfıyla işaretlemelisiniz `Serializable` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c6404-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="c6404-147">Bir sınıf seri hale getirilebilir olarak işaretlemek için</span><span class="sxs-lookup"><span data-stu-id="c6404-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="c6404-148">Kredi sınıfı için sınıf bildirimi aşağıdaki gibi değiştirin:</span><span class="sxs-lookup"><span data-stu-id="c6404-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="c6404-149">`Serializable` Özniteliği derleyici sınıftaki her şeyi bir dosyaya kalıcı olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c6404-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="c6404-150">Çünkü `PropertyChanged` olayı, bir Windows Form nesnesi tarafından işlenir, seri hale getirilemez.</span><span class="sxs-lookup"><span data-stu-id="c6404-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="c6404-151">`NonSerialized` Özniteliği, kalıcı sınıf üyeleri işaretlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c6404-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="c6404-152">Seri hale üyesi engellemek için</span><span class="sxs-lookup"><span data-stu-id="c6404-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="c6404-153">Bildirimi değiştirme `PropertyChanged` şekilde olay:</span><span class="sxs-lookup"><span data-stu-id="c6404-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="c6404-154">Sonraki adım, LoanApp uygulamaya serileştirme kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="c6404-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="c6404-155">Sınıf seri hale getirmek ve bir dosyaya yazmak için kullanacağınız <xref:System.IO> ve <xref:System.Xml.Serialization> ad alanları.</span><span class="sxs-lookup"><span data-stu-id="c6404-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="c6404-156">Tam olarak nitelenmiş adlar yazma zorunluluğunu ortadan kaldırmak için gerekli sınıf kitaplıkları başvurular ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6404-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="c6404-157">Ad alanlarına başvurular eklemek için</span><span class="sxs-lookup"><span data-stu-id="c6404-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="c6404-158">Aşağıdaki deyimleri en üst kısmına ekleyin `Form1` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="c6404-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="c6404-159">Bu durumda, nesneyi bir ikili dosya biçiminde kaydetmek için bir ikili biçimlendirici kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="c6404-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="c6404-160">Sonraki adım, nesne oluşturulduğunda dosyasından nesnesi seri durumdan çıkarılacak kod eklemektir.</span><span class="sxs-lookup"><span data-stu-id="c6404-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="c6404-161">Bir nesnenin serisini kaldırmak için</span><span class="sxs-lookup"><span data-stu-id="c6404-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="c6404-162">Bir sabit serileştirilmiş verilerinin dosya adı için sınıfına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6404-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="c6404-163">Kodda değişiklik `Form1_Load` olay yordamı şekilde:</span><span class="sxs-lookup"><span data-stu-id="c6404-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="c6404-164">Dosyanın var olduğunu ilk denetlemelisiniz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c6404-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="c6404-165">Varsa oluşturma bir <xref:System.IO.Stream> ikili dosya okuma için sınıf ve <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> dosyayı çevirmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c6404-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="c6404-166">Ayrıca akış türünden kredisi nesne türüne dönüştürmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6404-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="c6404-167">Metin kutuları için girilen verileri kaydetmek için kod sonraki eklemelisiniz `Loan` ve ardından, bir dosyaya sınıfı seri gerekir.</span><span class="sxs-lookup"><span data-stu-id="c6404-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="c6404-168">Verileri Kaydet ve sınıf seri hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="c6404-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="c6404-169">Aşağıdaki kodu ekleyin `Form1_FormClosing` olay yordamı:</span><span class="sxs-lookup"><span data-stu-id="c6404-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="c6404-170">Bu noktada, yeniden yapılandırabilir ve uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6404-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="c6404-171">Başlangıçta, varsayılan değerleri metin kutularında görünür.</span><span class="sxs-lookup"><span data-stu-id="c6404-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="c6404-172">Dördüncü metin kutusuna bir ad girin ve değerleri değiştirmek deneyin.</span><span class="sxs-lookup"><span data-stu-id="c6404-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="c6404-173">Uygulamayı kapatın ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="c6404-173">Close the application and then run it again.</span></span> <span data-ttu-id="c6404-174">Yeni değerler şimdi metin kutularına göründüğüne dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="c6404-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6404-175">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c6404-175">See Also</span></span>  
 [<span data-ttu-id="c6404-176">Seri hale getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="c6404-176">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="c6404-177">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c6404-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
