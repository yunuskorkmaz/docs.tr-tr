---
title: 'İzlenecek yol: Verileri Düzenleme (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 27ac9de488a92d838df06d4a501a9148e87b9c9f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742725"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="11008-102">İzlenecek yol: Verileri Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11008-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="11008-103">Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryo ekleme, değiştirme ve bir veritabanındaki verileri siliniyor.</span><span class="sxs-lookup"><span data-stu-id="11008-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="11008-104">Örnek Northwind veritabanının bir kopyasını bir müşteri eklemek, bir müşterinin adını değiştirin ve sipariş silmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="11008-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="11008-105">Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="11008-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="11008-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="11008-106">Prerequisites</span></span>  
 <span data-ttu-id="11008-107">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="11008-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="11008-108">Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest2") kullanır.</span><span class="sxs-lookup"><span data-stu-id="11008-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="11008-109">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="11008-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="11008-110">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="11008-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="11008-111">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11008-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="11008-112">Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="11008-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="11008-113">Veritabanı indirdikten sonra northwnd.mdf dosya c:\linqtest2 klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="11008-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="11008-114">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="11008-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="11008-115">Object Relational Designer'ı veya SQLMetal aracını kullanarak bu dosyayı oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11008-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="11008-116">Bu izlenecek yol, şu komut satırıyla SQLMetal Aracı'nı kullanarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="11008-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="11008-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="11008-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="11008-118">Daha fazla bilgi için [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="11008-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="11008-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="11008-119">Overview</span></span>  
 <span data-ttu-id="11008-120">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="11008-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="11008-121">Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.</span><span class="sxs-lookup"><span data-stu-id="11008-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="11008-122">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="11008-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="11008-123">Yeni bir müşteri nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="11008-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="11008-124">Bir müşteri kişi adını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="11008-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="11008-125">Bir sipariş siliniyor.</span><span class="sxs-lookup"><span data-stu-id="11008-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="11008-126">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="11008-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="11008-127">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="11008-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="11008-128">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="11008-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="11008-129">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="11008-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="11008-130">Visual Studio **dosya** menüsünü tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="11008-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="11008-131">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="11008-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="11008-132">İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="11008-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="11008-133">İçinde **adı** kutusuna **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="11008-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="11008-134">          **Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="11008-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="11008-135">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="11008-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="11008-136">Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="11008-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="11008-137">Varsa `System.Data.Linq` projenize bir başvuru olarak listelenmemiş (tıklayın **tüm dosyaları göster** içinde **Çözüm Gezgini** genişletin **başvuruları** düğümü), açıklandığı gibi ekleyin Aşağıdaki adımlar.</span><span class="sxs-lookup"><span data-stu-id="11008-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="11008-138">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="11008-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="11008-139">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="11008-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="11008-140">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="11008-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="11008-141">Derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="11008-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="11008-142">Kod Düzenleyicisi'nde, aşağıdaki yönergeleri yukarıdaki Ekle **Module1**:</span><span class="sxs-lookup"><span data-stu-id="11008-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="11008-143">Northwind kod dosyası projeye ekleniyor</span><span class="sxs-lookup"><span data-stu-id="11008-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="11008-144">Bu adımları, Northwind örnek veritabanındaki bir kod dosyası oluşturmak için SQLMetal Aracı'nı kullandığınızı varsayar.</span><span class="sxs-lookup"><span data-stu-id="11008-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="11008-145">Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="11008-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="11008-146">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="11008-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="11008-147">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="11008-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="11008-148">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest2\northwind.vb gidin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="11008-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="11008-149">Northwind.vb dosya projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="11008-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="11008-150">Veritabanı bağlantısı kurma</span><span class="sxs-lookup"><span data-stu-id="11008-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="11008-151">İlk olarak, veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="11008-151">First, test your connection to the database.</span></span> <span data-ttu-id="11008-152">Özellikle Northwnd, veritabanının adı yok i olduğunu unutmayın. karakter.</span><span class="sxs-lookup"><span data-stu-id="11008-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="11008-153">Sonraki adımlarda hatalar oluşturur, Northwind kısmi sınıf nasıl yazıldığını belirlemek için northwind.vb dosyasını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="11008-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="11008-154">Veritabanı bağlantısını test etmek ve ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="11008-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="11008-155">İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="11008-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="11008-156">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11008-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="11008-157">A **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="11008-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="11008-158">Enter tuşuna basarak uygulamayı kapatmak **konsol** penceresinde veya tıklayarak **hata ayıklamayı Durdur** Visual Studio **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="11008-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="11008-159">Yeni varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="11008-159">Creating a New Entity</span></span>  
 <span data-ttu-id="11008-160">Yeni bir varlık oluştururken oldukça basittir.</span><span class="sxs-lookup"><span data-stu-id="11008-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="11008-161">Nesneleri oluşturabilirsiniz (gibi `Customer`) kullanarak `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="11008-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="11008-162">Bu ve aşağıdaki bölümler, yalnızca yerel önbelleğe değişiklikler yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="11008-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="11008-163">Çağırana kadar hiçbir değişiklik veritabanına gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Bu izlenecek yolun sonuna doğru.</span><span class="sxs-lookup"><span data-stu-id="11008-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="11008-164">Yeni bir müşteri varlığı nesne eklemek için</span><span class="sxs-lookup"><span data-stu-id="11008-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="11008-165">Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine` içinde `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="11008-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="11008-166">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11008-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="11008-167">Konsol penceresinde gösterilen sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="11008-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="11008-168">Yeni satır sonuçlarında görünmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="11008-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="11008-169">Veritabanına yeni veriler henüz gönderilmedi.</span><span class="sxs-lookup"><span data-stu-id="11008-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="11008-170">Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="11008-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="11008-171">Bir varlığı güncelleştirmek</span><span class="sxs-lookup"><span data-stu-id="11008-171">Updating an Entity</span></span>  
 <span data-ttu-id="11008-172">Aşağıdaki adımlarda, alacak bir `Customer` nesne ve onun özelliklerden birini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="11008-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="11008-173">Bir müşteri adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="11008-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="11008-174">Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="11008-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="11008-175">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="11008-175">Deleting an Entity</span></span>  
 <span data-ttu-id="11008-176">Aynı müşteri nesnesini kullanarak, ilk sırada silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11008-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="11008-177">Aşağıdaki kod ilişkileri sever gösterilmektedir satırlar ve veritabanından satır silme arasında.</span><span class="sxs-lookup"><span data-stu-id="11008-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="11008-178">Bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="11008-178">To delete a row</span></span>  
  
- <span data-ttu-id="11008-179">Aşağıdaki kodu ekleyin hemen üzerinde `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="11008-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="11008-180">Veritabanına değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="11008-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="11008-181">Son adım gereklidir oluşturmak için güncelleştirme ve silme nesneleri gerçekten veritabanına değişiklikleri göndermek için.</span><span class="sxs-lookup"><span data-stu-id="11008-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="11008-182">Bu adım olmadan yaptığınız değişiklikleri yalnızca yerel ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="11008-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="11008-183">Değişiklikleri veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="11008-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="11008-184">Aşağıdaki kod hemen üstüne INSERT `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="11008-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="11008-185">Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve etkileri değişiklikleri gönderdikten sonra:</span><span class="sxs-lookup"><span data-stu-id="11008-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="11008-186">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="11008-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="11008-187">Konsol penceresinde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="11008-187">The console window appears as follows:</span></span>  
  
    ```  
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="11008-188">Enter tuşuna basarak **konsol** penceresi hata ayıklamayı durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="11008-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11008-189">Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemiyor yeniden olduğu gibi aynı müşteriye tekrar ekleyemezsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="11008-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="11008-190">Çözümü yeniden çalıştırmak için eklenecek müşteri Kimliğini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="11008-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11008-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11008-191">See also</span></span>

- [<span data-ttu-id="11008-192">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="11008-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
