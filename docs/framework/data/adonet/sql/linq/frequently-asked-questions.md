---
title: Sıkça Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634709"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="1a82c-102">Sıkça Sorulan Sorular</span><span class="sxs-lookup"><span data-stu-id="1a82c-102">Frequently Asked Questions</span></span>

<span data-ttu-id="1a82c-103">Aşağıdaki bölümlerde, LINQ uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıtlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-103">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="1a82c-104">[Sorun gidermede](troubleshooting.md)ek sorunlar ele alınır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="1a82c-105">Bağlanamıyor</span><span class="sxs-lookup"><span data-stu-id="1a82c-105">Cannot Connect</span></span>

<span data-ttu-id="1a82c-106">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-106">Q.</span></span> <span data-ttu-id="1a82c-107">Veritabanıma bağlanamıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a82c-107">I cannot connect to my database.</span></span>

<span data-ttu-id="1a82c-108">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-108">A.</span></span> <span data-ttu-id="1a82c-109">Bağlantı dizeniz doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="1a82c-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="1a82c-110">Ayrıca, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanallar protokolünün etkinleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="1a82c-111">Daha fazla bilgi için bkz. [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="1a82c-112">Veritabanında yapılan değişiklikler kayboldu</span><span class="sxs-lookup"><span data-stu-id="1a82c-112">Changes to Database Lost</span></span>

<span data-ttu-id="1a82c-113">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-113">Q.</span></span> <span data-ttu-id="1a82c-114">Veritabanında verilerde bir değişiklik yaptık, ancak uygulamamı yeniden kaydederken değişiklik artık orada yoktu.</span><span class="sxs-lookup"><span data-stu-id="1a82c-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="1a82c-115">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-115">A.</span></span> <span data-ttu-id="1a82c-116">Sonuçları veritabanına kaydetmek için <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="1a82c-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="1a82c-117">Veritabanı bağlantısı: ne kadar süreyle açık?</span><span class="sxs-lookup"><span data-stu-id="1a82c-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="1a82c-118">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-118">Q.</span></span> <span data-ttu-id="1a82c-119">Veritabanı bağlantısı ne kadar süreyle açık kalır?</span><span class="sxs-lookup"><span data-stu-id="1a82c-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="1a82c-120">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-120">A.</span></span> <span data-ttu-id="1a82c-121">Sorgu sonuçlarını tüketene kadar bağlantı genellikle açık kalır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="1a82c-122">Tüm sonuçları işlemek için zaman almayı beklemeniz ve sonuçların önbelleğe alınmasına izin vermek istiyorsanız sorguya <xref:System.Linq.Enumerable.ToList%2A> uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1a82c-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="1a82c-123">Her nesnenin yalnızca bir kez işlendiği yaygın senaryolarda, akış modeli hem `DataReader` hem de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]üst düzeydir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="1a82c-124">Bağlantı kullanımının tam ayrıntıları aşağıdakilere bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="1a82c-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="1a82c-125"><xref:System.Data.Linq.DataContext> bağlantı nesnesi ile oluşturulursa bağlantı durumu.</span><span class="sxs-lookup"><span data-stu-id="1a82c-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="1a82c-126">Bağlantı dizesi ayarları (örneğin, birden çok etkin sonuç kümesi (MARS) etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="1a82c-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="1a82c-127">Daha fazla bilgi için bkz. [birden çok etkin sonuç kümesi (mars)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="1a82c-128">Sorgulanmadan güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="1a82c-128">Updating Without Querying</span></span>

<span data-ttu-id="1a82c-129">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-129">Q.</span></span> <span data-ttu-id="1a82c-130">Veritabanını sorgulamadan tablo verilerini güncelleştirebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="1a82c-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="1a82c-131">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-131">A.</span></span> <span data-ttu-id="1a82c-132">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ayarlanan tabanlı güncelleştirme komutlarına sahip olmasa da, öncelikle güncelleştirme yapmak için aşağıdaki tekniklerden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a82c-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="1a82c-133">SQL kodu göndermek için <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a82c-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="1a82c-134">Nesnenin yeni bir örneğini oluşturun ve güncelleştirmeyi etkileyen tüm geçerli değerleri (alanlar) başlatın.</span><span class="sxs-lookup"><span data-stu-id="1a82c-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="1a82c-135">Sonra, <xref:System.Data.Linq.Table%601.Attach%2A> kullanarak nesneyi <xref:System.Data.Linq.DataContext> ekleyin ve değiştirmek istediğiniz alanı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1a82c-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="1a82c-136">Beklenmeyen sorgu sonuçları</span><span class="sxs-lookup"><span data-stu-id="1a82c-136">Unexpected Query Results</span></span>

<span data-ttu-id="1a82c-137">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-137">Q.</span></span> <span data-ttu-id="1a82c-138">Sorgum beklenmeyen sonuçlar döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="1a82c-138">My query is returning unexpected results.</span></span> <span data-ttu-id="1a82c-139">Ne olduğunu nasıl giderebilirim?</span><span class="sxs-lookup"><span data-stu-id="1a82c-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="1a82c-140">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a82c-141">, oluşturduğu SQL kodunu incelemek için çeşitli araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a82c-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="1a82c-142">En önemlileri bunlardan biri <xref:System.Data.Linq.DataContext.Log%2A>.</span><span class="sxs-lookup"><span data-stu-id="1a82c-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="1a82c-143">Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="1a82c-144">Beklenmeyen saklı yordam sonuçları</span><span class="sxs-lookup"><span data-stu-id="1a82c-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="1a82c-145">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-145">Q.</span></span> <span data-ttu-id="1a82c-146">Dönüş değeri `MAX()`tarafından hesaplanan bir saklı yordamım var.</span><span class="sxs-lookup"><span data-stu-id="1a82c-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="1a82c-147">Saklı yordamı O/R Designer yüzeyine sürükledikten sonra, dönüş değeri doğru değil.</span><span class="sxs-lookup"><span data-stu-id="1a82c-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="1a82c-148">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a82c-149">, saklı yordamlar yoluyla veritabanı tarafından oluşturulan değerleri döndürmek için iki yol sunar:</span><span class="sxs-lookup"><span data-stu-id="1a82c-149">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="1a82c-150">Çıkış sonucunu adlandırarak.</span><span class="sxs-lookup"><span data-stu-id="1a82c-150">By naming the output result.</span></span>

- <span data-ttu-id="1a82c-151">Açıkça bir çıkış parametresi belirterek.</span><span class="sxs-lookup"><span data-stu-id="1a82c-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="1a82c-152">Aşağıda yanlış çıktının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="1a82c-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonuçları eşlemediğinden, her zaman 0 değerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="1a82c-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="1a82c-154">Aşağıda, çıkış parametresi kullanarak doğru çıkışın bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1a82c-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="1a82c-155">Aşağıda, çıkış sonucunu adlandırarak doğru çıkışın bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1a82c-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="1a82c-156">Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="1a82c-157">Serileştirme hataları</span><span class="sxs-lookup"><span data-stu-id="1a82c-157">Serialization Errors</span></span>

<span data-ttu-id="1a82c-158">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-158">Q.</span></span> <span data-ttu-id="1a82c-159">Seri hale getirme yapmayı denediğimde şu hatayı alıyorum: "System. Data. LINQ. ChangeTracker + StandardChangeTracker ' yazın... seri hale getirilebilir olarak işaretlenmemiş. "</span><span class="sxs-lookup"><span data-stu-id="1a82c-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="1a82c-160">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-160">A.</span></span> <span data-ttu-id="1a82c-161">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod üretimi <xref:System.Runtime.Serialization.DataContractSerializer> Serileştirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="1a82c-162"><xref:System.Xml.Serialization.XmlSerializer> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1a82c-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="1a82c-163">Daha fazla bilgi için bkz. [serileştirme](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="1a82c-164">Birden çok DBML dosyası</span><span class="sxs-lookup"><span data-stu-id="1a82c-164">Multiple DBML Files</span></span>

<span data-ttu-id="1a82c-165">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-165">Q.</span></span> <span data-ttu-id="1a82c-166">Ortak olarak bazı tabloları paylaşan birden çok DBML dosyası olduğunda bir derleyici hatası alıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a82c-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="1a82c-167">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-167">A.</span></span> <span data-ttu-id="1a82c-168">**Bağlam ad alanını** ve **varlık ad alanı** özelliklerini nesne ilişkisel Tasarımcısı her dbml dosyası için ayrı bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1a82c-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="1a82c-169">Bu yaklaşım ad/ad alanı çarpışmasını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="1a82c-170">INSERT veya Update üzerinde veritabanı tarafından oluşturulan değerlerin açık ayarından kaçınma</span><span class="sxs-lookup"><span data-stu-id="1a82c-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="1a82c-171">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-171">Q.</span></span> <span data-ttu-id="1a82c-172">SQL `Getdate()`varsayılan olarak `DateCreated` sütunu olan bir veritabanı tablom var.</span><span class="sxs-lookup"><span data-stu-id="1a82c-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="1a82c-173">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanarak yeni bir kayıt eklemeye çalıştığımda, değer `NULL`olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="1a82c-174">Veritabanının varsayılan olarak ayarlanmış olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="1a82c-175">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1a82c-176">kimlik (otomatik artış) ve ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için bu durumu otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="1a82c-177">Diğer durumlarda, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/özelliklerini el ile ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="1a82c-178">Çoklu dataloadoçen</span><span class="sxs-lookup"><span data-stu-id="1a82c-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="1a82c-179">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-179">Q.</span></span> <span data-ttu-id="1a82c-180">İlk üzerine yazmadan ek yükleme seçenekleri belirtebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="1a82c-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="1a82c-181">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-181">A.</span></span> <span data-ttu-id="1a82c-182">Evet.</span><span class="sxs-lookup"><span data-stu-id="1a82c-182">Yes.</span></span> <span data-ttu-id="1a82c-183">Aşağıdaki örnekte olduğu gibi ilki üzerine yazılmaz:</span><span class="sxs-lookup"><span data-stu-id="1a82c-183">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="1a82c-184">SQL Compact 3,5 kullanarak hatalar</span><span class="sxs-lookup"><span data-stu-id="1a82c-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="1a82c-185">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-185">Q.</span></span> <span data-ttu-id="1a82c-186">SQL Server Compact 3,5 veritabanından tablo sürüklediğiniz zaman bir hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a82c-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="1a82c-187">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-187">A.</span></span> <span data-ttu-id="1a82c-188">Nesne İlişkisel Tasarımcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı olsa da SQL Server Compact 3,5 ' i desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1a82c-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="1a82c-189">Bu durumda, kendi varlık sınıflarınızı oluşturmanız ve uygun öznitelikleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="1a82c-190">Devralma Ilişkilerinde hatalar</span><span class="sxs-lookup"><span data-stu-id="1a82c-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="1a82c-191">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-191">Q.</span></span> <span data-ttu-id="1a82c-192">İki varlığa bağlanmak için Nesne İlişkisel Tasarımcısı araç kutusu devralma şeklini kullandım, ancak hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a82c-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="1a82c-193">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-193">A.</span></span> <span data-ttu-id="1a82c-194">İlişki oluşturma yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="1a82c-195">Ayrıştırıcı sütunu, taban sınıf ayrıştırıcı değeri ve türetilmiş sınıf ayrıştırıcı değeri gibi bilgileri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="1a82c-196">Sağlayıcı modeli</span><span class="sxs-lookup"><span data-stu-id="1a82c-196">Provider Model</span></span>

<span data-ttu-id="1a82c-197">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-197">Q.</span></span> <span data-ttu-id="1a82c-198">Ortak bir sağlayıcı modeli kullanılabilir mi?</span><span class="sxs-lookup"><span data-stu-id="1a82c-198">Is a public provider model available?</span></span>

<span data-ttu-id="1a82c-199">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-199">A.</span></span> <span data-ttu-id="1a82c-200">Kullanılabilir ortak sağlayıcı modeli yok.</span><span class="sxs-lookup"><span data-stu-id="1a82c-200">No public provider model is available.</span></span> <span data-ttu-id="1a82c-201">Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server ve yalnızca 3,5 SQL Server Compact destekler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="1a82c-202">SQL ekleme saldırıları</span><span class="sxs-lookup"><span data-stu-id="1a82c-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="1a82c-203">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-203">Q.</span></span> <span data-ttu-id="1a82c-204">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL ekleme saldırılarından nasıl korunur?</span><span class="sxs-lookup"><span data-stu-id="1a82c-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="1a82c-205">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-205">A.</span></span> <span data-ttu-id="1a82c-206">SQL ekleme, Kullanıcı girişini birleştirerek oluşturulan geleneksel SQL sorguları için önemli bir risk oldu.</span><span class="sxs-lookup"><span data-stu-id="1a82c-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a82c-207">, sorgularda <xref:System.Data.SqlClient.SqlParameter> kullanarak bu tür ekleme işlemini önler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="1a82c-208">Kullanıcı girişi parametre değerlerine açıktır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-208">User input is turned into parameter values.</span></span> <span data-ttu-id="1a82c-209">Bu yaklaşım, kötü amaçlı komutların müşteri girişinden kullanılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="1a82c-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="1a82c-210">DBML dosyalarındaki salt okunurdur bayrağını değiştirme</span><span class="sxs-lookup"><span data-stu-id="1a82c-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="1a82c-211">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-211">Q.</span></span> <span data-ttu-id="1a82c-212">DBML dosyasından bir nesne modeli oluştururken bazı özelliklerden ayarlayıcıları ortadan kaldırmak Nasıl yaparım??</span><span class="sxs-lookup"><span data-stu-id="1a82c-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="1a82c-213">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-213">A.</span></span> <span data-ttu-id="1a82c-214">Bu gelişmiş senaryo için aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="1a82c-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="1a82c-215">. Dbml dosyasında, <xref:System.Data.Linq.ITable.IsReadOnly%2A> bayrağını `True`değiştirerek özelliği değiştirin.</span><span class="sxs-lookup"><span data-stu-id="1a82c-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="1a82c-216">Kısmi bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="1a82c-216">Add a partial class.</span></span> <span data-ttu-id="1a82c-217">Salt okunurdur üyeleri için parametrelere sahip bir Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1a82c-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="1a82c-218">Uygulamanızın doğru değeri olup olmadığını öğrenmek için varsayılan <xref:System.Data.Linq.Mapping.UpdateCheck> değerini (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="1a82c-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="1a82c-219">Visual Studio 'da Nesne İlişkisel Tasarımcısı kullanıyorsanız değişikliklerinizin üzerine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="1a82c-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="1a82c-220">APTCA</span></span>

<span data-ttu-id="1a82c-221">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-221">Q.</span></span> <span data-ttu-id="1a82c-222">System. Data. Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlendi mi?</span><span class="sxs-lookup"><span data-stu-id="1a82c-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="1a82c-223">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-223">A.</span></span> <span data-ttu-id="1a82c-224">Evet, System. Data. LINQ. dll derlemesi, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğiyle işaretlenmiş .NET Framework derlemeleri arasındadır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="1a82c-225">Bu işaret olmadan, .NET Framework derlemeler yalnızca tam olarak güvenilen kod tarafından kullanılmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="1a82c-226">Kısmi güvenilir arayanlara izin vermek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' deki asıl senaryo, *güven* yapılandırmasının Orta olduğu Web uygulamalarından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] derlemeye erişilmesine imkan tanımalıdır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="1a82c-227">Birden çok tablodan veri eşleme</span><span class="sxs-lookup"><span data-stu-id="1a82c-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="1a82c-228">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-228">Q.</span></span> <span data-ttu-id="1a82c-229">Varlığındaki veriler birden çok tablodan geliyor.</span><span class="sxs-lookup"><span data-stu-id="1a82c-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="1a82c-230">Nasıl yaparım? eşleme yapılsın mı?</span><span class="sxs-lookup"><span data-stu-id="1a82c-230">How do I map it?</span></span>

<span data-ttu-id="1a82c-231">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-231">A.</span></span> <span data-ttu-id="1a82c-232">Veritabanında bir görünüm oluşturabilir ve varlığı görünüme eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a82c-233">, görünümler için aynı SQL 'i tablolar için yaptığı gibi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1a82c-233">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="1a82c-234">Bu senaryodaki görünümlerin kullanımı sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="1a82c-235">Bu yaklaşım, <xref:System.Data.Linq.Table%601> üzerinde gerçekleştirilen işlemler temel alınan görünüm tarafından desteklense de en güvenli şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="1a82c-236">Yalnızca hangi işlemlerin hedeflendiklerini bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-236">Only you know which operations are intended.</span></span> <span data-ttu-id="1a82c-237">Örneğin, çoğu uygulama salt okunurdur ve başka bir boyutlandırılabilir sayı, yalnızca görünümlerde yapılan saklı yordamları kullanarak /`Delete` işlemleri `Update``Create`/.</span><span class="sxs-lookup"><span data-stu-id="1a82c-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="1a82c-238">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="1a82c-238">Connection Pooling</span></span>

<span data-ttu-id="1a82c-239">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-239">Q.</span></span> <span data-ttu-id="1a82c-240"><xref:System.Data.Linq.DataContext> havuzda yardımcı olabilecek bir yapı var mı?</span><span class="sxs-lookup"><span data-stu-id="1a82c-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="1a82c-241">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-241">A.</span></span> <span data-ttu-id="1a82c-242"><xref:System.Data.Linq.DataContext>örneklerini yeniden kullanmayı denemeyin.</span><span class="sxs-lookup"><span data-stu-id="1a82c-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="1a82c-243">Her <xref:System.Data.Linq.DataContext>, belirli bir düzenleme/sorgu oturumu için durumu (kimlik önbelleği dahil) korur.</span><span class="sxs-lookup"><span data-stu-id="1a82c-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="1a82c-244">Veritabanının geçerli durumuna göre yeni örnekler almak için yeni bir <xref:System.Data.Linq.DataContext>kullanın.</span><span class="sxs-lookup"><span data-stu-id="1a82c-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="1a82c-245">Temel ADO.NET bağlantı havuzunu kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="1a82c-246">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="1a82c-247">İkinci DataContext güncelleştirilmedi</span><span class="sxs-lookup"><span data-stu-id="1a82c-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="1a82c-248">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-248">Q.</span></span> <span data-ttu-id="1a82c-249">Değerleri veritabanında depolamak için bir <xref:System.Data.Linq.DataContext> örneği kullandım.</span><span class="sxs-lookup"><span data-stu-id="1a82c-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="1a82c-250">Ancak, aynı veritabanındaki ikinci bir <xref:System.Data.Linq.DataContext> güncelleştirilmiş değerleri yansıtmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="1a82c-251">İkinci <xref:System.Data.Linq.DataContext> örnek, önbelleğe alınmış değerler döndürüyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="1a82c-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="1a82c-252">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-252">A.</span></span> <span data-ttu-id="1a82c-253">Bu davranış tasarım gereğidir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1a82c-254">, ilk örnekte gördüğünüz örnekleri/değerleri döndürmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="1a82c-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="1a82c-255">Güncelleştirmeler yaptığınızda iyimser eşzamanlılık kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="1a82c-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="1a82c-256">Özgün veriler, gerçekten de değişmeden olduğunu doğrulamak üzere geçerli veritabanı durumunu denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="1a82c-257">Değiştirildiyse, bir çakışma oluşur ve uygulamanız bunu çözmelidir.</span><span class="sxs-lookup"><span data-stu-id="1a82c-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="1a82c-258">Uygulamanızın bir seçeneği, özgün durumu geçerli veritabanı durumuna sıfırlamadır ve güncelleştirmeyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="1a82c-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="1a82c-259">Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="1a82c-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="1a82c-260">Ayrıca, önbelleğe alma ve değişiklik izlemeyi kapatan <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> false olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="1a82c-261">Daha sonra, her sorgumanızda en son değerleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="1a82c-262">Salt okuma modunda SubmitChanges çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="1a82c-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="1a82c-263">S.</span><span class="sxs-lookup"><span data-stu-id="1a82c-263">Q.</span></span> <span data-ttu-id="1a82c-264"><xref:System.Data.Linq.DataContext.SubmitChanges%2A> salt okunurdur modda çağırmaya çalıştığımda bir hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="1a82c-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="1a82c-265">BİR.</span><span class="sxs-lookup"><span data-stu-id="1a82c-265">A.</span></span> <span data-ttu-id="1a82c-266">Salt okuma modu, içeriğin değişiklikleri izleme özelliğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="1a82c-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="1a82c-267">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a82c-267">See also</span></span>

- [<span data-ttu-id="1a82c-268">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1a82c-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="1a82c-269">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1a82c-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="1a82c-270">LINQ to SQL’de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="1a82c-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
