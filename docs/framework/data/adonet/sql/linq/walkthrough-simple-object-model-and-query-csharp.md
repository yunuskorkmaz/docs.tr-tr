---
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)'
description: Örnek veritabanında bir tabloyu modelleyen bir varlık sınıfı oluşturmak için bu yönergeyi izleyin. Ardından belirli bir konumdaki müşterileri listelemek için basit bir sorgu oluşturun.
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: 4637fabecc1726d8fec12857a667073912cfbed5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286307"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="32040-104">İzlenecek yol: Basit Nesne Modeli ve Sorgu (C#)</span><span class="sxs-lookup"><span data-stu-id="32040-104">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="32040-105">Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en az karmaşıklıklarla temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="32040-105">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="32040-106">Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="32040-106">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="32040-107">Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="32040-107">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="32040-108">Bu izlenecek yol, kavramları göstermeye yardımcı olmak için tasarıma göre kod odaklı bir yönergedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="32040-108">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="32040-109">Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="32040-109">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="32040-110">Bu izlenecek yol, Visual C# geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="32040-110">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="32040-111">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="32040-111">Prerequisites</span></span>

- <span data-ttu-id="32040-112">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest5") kullanır.</span><span class="sxs-lookup"><span data-stu-id="32040-112">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="32040-113">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="32040-113">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="32040-114">Bu izlenecek yol, Northwind örnek veritabanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="32040-114">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="32040-115">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-115">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="32040-116">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="32040-116">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="32040-117">Veritabanını indirdikten sonra, dosyayı c:\linqtest5 klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="32040-117">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="32040-118">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="32040-118">Overview</span></span>

<span data-ttu-id="32040-119">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="32040-119">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="32040-120">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="32040-120">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="32040-121">Bir sınıfı bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="32040-121">Mapping a class to a database table.</span></span>

- <span data-ttu-id="32040-122">Veritabanı sütunlarını temsil etmek için sınıfında Özellikler belirleme.</span><span class="sxs-lookup"><span data-stu-id="32040-122">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="32040-123">Northwind veritabanı bağlantısı belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="32040-123">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="32040-124">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="32040-124">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="32040-125">Sorgu Yürütülüyor ve sonuçları gözlemleme.</span><span class="sxs-lookup"><span data-stu-id="32040-125">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="32040-126">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="32040-126">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="32040-127">Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="32040-127">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="32040-128">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32040-128">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="32040-129">Visual Studio **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-129">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="32040-130">**Yeni proje** Iletişim kutusunun **Proje türleri** bölmesinde, **Visual C#**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-130">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="32040-131">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-131">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="32040-132">**Ad** kutusuna **LinqConsoleApp**yazın.</span><span class="sxs-lookup"><span data-stu-id="32040-132">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="32040-133">**Konum** kutusunda, proje dosyalarınızı nerede depolamak istediğinizi doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="32040-133">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="32040-134">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-134">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="32040-135">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="32040-135">Adding LINQ References and Directives</span></span>

<span data-ttu-id="32040-136">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="32040-136">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="32040-137">System. Data. LINQ, projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="32040-137">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="32040-138">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="32040-138">To add System.Data.Linq</span></span>

1. <span data-ttu-id="32040-139">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-139">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="32040-140">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="32040-140">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="32040-141">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="32040-141">The assembly is added to the project.</span></span>

3. <span data-ttu-id="32040-142">Aşağıdaki yönergeleri **program.cs**üst kısmına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="32040-142">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="32040-143">Bir sınıfı bir veritabanı tablosuna eşleme</span><span class="sxs-lookup"><span data-stu-id="32040-143">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="32040-144">Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="32040-144">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="32040-145">Böyle bir sınıf bir *varlık sınıfı*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="32040-145">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="32040-146">Eşlemenin yalnızca özniteliği eklenerek gerçekleştirildiğine unutmayın <xref:System.Data.Linq.Mapping.TableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="32040-146">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="32040-147"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Özelliği, veritabanında tablonun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="32040-147">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="32040-148">Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="32040-148">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="32040-149">Aşağıdaki kodu, sınıf bildiriminin hemen üstüne Program.cs içine yazın veya yapıştırın `Program` :</span><span class="sxs-lookup"><span data-stu-id="32040-149">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="32040-150">Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme</span><span class="sxs-lookup"><span data-stu-id="32040-150">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="32040-151">Bu adımda, birkaç görevi gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-151">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="32040-152"><xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği, `CustomerID` `City` veritabanı tablosundaki sütunları temsil eden varlık sınıfını belirlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="32040-152">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="32040-153">`CustomerID`Özelliği, veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-153">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="32040-154">`_CustomerID` `_City` Özel depolama alanı için ve alanlarını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-154">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="32040-155">daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.</span><span class="sxs-lookup"><span data-stu-id="32040-155">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="32040-156">İki veritabanı sütununun özelliklerini temsil etmek için</span><span class="sxs-lookup"><span data-stu-id="32040-156">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="32040-157">Aşağıdaki kodu, sınıfının küme ayraçları içine yazın veya Program.cs içine yapıştırın `Customer` .</span><span class="sxs-lookup"><span data-stu-id="32040-157">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="32040-158">Northwind veritabanı bağlantısını belirtme</span><span class="sxs-lookup"><span data-stu-id="32040-158">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="32040-159">Bu adımda, <xref:System.Data.Linq.DataContext> kod tabanlı veri yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="32040-159">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="32040-160">, <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.</span><span class="sxs-lookup"><span data-stu-id="32040-160">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="32040-161">Ayrıca `Table<Customer>` , veritabanınızdaki Müşteriler tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir.</span><span class="sxs-lookup"><span data-stu-id="32040-161">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="32040-162">Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-162">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="32040-163">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="32040-163">To specify the database connection</span></span>

- <span data-ttu-id="32040-164">Yöntemine aşağıdaki kodu yazın veya yapıştırın `Main` .</span><span class="sxs-lookup"><span data-stu-id="32040-164">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="32040-165">`northwnd.mdf`Dosyanın linqtest5 klasöründe olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="32040-165">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="32040-166">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32040-166">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="32040-167">Basit sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="32040-167">Creating a Simple Query</span></span>

<span data-ttu-id="32040-168">Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="32040-168">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="32040-169">Bu adımdaki sorgu kodu yalnızca sorguyu açıklar.</span><span class="sxs-lookup"><span data-stu-id="32040-169">The query code in this step just describes the query.</span></span> <span data-ttu-id="32040-170">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="32040-170">It does not execute it.</span></span> <span data-ttu-id="32040-171">Bu yaklaşım *ertelenmiş yürütme*olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="32040-171">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="32040-172">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="32040-172">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="32040-173">Ayrıca, üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="32040-173">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="32040-174">Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A> ) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="32040-174">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="32040-175">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="32040-175">To create a simple query</span></span>

- <span data-ttu-id="32040-176">Aşağıdaki kodu, `Main` bildiriminden sonraki yönteme yazın veya yapıştırın `Table<Customer>` .</span><span class="sxs-lookup"><span data-stu-id="32040-176">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="32040-177">Sorgu Yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="32040-177">Executing the Query</span></span>

<span data-ttu-id="32040-178">Bu adımda, aslında sorguyu yürütütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="32040-178">In this step, you actually execute the query.</span></span> <span data-ttu-id="32040-179">Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="32040-179">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="32040-180">`foreach`Yinelemeye başladığınızda, veritabanına karşı BIR SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="32040-180">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="32040-181">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="32040-181">To execute the query</span></span>

1. <span data-ttu-id="32040-182">`Main`Yönteminin sonuna (sorgu açıkladıktan sonra) aşağıdaki kodu yazın veya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="32040-182">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="32040-183">Uygulamada hata ayıklamak için F5’e basın.</span><span class="sxs-lookup"><span data-stu-id="32040-183">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="32040-184">Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="32040-184">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="32040-185">Konsol penceresinde sorgu sonuçları aşağıdaki gibi görünmelidir:</span><span class="sxs-lookup"><span data-stu-id="32040-185">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="32040-186">Uygulamayı kapatmak için konsol penceresinde ENTER tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="32040-186">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="32040-187">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="32040-187">Next Steps</span></span>

<span data-ttu-id="32040-188">[Izlenecek yol: Ilişkiler genelinde sorgulama (C#)](walkthrough-querying-across-relationships-csharp.md) konusu Bu izlenecek yolun sona erdiği yerde devam eder.</span><span class="sxs-lookup"><span data-stu-id="32040-188">The [Walkthrough: Querying Across Relationships (C#)](walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="32040-189">Ilişkiler Kılavuzu 'ndaki sorgu, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilişkisel bir veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="32040-189">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="32040-190">Sorgu Ilişkileri genelinde sorgu yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız izlenecek yol için çözümü kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="32040-190">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="32040-191">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32040-191">See also</span></span>

- [<span data-ttu-id="32040-192">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="32040-192">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
