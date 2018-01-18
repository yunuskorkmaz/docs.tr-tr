---
title: "İzlenecek yol: Basit bir nesne modeli ve sorgu (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9d72c0e1f432679f4dc818703dafb813ab8ebd19
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="be8fc-102">İzlenecek yol: Basit bir nesne modeli ve sorgu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be8fc-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="be8fc-103">Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık senaryoyla.</span><span class="sxs-lookup"><span data-stu-id="be8fc-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="be8fc-104">Örnek Northwind veritabanı Müşteriler tablosunda modeller bir varlık sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be8fc-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="be8fc-105">Ardından, Londra'da buluna listesi müşteriler için basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be8fc-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="be8fc-106">Bu kılavuzda kod odaklı yardımcı olmak için tasarım gereği Göster [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kavramları.</span><span class="sxs-lookup"><span data-stu-id="be8fc-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="be8fc-107">Kullanacağınız normalde konuşarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="be8fc-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="be8fc-108">Bu kılavuz, Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="be8fc-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="be8fc-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="be8fc-110">Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="be8fc-111">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be8fc-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="be8fc-112">Bu kılavuz, Northwind örnek veritabanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="be8fc-113">Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be8fc-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="be8fc-114">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="be8fc-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="be8fc-115">Veritabanı indirdikten sonra dosyanın c:\linqtest klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="be8fc-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="be8fc-116">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="be8fc-116">Overview</span></span>  
 <span data-ttu-id="be8fc-117">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="be8fc-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="be8fc-118">Oluşturma bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çözümde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be8fc-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="be8fc-119">Bir sınıf bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="be8fc-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="be8fc-120">Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="be8fc-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="be8fc-121">Northwind veritabanı bağlantısı belirtme.</span><span class="sxs-lookup"><span data-stu-id="be8fc-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="be8fc-122">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="be8fc-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="be8fc-123">Sorgu yürütülürken ve sonuçları gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be8fc-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="be8fc-124">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="be8fc-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="be8fc-125">Bu ilk görevde oluşturduğunuz bir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] derlemek ve çalıştırmak için gerekli başvuruları içeren çözüm bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="be8fc-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="be8fc-126">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be8fc-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="be8fc-127">Üzerinde **dosya** menüsünde tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-127">On the **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="be8fc-128">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3.  <span data-ttu-id="be8fc-129">İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="be8fc-130">İçinde **adı** kutusuna **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="be8fc-131">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="be8fc-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="be8fc-132">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="be8fc-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="be8fc-133">Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="be8fc-134">Varsa `System.Data.Linq` projenizdeki bir başvuru olarak listelenmemiş (tıklatın **tüm dosyaları göster** içinde **Çözüm Gezgini** ve genişletin **başvuruları** düğüm), açıklandığı gibi eklemek Aşağıdaki adımlar.</span><span class="sxs-lookup"><span data-stu-id="be8fc-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="be8fc-135">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="be8fc-135">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="be8fc-136">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="be8fc-137">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="be8fc-138">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-138">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="be8fc-139">Ayrıca, **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**kaydırın ve System.Windows.Forms'ı tıklatın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="be8fc-140">İleti kutusu kılavuzda destekler, bu derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4.  <span data-ttu-id="be8fc-141">Yukarıdaki aşağıdaki yönergeleri eklemek `Module1`:</span><span class="sxs-lookup"><span data-stu-id="be8fc-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="be8fc-142">Bir sınıf bir veritabanı tablosuna eşleme</span><span class="sxs-lookup"><span data-stu-id="be8fc-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="be8fc-143">Bu adımda, bir sınıf oluşturun ve bir veritabanı tablosuna eşleyin.</span><span class="sxs-lookup"><span data-stu-id="be8fc-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="be8fc-144">Bu tür bir sınıf olarak adlandırılır bir *varlık sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="be8fc-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="be8fc-145">Eşleme yalnızca ekleyerek gerçekleştirilir Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="be8fc-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="be8fc-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği, veritabanında tablonun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="be8fc-147">Bir varlık sınıfı oluşturmak ve bir veritabanı tablosuna eşlemek için</span><span class="sxs-lookup"><span data-stu-id="be8fc-147">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="be8fc-148">Yazın veya Module1.vb hemen yukarıdaki aşağıdaki kodu yapıştırın `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="be8fc-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="be8fc-149">Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme</span><span class="sxs-lookup"><span data-stu-id="be8fc-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="be8fc-150">Bu adımda, çeşitli görevleri yerine getirin.</span><span class="sxs-lookup"><span data-stu-id="be8fc-150">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="be8fc-151">Kullandığınız <xref:System.Data.Linq.Mapping.ColumnAttribute> belirlemek için öznitelik `CustomerID` ve `City` sınıf özellikleri varlık üzerinde veritabanı tablosundaki sütunlarla temsil eden olarak.</span><span class="sxs-lookup"><span data-stu-id="be8fc-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="be8fc-152">Belirttiğiniz `CustomerID` veritabanının birincil anahtar sütunu temsil eden olarak özelliği.</span><span class="sxs-lookup"><span data-stu-id="be8fc-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="be8fc-153">Belirttiğiniz `_CustomerID` ve `_City` özel depolama alanları.</span><span class="sxs-lookup"><span data-stu-id="be8fc-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="be8fc-154">ardından depolayabilir ve iş mantığı içerebilecek ortak erişimciler kullanmak yerine doğrudan değerleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="be8fc-154"> can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="be8fc-155">İki veritabanı sütun özelliklerini göstermek için</span><span class="sxs-lookup"><span data-stu-id="be8fc-155">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="be8fc-156">Yazın veya Module1.vb hemen öncesine aşağıdaki kodu yapıştırın `End Class`:</span><span class="sxs-lookup"><span data-stu-id="be8fc-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="be8fc-157">Northwind veritabanı bağlantısı belirtme</span><span class="sxs-lookup"><span data-stu-id="be8fc-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="be8fc-158">Bu adımda, kullandığınız bir <xref:System.Data.Linq.DataContext> nesnesi, kod tabanlı veri yapılarını ve veritabanının kendisi arasında bağlantı kurun.</span><span class="sxs-lookup"><span data-stu-id="be8fc-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="be8fc-159"><xref:System.Data.Linq.DataContext> Ana kanal üzerinden veritabanından nesneleri almak ve değişiklikleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="be8fc-160">Ayrıca bildirme bir `Table(Of Customer)` veritabanı Müşteriler tablosunda, sorguları için mantıksal, yazılı tablo olarak hareket edecek.</span><span class="sxs-lookup"><span data-stu-id="be8fc-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="be8fc-161">Oluşturacak ve daha sonraki adımlarda bu sorgular yürütün.</span><span class="sxs-lookup"><span data-stu-id="be8fc-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="be8fc-162">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="be8fc-162">To specify the database connection</span></span>  
  
-   <span data-ttu-id="be8fc-163">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Sub Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="be8fc-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="be8fc-164">Unutmayın `northwnd.mdf` dosya linqtest klasöründe olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="be8fc-165">Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="be8fc-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="be8fc-166">Basit bir sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="be8fc-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="be8fc-167">Bu adımda, hangi müşterilerin veritabanı Müşteriler tablosunda Londra'da bulmak için bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be8fc-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="be8fc-168">Bu adımda sorgu kod yalnızca sorgu açıklar.</span><span class="sxs-lookup"><span data-stu-id="be8fc-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="be8fc-169">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="be8fc-169">It does not execute it.</span></span> <span data-ttu-id="be8fc-170">Bu yaklaşım olarak bilinen *yürütme ertelenmiş*.</span><span class="sxs-lookup"><span data-stu-id="be8fc-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="be8fc-171">Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="be8fc-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="be8fc-172">Ayrıca bir günlük çıktısı SQL göstermek için üretim komutları, olacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be8fc-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="be8fc-173">Bu günlük kaydı özelliği (kullanan <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama ve veritabanına doğru gönderilen komutları sorgunuzu temsil ettiğini belirlemede yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="be8fc-174">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be8fc-174">To create a simple query</span></span>  
  
-   <span data-ttu-id="be8fc-175">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Sub Main` sonra yöntemi `Table(Of Customer)` bildirimi:</span><span class="sxs-lookup"><span data-stu-id="be8fc-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="be8fc-176">Sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="be8fc-176">Executing the Query</span></span>  
 <span data-ttu-id="be8fc-177">Bu adımda, aslında sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="be8fc-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="be8fc-178">Sonuçları gerektiği kadar önceki adımlarda oluşturduğunuz sorgu ifadeleri değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="be8fc-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="be8fc-179">Başladığınızda `For Each` yineleme, veritabanında bir SQL komutu yürütülür ve nesneleri gerçekleştirilip.</span><span class="sxs-lookup"><span data-stu-id="be8fc-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="be8fc-180">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="be8fc-180">To execute the query</span></span>  
  
1.  <span data-ttu-id="be8fc-181">Yazın veya sonuna aşağıdaki kodu yapıştırın `Sub Main` yöntemi (sonra sorgu açıklaması):</span><span class="sxs-lookup"><span data-stu-id="be8fc-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2.  <span data-ttu-id="be8fc-182">Uygulamada hata ayıklama için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="be8fc-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="be8fc-183">Uygulamanızı bir çalışma zamanı hatası oluşturur, sorun giderme bölümüne bakın. [tarafından izlenecek yollar öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="be8fc-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="be8fc-184">İleti kutusu altı müşterilerin listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be8fc-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="be8fc-185">Konsol penceresinde oluşturulan SQL kodunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be8fc-185">The Console window displays the generated SQL code.</span></span>  
  
3.  <span data-ttu-id="be8fc-186">Tıklatın **Tamam** ileti kutusu kapatılamadı.</span><span class="sxs-lookup"><span data-stu-id="be8fc-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="be8fc-187">Uygulamayı kapatır.</span><span class="sxs-lookup"><span data-stu-id="be8fc-187">The application closes.</span></span>  
  
4.  <span data-ttu-id="be8fc-188">Üzerinde **dosya** menüsünde tıklatın **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="be8fc-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="be8fc-189">Sonraki Kılavuzu ile devam ederseniz bu uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="be8fc-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="be8fc-190">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="be8fc-190">Next Steps</span></span>  
 <span data-ttu-id="be8fc-191">[İzlenecek yol: arasında sorgulama ilişkileri (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) konu devam bu kılavuzda bittiği.</span><span class="sxs-lookup"><span data-stu-id="be8fc-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="be8fc-192">Sorgulama arasında ilişkiler anlatımda gösterilir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tabloları, benzer arasında sorgulayabilirsiniz *birleştirmeler* ilişkisel bir veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="be8fc-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="be8fc-193">Sorgulama arasında ilişkiler izlenecek yapmak istiyorsanız, çözüm geçirmesini tamamladınız, izlenecek yol için bir önkoşul olduğu kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="be8fc-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8fc-194">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be8fc-194">See Also</span></span>  
 [<span data-ttu-id="be8fc-195">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="be8fc-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
