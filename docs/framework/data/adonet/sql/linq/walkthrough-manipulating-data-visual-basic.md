---
title: "İzlenecek yol: Veri (Visual Basic) düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: 1f6a54f6-ec33-452a-a37d-48122207bf14
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: b4bc7baee8e95243cf05a52f49c37aa2d8916666
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-manipulating-data-visual-basic"></a><span data-ttu-id="c589f-102">İzlenecek yol: Veri (Visual Basic) düzenleme</span><span class="sxs-lookup"><span data-stu-id="c589f-102">Walkthrough: Manipulating Data (Visual Basic)</span></span>
<span data-ttu-id="c589f-103">Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] senaryosu ekleme, değiştirme ve bir veritabanındaki verileri silme.</span><span class="sxs-lookup"><span data-stu-id="c589f-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for adding, modifying, and deleting data in a database.</span></span> <span data-ttu-id="c589f-104">Bir müşteri ekleyin, bir müşterinin adını değiştirin ve sipariş silmek için örnek Northwind veritabanının bir kopyasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c589f-104">You will use a copy of the sample Northwind database to add a customer, change the name of a customer, and delete an order.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="c589f-105">Bu kılavuz, Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c589f-105">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c589f-106">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c589f-106">Prerequisites</span></span>  
 <span data-ttu-id="c589f-107">Bu kılavuz aşağıdakileri gerektirir:</span><span class="sxs-lookup"><span data-stu-id="c589f-107">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="c589f-108">Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest2") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c589f-108">This walkthrough uses a dedicated folder ("c:\linqtest2") to hold files.</span></span> <span data-ttu-id="c589f-109">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c589f-109">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="c589f-110">Northwind örnek veritabanı.</span><span class="sxs-lookup"><span data-stu-id="c589f-110">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="c589f-111">Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c589f-111">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="c589f-112">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c589f-112">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="c589f-113">Veritabanı indirdikten sonra northwnd.mdf dosyasını c:\linqtest2 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c589f-113">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest2 folder.</span></span>  
  
-   <span data-ttu-id="c589f-114">Northwind veritabanından oluşturulan Visual Basic kod dosyası.</span><span class="sxs-lookup"><span data-stu-id="c589f-114">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="c589f-115">Bu dosyayı kullanarak oluşturabileceğiniz [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] veya SQLMetal aracı.</span><span class="sxs-lookup"><span data-stu-id="c589f-115">You can generate this file by using either the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] or the SQLMetal tool.</span></span> <span data-ttu-id="c589f-116">Bu kılavuz, aşağıdaki komut satırı ile SQLMetal aracı kullanılarak yazılmış olduğundan:</span><span class="sxs-lookup"><span data-stu-id="c589f-116">This walkthrough was written by using the SQLMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="c589f-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span><span class="sxs-lookup"><span data-stu-id="c589f-117">**sqlmetal /code:"c:\linqtest2\northwind.vb" /language:vb "C:\linqtest2\northwnd.mdf" /pluralize**</span></span>  
  
     <span data-ttu-id="c589f-118">Daha fazla bilgi için bkz: [SqlMetal.exe (kod üretme aracı)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c589f-118">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c589f-119">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c589f-119">Overview</span></span>  
 <span data-ttu-id="c589f-120">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="c589f-120">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="c589f-121">Oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çözümde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c589f-121">Creating the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="c589f-122">Veritabanı kod dosyası projesine ekleniyor.</span><span class="sxs-lookup"><span data-stu-id="c589f-122">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="c589f-123">Yeni bir müşteri nesnesi oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c589f-123">Creating a new customer object.</span></span>  
  
-   <span data-ttu-id="c589f-124">Bir müşterinin ilgili kişi adı değiştirme.</span><span class="sxs-lookup"><span data-stu-id="c589f-124">Modifying the contact name of a customer.</span></span>  
  
-   <span data-ttu-id="c589f-125">Bir sipariş siliniyor.</span><span class="sxs-lookup"><span data-stu-id="c589f-125">Deleting an order.</span></span>  
  
-   <span data-ttu-id="c589f-126">Bu değişiklikler Northwind veritabanına gönderiliyor.</span><span class="sxs-lookup"><span data-stu-id="c589f-126">Submitting these changes to the Northwind database.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="c589f-127">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c589f-127">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="c589f-128">Bu ilk görevde oluşturduğunuz bir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] derlemek ve çalıştırmak için gerekli başvuruları içeren çözüm bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="c589f-128">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="c589f-129">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c589f-129">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="c589f-130">Üzerinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **dosya** menüsünde tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="c589f-130">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="c589f-131">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="c589f-131">In the **Project types** pane in the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="c589f-132">İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="c589f-132">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="c589f-133">İçinde **adı** kutusuna **LinqDataManipulationApp**.</span><span class="sxs-lookup"><span data-stu-id="c589f-133">In the **Name** box, type **LinqDataManipulationApp**.</span></span>  
  
5.  <span data-ttu-id="c589f-134">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c589f-134">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="c589f-135">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c589f-135">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="c589f-136">Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c589f-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="c589f-137">Varsa `System.Data.Linq` projenizdeki bir başvuru olarak listelenmemiş (tıklatın **tüm dosyaları göster** içinde **Çözüm Gezgini** ve genişletin **başvuruları** düğüm), açıklandığı gibi eklemek Aşağıdaki adımlar.</span><span class="sxs-lookup"><span data-stu-id="c589f-137">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="c589f-138">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="c589f-138">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="c589f-139">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c589f-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="c589f-140">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c589f-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c589f-141">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c589f-141">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="c589f-142">Kod Düzenleyicisi'nde, yukarıdaki aşağıdaki yönergeleri eklemek **Module1**:</span><span class="sxs-lookup"><span data-stu-id="c589f-142">In the code editor, add the following directives above **Module1**:</span></span>  
  
     [!code-vb[DLinqWalk3VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#1)]  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="c589f-143">Northwind kod dosyası projeye ekleme</span><span class="sxs-lookup"><span data-stu-id="c589f-143">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="c589f-144">Bu adımlarda, SQLMetal aracı Northwind örnek veritabanı'ndaki bir kod dosyası oluşturmak için kullandığınız varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c589f-144">These steps assume that you have used the SQLMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="c589f-145">Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c589f-145">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="c589f-146">Northwind kod dosyası projeye eklemek için</span><span class="sxs-lookup"><span data-stu-id="c589f-146">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="c589f-147">Üzerinde **proje** menüsünde tıklatın **varolan öğeyi Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c589f-147">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="c589f-148">İçinde **varolan öğeyi Ekle** iletişim kutusu için c:\linqtest2\northwind.vb gidin ve ardından **Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c589f-148">In the **Add Existing Item** dialog box, navigate to c:\linqtest2\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="c589f-149">Northwind.vb dosyası projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c589f-149">The northwind.vb file is added to the project.</span></span>  
  
## <a name="setting-up-the-database-connection"></a><span data-ttu-id="c589f-150">Veritabanı bağlantısı kurma</span><span class="sxs-lookup"><span data-stu-id="c589f-150">Setting Up the Database Connection</span></span>  
 <span data-ttu-id="c589f-151">İlk olarak, veritabanı bağlantınızı test edin.</span><span class="sxs-lookup"><span data-stu-id="c589f-151">First, test your connection to the database.</span></span> <span data-ttu-id="c589f-152">Özellikle Northwnd, veritabanının adını hiçbir i olduğuna dikkat edin karakter.</span><span class="sxs-lookup"><span data-stu-id="c589f-152">Note especially that the name of the database, Northwnd, has no i character.</span></span> <span data-ttu-id="c589f-153">Sonraki adımlarda hatalara neden Northwind parçalı sınıf nasıl yazıldığını belirlemek için northwind.vb dosyasını gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="c589f-153">If you generate errors in the next steps, review the northwind.vb file to determine how the Northwind partial class is spelled.</span></span>  
  
#### <a name="to-set-up-and-test-the-database-connection"></a><span data-ttu-id="c589f-154">Ayarlama ve veritabanı bağlantısını test etme</span><span class="sxs-lookup"><span data-stu-id="c589f-154">To set up and test the database connection</span></span>  
  
1.  <span data-ttu-id="c589f-155">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="c589f-155">Type or paste the following code into `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#2)]  
  
2.  <span data-ttu-id="c589f-156">Bu noktada uygulamayı test etmek için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c589f-156">Press F5 to test the application at this point.</span></span>  
  
     <span data-ttu-id="c589f-157">A **konsol** penceresi açılır.</span><span class="sxs-lookup"><span data-stu-id="c589f-157">A **Console** window opens.</span></span>  
  
     <span data-ttu-id="c589f-158">Enter tuşuna basarak uygulamayı kapatmak **konsol** penceresinde veya tıklatarak **durdurma hata ayıklama** üzerinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **hata ayıklama** menüsü.</span><span class="sxs-lookup"><span data-stu-id="c589f-158">Close the application by pressing Enter in the **Console** window, or by clicking **Stop Debugging** on the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **Debug** menu.</span></span>  
  
## <a name="creating-a-new-entity"></a><span data-ttu-id="c589f-159">Yeni bir varlık oluşturma</span><span class="sxs-lookup"><span data-stu-id="c589f-159">Creating a New Entity</span></span>  
 <span data-ttu-id="c589f-160">Yeni bir varlık oluşturma basittir.</span><span class="sxs-lookup"><span data-stu-id="c589f-160">Creating a new entity is straightforward.</span></span> <span data-ttu-id="c589f-161">Nesne oluşturma (gibi `Customer`) kullanarak `New` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="c589f-161">You can create objects (such as `Customer`) by using the `New` keyword.</span></span>  
  
 <span data-ttu-id="c589f-162">Bu ve aşağıdaki bölümlerde, yalnızca yerel önbelleğe değişiklikler yapıyor.</span><span class="sxs-lookup"><span data-stu-id="c589f-162">In this and the following sections, you are making changes only to the local cache.</span></span> <span data-ttu-id="c589f-163">Çağrısı tamamlanana kadar hiçbir değişiklik veritabanına gönderilen <xref:System.Data.Linq.DataContext.SubmitChanges%2A> bu kılavuzda sonuna doğru.</span><span class="sxs-lookup"><span data-stu-id="c589f-163">No changes are sent to the database until you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> toward the end of this walkthrough.</span></span>  
  
#### <a name="to-add-a-new-customer-entity-object"></a><span data-ttu-id="c589f-164">Yeni bir müşteri varlık nesnesini eklemek için</span><span class="sxs-lookup"><span data-stu-id="c589f-164">To add a new Customer entity object</span></span>  
  
1.  <span data-ttu-id="c589f-165">Yeni bir `Customer` önce aşağıdaki kodu ekleyerek `Console.ReadLine` içinde `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="c589f-165">Create a new `Customer` by adding the following code before `Console.ReadLine` in `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#3)]  
  
2.  <span data-ttu-id="c589f-166">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c589f-166">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="c589f-167">Konsol penceresinde gösterilen sonuçları aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="c589f-167">The results that are shown in the console window are as follows:</span></span>  
  
     `Customers matching CA before insert:`  
  
     `Customer ID: CACTU`  
  
     `Customer ID: RICAR`  
  
     <span data-ttu-id="c589f-168">Yeni satır sonuçlarında görünmez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c589f-168">Note that the new row does not appear in the results.</span></span> <span data-ttu-id="c589f-169">Yeni veriler veritabanına henüz gönderilmedi.</span><span class="sxs-lookup"><span data-stu-id="c589f-169">The new data has not yet been submitted to the database.</span></span>  
  
3.  <span data-ttu-id="c589f-170">Enter tuşuna basın **konsol** penceresi hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c589f-170">Press Enter in the **Console** window to stop debugging.</span></span>  
  
## <a name="updating-an-entity"></a><span data-ttu-id="c589f-171">Bir varlık güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="c589f-171">Updating an Entity</span></span>  
 <span data-ttu-id="c589f-172">Aşağıdaki adımlarda, alacak bir `Customer` nesne ve özelliklerinden biri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c589f-172">In the following steps, you will retrieve a `Customer` object and modify one of its properties.</span></span>  
  
#### <a name="to-change-the-name-of-a-customer"></a><span data-ttu-id="c589f-173">Bir müşterinin adını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c589f-173">To change the name of a Customer</span></span>  
  
-   <span data-ttu-id="c589f-174">Yukarıdaki aşağıdaki kodu ekleyin `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="c589f-174">Add the following code above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#4)]  
  
## <a name="deleting-an-entity"></a><span data-ttu-id="c589f-175">Bir varlığı silme</span><span class="sxs-lookup"><span data-stu-id="c589f-175">Deleting an Entity</span></span>  
 <span data-ttu-id="c589f-176">Aynı müşteri nesnesini kullanarak, ilk sipariş silebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c589f-176">Using the same customer object, you can delete the first order.</span></span>  
  
 <span data-ttu-id="c589f-177">Aşağıdaki kod ilişkileri sever gösterilmiştir satırları ve satır veritabanından silmek nasıl arasında.</span><span class="sxs-lookup"><span data-stu-id="c589f-177">The following code demonstrates how to sever relationships between rows, and how to delete a row from the database.</span></span>  
  
#### <a name="to-delete-a-row"></a><span data-ttu-id="c589f-178">Bir satır silmek için</span><span class="sxs-lookup"><span data-stu-id="c589f-178">To delete a row</span></span>  
  
-   <span data-ttu-id="c589f-179">Aşağıdaki kodu ekleyin yukarıdaki `Console.ReadLine()`:</span><span class="sxs-lookup"><span data-stu-id="c589f-179">Add the following code just above `Console.ReadLine()`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#5)]  
  
## <a name="submitting-changes-to-the-database"></a><span data-ttu-id="c589f-180">Veritabanı değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="c589f-180">Submitting Changes to the Database</span></span>  
 <span data-ttu-id="c589f-181">Son adım gereklidir oluşturmak için güncelleştirme ve nesneleri silme gerçekte değişiklikler veritabanına göndermek için.</span><span class="sxs-lookup"><span data-stu-id="c589f-181">The final step required for creating, updating, and deleting objects is to actually submit the changes to the database.</span></span> <span data-ttu-id="c589f-182">Bu adım olmadan yaptığınız değişiklikler yalnızca yerel ve sorgu sonuçlarında görünmez.</span><span class="sxs-lookup"><span data-stu-id="c589f-182">Without this step, your changes are only local and will not appear in query results.</span></span>  
  
#### <a name="to-submit-changes-to-the-database"></a><span data-ttu-id="c589f-183">Değişiklikler veritabanına göndermek için</span><span class="sxs-lookup"><span data-stu-id="c589f-183">To submit changes to the database</span></span>  
  
1.  <span data-ttu-id="c589f-184">Aşağıdaki kod yalnızca yukarıda INSERT `Console.ReadLine`:</span><span class="sxs-lookup"><span data-stu-id="c589f-184">Insert the following code just above `Console.ReadLine`:</span></span>  
  
     [!code-vb[DLinqWalk3VB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="c589f-185">Aşağıdaki kodu ekleyin (sonra `SubmitChanges`) göstermek için önce ve sonra değişiklikleri gönderme etkilerini:</span><span class="sxs-lookup"><span data-stu-id="c589f-185">Insert the following code (after `SubmitChanges`) to show the before and after effects of submitting the changes:</span></span>  
  
     [!code-vb[DLinqWalk3VB#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk3VB/vb/Module1.vb#7)]  
  
3.  <span data-ttu-id="c589f-186">Çözüm hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c589f-186">Press F5 to debug the solution.</span></span>  
  
     <span data-ttu-id="c589f-187">Konsol penceresinde aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="c589f-187">The console window appears as follows:</span></span>  
  
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
  
4.  <span data-ttu-id="c589f-188">Enter tuşuna basın **konsol** penceresi hata ayıklamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="c589f-188">Press Enter in the **Console** window to stop debugging.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c589f-189">Değişiklikleri göndererek yeni müşteri ekledikten sonra bu çözüm yürütülemiyor yeniden olduğu gibi aynı müşteriye yeniden eklenemiyor çünkü.</span><span class="sxs-lookup"><span data-stu-id="c589f-189">After you have added the new customer by submitting the changes, you cannot execute this solution again as is, because you cannot add the same customer again as is.</span></span> <span data-ttu-id="c589f-190">Çözümü yeniden yürütmek için eklenecek Müşteri Kimliği değerini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="c589f-190">To execute the solution again, change the value of the customer ID to be added.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c589f-191">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c589f-191">See Also</span></span>  
 [<span data-ttu-id="c589f-192">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="c589f-192">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
