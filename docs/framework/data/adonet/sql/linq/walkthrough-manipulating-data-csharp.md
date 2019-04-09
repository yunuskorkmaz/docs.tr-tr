---
title: 'İzlenecek yol: Verileri Düzenleme (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: 2a4b9fc5bf9afcace373a3f09b246e2bffd49e3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143292"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="8c3da-102">İzlenecek yol: Verileri Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="8c3da-102">Walkthrough: Manipulating Data (C#)</span></span>
<span data-ttu-id="8c3da-103">Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryo ekleme, değiştirme ve bir veritabanındaki verileri siliniyor.</span><span class="sxs-lookup"><span data-stu-id="8c3da-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="8c3da-104">Örnek Northwind veritabanının bir kopyasını bir müşteri eklemek, bir müşterinin adını değiştirin ve sipariş silmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="8c3da-105">Bu izlenecek yol, Visual kullanılarak yazılmış olduğundan C# geliştirme ayarları.</span><span class="sxs-lookup"><span data-stu-id="8c3da-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8c3da-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="8c3da-106">Prerequisites</span></span>  
 <span data-ttu-id="8c3da-107">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8c3da-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="8c3da-108">Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest6") kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c3da-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="8c3da-109">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8c3da-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="8c3da-110">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="8c3da-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="8c3da-111">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3da-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="8c3da-112">Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8c3da-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="8c3da-113">Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest6 klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
-   <span data-ttu-id="8c3da-114">A C# Northwind veritabanından oluşturulan kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="8c3da-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="8c3da-115">Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı.</span><span class="sxs-lookup"><span data-stu-id="8c3da-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="8c3da-116">Bu izlenecek yol, şu komut satırıyla SQLMetal Aracı'nı kullanarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="8c3da-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     **<span data-ttu-id="8c3da-117">sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" / pluralize</span><span class="sxs-lookup"><span data-stu-id="8c3da-117">sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize</span></span>**  
  
     <span data-ttu-id="8c3da-118">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="8c3da-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8c3da-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8c3da-119">Overview</span></span>  
 <span data-ttu-id="8c3da-120">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="8c3da-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="8c3da-121">Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.</span><span class="sxs-lookup"><span data-stu-id="8c3da-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="8c3da-122">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="8c3da-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="8c3da-123">Yeni bir müşteri nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="8c3da-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="8c3da-124">Bir müşteri kişi adını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="8c3da-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="8c3da-125">Bir sipariş siliniyor.</span><span class="sxs-lookup"><span data-stu-id="8c3da-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="8c3da-126">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="8c3da-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="8c3da-127">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c3da-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="8c3da-128">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="8c3da-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="8c3da-129">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8c3da-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="8c3da-130">Visual Studio'da **dosya** menüsünde **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="8c3da-131">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual C#** .</span><span class="sxs-lookup"><span data-stu-id="8c3da-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="8c3da-132">İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="8c3da-133">İçinde **adı** kutusuna **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="8c3da-134">İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="8c3da-135">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="8c3da-136">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="8c3da-136">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="8c3da-137">Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8c3da-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="8c3da-138">Projenize bir başvuru olarak System.Data.Linq listede yoksa, aşağıdaki adımlarda açıklandığı gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c3da-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="8c3da-139">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-139">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="8c3da-140">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="8c3da-141">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8c3da-142">Derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="8c3da-142">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="8c3da-143">Aşağıdaki yönergeler, Program.cs dosyasının en üstüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8c3da-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8c3da-144">Northwind kod dosyası projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="8c3da-144">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="8c3da-145">Bu adımları, Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SQLMetal Aracı'nı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="8c3da-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="8c3da-146">Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="8c3da-147">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-147">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="8c3da-148">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="8c3da-149">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest6\northwind.cs gidin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="8c3da-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="8c3da-150">Northwind.cs dosya projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="8c3da-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="8c3da-151">Veritabanı bağlantısı kurma</span><span class="sxs-lookup"><span data-stu-id="8c3da-151">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="8c3da-152">İlk olarak, veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="8c3da-152">First, test your connection to the database.</span></span> <span data-ttu-id="8c3da-153">Özellikle veritabanı Northwnd, hiçbir i olduğunu unutmayın. karakter.</span><span class="sxs-lookup"><span data-stu-id="8c3da-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="8c3da-154">Sonraki adımlarda hatalar oluşturur, Northwind kısmi sınıf nasıl yazıldığını belirlemek için northwind.cs dosyasını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="8c3da-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="8c3da-155">Veritabanı bağlantısını test etmek ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="8c3da-155">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="8c3da-156">İçine aşağıdaki kodu yazın veya yapıştırın `Main` Program sınıfına yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c3da-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2.  <span data-ttu-id="8c3da-157">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="8c3da-158">A **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="8c3da-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="8c3da-159">Enter tuşuna basarak uygulamayı kapatabilirsiniz **konsol** penceresinde veya tıklayarak **hata ayıklamayı Durdur** Visual Studio **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="8c3da-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="8c3da-160">Yeni varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="8c3da-160">Creating a New Entity</span></span>  
 <span data-ttu-id="8c3da-161">Yeni bir varlık oluştururken oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="8c3da-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="8c3da-162">Nesneleri oluşturabilirsiniz (gibi `Customer`) kullanarak `new` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="8c3da-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="8c3da-163">Bu ve aşağıdaki bölümler, yalnızca yerel önbelleğe değişiklikler yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="8c3da-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="8c3da-164">Çağırana kadar hiçbir değişiklik veritabanına gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Bu izlenecek yolun sonuna doğru.</span><span class="sxs-lookup"><span data-stu-id="8c3da-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="8c3da-165">Yeni bir müşteri varlığı nesne eklemek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-165">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="8c3da-166">Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine();` içinde `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="8c3da-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2.  <span data-ttu-id="8c3da-167">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-167">Press F5 to debug the solution.</span></span>  
  
3.  <span data-ttu-id="8c3da-168">Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak ve gözden geçirme devam etmek için.</span><span class="sxs-lookup"><span data-stu-id="8c3da-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="8c3da-169">Bir varlığı güncelleştirmek</span><span class="sxs-lookup"><span data-stu-id="8c3da-169">Updating an Entity</span></span>  
 <span data-ttu-id="8c3da-170">Aşağıdaki adımlarda, alacak bir `Customer` nesne ve onun özelliklerden birini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8c3da-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="8c3da-171">Bir müşteri adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-171">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="8c3da-172">Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="8c3da-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="8c3da-173">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="8c3da-173">Deleting an Entity</span></span>  
 <span data-ttu-id="8c3da-174">Aynı müşteri nesnesini kullanarak, ilk sırada silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8c3da-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="8c3da-175">Aşağıdaki kod ilişkileri sever gösterilmektedir satırlar ve veritabanından satır silme arasında.</span><span class="sxs-lookup"><span data-stu-id="8c3da-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="8c3da-176">Önce aşağıdaki kodu ekleyin `Console.ReadLine` nesnelerin nasıl silinebilir görmek için:</span><span class="sxs-lookup"><span data-stu-id="8c3da-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="8c3da-177">Bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-177">To delete a row</span></span>  
  
-   <span data-ttu-id="8c3da-178">Aşağıdaki kodu ekleyin hemen üzerinde `Console.ReadLine();`:</span><span class="sxs-lookup"><span data-stu-id="8c3da-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="8c3da-179">Veritabanına değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="8c3da-179">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="8c3da-180">Oluşturmak için gereken son güncelleştirme ve silme nesneleri, aslında veritabanına değişiklikleri göndermek için adımdır.</span><span class="sxs-lookup"><span data-stu-id="8c3da-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="8c3da-181">Bu adım olmadan yaptığınız değişiklikleri yalnızca yerel ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="8c3da-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="8c3da-182">Değişiklikleri veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="8c3da-182">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="8c3da-183">Aşağıdaki kod hemen üstüne INSERT `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="8c3da-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="8c3da-184">Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve etkileri değişiklikleri gönderdikten sonra:</span><span class="sxs-lookup"><span data-stu-id="8c3da-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3.  <span data-ttu-id="8c3da-185">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="8c3da-185">Press F5 to debug the solution.</span></span>  
  
4.  <span data-ttu-id="8c3da-186">Enter tuşuna basarak **konsol** uygulamayı kapatmak için penceresi.</span><span class="sxs-lookup"><span data-stu-id="8c3da-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c3da-187">Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemez olduğu gibi yeniden.</span><span class="sxs-lookup"><span data-stu-id="8c3da-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="8c3da-188">Çözümü yeniden çalıştırmak için Müşteri Kimliği ve müşteri eklenecek adını değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8c3da-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c3da-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c3da-189">See also</span></span>

- [<span data-ttu-id="8c3da-190">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="8c3da-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
