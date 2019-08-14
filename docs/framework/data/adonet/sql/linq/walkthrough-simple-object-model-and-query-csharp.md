---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)'
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 43092eb7490d5629f1ababac1d8f8b3aff94299b
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971862"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="c1dca-102">İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)</span><span class="sxs-lookup"><span data-stu-id="c1dca-102">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="c1dca-103">Bu izlenecek yol, en az karmaşıklıklarla temel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1dca-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="c1dca-104">Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c1dca-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="c1dca-105">Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c1dca-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="c1dca-106">Bu izlenecek yol, kavramları göstermeye [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yardımcı olmak için tasarıma göre kod odaklı bir yönergedir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="c1dca-107">Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="c1dca-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="c1dca-108">Bu izlenecek yol, Visual C# Development ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-108">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c1dca-109">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="c1dca-109">Prerequisites</span></span>

- <span data-ttu-id="c1dca-110">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest5") kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="c1dca-111">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="c1dca-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="c1dca-112">Bu izlenecek yol, Northwind örnek veritabanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="c1dca-113">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="c1dca-114">Yönergeler için bkz. [örnek veritabanlarını indirme](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="c1dca-114">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="c1dca-115">Veritabanını indirdikten sonra, dosyayı c:\linqtest5 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="c1dca-116">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1dca-116">Overview</span></span>

<span data-ttu-id="c1dca-117">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="c1dca-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="c1dca-118">Visual Studio 'da çözüm oluşturma. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1dca-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="c1dca-119">Bir sınıfı bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="c1dca-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="c1dca-120">Veritabanı sütunlarını temsil etmek için sınıfında Özellikler belirleme.</span><span class="sxs-lookup"><span data-stu-id="c1dca-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="c1dca-121">Northwind veritabanı bağlantısı belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="c1dca-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="c1dca-122">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="c1dca-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="c1dca-123">Sorgu Yürütülüyor ve sonuçları gözlemleme.</span><span class="sxs-lookup"><span data-stu-id="c1dca-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="c1dca-124">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1dca-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="c1dca-125">Bu ilk görevde, bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="c1dca-126">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1dca-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="c1dca-127">Visual Studio **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="c1dca-128">**Yeni proje** Iletişim kutusunun **Proje türleri** bölmesinde, **C#görsel**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="c1dca-129">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="c1dca-130">**Ad** kutusuna **LinqConsoleApp**yazın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="c1dca-131">**Konum** kutusunda, proje dosyalarınızı nerede depolamak istediğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-131">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="c1dca-132">          **Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="c1dca-133">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="c1dca-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="c1dca-134">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="c1dca-135">System. Data. LINQ, projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dca-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="c1dca-136">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="c1dca-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="c1dca-137">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="c1dca-138">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="c1dca-139">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="c1dca-140">Aşağıdaki yönergeleri **program.cs**üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c1dca-140">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="c1dca-141">Bir sınıfı bir veritabanı tablosuna eşleme</span><span class="sxs-lookup"><span data-stu-id="c1dca-141">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="c1dca-142">Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="c1dca-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="c1dca-143">Böyle bir sınıf bir *varlık sınıfı*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="c1dca-144">Eşlemenin yalnızca <xref:System.Data.Linq.Mapping.TableAttribute> özniteliği eklenerek gerçekleştirildiğine unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="c1dca-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> Özelliği, veritabanında tablonun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="c1dca-146">Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="c1dca-146">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="c1dca-147">Aşağıdaki kodu, `Program` sınıf bildiriminin hemen üstüne program.cs içine yazın veya yapıştırın:</span><span class="sxs-lookup"><span data-stu-id="c1dca-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="c1dca-148">Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme</span><span class="sxs-lookup"><span data-stu-id="c1dca-148">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="c1dca-149">Bu adımda, birkaç görevi gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-149">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="c1dca-150"><xref:System.Data.Linq.Mapping.ColumnAttribute> Özniteliği, veritabanı tablosundaki sütunları temsil eden `City` varlık sınıfını belirlemek `CustomerID` için kullanın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="c1dca-151">Özelliği, `CustomerID` veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="c1dca-152">Özel depolama `_CustomerID` alanı `_City` için ve alanlarını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="c1dca-153">daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-153">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="c1dca-154">İki veritabanı sütununun özelliklerini temsil etmek için</span><span class="sxs-lookup"><span data-stu-id="c1dca-154">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="c1dca-155">Aşağıdaki kodu, `Customer` sınıfının küme ayraçları içine yazın veya program.cs içine yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="c1dca-156">Northwind veritabanı bağlantısını belirtme</span><span class="sxs-lookup"><span data-stu-id="c1dca-156">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="c1dca-157">Bu adımda, kod tabanlı veri <xref:System.Data.Linq.DataContext> yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="c1dca-158">, <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="c1dca-159">Ayrıca, veritabanınızdaki müşteriler `Table<Customer>` tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="c1dca-160">Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-160">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="c1dca-161">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="c1dca-161">To specify the database connection</span></span>

- <span data-ttu-id="c1dca-162">`Main` Yöntemine aşağıdaki kodu yazın veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-162">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="c1dca-163">`northwnd.mdf` Dosyanın linqtest5 klasöründe olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="c1dca-164">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="c1dca-165">Basit sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1dca-165">Creating a Simple Query</span></span>

<span data-ttu-id="c1dca-166">Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="c1dca-167">Bu adımdaki sorgu kodu yalnızca sorguyu açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1dca-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="c1dca-168">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="c1dca-168">It does not execute it.</span></span> <span data-ttu-id="c1dca-169">Bu yaklaşım *ertelenmiş yürütme*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="c1dca-170">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="c1dca-170">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="c1dca-171">Ayrıca, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c1dca-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="c1dca-172">Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A>) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="c1dca-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="c1dca-173">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="c1dca-173">To create a simple query</span></span>

- <span data-ttu-id="c1dca-174">Aşağıdaki kodu `Main` , `Table<Customer>` bildiriminden sonraki yönteme yazın veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="c1dca-175">Sorgu Yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="c1dca-175">Executing the Query</span></span>

<span data-ttu-id="c1dca-176">Bu adımda, aslında sorguyu yürütütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="c1dca-177">Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="c1dca-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="c1dca-178">`foreach` Yinelemeye başladığınızda, veritabanına karşı bir SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="c1dca-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="c1dca-179">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="c1dca-179">To execute the query</span></span>

1. <span data-ttu-id="c1dca-180">`Main` Yönteminin sonuna (sorgu açıkladıktan sonra) aşağıdaki kodu yazın veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="c1dca-181">Uygulamada hata ayıklamak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-181">Press F5 to debug the application.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="c1dca-182">Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="c1dca-183">Konsol penceresinde sorgu sonuçları aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="c1dca-183">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="c1dca-184">Uygulamayı kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="c1dca-184">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c1dca-185">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="c1dca-185">Next Steps</span></span>

<span data-ttu-id="c1dca-186">[İzlenecek yol: İlişkiler genelinde sorgulama (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) konusu Bu izlenecek yolun sona erdiği yerde devam eder.</span><span class="sxs-lookup"><span data-stu-id="c1dca-186">The [Walkthrough: Querying Across Relationships (C#)](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="c1dca-187">İlişkiler Kılavuzu 'ndaki sorgu, ilişkisel bir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1dca-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="c1dca-188">Sorgu Ilişkileri genelinde sorgu yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız izlenecek yol için çözümü kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="c1dca-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1dca-189">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1dca-189">See also</span></span>

- [<span data-ttu-id="c1dca-190">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="c1dca-190">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
