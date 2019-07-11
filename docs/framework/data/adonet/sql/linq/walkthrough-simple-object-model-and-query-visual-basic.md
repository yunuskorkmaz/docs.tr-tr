---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: 9bf97263bf8ae0ac3ece187e81a51edfaef48a54
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742583"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="a54b7-102">İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a54b7-102">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>
<span data-ttu-id="a54b7-103">Bu izlenecek yol sağlayan bir temel için uçtan uca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en düşük karmaşıklık bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="a54b7-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="a54b7-104">Örnek Northwind veritabanındaki Müşteriler tablosunu modeller bir varlık sınıfı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a54b7-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="a54b7-105">Ardından, Londra'da buluna listesi müşteriler için basit bir sorgu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a54b7-105">You will then create a simple query to list customers who are located in London.</span></span>  
  
 <span data-ttu-id="a54b7-106">Bu izlenecek yol, kod odaklı yardımcı olmak için tasarım gereği Göster [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kavramları.</span><span class="sxs-lookup"><span data-stu-id="a54b7-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="a54b7-107">Normal şekilde açıklamak gerekirse, Nesne İlişkisel Tasarımcısı, nesne modeli oluşturmak için kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="a54b7-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="a54b7-108">Bu izlenecek yol, Visual Basic geliştirme ayarlarını kullanarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-108">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a54b7-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="a54b7-109">Prerequisites</span></span>  
  
- <span data-ttu-id="a54b7-110">Bu izlenecek yol, dosyaları tutmak için ayrılmış bir klasör ("c:\linqtest") kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-110">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="a54b7-111">İzlenecek yol başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a54b7-111">Create this folder before you begin the walkthrough.</span></span>  
  
- <span data-ttu-id="a54b7-112">Bu izlenecek yol, Northwind örnek veritabanıyla kurulan gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a54b7-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="a54b7-113">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Yükleme sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a54b7-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="a54b7-114">Yönergeler için [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a54b7-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="a54b7-115">Veritabanı indirdikten sonra dosyayı c:\linqtest klasöre kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="a54b7-115">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a54b7-116">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a54b7-116">Overview</span></span>  
 <span data-ttu-id="a54b7-117">Bu kılavuz altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="a54b7-117">This walkthrough consists of six main tasks:</span></span>  
  
- <span data-ttu-id="a54b7-118">Oluşturma bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Visual Studio'daki çözüm.</span><span class="sxs-lookup"><span data-stu-id="a54b7-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
- <span data-ttu-id="a54b7-119">Bir sınıf, bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="a54b7-119">Mapping a class to a database table.</span></span>  
  
- <span data-ttu-id="a54b7-120">Veritabanı sütunlarını gösteren sınıf özelliklerini belirleme.</span><span class="sxs-lookup"><span data-stu-id="a54b7-120">Designating properties on the class to represent database columns.</span></span>  
  
- <span data-ttu-id="a54b7-121">Northwind veritabanına bir bağlantı belirtme.</span><span class="sxs-lookup"><span data-stu-id="a54b7-121">Specifying the connection to the Northwind database.</span></span>  
  
- <span data-ttu-id="a54b7-122">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a54b7-122">Creating a simple query to run against the database.</span></span>  
  
- <span data-ttu-id="a54b7-123">Sorguyu yürüten ve sonuçları gözleme.</span><span class="sxs-lookup"><span data-stu-id="a54b7-123">Executing the query and observing the results.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="a54b7-124">Bir LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a54b7-124">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="a54b7-125">Bu ilk görevde oluşturduğunuz derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje.</span><span class="sxs-lookup"><span data-stu-id="a54b7-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="a54b7-126">Bir LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a54b7-126">To create a LINQ to SQL solution</span></span>  
  
1. <span data-ttu-id="a54b7-127">Üzerinde **dosya** menüsünü tıklatın **yeni proje**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-127">On the **File** menu, click **New Project**.</span></span>  
  
2. <span data-ttu-id="a54b7-128">İçinde **proje türleri** bölmesinde **yeni proje** iletişim kutusu, tıklayın **Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-128">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>  
  
3. <span data-ttu-id="a54b7-129">İçinde **şablonları** bölmesinde tıklayın **konsol uygulaması**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-129">In the **Templates** pane, click **Console Application**.</span></span>  
  
4. <span data-ttu-id="a54b7-130">İçinde **adı** kutusuna **LinqConsoleApp**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-130">In the **Name** box, type **LinqConsoleApp**.</span></span>  
  
5. <span data-ttu-id="a54b7-131">          **Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="a54b7-131">Click **OK**.</span></span>  
  
## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="a54b7-132">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="a54b7-132">Adding LINQ References and Directives</span></span>  
 <span data-ttu-id="a54b7-133">Bu izlenecek yol, projenizdeki varsayılan olarak yüklü olmayabilir derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-133">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="a54b7-134">Varsa `System.Data.Linq` projenize bir başvuru olarak listelenmemiş (tıklayın **tüm dosyaları göster** içinde **Çözüm Gezgini** genişletin **başvuruları** düğümü), açıklandığı gibi ekleyin Aşağıdaki adımlar.</span><span class="sxs-lookup"><span data-stu-id="a54b7-134">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>  
  
#### <a name="to-add-systemdatalinq"></a><span data-ttu-id="a54b7-135">System.Data.Linq eklemek için</span><span class="sxs-lookup"><span data-stu-id="a54b7-135">To add System.Data.Linq</span></span>  
  
1. <span data-ttu-id="a54b7-136">İçinde **Çözüm Gezgini**, sağ **başvuruları**ve ardından **Başvuru Ekle**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-136">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2. <span data-ttu-id="a54b7-137">İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**System.Data.Linq derleme tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-137">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a54b7-138">Derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="a54b7-138">The assembly is added to the project.</span></span>  
  
3. <span data-ttu-id="a54b7-139">Ayrıca **Başvuru Ekle** iletişim kutusu, tıklayın **.NET**kaydırın ve System.Windows.Forms öğelerini tıklayın ve ardından **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-139">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a54b7-140">İleti kutusu izlenecek yolda destekler, bu derleme, projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="a54b7-140">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>  
  
4. <span data-ttu-id="a54b7-141">Yukarıdaki aşağıdaki yönergeleri ekleme `Module1`:</span><span class="sxs-lookup"><span data-stu-id="a54b7-141">Add the following directives above `Module1`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]  
  
## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="a54b7-142">Bir sınıf için bir veritabanı tablosu eşleme</span><span class="sxs-lookup"><span data-stu-id="a54b7-142">Mapping a Class to a Database Table</span></span>  
 <span data-ttu-id="a54b7-143">Bu adımda, bir sınıf oluşturun ve bir veritabanı tablosuna eşleyin.</span><span class="sxs-lookup"><span data-stu-id="a54b7-143">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="a54b7-144">Bu tür bir sınıf olarak adlandırılır bir *varlık sınıfı*.</span><span class="sxs-lookup"><span data-stu-id="a54b7-144">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="a54b7-145">Eşleme yalnızca ekleyerek gerçekleştirilir Not <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="a54b7-145">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="a54b7-146"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği veritabanında tablo adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a54b7-146">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>  
  
#### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="a54b7-147">Bir varlık sınıfı oluşturun ve bir veritabanı tablosuna eşlemek için</span><span class="sxs-lookup"><span data-stu-id="a54b7-147">To create an entity class and map it to a database table</span></span>  
  
- <span data-ttu-id="a54b7-148">Yazın veya Module1.vb hemen yukarıdaki aşağıdaki kodu yapıştırın `Sub Main`:</span><span class="sxs-lookup"><span data-stu-id="a54b7-148">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]  
  
## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="a54b7-149">Veritabanı sütunlarını gösteren sınıf özelliklerini belirleme</span><span class="sxs-lookup"><span data-stu-id="a54b7-149">Designating Properties on the Class to Represent Database Columns</span></span>  
 <span data-ttu-id="a54b7-150">Bu adımda, çeşitli görevleri gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a54b7-150">In this step, you accomplish several tasks.</span></span>  
  
- <span data-ttu-id="a54b7-151">Kullandığınız <xref:System.Data.Linq.Mapping.ColumnAttribute> belirtmek için özniteliği `CustomerID` ve `City` sınıf özellikleri varlığı temsil eden bir veritabanı tablosundaki sütun olarak.</span><span class="sxs-lookup"><span data-stu-id="a54b7-151">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>  
  
- <span data-ttu-id="a54b7-152">Belirlediğiniz `CustomerID` veritabanı birincil anahtar sütunu temsil eden olarak özelliği.</span><span class="sxs-lookup"><span data-stu-id="a54b7-152">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>  
  
- <span data-ttu-id="a54b7-153">Belirlediğiniz `_CustomerID` ve `_City` özel depolama alanları.</span><span class="sxs-lookup"><span data-stu-id="a54b7-153">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a54b7-154">sonra depolayabilir ve iş mantığı içerebilecek ortak erişimciler kullanmak yerine doğrudan değerleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a54b7-154">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>  
  
#### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="a54b7-155">İki veritabanı sütun özellikleri temsil etmek için</span><span class="sxs-lookup"><span data-stu-id="a54b7-155">To represent characteristics of two database columns</span></span>  
  
- <span data-ttu-id="a54b7-156">Yazın veya Module1.vb aşağıdaki kodu yapıştırın, hemen önce `End Class`:</span><span class="sxs-lookup"><span data-stu-id="a54b7-156">Type or paste the following code into Module1.vb just before `End Class`:</span></span>  
  
     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]  
  
## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="a54b7-157">Northwind veritabanına bir bağlantı belirtme</span><span class="sxs-lookup"><span data-stu-id="a54b7-157">Specifying the Connection to the Northwind Database</span></span>  
 <span data-ttu-id="a54b7-158">Bu adımda kullandığınız bir <xref:System.Data.Linq.DataContext> , kod tabanlı veri yapıları ve veritabanı arasında bir bağlantı kurmak için nesne.</span><span class="sxs-lookup"><span data-stu-id="a54b7-158">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="a54b7-159"><xref:System.Data.Linq.DataContext> Ana kanal üzerinden veritabanından nesneleri almak ve değişiklikleri gönderme.</span><span class="sxs-lookup"><span data-stu-id="a54b7-159">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>  
  
 <span data-ttu-id="a54b7-160">Ayrıca bildirdiğiniz bir `Table(Of Customer)` veritabanındaki Müşteriler tablosunu karşı sorgularınız için mantıksal, belirlenmiş tablosu olarak görev yapacak.</span><span class="sxs-lookup"><span data-stu-id="a54b7-160">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="a54b7-161">Oluşturacak ve sonraki adımlarda aşağıdaki sorguları yürütün.</span><span class="sxs-lookup"><span data-stu-id="a54b7-161">You will create and execute these queries in later steps.</span></span>  
  
#### <a name="to-specify-the-database-connection"></a><span data-ttu-id="a54b7-162">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="a54b7-162">To specify the database connection</span></span>  
  
- <span data-ttu-id="a54b7-163">İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a54b7-163">Type or paste the following code into the `Sub Main` method.</span></span>  
  
     <span data-ttu-id="a54b7-164">Unutmayın `northwnd.mdf` linqtest klasörü içinde dosya varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-164">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="a54b7-165">Daha fazla bilgi için bu kılavuzda daha önce açıklanan Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a54b7-165">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]  
  
## <a name="creating-a-simple-query"></a><span data-ttu-id="a54b7-166">Basit bir sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="a54b7-166">Creating a Simple Query</span></span>  
 <span data-ttu-id="a54b7-167">Bu adımda, veritabanı Müşteriler tablosundaki hangi müşteriler Londra'da bulmak için bir sorgu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a54b7-167">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="a54b7-168">Bu adımda sorgu kod yalnızca sorgu açıklar.</span><span class="sxs-lookup"><span data-stu-id="a54b7-168">The query code in this step just describes the query.</span></span> <span data-ttu-id="a54b7-169">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="a54b7-169">It does not execute it.</span></span> <span data-ttu-id="a54b7-170">Bu yaklaşım olarak da bilinen *ertelenmiş yürütme*.</span><span class="sxs-lookup"><span data-stu-id="a54b7-170">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="a54b7-171">Daha fazla bilgi için [(C#) LINQ sorgularına giriş](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a54b7-171">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 <span data-ttu-id="a54b7-172">Ayrıca SQL göstermek için bir günlük çıktı üretebilir komutlarının olacak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a54b7-172">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="a54b7-173">Bu günlük özelliğini (kullanan <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama ve doğru bir şekilde veritabanına gönderilen komutları sorgunuzu temsil belirlemede yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-173">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>  
  
#### <a name="to-create-a-simple-query"></a><span data-ttu-id="a54b7-174">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a54b7-174">To create a simple query</span></span>  
  
- <span data-ttu-id="a54b7-175">İçine aşağıdaki kodu yazın veya yapıştırın `Sub Main` sonrasına `Table(Of Customer)` bildirimi:</span><span class="sxs-lookup"><span data-stu-id="a54b7-175">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>  
  
     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]  
  
## <a name="executing-the-query"></a><span data-ttu-id="a54b7-176">Sorgu yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="a54b7-176">Executing the Query</span></span>  
 <span data-ttu-id="a54b7-177">Bu adımda, aslında sorguyu yürütün.</span><span class="sxs-lookup"><span data-stu-id="a54b7-177">In this step, you actually execute the query.</span></span> <span data-ttu-id="a54b7-178">Sonuçları gerekli olana kadar önceki adımlarda oluşturulan sorgu ifadeleri değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="a54b7-178">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="a54b7-179">Başladığınızda `For Each` yineleme, veritabanında bir SQL komutu yürütülür ve nesneleri gerçekleştirilmiş.</span><span class="sxs-lookup"><span data-stu-id="a54b7-179">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="a54b7-180">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="a54b7-180">To execute the query</span></span>  
  
1. <span data-ttu-id="a54b7-181">Sonuna aşağıdaki kodu yapıştırın veya yazın `Sub Main` yöntemi (sonra sorgu açıklama):</span><span class="sxs-lookup"><span data-stu-id="a54b7-181">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>  
  
     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]  
  
2. <span data-ttu-id="a54b7-182">Uygulamada hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="a54b7-182">Press F5 to debug the application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a54b7-183">Uygulamanızı bir çalışma zamanı hatası oluşturur, sorun giderme bölümüne bakın. [izlenecek yollarla öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="a54b7-183">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>  
  
     <span data-ttu-id="a54b7-184">İleti kutusunda altı Müşteri listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a54b7-184">The message box displays a list of six customers.</span></span> <span data-ttu-id="a54b7-185">Konsol penceresinde oluşturulan SQL kodunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a54b7-185">The Console window displays the generated SQL code.</span></span>  
  
3. <span data-ttu-id="a54b7-186">Tıklayın **Tamam** ileti kutusunu kapatın.</span><span class="sxs-lookup"><span data-stu-id="a54b7-186">Click **OK** to dismiss the message box.</span></span>  
  
     <span data-ttu-id="a54b7-187">Uygulamayı kapatır.</span><span class="sxs-lookup"><span data-stu-id="a54b7-187">The application closes.</span></span>  
  
4. <span data-ttu-id="a54b7-188">Üzerinde **dosya** menüsünü tıklatın **Tümünü Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="a54b7-188">On the **File** menu, click **Save All**.</span></span>  
  
     <span data-ttu-id="a54b7-189">Sonraki adım adım kılavuza devam ederseniz, bu uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="a54b7-189">You will need this application if you continue with the next walkthrough.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="a54b7-190">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="a54b7-190">Next Steps</span></span>  
 <span data-ttu-id="a54b7-191">[İzlenecek yol: İlişkiler üzerinde sorgulama (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) konu, bu gözden geçirme sona ereceği devam eder.</span><span class="sxs-lookup"><span data-stu-id="a54b7-191">The [Walkthrough: Querying Across Relationships (Visual Basic)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="a54b7-192">İlişkiler üzerinde sorgulama yönerge gösterir nasıl [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tablolarda, benzer şekilde sorgulayabilirsiniz *birleştirmeler* ilişkisel bir veritabanındaki.</span><span class="sxs-lookup"><span data-stu-id="a54b7-192">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>  
  
 <span data-ttu-id="a54b7-193">İlişkiler üzerinde sorgulama Kılavuzu uygulamak istiyorsanız, önkoşul olan çözüm geçirmesini tamamladınız, gözden geçirme için kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a54b7-193">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a54b7-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a54b7-194">See also</span></span>

- [<span data-ttu-id="a54b7-195">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="a54b7-195">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
