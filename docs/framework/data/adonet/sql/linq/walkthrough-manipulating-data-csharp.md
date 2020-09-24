---
title: 'İzlenecek yol: Verileri Düzenleme (C#)'
ms.date: 03/30/2017
ms.assetid: 24adfbe0-0ad6-449f-997d-8808e0770d2e
ms.openlocfilehash: fefbee533634ee42785c65e0265ce1e0567561b5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164070"
---
# <a name="walkthrough-manipulating-data-c"></a><span data-ttu-id="e3cdf-102">İzlenecek yol: Verileri Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="e3cdf-102">Walkthrough: Manipulating Data (C#)</span></span>

<span data-ttu-id="e3cdf-103">Bu izlenecek yol [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir veritabanındaki verileri eklemek, değiştirmek ve silmek için temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="e3cdf-104">Müşteri eklemek, bir müşterinin adını değiştirmek ve bir siparişi silmek için örnek Northwind veritabanının bir kopyasını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="e3cdf-105">Bu izlenecek yol, Visual C# geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-105">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e3cdf-106">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="e3cdf-106">Prerequisites</span></span>  

 <span data-ttu-id="e3cdf-107">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="e3cdf-108">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest6") kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-108">This walkthrough uses a dedicated folder ("c:\linqtest6") to hold files.</span></span> <span data-ttu-id="e3cdf-109">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="e3cdf-110">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="e3cdf-111">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="e3cdf-112">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="e3cdf-112">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="e3cdf-113">Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest6 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest6 folder.</span></span>  
  
- <span data-ttu-id="e3cdf-114">Northwind veritabanından oluşturulan bir C# kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-114">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="e3cdf-115">Bu dosyayı Nesne İlişkisel Tasarımcısı ya da SQLMetal aracını kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="e3cdf-116">Bu izlenecek yol, aşağıdaki komut satırı ile SQLMetal Aracı kullanılarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="e3cdf-117">**SqlMetal/Code: "c:\linqtest6\northwind.cs"/Language: CSharp "C:\linqtest6\kuzeydoğu"/plurlaştır**</span><span class="sxs-lookup"><span data-stu-id="e3cdf-117">**sqlmetal /code:"c:\linqtest6\northwind.cs" /language:csharp "C:\linqtest6\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="e3cdf-118">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e3cdf-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="e3cdf-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e3cdf-119">Overview</span></span>  

 <span data-ttu-id="e3cdf-120">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="e3cdf-121">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="e3cdf-122">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="e3cdf-123">Yeni bir müşteri nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="e3cdf-124">Müşterinin kişi adını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="e3cdf-125">Bir siparişi silme.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="e3cdf-126">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="e3cdf-127">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3cdf-127">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="e3cdf-128">Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e3cdf-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="e3cdf-129">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="e3cdf-130">Visual Studio **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-130">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2. <span data-ttu-id="e3cdf-131">**Yeni proje** Iletişim kutusundaki **Proje türleri** bölmesinde, **Visual C#**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-131">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3. <span data-ttu-id="e3cdf-132">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="e3cdf-133">**Ad** kutusuna **Linqdatalationtionapp**yazın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="e3cdf-134">**Konum** kutusunda, proje dosyalarınızı nerede depolamak istediğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-134">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6. <span data-ttu-id="e3cdf-135">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="e3cdf-136">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-136">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="e3cdf-137">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="e3cdf-138">System. Data. LINQ, projenizde bir başvuru olarak listelenmiyorsa, aşağıdaki adımlarda açıklandığı gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-138">If System.Data.Linq is not listed as a reference in your project, add it, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="e3cdf-139">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="e3cdf-140">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="e3cdf-141">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="e3cdf-142">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="e3cdf-143">Aşağıdaki yönergeleri Program.cs üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-143">Add the following directives at the top of Program.cs:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e3cdf-144">Northwind kod dosyasını projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-144">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="e3cdf-145">Bu adımlarda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SQLMetal aracını kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="e3cdf-146">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="e3cdf-147">Projeye Northwind kod dosyasını eklemek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="e3cdf-148">**Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="e3cdf-149">**Varolan öğe Ekle** iletişim kutusunda c:\linqtest6\northwind.cs dizinine gidin ve **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest6\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="e3cdf-150">Northwind.cs dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-150">The northwind.cs file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="e3cdf-151">Veritabanı bağlantısını ayarlama</span><span class="sxs-lookup"><span data-stu-id="e3cdf-151">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="e3cdf-152">İlk olarak, Veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-152">First, test your connection to the database.</span></span> <span data-ttu-id="e3cdf-153">Özellikle, Kuzey WND veritabanının bir i karakteri olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-153">Note especially that the database, Northwnd, has no i character.</span></span> <span data-ttu-id="e3cdf-154">Sonraki adımlarda hata oluşturursanız, Northwind kısmi sınıfının nasıl yazıldığını öğrenmek için northwind.cs dosyasını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-154">If you generate errors in the next steps, review the northwind.cs file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="e3cdf-155">Veritabanı bağlantısını ayarlama ve test etme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="e3cdf-156">Aşağıdaki kodu program sınıfındaki yöntemine yazın veya yapıştırın `Main` :</span><span class="sxs-lookup"><span data-stu-id="e3cdf-156">Type or paste the following code into the `Main` method in the Program class:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#2)]  
  
2. <span data-ttu-id="e3cdf-157">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="e3cdf-158">Bir **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="e3cdf-159">Uygulamayı **konsol** penceresinde ENTER tuşuna basarak veya Visual Studio **hata ayıklama** menüsünde **hata ayıklamayı Durdur** ' a tıklayarak kapatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-159">You can close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="e3cdf-160">Yeni varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="e3cdf-160">Creating a New Entity</span></span>  

 <span data-ttu-id="e3cdf-161">Yeni varlık oluşturma basittir.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="e3cdf-162">`Customer`Anahtar sözcüğünü kullanarak nesneler (gibi) oluşturabilirsiniz `new` .</span><span class="sxs-lookup"><span data-stu-id="e3cdf-162">You can create objects (such as `Customer`) by using the `new` keyword.</span></span>  
  
 <span data-ttu-id="e3cdf-163">Bu ve aşağıdaki bölümlerde yalnızca yerel önbellekte değişiklik yapmakta olursunuz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="e3cdf-164">Bu izlenecek yolun sonuna doğru çağrı yapana kadar veritabanına hiçbir değişiklik gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="e3cdf-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="e3cdf-165">Yeni bir müşteri varlık nesnesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="e3cdf-166">`Customer`Aşağıdaki kodu yöntemine ekleyerek yeni bir oluşturun `Console.ReadLine();` `Main` :</span><span class="sxs-lookup"><span data-stu-id="e3cdf-166">Create a new `Customer` by adding the following code before `Console.ReadLine();` in the `Main` method:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#3)]  
  
2. <span data-ttu-id="e3cdf-167">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-167">Press F5 to debug the solution.</span></span>  
  
3. <span data-ttu-id="e3cdf-168">Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın ve yönergeyi devam edin.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-168">Press Enter in the **Console** window to stop debugging and continue the walkthrough.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="e3cdf-169">Bir varlığı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-169">Updating an Entity</span></span>  

 <span data-ttu-id="e3cdf-170">Aşağıdaki adımlarda, bir `Customer` nesnesi alacak ve özelliklerinden birini değiştirecaksınız.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-170">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="e3cdf-171">Müşterinin adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-171">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="e3cdf-172">Aşağıdaki kodu yukarıya ekleyin `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="e3cdf-172">Add the following code above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="e3cdf-173">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-173">Deleting an Entity</span></span>  

 <span data-ttu-id="e3cdf-174">Aynı müşteri nesnesini kullanarak, ilk siparişi silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-174">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="e3cdf-175">Aşağıdaki kod, satırlar arasındaki ilişkilerin nasıl oluşturulduğunu ve veritabanından bir satırın nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-175">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span> <span data-ttu-id="e3cdf-176">`Console.ReadLine`Nesnelerin nasıl silinebilecek anlamak için önce aşağıdaki kodu ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-176">Add the following code before `Console.ReadLine` to see how objects can be deleted:</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="e3cdf-177">Bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-177">To delete a row</span></span>  
  
- <span data-ttu-id="e3cdf-178">Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine();` :</span><span class="sxs-lookup"><span data-stu-id="e3cdf-178">Add the following code just above `Console.ReadLine();`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="e3cdf-179">Değişiklikleri veritabanına gönderme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-179">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="e3cdf-180">Nesneleri oluşturmak, güncelleştirmek ve silmek için gereken son adım aslında değişiklikleri veritabanına göndermeleridir.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-180">The final step required for creating, updating, and deleting objects, is to actually submit the changes to the database.</span></span> <span data-ttu-id="e3cdf-181">Bu adım olmadan yaptığınız değişiklikler yalnızca yereldir ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-181">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="e3cdf-182">Değişiklikleri veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="e3cdf-182">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="e3cdf-183">Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="e3cdf-183">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#6)]  
  
2. <span data-ttu-id="e3cdf-184">`SubmitChanges`Değişiklikleri gönderme etkilerine ilişkin önceki ve sonraki etkileri göstermek için aşağıdaki kodu (sonra) ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e3cdf-184">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-csharp[DLinqWalk3CS#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk3CS/cs/Program.cs#7)]  
  
3. <span data-ttu-id="e3cdf-185">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-185">Press F5 to debug the solution.</span></span>  
  
4. <span data-ttu-id="e3cdf-186">Uygulamayı kapatmak için **konsol** penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-186">Press Enter in the **Console** window to close the application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3cdf-187">Değişiklikleri göndererek yeni müşteriyi ekledikten sonra, bu çözümü olduğu gibi yeniden yürütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-187">After you have added the new customer by submitting the changes, you cannot execute this solution again as is.</span></span> <span data-ttu-id="e3cdf-188">Çözümü yeniden yürütmek için, eklenecek müşterinin adını ve müşteri KIMLIĞINI değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-188">To execute the solution again, change the name of the customer and customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cdf-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3cdf-189">See also</span></span>

- [<span data-ttu-id="e3cdf-190">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="e3cdf-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
