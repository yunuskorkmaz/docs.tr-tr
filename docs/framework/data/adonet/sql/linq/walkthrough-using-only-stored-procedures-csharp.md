---
title: 'İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: e5497c1c6bfe032ba272c911217adaa3bd7f4f4f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332709"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="b79ee-102">İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="b79ee-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="b79ee-103">Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yürüterek verilerine erişmek için senaryo, depolanan yordamlar yalnızca.</span><span class="sxs-lookup"><span data-stu-id="b79ee-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="b79ee-104">Bu yaklaşım, genellikle veri deposu nasıl erişilir sınırlamak için Veritabanı yöneticileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b79ee-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b79ee-105">Saklı yordamları kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle de varsayılan davranışı geçersiz kılmak için uygulamaları `Create`, `Update`, ve `Delete` işlemler.</span><span class="sxs-lookup"><span data-stu-id="b79ee-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="b79ee-106">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b79ee-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="b79ee-107">Bu izlenecek yolda amacı doğrultusunda, Northwind örnek veritabanındaki saklı yordamlar için eşlenen iki yöntemi kullanır: CustOrdersDetail ve CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="b79ee-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="b79ee-108">Eşleme oluşturmak için SqlMetal komut satırı aracını çalıştırdığınızda oluşur bir C# dosya.</span><span class="sxs-lookup"><span data-stu-id="b79ee-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="b79ee-109">Daha fazla bilgi için bu kılavuzda daha sonra Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="b79ee-110">Bu izlenecek yol üzerinde kullanmayan [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b79ee-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="b79ee-111">Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] saklı yordam işlevselliği uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="b79ee-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="b79ee-112">Bkz: [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="b79ee-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="b79ee-113">Bu izlenecek yol, Visual kullanılarak yazılmış olduğundan C# geliştirme ayarları.</span><span class="sxs-lookup"><span data-stu-id="b79ee-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b79ee-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="b79ee-114">Prerequisites</span></span>  
 <span data-ttu-id="b79ee-115">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b79ee-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="b79ee-116">Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest7") kullanır.</span><span class="sxs-lookup"><span data-stu-id="b79ee-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="b79ee-117">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b79ee-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="b79ee-118">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="b79ee-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="b79ee-119">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b79ee-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="b79ee-120">Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="b79ee-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="b79ee-121">Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest7 klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="b79ee-122">A C# Northwind veritabanından oluşturulan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="b79ee-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="b79ee-123">Bu izlenecek yol, şu komut satırıyla SqlMetal Aracı'nı kullanarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="b79ee-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     **<span data-ttu-id="b79ee-124">sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / pluralize</span><span class="sxs-lookup"><span data-stu-id="b79ee-124">sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize</span></span>**  
  
     <span data-ttu-id="b79ee-125">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="b79ee-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b79ee-126">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b79ee-126">Overview</span></span>  
 <span data-ttu-id="b79ee-127">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="b79ee-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="b79ee-128">Ayarlama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.</span><span class="sxs-lookup"><span data-stu-id="b79ee-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="b79ee-129">System.Data.Linq derleme projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="b79ee-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="b79ee-130">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="b79ee-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="b79ee-131">Veritabanıyla bağlantı oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b79ee-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="b79ee-132">Kullanıcı arabirimi ayarlama.</span><span class="sxs-lookup"><span data-stu-id="b79ee-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="b79ee-133">Çalıştıran ve uygulamayı test etme.</span><span class="sxs-lookup"><span data-stu-id="b79ee-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="b79ee-134">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="b79ee-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="b79ee-135">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="b79ee-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="b79ee-136">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b79ee-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="b79ee-137">Visual Studio'da **dosya** menüsünde **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="b79ee-138">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="b79ee-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="b79ee-139">İçinde **şablonları** bölmesinde tıklayın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="b79ee-140">İçinde **adı** kutusuna **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="b79ee-141">İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="b79ee-142">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="b79ee-143">Windows Forms Tasarımcısı'nı açar.</span><span class="sxs-lookup"><span data-stu-id="b79ee-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="b79ee-144">LINQ SQL bütünleştirilmiş kod başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="b79ee-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="b79ee-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Derleme standart Windows Forms uygulaması şablonu dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="b79ee-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="b79ee-146">Aşağıdaki adımlarda açıklandığı gibi derleme kendiniz eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b79ee-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="b79ee-147">System.Data.Linq.dll eklemek için</span><span class="sxs-lookup"><span data-stu-id="b79ee-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="b79ee-148">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="b79ee-149">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="b79ee-150">Derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="b79ee-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b79ee-151">Northwind kod dosyası projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="b79ee-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="b79ee-152">Bu adım Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SqlMetal Aracı'nı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="b79ee-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="b79ee-153">Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="b79ee-154">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="b79ee-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="b79ee-155">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="b79ee-156">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest7\northwind.cs taşıyın ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="b79ee-157">Northwind.cs dosya projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="b79ee-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="b79ee-158">Veritabanı bağlantısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="b79ee-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="b79ee-159">Bu adımda, Northwind örnek veritabanına bir bağlantı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="b79ee-160">Bu izlenecek yolu olarak "c:\linqtest7\northwnd.mdf" kullanır.</span><span class="sxs-lookup"><span data-stu-id="b79ee-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="b79ee-161">Veritabanı bağlantısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="b79ee-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="b79ee-162">İçinde **Çözüm Gezgini**, sağ **Form1.cs**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2. <span data-ttu-id="b79ee-163">Aşağıdaki kodu yazın `Form1` sınıfı:</span><span class="sxs-lookup"><span data-stu-id="b79ee-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="b79ee-164">Kullanıcı arabirimi ayarlama</span><span class="sxs-lookup"><span data-stu-id="b79ee-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="b79ee-165">Bu görevde, böylece kullanıcılar, veritabanındaki verilere erişmek için saklı yordamlar yürütebilir bir arabirimi oluşturan ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="b79ee-166">Bu adım adım kılavuza geliştirmekte olduğunuz uygulamalar, yalnızca katıştırılmış uygulama içinde saklı yordamları kullanarak veritabanındaki verileri kullanıcılar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="b79ee-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="b79ee-167">Kullanıcı arabirimi oluşturan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="b79ee-167">To set up the user interface</span></span>  
  
1. <span data-ttu-id="b79ee-168">İade için Windows Forms Tasarımcısı (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="b79ee-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2. <span data-ttu-id="b79ee-169">Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="b79ee-170">Araç kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="b79ee-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b79ee-171">Tıklayın **AutoHide** Raptiye kalan gerçekleştirirken araç kutusu açık tutmak için bu bölümdeki adımlar.</span><span class="sxs-lookup"><span data-stu-id="b79ee-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="b79ee-172">Sürükleyin iki düğme, iki metin kutuları ve iki etiket araç kutusundan **Form1**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="b79ee-173">Eşlik eden resimde olduğu gibi denetimleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="b79ee-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="b79ee-174">Genişletin **Form1** denetimleri bir kolayca uyacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="b79ee-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="b79ee-175">Sağ **label1**ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="b79ee-176">Değişiklik **metin** özelliğinden **label1** için **OrderID girin:**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="b79ee-177">Aynı şekilde **etiket 2**, değiştirme **metin** özelliğinden **etiket 2** için **CustomerID girin:**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="b79ee-178">Aynı şekilde değiştirme **metin** özelliği **button1** için **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="b79ee-179">Değişiklik **metin** özelliği **button2** için **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="b79ee-180">Tüm metni görünür olması düğme denetimleri genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b79ee-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="b79ee-181">Düğme tıklamaları işlemek için</span><span class="sxs-lookup"><span data-stu-id="b79ee-181">To handle button clicks</span></span>  
  
1. <span data-ttu-id="b79ee-182">Çift **sipariş ayrıntıları** üzerinde **Form1** button1 olay işleyicisine kod Düzenleyicisi'nde açın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2. <span data-ttu-id="b79ee-183">Aşağıdaki kodu yazın `button1` işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="b79ee-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3. <span data-ttu-id="b79ee-184">Şimdi çift **button2** üzerinde **Form1** açmak için `button2` işleyicisi</span><span class="sxs-lookup"><span data-stu-id="b79ee-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4. <span data-ttu-id="b79ee-185">Aşağıdaki kodu yazın `button2` işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="b79ee-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="b79ee-186">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="b79ee-186">Testing the Application</span></span>  
 <span data-ttu-id="b79ee-187">Artık uygulamanızı test etmek için zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="b79ee-187">Now it is time to test your application.</span></span> <span data-ttu-id="b79ee-188">Veri deposu ile ilgili iki saklı yordam hangi eylemleri için sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="b79ee-189">Bu, girdiğiniz tüm OrderID için dahil edilen ürünleri döndürmek için veya bir geçmiş girdiğiniz CustomerID sipariş edilen ürünleri döndürmek için eylemlerdir.</span><span class="sxs-lookup"><span data-stu-id="b79ee-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="b79ee-190">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="b79ee-190">To test the application</span></span>  
  
1. <span data-ttu-id="b79ee-191">Hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="b79ee-192">Form1 görünür.</span><span class="sxs-lookup"><span data-stu-id="b79ee-192">Form1 appears.</span></span>  
  
2. <span data-ttu-id="b79ee-193">İçinde **girin OrderID** kutusuna `10249`ve ardından **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b79ee-194">Bir ileti kutusu 10249 siparişteki ürünleri listeler.</span><span class="sxs-lookup"><span data-stu-id="b79ee-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="b79ee-195">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-195">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="b79ee-196">İçinde **girin CustomerID** kutusuna `ALFKI`ve ardından **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="b79ee-197">ALFKI müşteri siparişi geçmişi listeleyen bir ileti kutusu görünür.</span><span class="sxs-lookup"><span data-stu-id="b79ee-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="b79ee-198">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-198">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="b79ee-199">İçinde **girin OrderID** kutusuna `123`ve ardından **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="b79ee-200">"Sonuç yok." görüntüleyen bir ileti kutusu görünür</span><span class="sxs-lookup"><span data-stu-id="b79ee-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="b79ee-201">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="b79ee-201">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="b79ee-202">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="b79ee-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="b79ee-203">Hata ayıklama oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="b79ee-203">The debug session closes.</span></span>  
  
6. <span data-ttu-id="b79ee-204">Denemeler tamamladınız, tıklayabilirsiniz **Projeyi Kapat** üzerinde **dosya** menüsünde ve istendiğinde projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="b79ee-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b79ee-205">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="b79ee-205">Next Steps</span></span>  
 <span data-ttu-id="b79ee-206">Bu proje, bazı değişiklikler yaparak geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b79ee-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="b79ee-207">Örneğin, bir liste kutusunda mevcut saklı yordamları listeler ve yürütmek için hangi yordamların seçmesine sahip.</span><span class="sxs-lookup"><span data-stu-id="b79ee-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="b79ee-208">Ayrıca, raporları bir metin dosyasına çıkışı akış.</span><span class="sxs-lookup"><span data-stu-id="b79ee-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b79ee-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b79ee-209">See also</span></span>

- [<span data-ttu-id="b79ee-210">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="b79ee-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="b79ee-211">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="b79ee-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
