---
title: 'İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 1527e3b4b614d4e700ae0c2c0fc555e14c7bc8d2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314834"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="8b6b5-102">İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6b5-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="8b6b5-103">Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryosu kullanarak verilerine erişmek için saklı yordamlar yalnızca.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="8b6b5-104">Bu yaklaşım, genellikle veri deposu nasıl erişilir sınırlamak için Veritabanı yöneticileri tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b6b5-105">Saklı yordamları kullanabilirsiniz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle de varsayılan davranışı geçersiz kılmak için uygulamaları `Create`, `Update`, ve `Delete` işlemler.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="8b6b5-106">Daha fazla bilgi için [özelleştirme ekleme, güncelleştirme ve silme işlemleri](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b5-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="8b6b5-107">Bu izlenecek yolda amacı doğrultusunda, Northwind örnek veritabanındaki saklı yordamlar için eşlenen iki yöntemi kullanır: CustOrdersDetail ve CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="8b6b5-108">Eşleme, bir Visual Basic dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınız oluşur.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="8b6b5-109">Daha fazla bilgi için bu kılavuzda daha sonra Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="8b6b5-110">Bu izlenecek yol üzerinde kullanmayan [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b6b5-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="8b6b5-111">Visual Studio kullanan geliştiricilerin de kullanabilir [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] saklı yordam işlevselliği uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="8b6b5-112">Bkz: [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="8b6b5-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="8b6b5-113">Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8b6b5-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8b6b5-114">Prerequisites</span></span>  
 <span data-ttu-id="8b6b5-115">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="8b6b5-116">Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest3") kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="8b6b5-117">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="8b6b5-118">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="8b6b5-119">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="8b6b5-120">Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b5-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="8b6b5-121">Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest3 klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="8b6b5-122">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="8b6b5-123">Bu izlenecek yol, şu komut satırıyla SqlMetal Aracı'nı kullanarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     **<span data-ttu-id="8b6b5-124">sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions / pluralize</span><span class="sxs-lookup"><span data-stu-id="8b6b5-124">sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize</span></span>**  
  
     <span data-ttu-id="8b6b5-125">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8b6b5-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8b6b5-126">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8b6b5-126">Overview</span></span>  
 <span data-ttu-id="8b6b5-127">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="8b6b5-128">Ayarlama [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="8b6b5-129">System.Data.Linq derleme projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="8b6b5-130">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="8b6b5-131">Veritabanına bir bağlantı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="8b6b5-132">Kullanıcı arabirimi ayarlama.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="8b6b5-133">Çalıştıran ve uygulamayı test etme.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="8b6b5-134">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b5-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="8b6b5-135">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="8b6b5-136">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-136">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="8b6b5-137">Visual Studio **dosya** menüsünü tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="8b6b5-138">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusunda **Visual Basic**ve ardından **Windows**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="8b6b5-139">İçinde **şablonları** bölmesinde tıklayın **Windows Forms uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="8b6b5-140">İçinde **adı** kutusuna **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="8b6b5-141">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="8b6b5-142">Windows Forms Tasarımcısı'nı açar.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="8b6b5-143">LINQ SQL bütünleştirilmiş kod başvurusu ekleme</span><span class="sxs-lookup"><span data-stu-id="8b6b5-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="8b6b5-144">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Derleme standart Windows Forms uygulaması şablonu dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="8b6b5-145">Aşağıdaki adımlarda açıklandığı gibi derleme kendiniz eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="8b6b5-146">System.Data.Linq.dll eklemek için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-146">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="8b6b5-147">İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="8b6b5-148">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="8b6b5-149">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8b6b5-150">Derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8b6b5-151">Northwind kod dosyası projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="8b6b5-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="8b6b5-152">Bu adım Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SqlMetal Aracı'nı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="8b6b5-153">Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8b6b5-154">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-154">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="8b6b5-155">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="8b6b5-156">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest3\northwind.vb taşıyın ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="8b6b5-157">Northwind.vb dosya projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="8b6b5-158">Veritabanı bağlantısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="8b6b5-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="8b6b5-159">Bu adımda, Northwind örnek veritabanına bir bağlantı tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="8b6b5-160">Bu izlenecek yolu olarak "c:\linqtest3\northwnd.mdf" kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="8b6b5-161">Veritabanı bağlantısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-161">To create the database connection</span></span>  
  
1. <span data-ttu-id="8b6b5-162">İçinde **Çözüm Gezgini**, sağ **Form1.vb**ve ardından **kodu görüntüle**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     `Class Form1` <span data-ttu-id="8b6b5-163">Kod Düzenleyicisi'nde görünür.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-163">appears in the code editor.</span></span>  
  
2. <span data-ttu-id="8b6b5-164">Aşağıdaki kodu yazın `Form1` kod bloğu:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="8b6b5-165">Kullanıcı arabirimi ayarlama</span><span class="sxs-lookup"><span data-stu-id="8b6b5-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="8b6b5-166">Bu görevde, böylece kullanıcılar, veritabanındaki verilere erişmek için saklı yordamlar yürütebilir bir arabirim oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="8b6b5-167">Bu izlenecek yol ile geliştirdiğiniz uygulamada yalnızca katıştırılmış uygulama içinde saklı yordamları kullanarak veritabanındaki verileri kullanıcılar erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="8b6b5-168">Kullanıcı arabirimi oluşturan ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-168">To set up the user interface</span></span>  
  
1. <span data-ttu-id="8b6b5-169">İade için Windows Forms Tasarımcısı (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="8b6b5-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="8b6b5-170">Üzerinde **görünümü** menüsünde tıklatın **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="8b6b5-171">Araç kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b6b5-172">Tıklayın **AutoHide** Raptiye kalan gerçekleştirirken araç kutusu açık tutmak için bu bölümdeki adımlar.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="8b6b5-173">Sürükleyin iki düğme, iki metin kutuları ve iki etiket araç kutusundan **Form1**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="8b6b5-174">Eşlik eden resimde olduğu gibi denetimleri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="8b6b5-175">Genişletin **Form1** denetimleri bir kolayca uyacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="8b6b5-176">Sağ **Label1**ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="8b6b5-177">Değişiklik **metin** özelliğinden **Label1** için **OrderID girin:**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="8b6b5-178">Aynı şekilde **etiket 2**, değiştirme **metin** özelliğinden **etiket 2** için **CustomerID girin:**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="8b6b5-179">Aynı şekilde değiştirme **metin** özelliği **Button1** için **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="8b6b5-180">Değişiklik **metin** özelliği **Button2** için **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="8b6b5-181">Tüm metni görünür olması düğme denetimleri genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="8b6b5-182">Düğme tıklamaları işlemek için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-182">To handle button clicks</span></span>  
  
1. <span data-ttu-id="8b6b5-183">Çift **sipariş ayrıntıları** üzerinde **Form1** oluşturmak için `Button1` olay işleyicisi ve Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="8b6b5-184">Aşağıdaki kodu yazın `Button1` işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="8b6b5-185">Şimdi çift **Button2** oluşturmak için Form1 üzerinde `Button2` olay işleyicisi ve Kod Düzenleyicisi'ni açın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="8b6b5-186">Aşağıdaki kodu yazın `Button2` işleyicisi:</span><span class="sxs-lookup"><span data-stu-id="8b6b5-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="8b6b5-187">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="8b6b5-187">Testing the Application</span></span>  
 <span data-ttu-id="8b6b5-188">Artık uygulamanızı test etmek için zamanı geldi.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-188">Now it is time to test your application.</span></span> <span data-ttu-id="8b6b5-189">Veri deposu ile ilgili iki saklı yordam hangi eylemleri için sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="8b6b5-190">Bu, girdiğiniz tüm OrderID için dahil edilen ürünleri döndürmek için veya bir geçmiş girdiğiniz CustomerID sipariş edilen ürünleri döndürmek için eylemlerdir.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="8b6b5-191">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="8b6b5-191">To test the application</span></span>  
  
1. <span data-ttu-id="8b6b5-192">Hata ayıklamayı başlatmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="8b6b5-193">Form1 görünür.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-193">Form1 appears.</span></span>  
  
2. <span data-ttu-id="8b6b5-194">İçinde **girin OrderID** kutusuna **10249** ve ardından **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="8b6b5-195">Bir ileti kutusu 10249 siparişteki ürünleri listeler.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="8b6b5-196">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-196">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="8b6b5-197">İçinde **girin CustomerID** kutusuna `ALFKI`ve ardından **siparişi geçmişi**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="8b6b5-198">Bir ileti kutusu ALFKI müşteri siparişi geçmişi listeler.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="8b6b5-199">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-199">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="8b6b5-200">İçinde **girin OrderID** kutusuna `123`ve ardından **sipariş ayrıntıları**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="8b6b5-201">"Sonuç yok." bir ileti kutusu görüntüler</span><span class="sxs-lookup"><span data-stu-id="8b6b5-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="8b6b5-202">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-202">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="8b6b5-203">Üzerinde **hata ayıklama** menüsünü tıklatın **hata ayıklamayı durdurmak**.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="8b6b5-204">Hata ayıklama oturumunu kapatır.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-204">The debug session closes.</span></span>  
  
6. <span data-ttu-id="8b6b5-205">Denemeler tamamladınız, tıklayabilirsiniz **Projeyi Kapat** üzerinde **dosya** menüsünde ve istendiğinde projenizi kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8b6b5-206">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="8b6b5-206">Next Steps</span></span>  
 <span data-ttu-id="8b6b5-207">Bu proje, bazı değişiklikler yaparak geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="8b6b5-208">Örneğin, bir liste kutusunda mevcut saklı yordamları listeler ve yürütmek için hangi yordamların seçmesine sahip.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="8b6b5-209">Ayrıca, raporları bir metin dosyasına çıkışı akış.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6b5-210">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b6b5-210">See also</span></span>

- [<span data-ttu-id="8b6b5-211">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="8b6b5-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="8b6b5-212">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="8b6b5-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
