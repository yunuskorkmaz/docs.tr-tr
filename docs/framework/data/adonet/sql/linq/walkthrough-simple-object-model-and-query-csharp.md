---
title: "İzlenecek yol: Basit bir nesne modeli ve sorgu (C#)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d082b7d53330bf755f9f4322ae24d8ad3dc0ac7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="c2459-102">İzlenecek yol: Basit bir nesne modeli ve sorgu (C#)</span><span class="sxs-lookup"><span data-stu-id="c2459-102">Walkthrough: Simple Object Model and Query (C#)</span></span>
<span data-ttu-id="c2459-103">Bu kılavuz bir temel uçtan uca sağlar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık senaryoyla.</span><span class="sxs-lookup"><span data-stu-id="c2459-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="c2459-104">Örnek Northwind veritabanı Müşteriler tablosunda modeller bir varlık sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2459-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="c2459-105">Ardından, Londra'da buluna listesi müşteriler için basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2459-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="c2459-106">Bu kılavuzda kod odaklı yardımcı olmak için tasarım gereği Göster [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kavramları.</span><span class="sxs-lookup"><span data-stu-id="c2459-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="c2459-107">Kullanacağınız normalde konuşarak [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] nesne modeli oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="c2459-107">Normally speaking, you would use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="c2459-108">Bu kılavuz, Visual C# geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c2459-108">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c2459-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c2459-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="c2459-110">Bu kılavuzda, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest5") kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2459-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="c2459-111">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2459-111">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="c2459-112">Bu kılavuz, Northwind örnek veritabanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c2459-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="c2459-113">Bu veritabanı geliştirme bilgisayarınızda yoksa Microsoft sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2459-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="c2459-114">Yönergeler için bkz: [örnek veritabanları yükleme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c2459-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="c2459-115">Veritabanı indirdikten sonra dosyanın c:\linqtest5 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c2459-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c2459-116">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c2459-116">Overview</span></span>  
 <span data-ttu-id="c2459-117">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="c2459-117">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="c2459-118">Oluşturma bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çözümde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c2459-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="c2459-119">Bir sınıf bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="c2459-119">Mapping a class to a database table.</span></span>  
  
-   <span data-ttu-id="c2459-120">Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme.</span><span class="sxs-lookup"><span data-stu-id="c2459-120">Designating properties on the class to represent database columns.</span></span>  
  
-   <span data-ttu-id="c2459-121">Northwind veritabanı bağlantısı belirtme.</span><span class="sxs-lookup"><span data-stu-id="c2459-121">Specifying the connection to the Northwind database.</span></span>  
  
-   <span data-ttu-id="c2459-122">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c2459-122">Creating a simple query to run against the database.</span></span>  
  
-   <span data-ttu-id="c2459-123">Sorgu yürütülürken ve sonuçları gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2459-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="c2459-124">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2459-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="c2459-125">Bu ilk görevde oluşturduğunuz bir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] derlemek ve çalıştırmak için gerekli başvuruları içeren çözüm bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projesi.</span><span class="sxs-lookup"><span data-stu-id="c2459-125">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="c2459-126">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c2459-126">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="c2459-127">Üzerinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **dosya** menüsündeki **yeni**ve ardından **proje**.</span><span class="sxs-lookup"><span data-stu-id="c2459-127">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c2459-128">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklatın **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="c2459-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="c2459-129">İçinde **şablonları** bölmesinde tıklatın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="c2459-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4.  <span data-ttu-id="c2459-130">İçinde **adı** kutusuna **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="c2459-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5.  <span data-ttu-id="c2459-131">İçinde **konumu** kutusunda, proje dosyalarını depolamak istediğiniz doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c2459-131">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="c2459-132">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c2459-132">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="c2459-133">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c2459-133">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="c2459-134">Bu kılavuzda projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c2459-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="c2459-135">System.Data.Linq projenize başvuru olarak listeleniyorsa değil (genişletin **başvuruları** düğümünde **Çözüm Gezgini**), bunu, aşağıdaki adımlarda açıklandığı gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c2459-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="c2459-136">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="c2459-136">To add System.Data.Linq</span></span>  
  
1.  <span data-ttu-id="c2459-137">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="c2459-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="c2459-138">İçinde **Başvuru Ekle** iletişim kutusu, tıklatın **.NET**System.Data.Linq derleme'yi tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="c2459-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="c2459-139">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c2459-139">The assembly is added to the project.</span></span>  
  
3.  <span data-ttu-id="c2459-140">Aşağıdaki yönergeleri en üstünde ekleyin **Program.cs**:</span><span class="sxs-lookup"><span data-stu-id="c2459-140">Add the following directives at the top of **Program.cs**:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="c2459-141">Bir sınıf bir veritabanı tablosuna eşleme</span><span class="sxs-lookup"><span data-stu-id="c2459-141">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="c2459-142">Bu adımda, bir sınıf oluşturun ve bir veritabanı tablosuna eşleyin.</span><span class="sxs-lookup"><span data-stu-id="c2459-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="c2459-143">Bu tür bir sınıf olarak adlandırılır bir *varlık sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="c2459-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="c2459-144">Eşleme yalnızca ekleyerek gerçekleştirilir Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="c2459-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="c2459-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği, veritabanında tablonun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2459-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="c2459-146">Bir varlık sınıfı oluşturmak ve bir veritabanı tablosuna eşlemek için</span><span class="sxs-lookup"><span data-stu-id="c2459-146">To create an entity class and map it to a database table</span></span>  
  
-   <span data-ttu-id="c2459-147">Yazın veya Program.cs hemen yukarıdaki aşağıdaki kodu yapıştırın `Program` sınıf bildiriminin:</span><span class="sxs-lookup"><span data-stu-id="c2459-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>  
  
     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="c2459-148">Veritabanı sütunlarını temsil etmek için sınıfındaki özellikleri belirleme</span><span class="sxs-lookup"><span data-stu-id="c2459-148">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="c2459-149">Bu adımda, çeşitli görevleri yerine getirin.</span><span class="sxs-lookup"><span data-stu-id="c2459-149">In this step, you accomplish several tasks.</span></span>  
  
-   <span data-ttu-id="c2459-150">Kullandığınız <xref:System.Data.Linq.Mapping.ColumnAttribute> belirlemek için öznitelik `CustomerID` ve `City` sınıf özellikleri varlık üzerinde veritabanı tablosundaki sütunlarla temsil eden olarak.</span><span class="sxs-lookup"><span data-stu-id="c2459-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
-   <span data-ttu-id="c2459-151">Belirttiğiniz `CustomerID` veritabanının birincil anahtar sütunu temsil eden olarak özelliği.</span><span class="sxs-lookup"><span data-stu-id="c2459-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
-   <span data-ttu-id="c2459-152">Belirttiğiniz `_CustomerID` ve `_City` özel depolama alanları.</span><span class="sxs-lookup"><span data-stu-id="c2459-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c2459-153">ardından depolayabilir ve iş mantığı içerebilecek ortak erişimciler kullanmak yerine doğrudan değerleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c2459-153"> can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="c2459-154">İki veritabanı sütun özelliklerini göstermek için</span><span class="sxs-lookup"><span data-stu-id="c2459-154">To represent characteristics of two database columns</span></span>  
  
-   <span data-ttu-id="c2459-155">Yazın veya için süslü ayraçlar içinde Program.cs aşağıdaki kodu yapıştırın `Customer` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="c2459-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="c2459-156">Northwind veritabanı bağlantısı belirtme</span><span class="sxs-lookup"><span data-stu-id="c2459-156">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="c2459-157">Bu adımda, kullandığınız bir <xref:System.Data.Linq.DataContext> nesnesi, kod tabanlı veri yapılarını ve veritabanının kendisi arasında bağlantı kurun.</span><span class="sxs-lookup"><span data-stu-id="c2459-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="c2459-158"><xref:System.Data.Linq.DataContext> Ana kanal üzerinden veritabanından nesneleri almak ve değişiklikleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="c2459-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="c2459-159">Ayrıca bildirme bir `Table<Customer>` veritabanı Müşteriler tablosunda, sorguları için mantıksal, yazılı tablo olarak hareket edecek.</span><span class="sxs-lookup"><span data-stu-id="c2459-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="c2459-160">Oluşturacak ve daha sonraki adımlarda bu sorgular yürütün.</span><span class="sxs-lookup"><span data-stu-id="c2459-160">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="c2459-161">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c2459-161">To specify the database connection</span></span>  
  
-   <span data-ttu-id="c2459-162">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c2459-162">Type or paste the following code into the `Main` method.</span></span>  
  
     <span data-ttu-id="c2459-163">Unutmayın `northwnd.mdf` dosya linqtest5 klasöründe olarak varsayılır.</span><span class="sxs-lookup"><span data-stu-id="c2459-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="c2459-164">Daha fazla bilgi için bu kılavuzda daha önce Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c2459-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="c2459-165">Basit bir sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c2459-165">Creating a Simple Query</span></span>  
 <span data-ttu-id="c2459-166">Bu adımda, hangi müşterilerin veritabanı Müşteriler tablosunda Londra'da bulmak için bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c2459-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="c2459-167">Bu adımda sorgu kod yalnızca sorgu açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2459-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="c2459-168">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="c2459-168">It does not execute it.</span></span> <span data-ttu-id="c2459-169">Bu yaklaşım olarak bilinen *yürütme ertelenmiş*.</span><span class="sxs-lookup"><span data-stu-id="c2459-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="c2459-170">Daha fazla bilgi için bkz: [LINQ sorgularını (C#) giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c2459-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="c2459-171">Ayrıca bir günlük çıktısı SQL göstermek için üretim komutları, olacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c2459-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="c2459-172">Bu günlük kaydı özelliği (kullanan <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama ve veritabanına doğru gönderilen komutları sorgunuzu temsil ettiğini belirlemede yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c2459-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="c2459-173">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c2459-173">To create a simple query</span></span>  
  
-   <span data-ttu-id="c2459-174">Uygulamasına aşağıdaki kodu yazın veya yapıştırın `Main` sonra yöntemi `Table<Customer>` bildirimi.</span><span class="sxs-lookup"><span data-stu-id="c2459-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="c2459-175">Sorgu yürütme</span><span class="sxs-lookup"><span data-stu-id="c2459-175">Executing the Query</span></span>  
 <span data-ttu-id="c2459-176">Bu adımda, aslında sorgu yürütün.</span><span class="sxs-lookup"><span data-stu-id="c2459-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="c2459-177">Sonuçları gerektiği kadar önceki adımlarda oluşturduğunuz sorgu ifadeleri değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c2459-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="c2459-178">Başladığınızda `foreach` yineleme, veritabanında bir SQL komutu yürütülür ve nesneleri gerçekleştirilip.</span><span class="sxs-lookup"><span data-stu-id="c2459-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="c2459-179">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="c2459-179">To execute the query</span></span>  
  
1.  <span data-ttu-id="c2459-180">Yazın veya sonuna aşağıdaki kodu yapıştırın `Main` yöntemi (sonra sorgu açıklama).</span><span class="sxs-lookup"><span data-stu-id="c2459-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>  
  
     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]  
  
2.  <span data-ttu-id="c2459-181">Uygulamada hata ayıklama için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c2459-181">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c2459-182">Uygulamanızı bir çalışma zamanı hatası oluşturur, sorun giderme bölümüne bakın. [tarafından izlenecek yollar öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="c2459-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="c2459-183">Sorgu sonuçları konsol penceresinde aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c2459-183">The query results in the console window should appear as follows:</span></span>  
  
     `ID=AROUT, City=London`  
  
     `ID=BSBEV, City=London`  
  
     `ID=CONSH, City=London`  
  
     `ID=EASTC, City=London`  
  
     `ID=NORTS, City=London`  
  
     `ID=SEVES, City=London`  
  
3.  <span data-ttu-id="c2459-184">Konsol penceresinde uygulamayı kapatmak için Enter tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c2459-184">Press Enter in the console window to close the application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c2459-185">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c2459-185">Next Steps</span></span>  
 <span data-ttu-id="c2459-186">[İzlenecek yol: ilişkileri üzerinden sorgulama (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) konu devam bu kılavuzda bittiği.</span><span class="sxs-lookup"><span data-stu-id="c2459-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="c2459-187">Sorgu arasında ilişkiler yönergeyi gösterir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tabloları, benzer arasında sorgulayabilirsiniz *birleştirmeler* ilişkisel bir veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="c2459-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="c2459-188">Sorgu arasında ilişkiler izlenecek yapmak istiyorsanız, çözüm geçirmesini tamamladınız, izlenecek yol için bir önkoşul olduğu kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c2459-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2459-189">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c2459-189">See Also</span></span>  
 [<span data-ttu-id="c2459-190">Öğrenme tarafından izlenecek yollar</span><span class="sxs-lookup"><span data-stu-id="c2459-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
