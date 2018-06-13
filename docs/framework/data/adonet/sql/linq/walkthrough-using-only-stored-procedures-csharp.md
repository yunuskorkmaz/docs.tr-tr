---
title: 'İzlenecek yol: Kullanarak yalnızca (C#) saklı yordamlar'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: 223c93a790e610414aa48c2aea8e884b9d841666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365429"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="5315c-102">İzlenecek yol: Kullanarak yalnızca (C#) saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="5315c-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="5315c-103">Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yürüterek verilere erişmek için senaryo saklı yordamlar yalnızca.</span><span class="sxs-lookup"><span data-stu-id="5315c-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="5315c-104">Bu yaklaşım, genellikle veri deposu nasıl erişilir sınırlamak için Veritabanı yöneticileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5315c-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5315c-105">Saklı yordamların de kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle için varsayılan davranışı geçersiz kılmak için uygulamalar `Create`, `Update`, ve `Delete` işlemler.</span><span class="sxs-lookup"><span data-stu-id="5315c-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="5315c-106">Daha fazla bilgi için bkz: [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="5315c-107">Bu kılavuzda amaçları doğrultusunda, Northwind örnek veritabanı saklı yordamlarda eşlenen iki yöntemi kullanır: CustOrdersDetail ve CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="5315c-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="5315c-108">Bir C# dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınızda eşleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="5315c-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="5315c-109">Daha fazla bilgi için bu kılavuzda daha sonra Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5315c-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="5315c-110">Bu kılavuzda üzerinde bağlı değildir [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5315c-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="5315c-111">Geliştiriciler Visual Studio kullanarak da kullanabilirsiniz [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] saklı yordam işlevleri uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="5315c-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="5315c-112">Bkz: [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="5315c-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="5315c-113">Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5315c-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5315c-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5315c-114">Prerequisites</span></span>  
 <span data-ttu-id="5315c-115">Bu kılavuz aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5315c-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="5315c-116">Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest7") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5315c-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="5315c-117">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5315c-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="5315c-118">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="5315c-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="5315c-119">Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5315c-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="5315c-120">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="5315c-121">Veritabanı indirdikten sonra northwnd.mdf dosyasını c:\linqtest7 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5315c-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="5315c-122">Northwind veritabanından oluşturulan bir C# kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="5315c-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="5315c-123">Bu kılavuz, aşağıdaki komut satırı ile SqlMetal aracı kullanılarak yazılmış olduğundan:</span><span class="sxs-lookup"><span data-stu-id="5315c-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="5315c-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / çoğul**</span><span class="sxs-lookup"><span data-stu-id="5315c-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="5315c-125">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5315c-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5315c-126">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5315c-126">Overview</span></span>  
 <span data-ttu-id="5315c-127">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5315c-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="5315c-128">Ayarlama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'da çözüm.</span><span class="sxs-lookup"><span data-stu-id="5315c-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="5315c-129">System.Data.Linq derleme projesine ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5315c-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="5315c-130">Veritabanı kod dosyası projesine ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5315c-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="5315c-131">Veritabanıyla bağlantı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5315c-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="5315c-132">Kullanıcı arabirimi ayarlama.</span><span class="sxs-lookup"><span data-stu-id="5315c-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="5315c-133">Çalıştıran ve uygulamayı test etme.</span><span class="sxs-lookup"><span data-stu-id="5315c-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="5315c-134">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5315c-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="5315c-135">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="5315c-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="5315c-136">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5315c-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="5315c-137">Visual Studio üzerinde **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="5315c-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="5315c-138">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="5315c-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="5315c-139">İçinde **şablonları** bölmesinde tıklatın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="5315c-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="5315c-140">İçinde **adı** kutusuna **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="5315c-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="5315c-141">İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="5315c-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="5315c-142">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5315c-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="5315c-143">Windows Forms Tasarımcısı'nı açar.</span><span class="sxs-lookup"><span data-stu-id="5315c-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="5315c-144">LINQ SQL derleme başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="5315c-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="5315c-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Standart Windows Forms uygulaması şablonunda derleme dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5315c-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="5315c-146">Aşağıdaki adımlarda açıklandığı gibi derleme kendiniz eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="5315c-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="5315c-147">System.Data.Linq.dll eklemek için</span><span class="sxs-lookup"><span data-stu-id="5315c-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="5315c-148">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="5315c-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="5315c-149">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="5315c-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5315c-150">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="5315c-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5315c-151">Northwind kod dosyası projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="5315c-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="5315c-152">Bu adım, Northwind örnek veritabanı'ndaki bir kod dosyası oluşturmak için SqlMetal Aracı'nı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="5315c-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="5315c-153">Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5315c-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5315c-154">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="5315c-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="5315c-155">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="5315c-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="5315c-156">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest7\northwind.cs taşıyın ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="5315c-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="5315c-157">Northwind.cs dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="5315c-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="5315c-158">Veritabanı bağlantısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5315c-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="5315c-159">Bu adımda, Northwind örnek veritabanı için bağlantı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="5315c-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="5315c-160">Bu izlenecek yolu olarak "c:\linqtest7\northwnd.mdf" kullanır.</span><span class="sxs-lookup"><span data-stu-id="5315c-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="5315c-161">Veritabanı bağlantısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5315c-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="5315c-162">İçinde **Çözüm Gezgini**, sağ **Form1.cs**ve ardından **görünümü kodu**.</span><span class="sxs-lookup"><span data-stu-id="5315c-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="5315c-163">Aşağıdaki kodu yazın `Form1` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="5315c-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="5315c-164">Kullanıcı arabirimi ayarlama</span><span class="sxs-lookup"><span data-stu-id="5315c-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="5315c-165">Bu görevde kullanıcıların veritabanındaki verilere erişmek için saklı yordamlar çalıştırabilmeniz için bir arabirim ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5315c-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="5315c-166">Bu kılavuzda ile geliştirdiğiniz uygulamalarda yalnızca uygulama içinde katıştırılmış saklı yordamları kullanarak veritabanındaki verileri kullanıcılar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="5315c-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="5315c-167">Kullanıcı arabirimini oluşturan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5315c-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="5315c-168">Return Windows Forms Tasarımcısı (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="5315c-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="5315c-169">Üzerinde **Görünüm** menüsünde tıklatın **araç**.</span><span class="sxs-lookup"><span data-stu-id="5315c-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="5315c-170">Araç kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5315c-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5315c-171">Tıklatın **AutoHide** Raptiye kalan gerçekleştirirken araç kutusunu açık tutmak için bu bölümdeki adımları.</span><span class="sxs-lookup"><span data-stu-id="5315c-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="5315c-172">Sürükleme iki düğmeler, iki metin kutusu ve iki etiket Kutusu'ndan **Form1**.</span><span class="sxs-lookup"><span data-stu-id="5315c-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="5315c-173">Denetimleri eşlik eden çizim olduğu gibi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="5315c-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="5315c-174">Genişletme **Form1** denetimleri kolayca uyacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="5315c-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="5315c-175">Sağ **label1**ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="5315c-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="5315c-176">Değişiklik **metin** özelliğinden **label1** için **OrderID girin:**.</span><span class="sxs-lookup"><span data-stu-id="5315c-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="5315c-177">İçin de aynı şekilde **label2**, değiştirme **metin** özelliğinden **label2** için **CustomerID girin:**.</span><span class="sxs-lookup"><span data-stu-id="5315c-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="5315c-178">Aynı şekilde değiştirme **metin** özelliği için **button1** için **sipariş ayrıntılarını**.</span><span class="sxs-lookup"><span data-stu-id="5315c-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="5315c-179">Değişiklik **metin** özelliği için **button2** için **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="5315c-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="5315c-180">Tüm metni görünür olmasını sağlamak düğmesi denetimleri genişletir.</span><span class="sxs-lookup"><span data-stu-id="5315c-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="5315c-181">Düğme tıklamaları işlemek için</span><span class="sxs-lookup"><span data-stu-id="5315c-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="5315c-182">Çift **sipariş ayrıntılarını** üzerinde **Form1** button1 olay işleyicisi Kod düzenleyicisinde açın.</span><span class="sxs-lookup"><span data-stu-id="5315c-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="5315c-183">Aşağıdaki kodu yazın `button1` işleyici:</span><span class="sxs-lookup"><span data-stu-id="5315c-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="5315c-184">Şimdi çift **button2** üzerinde **Form1** açmak için `button2` işleyicisi</span><span class="sxs-lookup"><span data-stu-id="5315c-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="5315c-185">Aşağıdaki kodu yazın `button2` işleyici:</span><span class="sxs-lookup"><span data-stu-id="5315c-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5315c-186">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="5315c-186">Testing the Application</span></span>  
 <span data-ttu-id="5315c-187">Artık uygulamanızı test etmek için zaman yapılır.</span><span class="sxs-lookup"><span data-stu-id="5315c-187">Now it is time to test your application.</span></span> <span data-ttu-id="5315c-188">Veri deposu ile ilgili iki saklı yordamlar hangi eylemleri için sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5315c-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="5315c-189">Bu, girdiğiniz tüm OrderID için eklenen ürünlerle döndürülecek veya girdiğiniz tüm CustomerID sipariş ürünleri geçmişini dönmek için eylemlerdir.</span><span class="sxs-lookup"><span data-stu-id="5315c-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="5315c-190">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="5315c-190">To test the application</span></span>  
  
1.  <span data-ttu-id="5315c-191">Hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="5315c-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="5315c-192">Form1 görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5315c-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="5315c-193">İçinde **girin OrderID** kutusuna `10249`ve ardından **sipariş ayrıntılarını**.</span><span class="sxs-lookup"><span data-stu-id="5315c-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="5315c-194">Bir ileti kutusu 10249 sırada dahil olduğu ürünleri listeler.</span><span class="sxs-lookup"><span data-stu-id="5315c-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="5315c-195">Tıklatın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5315c-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="5315c-196">İçinde **girin CustomerID** kutusuna `ALFKI`ve ardından **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="5315c-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="5315c-197">ALFKI müşteri siparişi geçmişi listeleyen bir ileti kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="5315c-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="5315c-198">Tıklatın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5315c-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="5315c-199">İçinde **girin OrderID** kutusuna `123`ve ardından **sipariş ayrıntılarını**.</span><span class="sxs-lookup"><span data-stu-id="5315c-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="5315c-200">"Sonuç yok." görüntüleyen bir ileti kutusu görünür</span><span class="sxs-lookup"><span data-stu-id="5315c-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="5315c-201">Tıklatın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="5315c-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="5315c-202">Üzerinde **hata ayıklama** menüsünde tıklatın **hata ayıklamayı durdurun**.</span><span class="sxs-lookup"><span data-stu-id="5315c-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="5315c-203">Hata ayıklama oturumu kapatır.</span><span class="sxs-lookup"><span data-stu-id="5315c-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="5315c-204">Denemeler bitirdikten, tıklayabilirsiniz **Projeyi Kapat** üzerinde **dosya** menüsünde ve istendiğinde projeyi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="5315c-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5315c-205">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="5315c-205">Next Steps</span></span>  
 <span data-ttu-id="5315c-206">Bazı değişiklikler yaparak bu proje geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5315c-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="5315c-207">Örneğin, liste kutusunda kullanılabilir saklı yordamları listeler, kullanıcı yürütmek için hangi yordamların Seç içerir.</span><span class="sxs-lookup"><span data-stu-id="5315c-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="5315c-208">Ayrıca bir metin dosyasına raporları çıkış akış.</span><span class="sxs-lookup"><span data-stu-id="5315c-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5315c-209">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5315c-209">See Also</span></span>  
 [<span data-ttu-id="5315c-210">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="5315c-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="5315c-211">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="5315c-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
