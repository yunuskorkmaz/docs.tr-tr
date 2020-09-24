---
title: Birden Çok Etkin Sonuç Kümesini Etkinleştirme
description: ADO.NET ' de tek bir bağlantıda birden çok toplu işlem çalıştırabilmeniz için, SQL Server ile birlikte çalışan bir bağlantı dizesinde MARS 'ı etkinleştirme/devre dışı bırakma hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 0c5b4043b389c7dde39a477f90e82bbf654331f7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156257"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="8554e-103">Birden Çok Etkin Sonuç Kümesini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="8554e-103">Enabling Multiple Active Result Sets</span></span>

<span data-ttu-id="8554e-104">Birden çok etkin sonuç kümesi (MARS), tek bir bağlantıda birden çok toplu işi yürütmeye izin vermek için SQL Server ile birlikte çalışarak bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="8554e-104">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="8554e-105">MARS, SQL Server ile kullanım için etkinleştirildiğinde, kullanılan her komut nesnesi bağlantıya bir oturum ekler.</span><span class="sxs-lookup"><span data-stu-id="8554e-105">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8554e-106">Tek bir MARS oturumu, MARS için bir mantıksal bağlantı ve her etkin komut için bir mantıksal bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="8554e-106">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="8554e-107">Bağlantı dizesinde MARS 'ı etkinleştirme ve devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="8554e-107">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8554e-108">Aşağıdaki bağlantı dizeleri SQL Server bulunan örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8554e-108">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="8554e-109">Belirtilen bağlantı dizeleri, veritabanının MSSQL1 adlı bir sunucuda yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="8554e-109">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="8554e-110">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="8554e-110">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="8554e-111">MARS özelliği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="8554e-111">The MARS feature is disabled by default.</span></span> <span data-ttu-id="8554e-112">Bağlantı dizenizi "MultipleActiveResultSets = true" anahtar sözcüğü çifti eklenerek etkinleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8554e-112">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="8554e-113">MARS 'ı etkinleştirmek için geçerli olan tek değer "true" değeridir.</span><span class="sxs-lookup"><span data-stu-id="8554e-113">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="8554e-114">Aşağıdaki örnek, bir SQL Server örneğine nasıl bağlanabileceğinizi ve bu MARS 'ın etkinleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8554e-114">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="8554e-115">Bağlantı dizenizi "MultipleActiveResultSets = false" anahtar sözcük çiftini ekleyerek MARS 'ı devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8554e-115">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="8554e-116">MARS devre dışı bırakmak için geçerli olan tek değer "false" değeridir.</span><span class="sxs-lookup"><span data-stu-id="8554e-116">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="8554e-117">Aşağıdaki bağlantı dizesi, MARS 'ın nasıl devre dışı bırakılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8554e-117">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="8554e-118">MARS kullanırken özel konular</span><span class="sxs-lookup"><span data-stu-id="8554e-118">Special Considerations When Using MARS</span></span>  

 <span data-ttu-id="8554e-119">Genel olarak, mevcut uygulamaların MARS özellikli bir bağlantı kullanması için değişiklik yapması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="8554e-119">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="8554e-120">Ancak, uygulamalarınızda MARS özelliklerini kullanmak istiyorsanız, aşağıdaki özel konuları anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8554e-120">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="8554e-121">İfade araya ekleme</span><span class="sxs-lookup"><span data-stu-id="8554e-121">Statement Interleaving</span></span>  

 <span data-ttu-id="8554e-122">MARS işlemleri sunucuda zaman uyumlu olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8554e-122">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="8554e-123">SELECT ve BULK INSERT deyimlerinin deyim araya ekleme değerlerine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="8554e-123">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="8554e-124">Ancak, veri işleme dili (DML) ve veri tanımlama dili (DDL) deyimleri otomatik olarak yürütülür.</span><span class="sxs-lookup"><span data-stu-id="8554e-124">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="8554e-125">Atomik bir toplu iş yürütülürken yürütülmeye çalışan tüm deyimler engellenir.</span><span class="sxs-lookup"><span data-stu-id="8554e-125">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="8554e-126">Sunucudaki paralel yürütme bir MARS özelliği değildir.</span><span class="sxs-lookup"><span data-stu-id="8554e-126">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="8554e-127">Bir MARS bağlantısı altında iki toplu işlem gönderilirse, bunlardan biri DML ifadesini içeren bir SELECT ifadesini içeriyorsa, DML SELECT ifadesinin yürütülmesi içinde yürütmeye başlayabilir.</span><span class="sxs-lookup"><span data-stu-id="8554e-127">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="8554e-128">Ancak, SELECT ifadesinin ilerleme yapabilmesi için DML bildiriminin tamamlanmasını çalıştırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8554e-128">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="8554e-129">Her iki deyim de aynı işlem altında çalışıyorsa, SELECT deyimi başladıktan sonra bir DML deyimi tarafından yapılan tüm değişiklikler okuma işlemine görünmez.</span><span class="sxs-lookup"><span data-stu-id="8554e-129">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="8554e-130">SELECT ifadesinin içindeki bir WAITFOR deyimleri, beklerken, ilk satır üretilene kadar işlem yapmaz.</span><span class="sxs-lookup"><span data-stu-id="8554e-130">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="8554e-131">Bu, bir WAITFOR bildirisi beklerken aynı bağlantı içinde başka hiçbir toplu iş yürütülemmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="8554e-131">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="8554e-132">MARS oturum önbelleği</span><span class="sxs-lookup"><span data-stu-id="8554e-132">MARS Session Cache</span></span>  

 <span data-ttu-id="8554e-133">Bir bağlantı MARS etkinken açıldığında, ek yük ekleyen bir mantıksal oturum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8554e-133">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="8554e-134">Ek yükü en aza indirmek ve performansı artırmak için, **SQLCLIENT** Mars oturumunu bir bağlantı içinde önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="8554e-134">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="8554e-135">Önbellekte en fazla 10 MARS oturumu bulunur.</span><span class="sxs-lookup"><span data-stu-id="8554e-135">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="8554e-136">Bu değer Kullanıcı tarafından ayarlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8554e-136">This value is not user adjustable.</span></span> <span data-ttu-id="8554e-137">Oturum sınırına ulaşıldığında, yeni bir oturum oluşturulur; bir hata oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="8554e-137">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="8554e-138">İçinde bulunan önbellek ve oturumlar bağlantı başına olur; bağlantılar arasında paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="8554e-138">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="8554e-139">Bir oturum bırakıldığında, havuzun üst sınırına ulaşılmadığı takdirde havuza döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8554e-139">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="8554e-140">Önbellek havuzu doluysa, oturum kapalıdır.</span><span class="sxs-lookup"><span data-stu-id="8554e-140">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="8554e-141">MARS oturumlarının süreleri dolmaz.</span><span class="sxs-lookup"><span data-stu-id="8554e-141">MARS sessions do not expire.</span></span> <span data-ttu-id="8554e-142">Bunlar yalnızca bağlantı nesnesi atıldığı zaman temizlenir.</span><span class="sxs-lookup"><span data-stu-id="8554e-142">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="8554e-143">MARS oturum önbelleği önceden yüklenmedi.</span><span class="sxs-lookup"><span data-stu-id="8554e-143">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="8554e-144">Uygulama daha fazla oturum gerektirdiğinden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8554e-144">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="8554e-145">İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="8554e-145">Thread Safety</span></span>  

 <span data-ttu-id="8554e-146">MARS işlemleri iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="8554e-146">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="8554e-147">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="8554e-147">Connection Pooling</span></span>  

 <span data-ttu-id="8554e-148">MARS etkin bağlantıları, diğer tüm bağlantılar gibi havuza alınır.</span><span class="sxs-lookup"><span data-stu-id="8554e-148">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="8554e-149">Bir uygulama iki bağlantı açarsa, MARS ve diğeri de MARS devre dışı bırakıldığında iki bağlantı ayrı havuzlardır.</span><span class="sxs-lookup"><span data-stu-id="8554e-149">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="8554e-150">Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="8554e-150">For more information, see [SQL Server Connection Pooling (ADO.NET)](../sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="8554e-151">Toplu yürütme ortamı SQL Server</span><span class="sxs-lookup"><span data-stu-id="8554e-151">SQL Server Batch Execution Environment</span></span>  

 <span data-ttu-id="8554e-152">Bir bağlantı açıldığında, varsayılan bir ortam tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8554e-152">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="8554e-153">Bu ortam daha sonra bir mantıksal MARS oturumuna kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="8554e-153">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="8554e-154">Toplu yürütme ortamı aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="8554e-154">The batch execution environment includes the following components:</span></span>  
  
- <span data-ttu-id="8554e-155">Seçenekleri ayarla (örneğin, ANSI_NULLS, DATE_FORMAT, DIL, TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="8554e-155">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
- <span data-ttu-id="8554e-156">Güvenlik bağlamı (Kullanıcı/uygulama rolü)</span><span class="sxs-lookup"><span data-stu-id="8554e-156">Security context (user/application role)</span></span>  
  
- <span data-ttu-id="8554e-157">Veritabanı bağlamı (geçerli veritabanı)</span><span class="sxs-lookup"><span data-stu-id="8554e-157">Database context (current database)</span></span>  
  
- <span data-ttu-id="8554e-158">Yürütme durumu değişkenleri (örneğin, @ @ERROR , @ @ROWCOUNT , @ @FETCH_STATUS @ @IDENTITY )</span><span class="sxs-lookup"><span data-stu-id="8554e-158">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
- <span data-ttu-id="8554e-159">Üst düzey geçici tablolar</span><span class="sxs-lookup"><span data-stu-id="8554e-159">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="8554e-160">MARS ile, varsayılan bir yürütme ortamı bir bağlantıyla ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="8554e-160">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="8554e-161">Belirli bir bağlantı altında yürütmeye başlayan her yeni toplu işlem, varsayılan ortamın bir kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="8554e-161">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="8554e-162">Belirli bir toplu iş altında kod yürütüldüğünde, ortamda yapılan tüm değişiklikler belirli bir toplu işe göre kapsamlandırılır.</span><span class="sxs-lookup"><span data-stu-id="8554e-162">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="8554e-163">Yürütme tamamlandıktan sonra, yürütme ayarları varsayılan ortama kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="8554e-163">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="8554e-164">Tek bir toplu iş, aynı işlem kapsamında sırayla yürütülmesi için birkaç komut veren bir toplu işlem söz konusu olduğunda, semantik, önceki istemci veya sunucuları içeren bağlantılar tarafından açığa çıkarılan olanlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="8554e-164">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="8554e-165">Paralel Yürütme</span><span class="sxs-lookup"><span data-stu-id="8554e-165">Parallel Execution</span></span>  

 <span data-ttu-id="8554e-166">MARS, bir uygulamadaki birden çok bağlantı için tüm gereksinimleri kaldırmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="8554e-166">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="8554e-167">Bir uygulamanın bir sunucuya karşı doğru paralel yürütülmesi gerekiyorsa, birden çok bağlantı kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8554e-167">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="8554e-168">Örneğin aşağıdaki senaryoları düşünün.</span><span class="sxs-lookup"><span data-stu-id="8554e-168">For example, consider the following scenario.</span></span> <span data-ttu-id="8554e-169">Bir sonuç kümesini işlemek için biri ve verileri güncelleştirmek için bir tane olmak üzere iki komut nesnesi oluşturulur; MARS aracılığıyla ortak bir bağlantı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="8554e-169">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="8554e-170">Bu senaryoda, `Transaction` .`Commit`</span><span class="sxs-lookup"><span data-stu-id="8554e-170">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="8554e-171">İlk komut nesnesinde tüm sonuçlar okunana kadar güncelleştirmede başarısız olur ve aşağıdaki özel durum ortaya çıkarsa:</span><span class="sxs-lookup"><span data-stu-id="8554e-171">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="8554e-172">İleti: Işlem bağlamı başka bir oturum tarafından kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="8554e-172">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="8554e-173">Kaynak: .NET SqlClient Veri Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="8554e-173">Source: .NET SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="8554e-174">Beklenen: (null)</span><span class="sxs-lookup"><span data-stu-id="8554e-174">Expected: (null)</span></span>  
  
 <span data-ttu-id="8554e-175">Alınan: System. Data. SqlClient. SqlException</span><span class="sxs-lookup"><span data-stu-id="8554e-175">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="8554e-176">Bu senaryoyu işlemek için üç seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="8554e-176">There are three options for handling this scenario:</span></span>  
  
1. <span data-ttu-id="8554e-177">İşlemin bir parçası olmaması için okuyucu oluşturulduktan sonra işlemi başlatın.</span><span class="sxs-lookup"><span data-stu-id="8554e-177">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="8554e-178">Her güncelleştirme, kendi işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="8554e-178">Every update then becomes its own transaction.</span></span>  
  
2. <span data-ttu-id="8554e-179">Okuyucu kapatıldıktan sonra tüm işleri yürütün.</span><span class="sxs-lookup"><span data-stu-id="8554e-179">Commit all work after the reader is closed.</span></span> <span data-ttu-id="8554e-180">Bu, önemli miktarda güncelleştirme için olası bir işlem içerir.</span><span class="sxs-lookup"><span data-stu-id="8554e-180">This has the potential for a substantial batch of updates.</span></span>  
  
3. <span data-ttu-id="8554e-181">MARS kullanmayın; Bunun yerine, MARS 'tan önce yaptığınız gibi her bir komut nesnesi için ayrı bir bağlantı kullanın.</span><span class="sxs-lookup"><span data-stu-id="8554e-181">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="8554e-182">MARS desteğini algılama</span><span class="sxs-lookup"><span data-stu-id="8554e-182">Detecting MARS Support</span></span>  

 <span data-ttu-id="8554e-183">Bir uygulama, değeri okuyarak MARS desteğini denetleyebilir `SqlConnection.ServerVersion` .</span><span class="sxs-lookup"><span data-stu-id="8554e-183">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="8554e-184">Ana sayı SQL Server 2005 için 9 ve SQL Server 2008 için 10 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8554e-184">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8554e-185">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8554e-185">See also</span></span>

- [<span data-ttu-id="8554e-186">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="8554e-186">Multiple Active Result Sets (MARS)</span></span>](multiple-active-result-sets-mars.md)
- [<span data-ttu-id="8554e-187">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8554e-187">ADO.NET Overview</span></span>](../ado-net-overview.md)
