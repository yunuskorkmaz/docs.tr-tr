---
description: 'Hakkında daha fazla bilgi edinin: Izlenecek yol: verileri düzenleme (Visual Basic)'
title: 'İzlenecek yol: Verileri Düzenleme (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
ms.openlocfilehash: 22bef61c294a92984446402063bf14b06f5b2b2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729529"
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="4d6a0-103">İzlenecek yol: Verileri Düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d6a0-103">Walkthrough: Manipulating Data (Visual Basic)</span></span>

<span data-ttu-id="4d6a0-104">Bu izlenecek yol [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , bir veritabanındaki verileri eklemek, değiştirmek ve silmek için temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="4d6a0-105">Müşteri eklemek, bir müşterinin adını değiştirmek ve bir siparişi silmek için örnek Northwind veritabanının bir kopyasını kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-105">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="4d6a0-106">Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-106">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4d6a0-107">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4d6a0-107">Prerequisites</span></span>  

 <span data-ttu-id="4d6a0-108">Bu izlenecek yol aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-108">This walkthrough requires the following:</span></span>  
  
- <span data-ttu-id="4d6a0-109">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest2") kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-109">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="4d6a0-110">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-110">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="4d6a0-111">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-111">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="4d6a0-112">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-112">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="4d6a0-113">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4d6a0-113">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="4d6a0-114">Veritabanını indirdikten sonra, Kuzey WND. mdf dosyasını c:\linqtest2 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-114">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
- <span data-ttu-id="4d6a0-115">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-115">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="4d6a0-116">Bu dosyayı Nesne İlişkisel Tasarımcısı ya da SQLMetal aracını kullanarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-116">You can generate this file by using either the Object Relational Designer or the SQLMetal tool.</span></span> <span data-ttu-id="4d6a0-117">Bu izlenecek yol, aşağıdaki komut satırı ile SQLMetal Aracı kullanılarak yazılmıştır:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-117">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="4d6a0-118">**SqlMetal/Code: "c:\linqtest2\northwind.exe"/Language: vb "C:\linqtest2\kuzeydoğu WND.exe"/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="4d6a0-118">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="4d6a0-119">Daha fazla bilgi için bkz. [SqlMetal.exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="4d6a0-119">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="4d6a0-120">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4d6a0-120">Overview</span></span>  

 <span data-ttu-id="4d6a0-121">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-121">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="4d6a0-122">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-122">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="4d6a0-123">Veritabanı kod dosyası projeye ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-123">Adding the database code file to the project.</span></span>  
  
- <span data-ttu-id="4d6a0-124">Yeni bir müşteri nesnesi oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-124">Creating a new customer object.</span></span>  
  
- <span data-ttu-id="4d6a0-125">Müşterinin kişi adını değiştirme.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-125">Modifying the contact name of a customer.</span></span>  
  
- <span data-ttu-id="4d6a0-126">Bir siparişi silme.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-126">Deleting an order.</span></span>  
  
- <span data-ttu-id="4d6a0-127">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-127">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="4d6a0-128">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d6a0-128">Creating a LINQ to SQL Solution</span></span>  

 <span data-ttu-id="4d6a0-129">Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d6a0-129">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="4d6a0-130">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-130">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="4d6a0-131">Visual Studio **Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-131">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="4d6a0-132">**Yeni proje** Iletişim kutusundaki **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-132">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="4d6a0-133">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-133">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="4d6a0-134">**Ad** kutusuna **Linqdatalationtionapp** yazın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-134">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5. <span data-ttu-id="4d6a0-135">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-135">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="4d6a0-136">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-136">Adding LINQ References and Directives</span></span>  

 <span data-ttu-id="4d6a0-137">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-137">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="4d6a0-138">`System.Data.Linq`Projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-138">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="4d6a0-139">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-139">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="4d6a0-140">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-140">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="4d6a0-141">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-141">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="4d6a0-142">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-142">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="4d6a0-143">Kod Düzenleyicisi 'nde, aşağıdaki yönergeleri **Module1** öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-143">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="4d6a0-144">Northwind kod dosyasını projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-144">Adding the Northwind Code File to the Project</span></span>  

 <span data-ttu-id="4d6a0-145">Bu adımlarda, Northwind örnek veritabanından bir kod dosyası oluşturmak için SQLMetal aracını kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-145">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="4d6a0-146">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-146">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="4d6a0-147">Projeye Northwind kod dosyasını eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-147">To add the northwind code file to the project</span></span>  
  
1. <span data-ttu-id="4d6a0-148">**Proje** menüsünde, **Varolan öğe Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-148">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2. <span data-ttu-id="4d6a0-149">**Varolan öğe Ekle** iletişim kutusunda c:\linqtest2\northwind.exe konumuna gidin ve ardından **Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-149">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="4d6a0-150">Northwind. vb dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-150">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="4d6a0-151">Veritabanı bağlantısını ayarlama</span><span class="sxs-lookup"><span data-stu-id="4d6a0-151">Setting Up the Database Connection</span></span>  

 <span data-ttu-id="4d6a0-152">İlk olarak, Veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-152">First, test your connection to the database.</span></span> <span data-ttu-id="4d6a0-153">Özellikle, Kuzey WND adlı veritabanının adının bir i karakteri olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-153">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="4d6a0-154">Sonraki adımlarda hata oluşturursanız Northwind. vb dosyasını gözden geçirerek Northwind kısmi sınıfının nasıl yazıldığını belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-154">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="4d6a0-155">Veritabanı bağlantısını ayarlama ve test etme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-155">To set up and test the database connection</span></span>  
  
1. <span data-ttu-id="4d6a0-156">Aşağıdaki kodu yazın veya içine yapıştırın `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="4d6a0-156">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2. <span data-ttu-id="4d6a0-157">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-157">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="4d6a0-158">Bir **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-158">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="4d6a0-159">**Konsol** penceresinde ENTER tuşuna basarak veya Visual Studio **hata ayıklama** menüsünde **hata ayıklamayı Durdur** ' u tıklatarak uygulamayı kapatın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-159">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the Visual Studio **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="4d6a0-160">Yeni varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="4d6a0-160">Creating a New Entity</span></span>  

 <span data-ttu-id="4d6a0-161">Yeni varlık oluşturma basittir.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-161">Creating a new entity is straightforward.</span></span> <span data-ttu-id="4d6a0-162">`Customer`Anahtar sözcüğünü kullanarak nesneler (gibi) oluşturabilirsiniz `New` .</span><span class="sxs-lookup"><span data-stu-id="4d6a0-162">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="4d6a0-163">Bu ve aşağıdaki bölümlerde yalnızca yerel önbellekte değişiklik yapmakta olursunuz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-163">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="4d6a0-164">Bu izlenecek yolun sonuna doğru çağrı yapana kadar veritabanına hiçbir değişiklik gönderilmez <xref:System.Data.Linq.DataContext.SubmitChanges%2A> .</span><span class="sxs-lookup"><span data-stu-id="4d6a0-164">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="4d6a0-165">Yeni bir müşteri varlık nesnesi eklemek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-165">To add a new Customer entity object</span></span>  
  
1. <span data-ttu-id="4d6a0-166">`Customer`' Den önce aşağıdaki kodu ekleyerek yeni bir oluşturun `Console.ReadLine` `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="4d6a0-166">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2. <span data-ttu-id="4d6a0-167">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-167">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="4d6a0-168">Konsol penceresinde gösterilen sonuçlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-168">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="4d6a0-169">Yeni satırın sonuçlarda görünmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-169">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="4d6a0-170">Yeni veriler henüz veritabanına gönderilmedi.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-170">The new data has not yet been submitted to the database.</span></span>  
  
3. <span data-ttu-id="4d6a0-171">Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-171">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="4d6a0-172">Bir varlığı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-172">Updating an Entity</span></span>  

 <span data-ttu-id="4d6a0-173">Aşağıdaki adımlarda, bir `Customer` nesnesi alacak ve özelliklerinden birini değiştirecaksınız.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-173">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="4d6a0-174">Müşterinin adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-174">To change the name of a Customer</span></span>  
  
- <span data-ttu-id="4d6a0-175">Aşağıdaki kodu yukarıya ekleyin `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="4d6a0-175">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="4d6a0-176">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-176">Deleting an Entity</span></span>  

 <span data-ttu-id="4d6a0-177">Aynı müşteri nesnesini kullanarak, ilk siparişi silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-177">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="4d6a0-178">Aşağıdaki kod, satırlar arasındaki ilişkilerin nasıl oluşturulduğunu ve veritabanından bir satırın nasıl silineceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-178">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="4d6a0-179">Bir satırı silmek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-179">To delete a row</span></span>  
  
- <span data-ttu-id="4d6a0-180">Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine()` :</span><span class="sxs-lookup"><span data-stu-id="4d6a0-180">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="4d6a0-181">Değişiklikleri veritabanına gönderme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-181">Submitting Changes to the Database</span></span>  

 <span data-ttu-id="4d6a0-182">Nesneleri oluşturmak, güncelleştirmek ve silmek için gereken son adım aslında değişiklikleri veritabanına göndermeleridir.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-182">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="4d6a0-183">Bu adım olmadan yaptığınız değişiklikler yalnızca yereldir ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-183">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="4d6a0-184">Değişiklikleri veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="4d6a0-184">To submit changes to the database</span></span>  
  
1. <span data-ttu-id="4d6a0-185">Aşağıdaki kodu hemen yukarıya ekleyin `Console.ReadLine` :</span><span class="sxs-lookup"><span data-stu-id="4d6a0-185">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="4d6a0-186">`SubmitChanges`Değişiklikleri gönderme etkilerine ilişkin önceki ve sonraki etkileri göstermek için aşağıdaki kodu (sonra) ekleyin:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-186">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3. <span data-ttu-id="4d6a0-187">Çözümde hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-187">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="4d6a0-188">Konsol penceresi şu şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="4d6a0-188">The console window appears as follows:</span></span>  
  
    ```console
    Customers matching CA before update:  
    Customer ID: CACTU  
    Customer ID: RICAR  
  
    The Order Detail to be deleted is: OrderID = 10643  
  
    Customers matching CA after update:  
    Customer ID: A3VCA  
    Customer ID: CACTU  
    Customer ID: RICAR  
    ```  
  
4. <span data-ttu-id="4d6a0-189">Hata ayıklamayı durdurmak için **konsol** penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-189">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d6a0-190">Değişiklikleri göndererek yeni müşteriyi ekledikten sonra, aynı müşteriyi olduğu gibi yeniden ekleyemediği için bu çözümü olduğu gibi yeniden yürütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-190">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="4d6a0-191">Çözümü yeniden yürütmek için, eklenecek müşteri KIMLIĞI değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-191">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d6a0-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d6a0-192">See also</span></span>

- [<span data-ttu-id="4d6a0-193">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="4d6a0-193">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
