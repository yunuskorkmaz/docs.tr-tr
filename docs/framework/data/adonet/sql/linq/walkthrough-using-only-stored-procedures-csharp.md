---
title: 'İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792089"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="74e2b-102">İzlenecek yol: Yalnızca Saklı Yordamları Kullanma (C#)</span><span class="sxs-lookup"><span data-stu-id="74e2b-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="74e2b-103">Bu izlenecek yol, yalnızca saklı yordamları yürüterek verilere erişmek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] için temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="74e2b-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="74e2b-104">Bu yaklaşım genellikle veritabanı yöneticileri tarafından veri deposuna nasıl erişildiğini sınırlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="74e2b-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Uygulamalarda saklı yordamları, özellikle, `Update`ve `Delete` işlemleri için `Create`varsayılan davranışı geçersiz kılmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="74e2b-106">Daha fazla bilgi için bkz. [Insert, Update ve DELETE Işlemlerini özelleştirme](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="74e2b-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="74e2b-107">Bu izlenecek yolun amaçları doğrultusunda, Northwind örnek veritabanındaki Saklı yordamlarla eşleştirilmiş iki yöntem kullanacaksınız: CustOrdersDetail ve CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="74e2b-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="74e2b-108">Eşleme, bir C# dosya oluşturmak Için SQLMetal komut satırı aracını çalıştırdığınızda oluşur.</span><span class="sxs-lookup"><span data-stu-id="74e2b-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="74e2b-109">Daha fazla bilgi için bu izlenecek yolun ilerleyen kısımlarında yer aldığı Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="74e2b-110">Bu izlenecek yol, Nesne İlişkisel Tasarımcısı bağlı değildir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="74e2b-111">Visual Studio kullanan geliştiriciler, saklı yordam işlevselliğini uygulamak için O/R tasarımcısını da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="74e2b-112">Bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="74e2b-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="74e2b-113">Bu izlenecek yol, Visual C# Development ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="74e2b-114">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="74e2b-114">Prerequisites</span></span>

<span data-ttu-id="74e2b-115">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="74e2b-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="74e2b-116">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest7") kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="74e2b-117">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="74e2b-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="74e2b-118">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="74e2b-118">The Northwind sample database.</span></span>

     <span data-ttu-id="74e2b-119">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="74e2b-120">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="74e2b-120">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="74e2b-121">Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest7 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="74e2b-122">Northwind C# veritabanından oluşturulan bir kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="74e2b-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="74e2b-123">Bu izlenecek yol, aşağıdaki komut satırı ile SqlMetal Aracı kullanılarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="74e2b-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="74e2b-124">**SqlMetal/Code: "c:\linqtest7\northwind.cs"/Language: CSharp "c:\linqtest7\kuzey WND.mdf"/sprocs/Functions/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="74e2b-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="74e2b-125">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="74e2b-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="74e2b-126">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74e2b-126">Overview</span></span>

<span data-ttu-id="74e2b-127">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="74e2b-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="74e2b-128">Visual Studio 'da çözümü kurma. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e2b-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="74e2b-129">System. Data. LINQ bütünleştirilmiş kodu projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="74e2b-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="74e2b-130">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="74e2b-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="74e2b-131">Veritabanıyla bağlantı oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="74e2b-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="74e2b-132">Kullanıcı arabirimini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="74e2b-132">Setting up the user interface.</span></span>

- <span data-ttu-id="74e2b-133">Uygulamayı çalıştırma ve test etme.</span><span class="sxs-lookup"><span data-stu-id="74e2b-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="74e2b-134">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="74e2b-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="74e2b-135">Bu ilk görevde, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="74e2b-136">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="74e2b-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="74e2b-137">Visual Studio **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="74e2b-138">**Yeni proje** Iletişim kutusundaki **Proje türleri** bölmesinde, **C#görsel**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="74e2b-139">**Şablonlar** bölmesinde **Windows Forms uygulama**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="74e2b-140">**Ad** kutusuna **SprocOnlyApp**yazın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="74e2b-141">**Konum** kutusunda, proje dosyalarınızı nerede depolamak istediğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="74e2b-142">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-142">Click **OK**.</span></span>

     <span data-ttu-id="74e2b-143">Windows Form Tasarımcısı açılır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="74e2b-144">LINQ to SQL bütünleştirilmiş kod başvurusu ekleniyor</span><span class="sxs-lookup"><span data-stu-id="74e2b-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="74e2b-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Derleme, standart Windows Forms uygulama şablonuna dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="74e2b-146">Aşağıdaki adımlarda açıklandığı gibi derlemeyi kendiniz eklemeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="74e2b-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="74e2b-147">System. Data. LINQ. dll eklemek için</span><span class="sxs-lookup"><span data-stu-id="74e2b-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="74e2b-148">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="74e2b-149">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="74e2b-150">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="74e2b-151">Northwind kod dosyasını projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="74e2b-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="74e2b-152">Bu adımda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SqlMetal aracını kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="74e2b-153">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="74e2b-154">Projeye Northwind kod dosyasını eklemek için</span><span class="sxs-lookup"><span data-stu-id="74e2b-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="74e2b-155">**Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="74e2b-156">**Varolan öğe Ekle** iletişim kutusunda c:\linqtest7\northwind.cs dizinine gidin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="74e2b-157">Northwind.cs dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="74e2b-158">Veritabanı bağlantısı oluşturma</span><span class="sxs-lookup"><span data-stu-id="74e2b-158">Creating a Database Connection</span></span>

<span data-ttu-id="74e2b-159">Bu adımda, Northwind örnek veritabanına olan bağlantıyı tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="74e2b-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="74e2b-160">Bu izlenecek yol, yol olarak "c:\linqtest7\kuzeydoğu WND.exe" kullanır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="74e2b-161">Veritabanı bağlantısını oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="74e2b-161">To create the database connection</span></span>

1. <span data-ttu-id="74e2b-162">**Çözüm Gezgini**' de, **Form1.cs**' a sağ tıklayın ve ardından **kodu görüntüle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="74e2b-163">`Form1` Sınıfına aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="74e2b-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="74e2b-164">Kullanıcı arabirimini ayarlama</span><span class="sxs-lookup"><span data-stu-id="74e2b-164">Setting up the User Interface</span></span>

<span data-ttu-id="74e2b-165">Bu görevde, kullanıcıların veritabanındaki verilere erişmek için saklı yordamları yürütebilmesi için bir arayüz ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="74e2b-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="74e2b-166">Bu kılavuzlarla geliştirdiğiniz uygulamalarda, kullanıcılar veritabanındaki verilere yalnızca uygulamada gömülü saklı yordamları kullanarak erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="74e2b-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="74e2b-167">Kullanıcı arabirimini ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="74e2b-167">To set up the user interface</span></span>

1. <span data-ttu-id="74e2b-168">Windows Form Tasarımcısı dön (**Form1. cs [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="74e2b-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="74e2b-169">**Görünüm** menüsünde **araç kutusu**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="74e2b-170">Araç kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="74e2b-171">Bu bölümde kalan adımları gerçekleştirirken araç kutusunu açık tutmak için otomatik **gizleme** raptiye ' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="74e2b-172">İki düğme, iki metin kutusu ve iki etiketi araç kutusundan **Form1**üzerine sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="74e2b-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="74e2b-173">Denetimleri, eşlik eden çizimde olduğu gibi düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="74e2b-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="74e2b-174">Denetimlerin kolayca sığması için **Form1** ' i genişletin.</span><span class="sxs-lookup"><span data-stu-id="74e2b-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="74e2b-175">**Label1**öğesine sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="74e2b-176">**Text** özelliğini **Label1** olarak değiştirin, **OrderID: yazın**.</span><span class="sxs-lookup"><span data-stu-id="74e2b-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="74e2b-177">**Etiket 2**için aynı şekilde, **Etiket 2** ' deki **Text** özelliğini CustomerID olarak değiştirin **:** .</span><span class="sxs-lookup"><span data-stu-id="74e2b-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="74e2b-178">Aynı şekilde, **button1** için **metin** özelliğini **sipariş ayrıntıları**olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="74e2b-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="74e2b-179">**Button2** için **metin** özelliğini **sıra geçmişiyle**değiştirin.</span><span class="sxs-lookup"><span data-stu-id="74e2b-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="74e2b-180">Düğme denetimlerini tüm metinlerin görünür olması için genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="74e2b-181">Düğme tıklamalarını işlemek için</span><span class="sxs-lookup"><span data-stu-id="74e2b-181">To handle button clicks</span></span>

1. <span data-ttu-id="74e2b-182">Kod düzenleyicisinde button1 olay işleyicisini açmak için **Form1** üzerindeki **Order details** öğesine çift tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="74e2b-183">`button1` İşleyiciye aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="74e2b-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="74e2b-184">Şimdi `button2` işleyiciyi açmak için **Form1** üzerinde **button2** 'e çift tıklayın</span><span class="sxs-lookup"><span data-stu-id="74e2b-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="74e2b-185">`button2` İşleyiciye aşağıdaki kodu yazın:</span><span class="sxs-lookup"><span data-stu-id="74e2b-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="74e2b-186">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="74e2b-186">Testing the Application</span></span>

<span data-ttu-id="74e2b-187">Artık uygulamanızı test etmek zaman alabilir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-187">Now it is time to test your application.</span></span> <span data-ttu-id="74e2b-188">Veri deposu ile kişinizin, iki saklı yordamın gerçekleştirebileceği eylemlerle sınırlı olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="74e2b-189">Bu eylemler, girdiğiniz herhangi bir OrderID 'ye dahil edilen ürünleri döndürmek veya girdiğiniz her bir müşteri için sipariş edilen ürünlerin geçmişini döndürmemelidir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="74e2b-190">Uygulamayı test etmek için</span><span class="sxs-lookup"><span data-stu-id="74e2b-190">To test the application</span></span>

1. <span data-ttu-id="74e2b-191">Hata ayıklamayı başlatmak için F5 'e basın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="74e2b-192">Form1 görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-192">Form1 appears.</span></span>

2. <span data-ttu-id="74e2b-193">**OrderID girin** kutusuna yazın `10249`ve ardından **sipariş ayrıntıları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="74e2b-194">Sipariş 10249 ' de yer alan ürünler bir ileti kutusunda listelenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="74e2b-195">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="74e2b-196">**CustomerID girin** kutusuna yazın `ALFKI`ve ardından **Sipariş geçmişi**' ne tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="74e2b-197">Müşteri ALFKI için sipariş geçmişini listeleyen bir ileti kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="74e2b-198">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="74e2b-199">**OrderID girin** kutusuna yazın `123`ve ardından **sipariş ayrıntıları**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="74e2b-200">"Sonuç yok" iletisini görüntüleyen bir ileti kutusu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="74e2b-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="74e2b-201">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="74e2b-202">**Hata Ayıkla** menüsünde, **hata ayıklamayı Durdur**' u tıklatın.</span><span class="sxs-lookup"><span data-stu-id="74e2b-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="74e2b-203">Hata ayıklama oturumu kapanır.</span><span class="sxs-lookup"><span data-stu-id="74e2b-203">The debug session closes.</span></span>

6. <span data-ttu-id="74e2b-204">Deneme işleminizi tamamladıysanız **Dosya** menüsünde **Projeyi Kapat** ' a tıklayabilir ve istendiğinde projenizi kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="74e2b-205">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="74e2b-205">Next Steps</span></span>

<span data-ttu-id="74e2b-206">Bu projeyi, bazı değişiklikler yaparak geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="74e2b-207">Örneğin, kullanılabilir saklı yordamları bir liste kutusunda listeleyebilir ve kullanıcının hangi yordamları yürütebileceği seçmesini sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="74e2b-208">Ayrıca raporların çıkışını bir metin dosyasına akışla aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="74e2b-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74e2b-209">See also</span></span>

- [<span data-ttu-id="74e2b-210">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="74e2b-210">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="74e2b-211">Saklı Yordamlar</span><span class="sxs-lookup"><span data-stu-id="74e2b-211">Stored Procedures</span></span>](stored-procedures.md)
