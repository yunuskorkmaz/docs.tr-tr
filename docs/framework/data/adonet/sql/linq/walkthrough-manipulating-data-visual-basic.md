---
title: 'İzlenecek yol: Verileri Düzenleme (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 9e6039feb68d18ff5ce16b7a0532710d672c296e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946958"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="c6f91-102">İzlenecek yol: Verileri Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6f91-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="c6f91-103">Bu izlenecek yol, bir veritabanındaki verileri eklemek, değiştirmek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve silmek için temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6f91-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="c6f91-104">Müşteri eklemek, bir müşterinin adını değiştirmek ve bir siparişi silmek için örnek Northwind veritabanının bir kopyasını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c6f91-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="c6f91-105">Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c6f91-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6f91-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c6f91-106">Prerequisites</span></span>  
 <span data-ttu-id="c6f91-107">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c6f91-107">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="c6f91-108">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest2") kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6f91-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="c6f91-109">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c6f91-109">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="c6f91-110">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c6f91-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="c6f91-111">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="c6f91-112">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c6f91-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="c6f91-113">Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest2 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="c6f91-114">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="c6f91-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="c6f91-115">Bu dosyayı Nesne İlişkisel Tasarımcısı ya da SQLMetal aracını kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-115">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="c6f91-116">Bu izlenecek yol, aşağıdaki komut satırı ile SQLMetal Aracı kullanılarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="c6f91-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="c6f91-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="c6f91-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="c6f91-118">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c6f91-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c6f91-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6f91-119">Overview</span></span>  
 <span data-ttu-id="c6f91-120">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="c6f91-120">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="c6f91-121">Visual Studio 'da çözüm oluşturma. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6f91-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="c6f91-122">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="c6f91-122">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="c6f91-123">Yeni bir müşteri nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="c6f91-123">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="c6f91-124">Müşterinin kişi adını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="c6f91-124">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="c6f91-125">Bir siparişi silme.</span><span class="sxs-lookup"><span data-stu-id="c6f91-125">Deleting an order.</span></span>  
  
- <span data-ttu-id="c6f91-126">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="c6f91-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="c6f91-127">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6f91-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="c6f91-128">Bu ilk görevde, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-128">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="c6f91-129">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c6f91-129">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="c6f91-130">Visual Studio **Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-130">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="c6f91-131">**Yeni proje** Iletişim kutusundaki **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="c6f91-132">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="c6f91-133">**Ad** kutusuna **Linqdatalationtionapp**yazın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="c6f91-134">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="c6f91-135">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c6f91-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="c6f91-136">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c6f91-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="c6f91-137">Projenizde bir başvuru olarak listelenmiyorsa (Çözüm Gezgini **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin. `System.Data.Linq`</span><span class="sxs-lookup"><span data-stu-id="c6f91-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="c6f91-138">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-138">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="c6f91-139">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="c6f91-140">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c6f91-141">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c6f91-141">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="c6f91-142">Kod Düzenleyicisi 'nde, aşağıdaki yönergeleri **Module1**öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6f91-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="c6f91-143">Northwind kod dosyasını projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="c6f91-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="c6f91-144">Bu adımlarda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SQLMetal aracını kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c6f91-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="c6f91-145">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="c6f91-146">Projeye Northwind kod dosyasını eklemek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-146">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="c6f91-147">**Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="c6f91-148">**Varolan öğe Ekle** iletişim kutusunda c:\linqtest2\northwind.exe konumuna gidin ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="c6f91-149">Northwind. vb dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c6f91-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="c6f91-150">Veritabanı bağlantısını ayarlama</span><span class="sxs-lookup"><span data-stu-id="c6f91-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="c6f91-151">İlk olarak, Veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="c6f91-151">First, test your connection to the database.</span></span> <span data-ttu-id="c6f91-152">Özellikle, Kuzey WND adlı veritabanının adının bir i karakteri olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="c6f91-153">Sonraki adımlarda hata oluşturursanız Northwind. vb dosyasını gözden geçirerek Northwind kısmi sınıfının nasıl yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="c6f91-154">Veritabanı bağlantısını ayarlama ve test etme</span><span class="sxs-lookup"><span data-stu-id="c6f91-154">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="c6f91-155">Aşağıdaki kodu yazın veya içine `Sub Main`yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="c6f91-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="c6f91-156">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="c6f91-157">Bir **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="c6f91-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="c6f91-158">**Konsol** penceresinde ENTER tuşuna basarak veya Visual Studio **hata ayıklama** menüsünde **hata ayıklamayı Durdur** ' u tıklatarak uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="c6f91-159">Yeni varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="c6f91-159">Creating a New Entity</span></span>  
 <span data-ttu-id="c6f91-160">Yeni varlık oluşturma basittir.</span><span class="sxs-lookup"><span data-stu-id="c6f91-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="c6f91-161">Anahtar`New` sözcüğünü kullanarak nesneler ( `Customer`gibi) oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="c6f91-162">Bu ve aşağıdaki bölümlerde yalnızca yerel önbellekte değişiklik yapmakta olursunuz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="c6f91-163">Bu izlenecek yolun sonuna doğru çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yapana kadar veritabanına hiçbir değişiklik gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="c6f91-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="c6f91-164">Yeni bir müşteri varlık nesnesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-164">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="c6f91-165">' `Customer` `Console.ReadLine` Den önce aşağıdaki kodu ekleyerek yeni bir oluşturun: `Sub Main`</span><span class="sxs-lookup"><span data-stu-id="c6f91-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="c6f91-166">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="c6f91-167">Konsol penceresinde gösterilen sonuçlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="c6f91-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="c6f91-168">Yeni satırın sonuçlarda görünmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="c6f91-169">Yeni veriler henüz veritabanına gönderilmedi.</span><span class="sxs-lookup"><span data-stu-id="c6f91-169">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="c6f91-170">Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="c6f91-171">Bir varlığı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="c6f91-171">Updating an Entity</span></span>  
 <span data-ttu-id="c6f91-172">Aşağıdaki adımlarda, bir `Customer` nesnesi alacak ve özelliklerinden birini değiştirecaksınız.</span><span class="sxs-lookup"><span data-stu-id="c6f91-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="c6f91-173">Müşterinin adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-173">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="c6f91-174">Aşağıdaki kodu yukarıya `Console.ReadLine()`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6f91-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="c6f91-175">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="c6f91-175">Deleting an Entity</span></span>  
 <span data-ttu-id="c6f91-176">Aynı müşteri nesnesini kullanarak, ilk siparişi silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="c6f91-177">Aşağıdaki kod, satırlar arasındaki ilişkilerin nasıl oluşturulduğunu ve veritabanından bir satırın nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c6f91-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="c6f91-178">Bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-178">To delete a row</span></span>  
  
- <span data-ttu-id="c6f91-179">Aşağıdaki kodu hemen yukarıya `Console.ReadLine()`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6f91-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="c6f91-180">Değişiklikleri veritabanına gönderme</span><span class="sxs-lookup"><span data-stu-id="c6f91-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="c6f91-181">Nesneleri oluşturmak, güncelleştirmek ve silmek için gereken son adım aslında değişiklikleri veritabanına göndermeleridir.</span><span class="sxs-lookup"><span data-stu-id="c6f91-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="c6f91-182">Bu adım olmadan yaptığınız değişiklikler yalnızca yereldir ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="c6f91-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="c6f91-183">Değişiklikleri veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="c6f91-183">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="c6f91-184">Aşağıdaki kodu hemen yukarıya `Console.ReadLine`ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6f91-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="c6f91-185">Değişiklikleri gönderme etkilerine ilişkin önceki ve `SubmitChanges`sonraki etkileri göstermek için aşağıdaki kodu (sonra) ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6f91-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="c6f91-186">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="c6f91-187">Konsol penceresi şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="c6f91-187">The console window appears as follows:</span></span>  
  
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
  
4. <span data-ttu-id="c6f91-188">Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c6f91-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6f91-189">Değişiklikleri göndererek yeni müşteriyi ekledikten sonra, aynı müşteriyi olduğu gibi yeniden ekleyemediği için bu çözümü olduğu gibi yeniden yürütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="c6f91-190">Çözümü yeniden yürütmek için, eklenecek müşteri KIMLIĞI değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c6f91-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f91-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6f91-191">See also</span></span>

- [<span data-ttu-id="c6f91-192">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="c6f91-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
