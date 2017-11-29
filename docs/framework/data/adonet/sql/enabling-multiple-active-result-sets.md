---
title: "Birden fazla etkin sonuç kümesi etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d39d1666f63d7d6f7a6154a124280486c3fccce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="419ae-102">Birden fazla etkin sonuç kümesi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="419ae-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="419ae-103">Birden fazla etkin sonuç kümeleri (MARS) birden çok toplu işlem yürütme üzerinde tek bir bağlantıya izin vermek için SQL Server ile çalışan bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="419ae-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="419ae-104">MARS, SQL Server ile kullanmak için etkinleştirildiğinde, kullanılan her komut nesnesi bir oturum bağlantısı ekler.</span><span class="sxs-lookup"><span data-stu-id="419ae-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="419ae-105">Tek bir MARS oturumu MARS kullanmak için bir mantıksal bağlantı ve ardından her etkin komutu için bir mantıksal bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="419ae-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="419ae-106">Etkinleştirme ve bağlantı dizesindeki MARS devre dışı bırakma</span><span class="sxs-lookup"><span data-stu-id="419ae-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="419ae-107">Aşağıdaki bağlantı dizeleri örneği kullanmak **AdventureWorks** SQL Server'da bulunan veritabanı.</span><span class="sxs-lookup"><span data-stu-id="419ae-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="419ae-108">Sağlanan bağlantı dizeleri, veritabanı MSSQL1 adlı bir sunucuda yüklü olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="419ae-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="419ae-109">Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="419ae-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="419ae-110">MARS özelliği varsayılan olarak devre dışıdır.</span><span class="sxs-lookup"><span data-stu-id="419ae-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="419ae-111">Ekleyerek etkinleştirilebilir "MultipleActiveResultSets = True", bağlantı dizesi için anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="419ae-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="419ae-112">MARS etkinleştirmek için tek geçerli değer "True" dır.</span><span class="sxs-lookup"><span data-stu-id="419ae-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="419ae-113">Aşağıdaki örnek, SQL Server örneğine bağlanma ve MARS etkin olduğunu belirtmek nasıl gösterilir.</span><span class="sxs-lookup"><span data-stu-id="419ae-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
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
  
 <span data-ttu-id="419ae-114">Ekleyerek MARS devre dışı bırakabilirsiniz "MultipleActiveResultSets = False" bağlantı dizenizi için anahtar çifti.</span><span class="sxs-lookup"><span data-stu-id="419ae-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="419ae-115">MARS devre dışı bırakmak için tek geçerli değer "False" dır.</span><span class="sxs-lookup"><span data-stu-id="419ae-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="419ae-116">Aşağıdaki bağlantı dizesi MARS devre dışı bırakma gösterir.</span><span class="sxs-lookup"><span data-stu-id="419ae-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
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
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="419ae-117">MARS kullanırken özel durumları</span><span class="sxs-lookup"><span data-stu-id="419ae-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="419ae-118">Genel olarak, var olan uygulamaları MARS etkin bir bağlantı kullanmak için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="419ae-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="419ae-119">Ancak, uygulamalarınızda MARS özelliklerini kullanmak isterseniz, aşağıdaki özel hususlar anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="419ae-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="419ae-120">Deyimi Interleaving</span><span class="sxs-lookup"><span data-stu-id="419ae-120">Statement Interleaving</span></span>  
 <span data-ttu-id="419ae-121">MARS işlemleri zaman uyumlu olarak sunucuda yürütün.</span><span class="sxs-lookup"><span data-stu-id="419ae-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="419ae-122">Deyimi seçin ve BULK INSERT deyimleri Interleaving izin verilir.</span><span class="sxs-lookup"><span data-stu-id="419ae-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="419ae-123">Ancak, veri işleme dili (DML) ve veri tanımlama dili (DDL) deyimleri otomatik olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="419ae-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="419ae-124">Atomik bir toplu iş yürütülürken yürütme girişimi deyimleri engellenir.</span><span class="sxs-lookup"><span data-stu-id="419ae-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="419ae-125">Paralel yürütme sunucuda bir MARS özelliği değil.</span><span class="sxs-lookup"><span data-stu-id="419ae-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="419ae-126">Bir MARS bağlantısı altında biri bir SELECT deyimi içeren iki toplu gönderdiyseniz diğer bir DML deyimi içeren DML yürütme SELECT deyiminin içinde yürütme başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="419ae-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="419ae-127">Ancak, SELECT deyiminde ilerleme yapabilmeniz için önce DML deyimi tamamlanıncaya kadar çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="419ae-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="419ae-128">Her iki deyimleri aynı işlemde çalıştırıyorsanız, SELECT deyimi yürütme başlatıldıktan sonra bir DML deyimi tarafından yapılan değişiklikler okuma işlemi için görünür değildir.</span><span class="sxs-lookup"><span data-stu-id="419ae-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="419ae-129">İlk satırın üretilene kadar diğer bir deyişle, bekliyor ancak bir SELECT deyimi WAITFOR ifadeye işlem vermez.</span><span class="sxs-lookup"><span data-stu-id="419ae-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="419ae-130">Bu, bir WAITFOR ifadesi bekliyor. sırada başka bir toplu aynı bağlantı içinde yürütebilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="419ae-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="419ae-131">MARS oturumu önbelleği</span><span class="sxs-lookup"><span data-stu-id="419ae-131">MARS Session Cache</span></span>  
 <span data-ttu-id="419ae-132">Bağlantı etkin MARS ile açıldığında, ek yükü ekler mantıksal bir oturum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="419ae-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="419ae-133">Ek yükü en aza indirmek ve performansı geliştirmek için **SqlClient** bağlantı MARS oturumunda önbelleğe alır.</span><span class="sxs-lookup"><span data-stu-id="419ae-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="419ae-134">Önbelleği en fazla 10 MARS oturumu içerir.</span><span class="sxs-lookup"><span data-stu-id="419ae-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="419ae-135">Bu değer ayarlanabilir kullanıcı değil.</span><span class="sxs-lookup"><span data-stu-id="419ae-135">This value is not user adjustable.</span></span> <span data-ttu-id="419ae-136">Oturum sınırına ulaşıldığında, yeni bir oturum oluşturulur — bir hata değildir oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="419ae-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="419ae-137">Bağlantı başına önbellek ve içerdiği oturumları olan; bağlantılarında paylaşılmaz.</span><span class="sxs-lookup"><span data-stu-id="419ae-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="419ae-138">Oturumu serbest bırakıldığında havuzun üst sınırına ulaşıldı sürece havuzuna döndürülür.</span><span class="sxs-lookup"><span data-stu-id="419ae-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="419ae-139">Önbellek havuzun doluysa oturumu kapatılır.</span><span class="sxs-lookup"><span data-stu-id="419ae-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="419ae-140">MARS oturumları dolmaz.</span><span class="sxs-lookup"><span data-stu-id="419ae-140">MARS sessions do not expire.</span></span> <span data-ttu-id="419ae-141">Bağlantı nesnesi çıkarıldığından bunlar yalnızca temizlenmesini.</span><span class="sxs-lookup"><span data-stu-id="419ae-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="419ae-142">MARS oturumu önbelleği önceden yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="419ae-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="419ae-143">Daha fazla oturumları uygulamanın gerektirdiği şekilde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="419ae-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="419ae-144">İş Parçacığı Güvenliği</span><span class="sxs-lookup"><span data-stu-id="419ae-144">Thread Safety</span></span>  
 <span data-ttu-id="419ae-145">MARS işlem iş parçacığı açısından güvenli değildir.</span><span class="sxs-lookup"><span data-stu-id="419ae-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="419ae-146">Bağlantı havuzu</span><span class="sxs-lookup"><span data-stu-id="419ae-146">Connection Pooling</span></span>  
 <span data-ttu-id="419ae-147">MARS etkin bağlantılar gibi başka bir bağlantı havuza.</span><span class="sxs-lookup"><span data-stu-id="419ae-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="419ae-148">Bir uygulama biri etkin MARS diğeri devre dışı MARS ile iki bağlantı açılırsa, iki ayrı havuzlarında bağlantılardır.</span><span class="sxs-lookup"><span data-stu-id="419ae-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="419ae-149">Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="419ae-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="419ae-150">SQL Server toplu iş yürütme ortamı</span><span class="sxs-lookup"><span data-stu-id="419ae-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="419ae-151">Bağlantı açıldığında, varsayılan ortam tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="419ae-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="419ae-152">Bu ortam sonra mantıksal MARS oturuma kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="419ae-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="419ae-153">Toplu iş yürütme ortamı aşağıdaki bileşenleri içerir:</span><span class="sxs-lookup"><span data-stu-id="419ae-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="419ae-154">SET seçenekleri (örneğin, ANSI_NULLS DATE_FORMAT, dil, TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="419ae-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="419ae-155">Güvenlik bağlamı (kullanıcı/uygulama rolü)</span><span class="sxs-lookup"><span data-stu-id="419ae-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="419ae-156">Veritabanı bağlamı (geçerli veritabanı)</span><span class="sxs-lookup"><span data-stu-id="419ae-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="419ae-157">Yürütme durumu değişkenleri (örneğin, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="419ae-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="419ae-158">Üst düzey geçici tabloları</span><span class="sxs-lookup"><span data-stu-id="419ae-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="419ae-159">MARS ile bir varsayılan yürütme ortamı bağlantı ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="419ae-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="419ae-160">Verilen bağlantı altında yürütülmeye başlamadan her yeni toplu varsayılan ortamın kopyasını alır.</span><span class="sxs-lookup"><span data-stu-id="419ae-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="419ae-161">Her kod altında belirtilen bir toplu iş yürütüldüğünde, ortama yapılan tüm değişiklikler için belirli toplu kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="419ae-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="419ae-162">Bir kez yürütme tamamlandığında, yürütme ayarları varsayılan ortamına kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="419ae-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="419ae-163">Aynı işlemde sıralı olarak yürütülecek birkaç komutların veren tek bir toplu iş söz konusu olduğunda, semantiği önceki istemciler veya sunucular içeren bağlantılar tarafından kullanıma sunulan aynıdır.</span><span class="sxs-lookup"><span data-stu-id="419ae-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="419ae-164">Paralel Yürütme</span><span class="sxs-lookup"><span data-stu-id="419ae-164">Parallel Execution</span></span>  
 <span data-ttu-id="419ae-165">MARS bir uygulamada birden çok bağlantı için tüm gereksinimleri kaldırmak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="419ae-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="419ae-166">Bir uygulama bir sunucuya karşı komutların true Paralel yürütme gerekiyorsa, birden çok bağlantı kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="419ae-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="419ae-167">Örneğin, aşağıdaki senaryoyu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="419ae-167">For example, consider the following scenario.</span></span> <span data-ttu-id="419ae-168">İki komut nesneleri, bir sonuç kümesi ve verilerini güncelleştirmek için başka bir işleme için bir tane oluşturulur; MARS aracılığıyla ortak bağlantı paylaştıkları.</span><span class="sxs-lookup"><span data-stu-id="419ae-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="419ae-169">Bu senaryoda, `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="419ae-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="419ae-170">Tüm sonuçlar şu özel durum oluşturan ilk command nesnesinde okunan kadar güncelleştirme başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="419ae-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="419ae-171">İleti: İşlem bağlamı başka bir oturum tarafından kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="419ae-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="419ae-172">Kaynak: .net SqlClient veri sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="419ae-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="419ae-173">Beklenen: (boş)</span><span class="sxs-lookup"><span data-stu-id="419ae-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="419ae-174">Alınan: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="419ae-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="419ae-175">Bu senaryo işlemek için üç seçenek vardır:</span><span class="sxs-lookup"><span data-stu-id="419ae-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="419ae-176">Okuyucu oluşturulduktan sonra işlemin bir parçası değil işlem başlatın.</span><span class="sxs-lookup"><span data-stu-id="419ae-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="419ae-177">Her güncelleştirmeyi daha sonra kendi işlem olur.</span><span class="sxs-lookup"><span data-stu-id="419ae-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="419ae-178">Okuyucu kapatıldıktan sonra tüm iş uygulayın.</span><span class="sxs-lookup"><span data-stu-id="419ae-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="419ae-179">Bu güncelleştirmeler önemli toplu için olasılığı vardır.</span><span class="sxs-lookup"><span data-stu-id="419ae-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="419ae-180">MARS kullanmayın; Bunun yerine önce MARS yaptığınız gibi her komut nesnesi için ayrı bir bağlantı kullanın.</span><span class="sxs-lookup"><span data-stu-id="419ae-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="419ae-181">MARS destek algılama</span><span class="sxs-lookup"><span data-stu-id="419ae-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="419ae-182">MARS okuyarak desteği için bir uygulama denetleyebilirsiniz `SqlConnection.ServerVersion` değeri.</span><span class="sxs-lookup"><span data-stu-id="419ae-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="419ae-183">Ana 9 SQL Server 2005 ve SQL Server 2008 için 10 olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="419ae-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="419ae-184">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="419ae-184">See Also</span></span>  
 [<span data-ttu-id="419ae-185">Birden fazla etkin sonuç kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="419ae-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="419ae-186">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="419ae-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
