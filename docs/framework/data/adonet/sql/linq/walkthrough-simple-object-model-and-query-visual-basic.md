---
description: 'Daha fazla bilgi edinin: Izlenecek yol: basit nesne modeli ve sorgu (Visual Basic)'
title: 'İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: c878e457-f715-46e4-a136-ff14d6c86018
ms.openlocfilehash: def2fecf0d6d97841ebd47a1d675f85341053d39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791809"
---
# <a name="walkthrough-simple-object-model-and-query-visual-basic"></a><span data-ttu-id="4cf60-103">İzlenecek yol: Basit Nesne Modeli ve Sorgu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4cf60-103">Walkthrough: Simple Object Model and Query (Visual Basic)</span></span>

<span data-ttu-id="4cf60-104">Bu izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] en az karmaşıklıklarla temel uçtan uca bir senaryo sağlar.</span><span class="sxs-lookup"><span data-stu-id="4cf60-104">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="4cf60-105">Örnek Northwind veritabanındaki Customers tablosunu modelleyen bir varlık sınıfı oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4cf60-105">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="4cf60-106">Ardından, Londra 'da bulunan müşterileri listelemek için basit bir sorgu oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="4cf60-106">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="4cf60-107">Bu izlenecek yol, kavramları göstermeye yardımcı olmak için tasarıma göre kod odaklı bir yönergedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4cf60-107">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="4cf60-108">Normalde konuşarak, nesne modelinizi oluşturmak için Nesne İlişkisel Tasarımcısı kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4cf60-108">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="4cf60-109">Bu izlenecek yol Visual Basic geliştirme ayarları kullanılarak yazılmıştır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-109">This walkthrough was written by using Visual Basic Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cf60-110">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="4cf60-110">Prerequisites</span></span>

- <span data-ttu-id="4cf60-111">Bu izlenecek yol, dosyaları tutmak için adanmış bir klasör ("c:\linqtest") kullanır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-111">This walkthrough uses a dedicated folder ("c:\linqtest") to hold files.</span></span> <span data-ttu-id="4cf60-112">Yönergeye başlamadan önce bu klasörü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4cf60-112">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="4cf60-113">Bu izlenecek yol, Northwind örnek veritabanı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-113">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="4cf60-114">Geliştirme bilgisayarınızda bu veritabanı yoksa, Microsoft Download sitesinden indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-114">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="4cf60-115">Yönergeler için bkz. [örnek veritabanlarını indirme](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="4cf60-115">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="4cf60-116">Veritabanını indirdikten sonra, dosyayı c:\linqtest klasörüne kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-116">After you have downloaded the database, copy the file to the c:\linqtest folder.</span></span>

## <a name="overview"></a><span data-ttu-id="4cf60-117">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4cf60-117">Overview</span></span>

<span data-ttu-id="4cf60-118">Bu izlenecek yol altı ana görevden oluşur:</span><span class="sxs-lookup"><span data-stu-id="4cf60-118">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="4cf60-119">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Visual Studio 'da çözüm oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4cf60-119">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="4cf60-120">Bir sınıfı bir veritabanı tablosuna eşleme.</span><span class="sxs-lookup"><span data-stu-id="4cf60-120">Mapping a class to a database table.</span></span>

- <span data-ttu-id="4cf60-121">Veritabanı sütunlarını temsil etmek için sınıfında Özellikler belirleme.</span><span class="sxs-lookup"><span data-stu-id="4cf60-121">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="4cf60-122">Northwind veritabanı bağlantısı belirtiliyor.</span><span class="sxs-lookup"><span data-stu-id="4cf60-122">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="4cf60-123">Veritabanına karşı çalıştırmak için basit bir sorgu oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4cf60-123">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="4cf60-124">Sorgu Yürütülüyor ve sonuçları gözlemleme.</span><span class="sxs-lookup"><span data-stu-id="4cf60-124">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="4cf60-125">LINQ to SQL çözümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="4cf60-125">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="4cf60-126">Bu ilk görevde, bir proje derlemek ve çalıştırmak için gerekli başvuruları içeren bir Visual Studio çözümü oluşturursunuz [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4cf60-126">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="4cf60-127">LINQ to SQL çözümü oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4cf60-127">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="4cf60-128">**Dosya** menüsünde **Yeni proje**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-128">On the **File** menu, click **New Project**.</span></span>

2. <span data-ttu-id="4cf60-129">**Yeni proje** Iletişim kutusunun **proje türleri** bölmesinde **Visual Basic**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-129">In the **Project types** pane of the **New Project** dialog box, click **Visual Basic**.</span></span>

3. <span data-ttu-id="4cf60-130">**Şablonlar** bölmesinde **konsol uygulaması**' na tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-130">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="4cf60-131">**Ad** kutusuna **LinqConsoleApp** yazın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-131">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="4cf60-132">**Tamam**'a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="4cf60-133">LINQ başvuruları ve yönergeleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4cf60-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="4cf60-134">Bu izlenecek yol, projenize varsayılan olarak yüklenmemiş olabilecek derlemeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="4cf60-135">`System.Data.Linq`Projenizde bir başvuru olarak listelenmiyorsa ( **Çözüm Gezgini** **tüm dosyaları göster** ' e tıklayın ve **Başvurular** düğümünü genişletin), aşağıdaki adımlarda açıklandığı gibi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4cf60-135">If `System.Data.Linq` is not listed as a reference in your project (click **Show All Files** in **Solution Explorer** and expand the **References** node), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="4cf60-136">System. Data. LINQ eklemek için</span><span class="sxs-lookup"><span data-stu-id="4cf60-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="4cf60-137">**Çözüm Gezgini**' de, **Başvurular**' a sağ tıklayın ve ardından **Başvuru Ekle**' ye tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="4cf60-138">**Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, System. Data. LINQ derlemesine tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="4cf60-139">Derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="4cf60-140">Ayrıca, **Başvuru Ekle** iletişim kutusunda, **.net**' e tıklayın, öğesine gidin ve System. Windows. Forms ' a tıklayın ve ardından **Tamam**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-140">Also in the **Add Reference** dialog box, click **.NET**, scroll to and click System.Windows.Forms, and then click **OK**.</span></span>

     <span data-ttu-id="4cf60-141">Yönergedeki ileti kutusunu destekleyen bu derleme projeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-141">This assembly, which supports the message box in the walkthrough, is added to the project.</span></span>

4. <span data-ttu-id="4cf60-142">Aşağıdaki yönergeleri yukarıya ekleyin `Module1` :</span><span class="sxs-lookup"><span data-stu-id="4cf60-142">Add the following directives above `Module1`:</span></span>

     [!code-vb[DLinqWalk1VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="4cf60-143">Bir sınıfı bir veritabanı tablosuna eşleme</span><span class="sxs-lookup"><span data-stu-id="4cf60-143">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="4cf60-144">Bu adımda, bir sınıf oluşturur ve bunu bir veritabanı tablosuyla eşleyin.</span><span class="sxs-lookup"><span data-stu-id="4cf60-144">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="4cf60-145">Böyle bir sınıf bir *varlık sınıfı* olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-145">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="4cf60-146">Eşlemenin yalnızca özniteliği eklenerek gerçekleştirildiğine unutmayın <xref:System.Data.Linq.Mapping.TableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="4cf60-146">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="4cf60-147"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A>Özelliği, veritabanında tablonun adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-147">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="4cf60-148">Bir varlık sınıfı oluşturmak ve veritabanını bir veritabanı tablosuyla eşlemek için</span><span class="sxs-lookup"><span data-stu-id="4cf60-148">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="4cf60-149">Aşağıdaki kodu yazın veya hemen üstüne Module1. vb öğesine yapıştırın `Sub Main` :</span><span class="sxs-lookup"><span data-stu-id="4cf60-149">Type or paste the following code into Module1.vb immediately above `Sub Main`:</span></span>

     [!code-vb[DLinqWalk1VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="4cf60-150">Sınıf üzerinde veritabanı sütunlarını temsil etmek için özellikler belirleme</span><span class="sxs-lookup"><span data-stu-id="4cf60-150">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="4cf60-151">Bu adımda, birkaç görevi gerçekleştirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-151">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="4cf60-152"><xref:System.Data.Linq.Mapping.ColumnAttribute>Özniteliği, `CustomerID` `City` veritabanı tablosundaki sütunları temsil eden varlık sınıfını belirlemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-152">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="4cf60-153">`CustomerID`Özelliği, veritabanında bir birincil anahtar sütununu temsil edecek şekilde belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-153">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="4cf60-154">`_CustomerID` `_City` Özel depolama alanı için ve alanlarını belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-154">You designate `_CustomerID` and `_City` fields for private storage.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="4cf60-155">daha sonra, iş mantığını içerebilen ortak erişimcileri kullanmak yerine doğrudan değerleri saklayabilir ve alabilir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-155">can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="4cf60-156">İki veritabanı sütununun özelliklerini temsil etmek için</span><span class="sxs-lookup"><span data-stu-id="4cf60-156">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="4cf60-157">Aşağıdaki kodu bir daha önce Module1. vb öğesine yazın veya yapıştırın `End Class` :</span><span class="sxs-lookup"><span data-stu-id="4cf60-157">Type or paste the following code into Module1.vb just before `End Class`:</span></span>

     [!code-vb[DLinqWalk1VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="4cf60-158">Northwind veritabanı bağlantısını belirtme</span><span class="sxs-lookup"><span data-stu-id="4cf60-158">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="4cf60-159">Bu adımda, <xref:System.Data.Linq.DataContext> kod tabanlı veri yapılarınız ve veritabanının kendisi arasında bağlantı kurmak için bir nesnesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-159">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="4cf60-160">, <xref:System.Data.Linq.DataContext> Veritabanından nesneleri alıp değişiklikleri gönderdiğiniz ana kanaldır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-160">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="4cf60-161">Ayrıca `Table(Of Customer)` , veritabanınızdaki Müşteriler tablosuna karşı sorgularınız için mantıksal, türü belirlenmiş tablo olarak davranacak bir de bildirir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-161">You also declare a `Table(Of Customer)` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="4cf60-162">Daha sonraki adımlarda bu sorguları oluşturup yürüteceksiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-162">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="4cf60-163">Veritabanı bağlantısını belirtmek için</span><span class="sxs-lookup"><span data-stu-id="4cf60-163">To specify the database connection</span></span>

- <span data-ttu-id="4cf60-164">Yöntemine aşağıdaki kodu yazın veya yapıştırın `Sub Main` .</span><span class="sxs-lookup"><span data-stu-id="4cf60-164">Type or paste the following code into the `Sub Main` method.</span></span>

     <span data-ttu-id="4cf60-165">`northwnd.mdf`Dosyanın linqtest klasöründe olduğunu varsaydığına emin olun.</span><span class="sxs-lookup"><span data-stu-id="4cf60-165">Note that the `northwnd.mdf` file is assumed to be in the linqtest folder.</span></span> <span data-ttu-id="4cf60-166">Daha fazla bilgi için bu kılavuzda daha önce bahsedilen Önkoşullar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-166">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-vb[DLinqWalk1VB#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1VB/vb/Module1.vb#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="4cf60-167">Basit sorgu oluşturma</span><span class="sxs-lookup"><span data-stu-id="4cf60-167">Creating a Simple Query</span></span>

<span data-ttu-id="4cf60-168">Bu adımda, veritabanı müşterileri tablosundaki hangi müşterilerin Londra 'da bulunacağını bulmak için bir sorgu oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-168">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="4cf60-169">Bu adımdaki sorgu kodu yalnızca sorguyu açıklar.</span><span class="sxs-lookup"><span data-stu-id="4cf60-169">The query code in this step just describes the query.</span></span> <span data-ttu-id="4cf60-170">Bunu yürütmez.</span><span class="sxs-lookup"><span data-stu-id="4cf60-170">It does not execute it.</span></span> <span data-ttu-id="4cf60-171">Bu yaklaşım *ertelenmiş yürütme* olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-171">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="4cf60-172">Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="4cf60-172">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="4cf60-173">Ayrıca, üreten SQL komutlarını göstermek için bir günlük çıktısı oluşturacaksınız [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4cf60-173">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="4cf60-174">Bu günlüğe kaydetme özelliğinin (kullandığı <xref:System.Data.Linq.DataContext.Log%2A> ) hata ayıklama işlemi sırasında ve veritabanına gönderilen komutların sorgunuzu doğru şekilde temsil ettiğini belirlemek için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-174">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="4cf60-175">Basit bir sorgu oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="4cf60-175">To create a simple query</span></span>

- <span data-ttu-id="4cf60-176">Aşağıdaki kodu, `Sub Main` bildiriminden sonra yöntemine yazın veya yapıştırın `Table(Of Customer)` :</span><span class="sxs-lookup"><span data-stu-id="4cf60-176">Type or paste the following code into the `Sub Main` method after the `Table(Of Customer)` declaration:</span></span>

     [!code-vb[DLinqWalk1AVB#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#5)]

## <a name="executing-the-query"></a><span data-ttu-id="4cf60-177">Sorgu Yürütülüyor</span><span class="sxs-lookup"><span data-stu-id="4cf60-177">Executing the Query</span></span>

<span data-ttu-id="4cf60-178">Bu adımda, aslında sorguyu yürütütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-178">In this step, you actually execute the query.</span></span> <span data-ttu-id="4cf60-179">Önceki adımlarda oluşturduğunuz sorgu ifadeleri, sonuçlar gerekene kadar değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="4cf60-179">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="4cf60-180">`For Each`Yinelemeye başladığınızda, veritabanına karşı BIR SQL komutu yürütülür ve nesneler gerçekleştirilmiş olur.</span><span class="sxs-lookup"><span data-stu-id="4cf60-180">When you begin the `For Each` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="4cf60-181">Sorguyu yürütmek için</span><span class="sxs-lookup"><span data-stu-id="4cf60-181">To execute the query</span></span>

1. <span data-ttu-id="4cf60-182">Yönteminin sonuna aşağıdaki kodu yazın veya yapıştırın `Sub Main` (sorgu açıkladıktan sonra):</span><span class="sxs-lookup"><span data-stu-id="4cf60-182">Type or paste the following code at the end of the `Sub Main` method (after the query description):</span></span>

     [!code-vb[DLinqWalk1AVB#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk1AVB/vb/Module1.vb#6)]

2. <span data-ttu-id="4cf60-183">Uygulamada hata ayıklamak için F5’e basın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-183">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4cf60-184">Uygulamanız bir çalışma zamanı hatası oluşturursa, [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md)konusunun sorun giderme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-184">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="4cf60-185">İleti kutusu, altı müşterinin bir listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4cf60-185">The message box displays a list of six customers.</span></span> <span data-ttu-id="4cf60-186">Konsol penceresinde oluşturulan SQL kodu görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-186">The Console window displays the generated SQL code.</span></span>

3. <span data-ttu-id="4cf60-187">İleti kutusunu kapatmak için **Tamam** ' ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-187">Click **OK** to dismiss the message box.</span></span>

     <span data-ttu-id="4cf60-188">Uygulama kapanır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-188">The application closes.</span></span>

4. <span data-ttu-id="4cf60-189">**Dosya** menüsünde **Tümünü Kaydet**’e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="4cf60-189">On the **File** menu, click **Save All**.</span></span>

     <span data-ttu-id="4cf60-190">Sonraki yönergeye devam ederseniz bu uygulamaya ihtiyacınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="4cf60-190">You will need this application if you continue with the next walkthrough.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cf60-191">Sonraki Adımlar</span><span class="sxs-lookup"><span data-stu-id="4cf60-191">Next Steps</span></span>

<span data-ttu-id="4cf60-192">[Izlenecek yol: Ilişkiler genelinde sorgulama (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) konusu Bu izlenecek yolun bittiğini sürdürür.</span><span class="sxs-lookup"><span data-stu-id="4cf60-192">The [Walkthrough: Querying Across Relationships (Visual Basic)](walkthrough-querying-across-relationships-visual-basic.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="4cf60-193">Ilişkiler genelinde sorgulama izlenecek yol, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ilişkisel bir veritabanındaki *birleştirmelere* benzer şekilde tablolar arasında nasıl sorgu yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cf60-193">The Querying Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="4cf60-194">Ilişkiler genelinde sorgulama yapmak istiyorsanız, bir önkoşul olan, az önce tamamladığınız yönergeler için çözümü kaydettiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="4cf60-194">If you want to do the Querying Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cf60-195">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4cf60-195">See also</span></span>

- [<span data-ttu-id="4cf60-196">İzlenecek Yollarla Öğrenme</span><span class="sxs-lookup"><span data-stu-id="4cf60-196">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
