---
description: 'Hakkında daha fazla bilgi edinin: sık sorulan sorular'
title: Sık Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 476e9adc3dc88bce786b8b8423e05e800c821320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739085"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="8abf6-103">Sık Sorulan Sorular</span><span class="sxs-lookup"><span data-stu-id="8abf6-103">Frequently Asked Questions</span></span>

<span data-ttu-id="8abf6-104">Aşağıdaki bölümlerde, LINQ uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıtlanacaktır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-104">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="8abf6-105">[Sorun gidermede](troubleshooting.md)ek sorunlar ele alınır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-105">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="8abf6-106">Bağlanamıyor</span><span class="sxs-lookup"><span data-stu-id="8abf6-106">Cannot Connect</span></span>

<span data-ttu-id="8abf6-107">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-107">Q.</span></span> <span data-ttu-id="8abf6-108">Veritabanıma bağlanamıyorum.</span><span class="sxs-lookup"><span data-stu-id="8abf6-108">I cannot connect to my database.</span></span>

<span data-ttu-id="8abf6-109">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-109">A.</span></span> <span data-ttu-id="8abf6-110">Bağlantı dizeniz doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="8abf6-110">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="8abf6-111">Ayrıca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanallar protokolünün etkinleştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-111">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="8abf6-112">Daha fazla bilgi için bkz. [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-112">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="8abf6-113">Veritabanında yapılan değişiklikler kayboldu</span><span class="sxs-lookup"><span data-stu-id="8abf6-113">Changes to Database Lost</span></span>

<span data-ttu-id="8abf6-114">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-114">Q.</span></span> <span data-ttu-id="8abf6-115">Veritabanında verilerde bir değişiklik yaptık, ancak uygulamamı yeniden kaydederken değişiklik artık orada yoktu.</span><span class="sxs-lookup"><span data-stu-id="8abf6-115">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="8abf6-116">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-116">A.</span></span> <span data-ttu-id="8abf6-117"><xref:System.Data.Linq.DataContext.SubmitChanges%2A>Sonuçları veritabanına kaydetmek için çağırdığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="8abf6-117">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="8abf6-118">Veritabanı bağlantısı: ne kadar süreyle açık?</span><span class="sxs-lookup"><span data-stu-id="8abf6-118">Database Connection: Open How Long?</span></span>

<span data-ttu-id="8abf6-119">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-119">Q.</span></span> <span data-ttu-id="8abf6-120">Veritabanı bağlantısı ne kadar süreyle açık kalır?</span><span class="sxs-lookup"><span data-stu-id="8abf6-120">How long does my database connection remain open?</span></span>

<span data-ttu-id="8abf6-121">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-121">A.</span></span> <span data-ttu-id="8abf6-122">Sorgu sonuçlarını tüketene kadar bağlantı genellikle açık kalır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-122">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="8abf6-123">Tüm sonuçları işlemek için zaman almayı beklediğinizi ve sonuçların önbelleğe alınmasını istemiyorsanız, <xref:System.Linq.Enumerable.ToList%2A> sorguya uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8abf6-123">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="8abf6-124">Her nesnenin yalnızca bir kez işlendiği yaygın senaryolarda, akış modeli hem hem de ' de üst düzeydir `DataReader` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8abf6-124">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="8abf6-125">Bağlantı kullanımının tam ayrıntıları aşağıdakilere bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="8abf6-125">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="8abf6-126"><xref:System.Data.Linq.DataContext>Bir bağlantı nesnesi ile oluşturulursa bağlantı durumu.</span><span class="sxs-lookup"><span data-stu-id="8abf6-126">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="8abf6-127">Bağlantı dizesi ayarları (örneğin, birden çok etkin sonuç kümesi (MARS) etkinleştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="8abf6-127">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="8abf6-128">Daha fazla bilgi için bkz. [birden çok etkin sonuç kümesi (mars)](../multiple-active-result-sets-mars.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-128">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="8abf6-129">Sorgulanmadan güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="8abf6-129">Updating Without Querying</span></span>

<span data-ttu-id="8abf6-130">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-130">Q.</span></span> <span data-ttu-id="8abf6-131">Veritabanını sorgulamadan tablo verilerini güncelleştirebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="8abf6-131">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="8abf6-132">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-132">A.</span></span> <span data-ttu-id="8abf6-133">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Küme tabanlı güncelleştirme komutlarına sahip olmasa da, ilk sorgulanmadan güncelleştirmek için aşağıdaki tekniklerden birini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8abf6-133">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="8abf6-134"><xref:System.Data.Linq.DataContext.ExecuteCommand%2A>SQL kodu göndermek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8abf6-134">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="8abf6-135">Nesnenin yeni bir örneğini oluşturun ve güncelleştirmeyi etkileyen tüm geçerli değerleri (alanlar) başlatın.</span><span class="sxs-lookup"><span data-stu-id="8abf6-135">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="8abf6-136">Sonra öğesini kullanarak nesnesini öğesine ekleyin <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.Attach%2A> ve değiştirmek istediğiniz alanı değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8abf6-136">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="8abf6-137">Beklenmeyen sorgu sonuçları</span><span class="sxs-lookup"><span data-stu-id="8abf6-137">Unexpected Query Results</span></span>

<span data-ttu-id="8abf6-138">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-138">Q.</span></span> <span data-ttu-id="8abf6-139">Sorgum beklenmeyen sonuçlar döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="8abf6-139">My query is returning unexpected results.</span></span> <span data-ttu-id="8abf6-140">Ne olduğunu nasıl giderebilirim?</span><span class="sxs-lookup"><span data-stu-id="8abf6-140">How can I inspect what is occurring?</span></span>

<span data-ttu-id="8abf6-141">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-141">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-142">oluşturduğu SQL kodunu incelemek için çeşitli araçlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="8abf6-142">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="8abf6-143">En önemlileri bunlardan biridir <xref:System.Data.Linq.DataContext.Log%2A> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-143">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="8abf6-144">Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-144">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="8abf6-145">Beklenmeyen saklı yordam sonuçları</span><span class="sxs-lookup"><span data-stu-id="8abf6-145">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="8abf6-146">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-146">Q.</span></span> <span data-ttu-id="8abf6-147">Dönüş değeri tarafından hesaplanan bir saklı yordamım var `MAX()` .</span><span class="sxs-lookup"><span data-stu-id="8abf6-147">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="8abf6-148">Saklı yordamı O/R Designer yüzeyine sürükledikten sonra, dönüş değeri doğru değil.</span><span class="sxs-lookup"><span data-stu-id="8abf6-148">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="8abf6-149">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-149">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-150">, saklı yordamlar yoluyla veritabanı tarafından oluşturulan değerleri döndürmek için iki yol sunar:</span><span class="sxs-lookup"><span data-stu-id="8abf6-150">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="8abf6-151">Çıkış sonucunu adlandırarak.</span><span class="sxs-lookup"><span data-stu-id="8abf6-151">By naming the output result.</span></span>

- <span data-ttu-id="8abf6-152">Açıkça bir çıkış parametresi belirterek.</span><span class="sxs-lookup"><span data-stu-id="8abf6-152">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="8abf6-153">Aşağıda yanlış çıktının bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-153">The following is an example of incorrect output.</span></span> <span data-ttu-id="8abf6-154">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sonuçları eşlemediğinden, her zaman 0 değerini döndürür:</span><span class="sxs-lookup"><span data-stu-id="8abf6-154">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="8abf6-155">Aşağıda, çıkış parametresi kullanarak doğru çıkışın bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8abf6-155">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="8abf6-156">Aşağıda, çıkış sonucunu adlandırarak doğru çıkışın bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="8abf6-156">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="8abf6-157">Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-157">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="8abf6-158">Serileştirme hataları</span><span class="sxs-lookup"><span data-stu-id="8abf6-158">Serialization Errors</span></span>

<span data-ttu-id="8abf6-159">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-159">Q.</span></span> <span data-ttu-id="8abf6-160">Seri hale getirme yapmayı denediğimde şu hatayı alıyorum: "System. Data. LINQ. ChangeTracker + StandardChangeTracker ' yazın... seri hale getirilebilir olarak işaretlenmemiş. "</span><span class="sxs-lookup"><span data-stu-id="8abf6-160">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="8abf6-161">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-161">A.</span></span> <span data-ttu-id="8abf6-162">İçindeki kod üretimi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme destekler.</span><span class="sxs-lookup"><span data-stu-id="8abf6-162">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="8abf6-163"><xref:System.Xml.Serialization.XmlSerializer>Veya desteklemez <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-163">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="8abf6-164">Daha fazla bilgi için bkz. [serileştirme](serialization.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-164">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="8abf6-165">Birden çok DBML dosyası</span><span class="sxs-lookup"><span data-stu-id="8abf6-165">Multiple DBML Files</span></span>

<span data-ttu-id="8abf6-166">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-166">Q.</span></span> <span data-ttu-id="8abf6-167">Ortak olarak bazı tabloları paylaşan birden çok DBML dosyası olduğunda bir derleyici hatası alıyorum.</span><span class="sxs-lookup"><span data-stu-id="8abf6-167">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="8abf6-168">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-168">A.</span></span> <span data-ttu-id="8abf6-169">**Bağlam ad alanını** ve **varlık ad alanı** özelliklerini nesne ilişkisel Tasarımcısı her dbml dosyası için ayrı bir değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8abf6-169">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="8abf6-170">Bu yaklaşım ad/ad alanı çarpışmasını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-170">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="8abf6-171">INSERT veya Update üzerinde Database-Generated değerlerinin açık ayarından kaçınma</span><span class="sxs-lookup"><span data-stu-id="8abf6-171">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="8abf6-172">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-172">Q.</span></span> <span data-ttu-id="8abf6-173">SQL için varsayılan olarak bir sütun içeren bir veritabanı tablom var `DateCreated` `Getdate()` .</span><span class="sxs-lookup"><span data-stu-id="8abf6-173">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="8abf6-174">Kullanarak yeni bir kayıt eklemeye çalıştığımda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , değer olarak ayarlanır `NULL` .</span><span class="sxs-lookup"><span data-stu-id="8abf6-174">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="8abf6-175">Veritabanının varsayılan olarak ayarlanmış olmasını bekler.</span><span class="sxs-lookup"><span data-stu-id="8abf6-175">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="8abf6-176">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-176">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-177">kimlik (otomatik artış) ve ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için bu durumu otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="8abf6-177">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="8abf6-178">Diğer durumlarda, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> özelliklerini el ile ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-178">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="8abf6-179">Çoklu dataloadoçen</span><span class="sxs-lookup"><span data-stu-id="8abf6-179">Multiple DataLoadOptions</span></span>

<span data-ttu-id="8abf6-180">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-180">Q.</span></span> <span data-ttu-id="8abf6-181">İlk üzerine yazmadan ek yükleme seçenekleri belirtebilir miyim?</span><span class="sxs-lookup"><span data-stu-id="8abf6-181">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="8abf6-182">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-182">A.</span></span> <span data-ttu-id="8abf6-183">Evet.</span><span class="sxs-lookup"><span data-stu-id="8abf6-183">Yes.</span></span> <span data-ttu-id="8abf6-184">Aşağıdaki örnekte olduğu gibi ilki üzerine yazılmaz:</span><span class="sxs-lookup"><span data-stu-id="8abf6-184">The first is not overwritten, as in the following example:</span></span>

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

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="8abf6-185">SQL Compact 3,5 kullanarak hatalar</span><span class="sxs-lookup"><span data-stu-id="8abf6-185">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="8abf6-186">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-186">Q.</span></span> <span data-ttu-id="8abf6-187">SQL Server Compact 3,5 veritabanından tablo sürüklediğiniz zaman bir hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="8abf6-187">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="8abf6-188">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-188">A.</span></span> <span data-ttu-id="8abf6-189">Nesne İlişkisel Tasarımcısı, çalışma zamanı olsa da, SQL Server Compact 3,5 'yi desteklemez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8abf6-189">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="8abf6-190">Bu durumda, kendi varlık sınıflarınızı oluşturmanız ve uygun öznitelikleri eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-190">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="8abf6-191">Devralma Ilişkilerinde hatalar</span><span class="sxs-lookup"><span data-stu-id="8abf6-191">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="8abf6-192">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-192">Q.</span></span> <span data-ttu-id="8abf6-193">İki varlığa bağlanmak için Nesne İlişkisel Tasarımcısı araç kutusu devralma şeklini kullandım, ancak hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="8abf6-193">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="8abf6-194">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-194">A.</span></span> <span data-ttu-id="8abf6-195">İlişki oluşturma yeterli değildir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-195">Creating the relationship is not enough.</span></span> <span data-ttu-id="8abf6-196">Ayrıştırıcı sütunu, taban sınıf ayrıştırıcı değeri ve türetilmiş sınıf ayrıştırıcı değeri gibi bilgileri sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-196">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="8abf6-197">Sağlayıcı modeli</span><span class="sxs-lookup"><span data-stu-id="8abf6-197">Provider Model</span></span>

<span data-ttu-id="8abf6-198">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-198">Q.</span></span> <span data-ttu-id="8abf6-199">Ortak bir sağlayıcı modeli kullanılabilir mi?</span><span class="sxs-lookup"><span data-stu-id="8abf6-199">Is a public provider model available?</span></span>

<span data-ttu-id="8abf6-200">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-200">A.</span></span> <span data-ttu-id="8abf6-201">Kullanılabilir ortak sağlayıcı modeli yok.</span><span class="sxs-lookup"><span data-stu-id="8abf6-201">No public provider model is available.</span></span> <span data-ttu-id="8abf6-202">Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yalnızca SQL Server ve SQL Server Compact 3,5 destekler.</span><span class="sxs-lookup"><span data-stu-id="8abf6-202">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="8abf6-203">SQL-Injection saldırıları</span><span class="sxs-lookup"><span data-stu-id="8abf6-203">SQL-Injection Attacks</span></span>

<span data-ttu-id="8abf6-204">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-204">Q.</span></span> <span data-ttu-id="8abf6-205">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL ekleme saldırılarından nasıl korunur?</span><span class="sxs-lookup"><span data-stu-id="8abf6-205">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="8abf6-206">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-206">A.</span></span> <span data-ttu-id="8abf6-207">SQL ekleme, Kullanıcı girişini birleştirerek oluşturulan geleneksel SQL sorguları için önemli bir risk oldu.</span><span class="sxs-lookup"><span data-stu-id="8abf6-207">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-208">sorgularda kullanarak bu tür ekleme işlemini önler <xref:System.Data.SqlClient.SqlParameter> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-208">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="8abf6-209">Kullanıcı girişi parametre değerlerine açıktır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-209">User input is turned into parameter values.</span></span> <span data-ttu-id="8abf6-210">Bu yaklaşım, kötü amaçlı komutların müşteri girişinden kullanılmasını önler.</span><span class="sxs-lookup"><span data-stu-id="8abf6-210">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="8abf6-211">DBML dosyalarındaki salt okunurdur bayrağını değiştirme</span><span class="sxs-lookup"><span data-stu-id="8abf6-211">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="8abf6-212">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-212">Q.</span></span> <span data-ttu-id="8abf6-213">DBML dosyasından bir nesne modeli oluştururken bazı özelliklerden ayarlayıcıları ortadan kaldırmak Nasıl yaparım??</span><span class="sxs-lookup"><span data-stu-id="8abf6-213">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="8abf6-214">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-214">A.</span></span> <span data-ttu-id="8abf6-215">Bu gelişmiş senaryo için aşağıdaki adımları uygulayın:</span><span class="sxs-lookup"><span data-stu-id="8abf6-215">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="8abf6-216">. Dbml dosyasında, bayrağını olarak değiştirerek özelliği değiştirin <xref:System.Data.Linq.ITable.IsReadOnly%2A> `True` .</span><span class="sxs-lookup"><span data-stu-id="8abf6-216">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="8abf6-217">Kısmi bir sınıf ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8abf6-217">Add a partial class.</span></span> <span data-ttu-id="8abf6-218">Salt okunurdur üyeleri için parametrelere sahip bir Oluşturucu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="8abf6-218">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="8abf6-219"><xref:System.Data.Linq.Mapping.UpdateCheck> <xref:System.Data.Linq.Mapping.UpdateCheck.Never> Uygulamanızın doğru değeri olup olmadığını anlamak için varsayılan değeri () gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="8abf6-219">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="8abf6-220">Visual Studio 'da Nesne İlişkisel Tasarımcısı kullanıyorsanız değişikliklerinizin üzerine yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-220">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="8abf6-221">APTCA</span><span class="sxs-lookup"><span data-stu-id="8abf6-221">APTCA</span></span>

<span data-ttu-id="8abf6-222">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-222">Q.</span></span> <span data-ttu-id="8abf6-223">System. Data. Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlendi mi?</span><span class="sxs-lookup"><span data-stu-id="8abf6-223">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="8abf6-224">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-224">A.</span></span> <span data-ttu-id="8abf6-225">Evet, System.Data.Linq.dll derlemesi özniteliğiyle işaretlenen bu .NET Framework derlemelerinden arasındadır <xref:System.Security.AllowPartiallyTrustedCallersAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-225">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="8abf6-226">Bu işaret olmadan, .NET Framework derlemeler yalnızca tam olarak güvenilen kod tarafından kullanılmaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-226">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="8abf6-227">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Kısmen güvenilen çağıranlara izin vermek için içindeki asıl senaryo, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *güven* yapılandırmasının Orta olduğu Web uygulamalarından erişilmesine imkan tanımalıdır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-227">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="8abf6-228">Birden çok tablodan veri eşleme</span><span class="sxs-lookup"><span data-stu-id="8abf6-228">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="8abf6-229">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-229">Q.</span></span> <span data-ttu-id="8abf6-230">Varlığındaki veriler birden çok tablodan geliyor.</span><span class="sxs-lookup"><span data-stu-id="8abf6-230">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="8abf6-231">Nasıl yaparım? eşleme yapılsın mı?</span><span class="sxs-lookup"><span data-stu-id="8abf6-231">How do I map it?</span></span>

<span data-ttu-id="8abf6-232">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-232">A.</span></span> <span data-ttu-id="8abf6-233">Veritabanında bir görünüm oluşturabilir ve varlığı görünüme eşleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-233">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-234">görünümler için aynı SQL 'i tablolar için yaptığı gibi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8abf6-234">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="8abf6-235">Bu senaryodaki görünümlerin kullanımı sınırlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-235">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="8abf6-236">Bu yaklaşım, üzerinde gerçekleştirilen işlemler <xref:System.Data.Linq.Table%601> temel alınan görünüm tarafından desteklense de en güvenli şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-236">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="8abf6-237">Yalnızca hangi işlemlerin hedeflendiklerini bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-237">Only you know which operations are intended.</span></span> <span data-ttu-id="8abf6-238">Örneğin, çoğu uygulama salt okunurdur ve diğer bir boyutlandırılabilir sayı `Create` / `Update` / `Delete` yalnızca görünümlerde uygulanan saklı yordamları kullanarak işlemleri gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-238">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="8abf6-239">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="8abf6-239">Connection Pooling</span></span>

<span data-ttu-id="8abf6-240">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-240">Q.</span></span> <span data-ttu-id="8abf6-241">Havuzda yardımcı olabilecek bir yapı var <xref:System.Data.Linq.DataContext> mı?</span><span class="sxs-lookup"><span data-stu-id="8abf6-241">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="8abf6-242">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-242">A.</span></span> <span data-ttu-id="8abf6-243">Örneklerini yeniden kullanmayı denemeyin <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-243">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="8abf6-244">Her biri <xref:System.Data.Linq.DataContext> belirli bir düzenleme/sorgu oturumu için durumu (kimlik önbelleği dahil) korur.</span><span class="sxs-lookup"><span data-stu-id="8abf6-244">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="8abf6-245">Veritabanının geçerli durumuna göre yeni örnekler almak için yeni bir kullanın <xref:System.Data.Linq.DataContext> .</span><span class="sxs-lookup"><span data-stu-id="8abf6-245">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="8abf6-246">Temel ADO.NET bağlantı havuzunu kullanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-246">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="8abf6-247">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-247">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="8abf6-248">İkinci DataContext güncelleştirilmedi</span><span class="sxs-lookup"><span data-stu-id="8abf6-248">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="8abf6-249">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-249">Q.</span></span> <span data-ttu-id="8abf6-250"><xref:System.Data.Linq.DataContext>Değerlerini veritabanında depolamak için bir örneğini kullandım.</span><span class="sxs-lookup"><span data-stu-id="8abf6-250">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="8abf6-251">Ancak, aynı veritabanında ikinci bir saniye <xref:System.Data.Linq.DataContext> güncelleştirilmiş değerleri yansıtmamaktadır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-251">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="8abf6-252">İkinci <xref:System.Data.Linq.DataContext> örnek, önbelleğe alınmış değerleri döndürüyor gibi görünüyor.</span><span class="sxs-lookup"><span data-stu-id="8abf6-252">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="8abf6-253">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-253">A.</span></span> <span data-ttu-id="8abf6-254">Bu davranış tasarım gereğidir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-254">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8abf6-255">İlk örnekte gördüğünüz örneklerin/değerlerin aynısını döndürmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="8abf6-255">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="8abf6-256">Güncelleştirmeler yaptığınızda iyimser eşzamanlılık kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="8abf6-256">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="8abf6-257">Özgün veriler, gerçekten de değişmeden olduğunu doğrulamak üzere geçerli veritabanı durumunu denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-257">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="8abf6-258">Değiştirildiyse, bir çakışma oluşur ve uygulamanız bunu çözmelidir.</span><span class="sxs-lookup"><span data-stu-id="8abf6-258">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="8abf6-259">Uygulamanızın bir seçeneği, özgün durumu geçerli veritabanı durumuna sıfırlamadır ve güncelleştirmeyi yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="8abf6-259">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="8abf6-260">Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="8abf6-260">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="8abf6-261">Ayrıca <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> , önbelleğe alma ve değişiklik izlemeyi kapatan yanlış olarak ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-261">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="8abf6-262">Daha sonra, her sorgumanızda en son değerleri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-262">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="8abf6-263">Salt okuma modunda SubmitChanges çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="8abf6-263">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="8abf6-264">S.</span><span class="sxs-lookup"><span data-stu-id="8abf6-264">Q.</span></span> <span data-ttu-id="8abf6-265"><xref:System.Data.Linq.DataContext.SubmitChanges%2A>Salt okuma modunda çağrı yapmayı denediğimde bir hata alıyorum.</span><span class="sxs-lookup"><span data-stu-id="8abf6-265">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="8abf6-266">A.</span><span class="sxs-lookup"><span data-stu-id="8abf6-266">A.</span></span> <span data-ttu-id="8abf6-267">Salt okuma modu, içeriğin değişiklikleri izleme özelliğini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="8abf6-267">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="8abf6-268">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8abf6-268">See also</span></span>

- [<span data-ttu-id="8abf6-269">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8abf6-269">Reference</span></span>](reference.md)
- [<span data-ttu-id="8abf6-270">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="8abf6-270">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="8abf6-271">LINQ to SQL’de Güvenlik</span><span class="sxs-lookup"><span data-stu-id="8abf6-271">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
