---
description: 'Daha fazla bilgi edinin: Izlenecek yol: yalnızca saklı yordamları kullanma (Visual Basic)'
title: 'İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: b368bdd5717c0f424192c3eabb8058d633cac61e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791770"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="5d38c-103">İzlenecek yol: Yalnızca Saklı Yordamlar Kullanma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d38c-103">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>

<span data-ttu-id="5d38c-104">Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yalnızca saklı yordamlar kullanılarak verilere erişmek için temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d38c-104">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="5d38c-105">Bu yaklaşım genellikle veritabanı yöneticileri tarafından veri deposuna nasıl erişildiğini sınırlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-105">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d38c-106">Uygulamalarda saklı yordamları, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] özellikle `Create` , `Update` ve işlemleri için varsayılan davranışı geçersiz kılmak için de kullanabilirsiniz `Delete` .</span><span class="sxs-lookup"><span data-stu-id="5d38c-106">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="5d38c-107">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5d38c-107">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="5d38c-108">Bu izlenecek yolun amaçları doğrultusunda, Northwind örnek veritabanındaki Saklı yordamlarla eşleştirilmiş iki yöntem kullanacaksınız: CustOrdersDetail ve CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="5d38c-108">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="5d38c-109">Eşleme, bir Visual Basic dosyası oluşturmak için SqlMetal komut satırı aracını çalıştırdığınızda oluşur.</span><span class="sxs-lookup"><span data-stu-id="5d38c-109">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="5d38c-110">Daha fazla bilgi için bu izlenecek yolun ilerleyen kısımlarında yer aldığı Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-110">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="5d38c-111">Bu izlenecek yol, Nesne İlişkisel Tasarımcısı bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-111">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="5d38c-112">Visual Studio kullanan geliştiriciler, saklı yordam işlevselliğini uygulamak için O/R tasarımcısını da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-112">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="5d38c-113">Bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="5d38c-113">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="5d38c-114">Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-114">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5d38c-115">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="5d38c-115">Prerequisites</span></span>  

 <span data-ttu-id="5d38c-116">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5d38c-116">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="5d38c-117">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest3") kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-117">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="5d38c-118">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d38c-118">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="5d38c-119">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="5d38c-119">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="5d38c-120">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-120">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="5d38c-121">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="5d38c-121">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="5d38c-122">Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest3 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-122">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
- <span data-ttu-id="5d38c-123">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="5d38c-123">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="5d38c-124">Bu izlenecek yol, aşağıdaki komut satırı ile SqlMetal Aracı kullanılarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="5d38c-124">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="5d38c-125">**SqlMetal/Code: "c:\linqtest3\northwind.exe"/Language: vb "c:\linqtest3\kuzeydoğu WND.exe"/sprocs/Functions/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="5d38c-125">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="5d38c-126">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5d38c-126">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5d38c-127">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5d38c-127">Overview</span></span>  

 <span data-ttu-id="5d38c-128">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="5d38c-128">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="5d38c-129">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözümü kurma.</span><span class="sxs-lookup"><span data-stu-id="5d38c-129">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="5d38c-130">System. Data. LINQ bütünleştirilmiş kodu projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5d38c-130">Adding the System.Data.Linq assembly to the project.</span></span>  
  
- <span data-ttu-id="5d38c-131">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="5d38c-131">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="5d38c-132">Veritabanına bağlantı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="5d38c-132">Creating a connection to the database.</span></span>  
  
- <span data-ttu-id="5d38c-133">Kullanıcı arabirimini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="5d38c-133">Setting up the user interface.</span></span>  
  
- <span data-ttu-id="5d38c-134">Uygulamayı çalıştırma ve test etme.</span><span class="sxs-lookup"><span data-stu-id="5d38c-134">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="5d38c-135">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d38c-135">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="5d38c-136">Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5d38c-136">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="5d38c-137">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5d38c-137">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="5d38c-138">Visual Studio **Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-138">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="5d38c-139">**Yeni proje** Iletişim kutusundaki **proje türleri** bölmesinde **Visual Basic** öğesini genişletin ve ardından **Windows**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-139">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3. <span data-ttu-id="5d38c-140">**Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-140">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4. <span data-ttu-id="5d38c-141">**Ad** kutusuna **SprocOnlyApp** yazın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-141">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5. <span data-ttu-id="5d38c-142">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="5d38c-143">Windows Form Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="5d38c-144">LINQ to SQL bütünleştirilmiş kod başvurusu ekleniyor</span><span class="sxs-lookup"><span data-stu-id="5d38c-144">Adding the LINQ to SQL Assembly Reference</span></span>  

 <span data-ttu-id="5d38c-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Derleme, standart Windows Forms uygulama şablonuna dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="5d38c-146">Aşağıdaki adımlarda açıklandığı gibi derlemeyi kendiniz eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="5d38c-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="5d38c-147">System.Data.Linq.dll eklemek için</span><span class="sxs-lookup"><span data-stu-id="5d38c-147">To add System.Data.Linq.dll</span></span>  
  
1. <span data-ttu-id="5d38c-148">**Çözüm Gezgini**, **tüm dosyaları göster**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-148">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2. <span data-ttu-id="5d38c-149">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-149">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3. <span data-ttu-id="5d38c-150">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-150">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="5d38c-151">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-151">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5d38c-152">Northwind kod dosyasını projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="5d38c-152">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="5d38c-153">Bu adımda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SqlMetal aracını kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-153">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="5d38c-154">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-154">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5d38c-155">Projeye Northwind kod dosyasını eklemek için</span><span class="sxs-lookup"><span data-stu-id="5d38c-155">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="5d38c-156">**Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-156">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="5d38c-157">**Varolan öğe Ekle** iletişim kutusunda c:\linqtest3\northwind.exe ' e gidin ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-157">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="5d38c-158">Northwind. vb dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-158">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="5d38c-159">Veritabanı bağlantısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d38c-159">Creating a Database Connection</span></span>  

 <span data-ttu-id="5d38c-160">Bu adımda, Northwind örnek veritabanına olan bağlantıyı tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="5d38c-160">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="5d38c-161">Bu izlenecek yol, yol olarak "c:\linqtest3\kuzeydoğu WND.exe" kullanır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-161">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
### <a name="to-create-the-database-connection"></a><span data-ttu-id="5d38c-162">Veritabanı bağlantısını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5d38c-162">To create the database connection</span></span>  
  
1. <span data-ttu-id="5d38c-163">**Çözüm Gezgini**, **Form1. vb** öğesine sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-163">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="5d38c-164">`Class Form1` Kod düzenleyicisinde görünür.</span><span class="sxs-lookup"><span data-stu-id="5d38c-164">`Class Form1` appears in the code editor.</span></span>  
  
2. <span data-ttu-id="5d38c-165">Kod bloğuna aşağıdaki kodu yazın `Form1` :</span><span class="sxs-lookup"><span data-stu-id="5d38c-165">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="5d38c-166">Kullanıcı arabirimini ayarlama</span><span class="sxs-lookup"><span data-stu-id="5d38c-166">Setting up the User Interface</span></span>  

 <span data-ttu-id="5d38c-167">Bu görevde, kullanıcıların veritabanındaki verilere erişmek için saklı yordamları yürütebilmesi için bir arabirim oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-167">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="5d38c-168">Bu kılavuzlarla geliştirdiğiniz uygulamada, kullanıcılar veritabanındaki verilere yalnızca uygulamada gömülü saklı yordamları kullanarak erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="5d38c-168">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="5d38c-169">Kullanıcı arabirimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="5d38c-169">To set up the user interface</span></span>  
  
1. <span data-ttu-id="5d38c-170">Windows Form Tasarımcısı dön (**Form1. vb [Design]**).</span><span class="sxs-lookup"><span data-stu-id="5d38c-170">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2. <span data-ttu-id="5d38c-171">**Görünüm** menüsünde **araç kutusu**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-171">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="5d38c-172">Araç kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-172">The toolbox opens.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5d38c-173">Bu bölümde kalan adımları gerçekleştirirken araç kutusunu açık tutmak için otomatik **gizleme** raptiye ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-173">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3. <span data-ttu-id="5d38c-174">İki düğme, iki metin kutusu ve iki etiketi araç kutusundan **Form1** üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="5d38c-174">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="5d38c-175">Denetimleri, eşlik eden çizimde olduğu gibi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="5d38c-175">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="5d38c-176">Denetimlerin kolayca sığması için **Form1** ' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="5d38c-176">Expand **Form1** so that the controls fit easily.</span></span>  
  
4. <span data-ttu-id="5d38c-177">**Label1** öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-177">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5. <span data-ttu-id="5d38c-178">**Text** özelliğini **Label1** olarak değiştirin, **OrderID: yazın**.</span><span class="sxs-lookup"><span data-stu-id="5d38c-178">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6. <span data-ttu-id="5d38c-179">**Etiket 2** için aynı şekilde, **Etiket 2** ' deki **Text** özelliğini CustomerID olarak değiştirin **:**.</span><span class="sxs-lookup"><span data-stu-id="5d38c-179">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7. <span data-ttu-id="5d38c-180">Aynı şekilde, **button1** için **metin** özelliğini **sipariş ayrıntıları** olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5d38c-180">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8. <span data-ttu-id="5d38c-181">**Button2** için **metin** özelliğini **sıra geçmişiyle** değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5d38c-181">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="5d38c-182">Düğme denetimlerini tüm metinlerin görünür olması için genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-182">Widen the button controls so that all the text is visible.</span></span>  
  
### <a name="to-handle-button-clicks"></a><span data-ttu-id="5d38c-183">Düğme tıklamalarını işlemek için</span><span class="sxs-lookup"><span data-stu-id="5d38c-183">To handle button clicks</span></span>  
  
1. <span data-ttu-id="5d38c-184">Olay işleyicisini oluşturmak ve kod düzenleyicisini açmak için **Form1** üzerindeki **Düzen ayrıntıları** ' na çift tıklayın `Button1` .</span><span class="sxs-lookup"><span data-stu-id="5d38c-184">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2. <span data-ttu-id="5d38c-185">İşleyiciye aşağıdaki kodu yazın `Button1` :</span><span class="sxs-lookup"><span data-stu-id="5d38c-185">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3. <span data-ttu-id="5d38c-186">Şimdi,  `Button2` olay işleyicisini oluşturmak ve kod düzenleyicisini açmak Için Form1 üzerinde Button2 'e çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-186">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4. <span data-ttu-id="5d38c-187">İşleyiciye aşağıdaki kodu yazın `Button2` :</span><span class="sxs-lookup"><span data-stu-id="5d38c-187">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5d38c-188">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="5d38c-188">Testing the Application</span></span>  

 <span data-ttu-id="5d38c-189">Artık uygulamanızı test etmek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-189">Now it is time to test your application.</span></span> <span data-ttu-id="5d38c-190">Veri deposu ile kişinizin, iki saklı yordamın gerçekleştirebileceği eylemlerle sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-190">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="5d38c-191">Bu eylemler, girdiğiniz herhangi bir OrderID 'ye dahil edilen ürünleri döndürmek veya girdiğiniz her bir müşteri için sipariş edilen ürünlerin geçmişini döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-191">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="5d38c-192">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="5d38c-192">To test the application</span></span>  
  
1. <span data-ttu-id="5d38c-193">Hata ayıklamaya başlamak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-193">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="5d38c-194">Form1 görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-194">Form1 appears.</span></span>  
  
2. <span data-ttu-id="5d38c-195">**OrderID girin** kutusuna **10249** yazın ve ardından **sipariş ayrıntıları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-195">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="5d38c-196">Sipariş 10249 ' de yer alan ürünler bir ileti kutusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="5d38c-196">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="5d38c-197">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-197">Click **OK** to close the message box.</span></span>  
  
3. <span data-ttu-id="5d38c-198">**CustomerID girin** kutusuna yazın `ALFKI` ve ardından **Sipariş geçmişi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-198">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="5d38c-199">Bir ileti kutusu, müşteri ALFKI için sipariş geçmişini listeler.</span><span class="sxs-lookup"><span data-stu-id="5d38c-199">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="5d38c-200">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-200">Click **OK** to close the message box.</span></span>  
  
4. <span data-ttu-id="5d38c-201">**OrderID girin** kutusuna yazın `123` ve ardından **sipariş ayrıntıları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-201">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="5d38c-202">İleti kutusu "sonuç yok" iletisini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5d38c-202">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="5d38c-203">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-203">Click **OK** to close the message box.</span></span>  
  
5. <span data-ttu-id="5d38c-204">**Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' u tıklatın.</span><span class="sxs-lookup"><span data-stu-id="5d38c-204">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="5d38c-205">Hata ayıklama oturumu kapanır.</span><span class="sxs-lookup"><span data-stu-id="5d38c-205">The debug session closes.</span></span>  
  
6. <span data-ttu-id="5d38c-206">Deneme işleminizi tamamladıysanız **Dosya** menüsünde **Projeyi Kapat** ' a tıklayabilir ve istendiğinde projenizi kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-206">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5d38c-207">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="5d38c-207">Next Steps</span></span>  

 <span data-ttu-id="5d38c-208">Bu projeyi, bazı değişiklikler yaparak geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-208">You can enhance this project by making some changes.</span></span> <span data-ttu-id="5d38c-209">Örneğin, kullanılabilir saklı yordamları bir liste kutusunda listeleyebilir ve kullanıcının hangi yordamları yürütebileceği seçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-209">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="5d38c-210">Ayrıca raporların çıkışını bir metin dosyasına akışla aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-210">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d38c-211">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d38c-211">See also</span></span>

- [<span data-ttu-id="5d38c-212">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="5d38c-212">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="5d38c-213">Saklı yordamlar</span><span class="sxs-lookup"><span data-stu-id="5d38c-213">Stored Procedures</span></span>](stored-procedures.md)
