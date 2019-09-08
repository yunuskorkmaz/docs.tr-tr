---
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: b6fa4207531e86cbde8657d0c47596f22c886f89
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791876"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="f4dc1-102">SQL Server için Sağlayıcı İstatistikleri</span><span class="sxs-lookup"><span data-stu-id="f4dc1-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="f4dc1-103">.NET Framework sürüm 2,0 ' den başlayarak, SQL Server için .NET Framework Veri Sağlayıcısı, çalışma zamanı istatistiklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="f4dc1-104">Geçerli bir Connection nesneniz oluşturulduktan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> `True` sonra <xref:System.Data.SqlClient.SqlConnection> nesnesinin özelliğini ayarlayarak istatistikleri etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="f4dc1-105">İstatistikler etkinleştirildikten sonra, <xref:System.Collections.IDictionary> <xref:System.Data.SqlClient.SqlConnection> nesnenin <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> yöntemi aracılığıyla bir başvuru alarak bunları bir "anlık görüntü" olarak gözden geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="f4dc1-106">Liste/değer çifti sözlüğü girdileri kümesi olarak listeyi numaralandırın.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="f4dc1-107">Bu ad/değer çiftleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="f4dc1-108">İstediğiniz zaman, sayaçları sıfırlamak için <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> nesnesinin yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="f4dc1-109">İstatistik toplama etkinleştirilmediyse, bir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="f4dc1-110">Ayrıca <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> , ilki çağrılmadan <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> çağrılırsa, alınan değerler her girdinin başlangıç değerleridir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="f4dc1-111">İstatistikleri etkinleştirir, uygulamanızı bir süre için çalıştırın ve sonra istatistikleri devre dışı bırakırsanız, alınan değerler istatistiklerin devre dışı bırakıldığı noktaya kadar toplanan değerleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="f4dc1-112">Toplanan tüm istatistiksel değerler her bağlantı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="f4dc1-113">İstatistiksel değerler kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="f4dc1-113">Statistical Values Available</span></span>  
 <span data-ttu-id="f4dc1-114">Şu anda Microsoft SQL Server sağlayıcısından 18 farklı öğe mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="f4dc1-115">Kullanılabilir öğelerin sayısına tarafından <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>döndürülen <xref:System.Collections.IDictionary> arabirim başvurusunun **Count** özelliği aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="f4dc1-116">Sağlayıcı istatistikleri için tüm sayaçlar, ortak dil çalışma zamanı <xref:System.Int64> türünü (**Long** in C# and Visual Basic) kullanır, bu da 64 bit geniştir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="f4dc1-117">Int64 tarafından tanımlanan en büyük **Int64** veri türü değeri **. MaxValue** alanı ((2 ^ 63)-1)).</span><span class="sxs-lookup"><span data-stu-id="f4dc1-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="f4dc1-118">Sayaçların değerleri bu en büyük değere ulaştığında, artık doğru olarak değerlendirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="f4dc1-119">Bu, söz konusu int64 anlamına gelir **. MaxValue**-1 ((2 ^ 63)-2), herhangi bir istatistiğin en büyük geçerli değeri etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4dc1-120">Döndürülen istatistiklerin sayısı, isimleri ve sırası gelecekte değiştirebileceğinden, sağlayıcı istatistiklerini döndürmek için bir sözlük kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="f4dc1-121">Uygulamalar, sözlükte bulunan belirli bir değere güvenmemelidir, ancak bunun yerine değerin aynı ve uygun olup olmadığını kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="f4dc1-122">Aşağıdaki tabloda mevcut istatistiksel değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="f4dc1-123">Tek tek değerler için anahtar adlarının, Microsoft .NET çerçevesinin bölgesel sürümlerinde yerelleştirilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="f4dc1-124">Anahtar adı</span><span class="sxs-lookup"><span data-stu-id="f4dc1-124">Key Name</span></span>|<span data-ttu-id="f4dc1-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4dc1-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="f4dc1-126">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra SQL Server sağlayıcı tarafından alınan tablo veri akışı (TDS) paketlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="f4dc1-127">İstatistikler etkinleştirildikten sonra sağlayıcı tarafından SQL Server gönderilen TDS paketlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="f4dc1-128">Büyük komutlar, birden çok arabellek gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="f4dc1-129">Örneğin, sunucuya büyük bir komut gönderiliyorsa ve altı paket gerektiriyorsa, `ServerRoundtrips` bunlardan biri ile artırılır ve `BuffersSent` altı ile artırılır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="f4dc1-130">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirmişse, SQL Server sağlayıcı tarafından alınan TDS paketlerindeki veri bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="f4dc1-131">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra TDS paketlerindeki SQL Server gönderilen verilerin bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="f4dc1-132">İstatistiklerin etkinleştirildikten sonra bağlantının açıldığı süre (milisaniye cinsinden) (bağlantı açılmadan önce istatistiklerin etkinleştirilmesi durumunda toplam bağlantı süresi).</span><span class="sxs-lookup"><span data-stu-id="f4dc1-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="f4dc1-133">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir imlecin bağlantı üzerinden kaç kez açık olduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="f4dc1-134">SELECT deyimlerinin döndürdüğü salt okuma/iletme sonuçlarının işaretçiler kabul edilmediğini ve bu nedenle bu sayacı etkilemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="f4dc1-135">Sağlayıcıdan alınan yanıtların yanı sıra sağlayıcının kendisindeki kodu çalıştırırken harcanan süre dahil olmak üzere, sağlayıcının, istatistikleri etkinleştirildikten sonra işlem harcadığı süreyi (milisaniye cinsinden) döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="f4dc1-136">Zamanlama kodu içeren sınıflar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f4dc1-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="f4dc1-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="f4dc1-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="f4dc1-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="f4dc1-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="f4dc1-139">Sýnýfý</span><span class="sxs-lookup"><span data-stu-id="f4dc1-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="f4dc1-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="f4dc1-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="f4dc1-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="f4dc1-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="f4dc1-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="f4dc1-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="f4dc1-143">Performans açısından kritik üyeleri mümkün olduğunca küçük tutmak için aşağıdaki Üyeler zaman aşımına uğramaz:</span><span class="sxs-lookup"><span data-stu-id="f4dc1-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="f4dc1-144">Sýnýfý</span><span class="sxs-lookup"><span data-stu-id="f4dc1-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="f4dc1-145">This [] işleci (tüm aşırı yüklemeler)</span><span class="sxs-lookup"><span data-stu-id="f4dc1-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="f4dc1-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="f4dc1-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="f4dc1-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="f4dc1-147">GetChar</span></span><br /><br /> <span data-ttu-id="f4dc1-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="f4dc1-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="f4dc1-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="f4dc1-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="f4dc1-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="f4dc1-150">GetDouble</span></span><br /><br /> <span data-ttu-id="f4dc1-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="f4dc1-151">GetFloat</span></span><br /><br /> <span data-ttu-id="f4dc1-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="f4dc1-152">GetGuid</span></span><br /><br /> <span data-ttu-id="f4dc1-153">Getınt16</span><span class="sxs-lookup"><span data-stu-id="f4dc1-153">GetInt16</span></span><br /><br /> <span data-ttu-id="f4dc1-154">GetInt32</span><span class="sxs-lookup"><span data-stu-id="f4dc1-154">GetInt32</span></span><br /><br /> <span data-ttu-id="f4dc1-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="f4dc1-155">GetInt64</span></span><br /><br /> <span data-ttu-id="f4dc1-156">GetName</span><span class="sxs-lookup"><span data-stu-id="f4dc1-156">GetName</span></span><br /><br /> <span data-ttu-id="f4dc1-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="f4dc1-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="f4dc1-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="f4dc1-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="f4dc1-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="f4dc1-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="f4dc1-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="f4dc1-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="f4dc1-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="f4dc1-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="f4dc1-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="f4dc1-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="f4dc1-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="f4dc1-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="f4dc1-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="f4dc1-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="f4dc1-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="f4dc1-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="f4dc1-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="f4dc1-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="f4dc1-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="f4dc1-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="f4dc1-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="f4dc1-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="f4dc1-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="f4dc1-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="f4dc1-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="f4dc1-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="f4dc1-171">GetString</span><span class="sxs-lookup"><span data-stu-id="f4dc1-171">GetString</span></span><br /><br /> <span data-ttu-id="f4dc1-172">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="f4dc1-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="f4dc1-173">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin toplam sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="f4dc1-174">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin etkilediği toplam satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="f4dc1-175">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklerin etkinleştirildiğinden, sağlayıcının sunucudan yanıt bekletmeyi beklediği toplam süreyi (milisaniye cinsinden) döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="f4dc1-176">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanan komutların sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="f4dc1-177">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla hazırlanan deyimlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="f4dc1-178">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen SELECT deyimlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="f4dc1-179">Bu, imleçlerden satırları almak için Fetch deyimlerini içerir ve sonuna <xref:System.Data.SqlClient.SqlDataReader> ulaşıldığında SELECT deyimlerinin sayısı güncellenir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="f4dc1-180">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra seçilen satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="f4dc1-181">Bu sayaç, SQL deyimleri tarafından oluşturulan ve aslında çağıran tarafından tüketilmemiş olanlar dahil tüm satırları yansıtır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="f4dc1-182">Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucuyu kapatmak sayıyı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="f4dc1-183">Bu, GETIRME deyimleri aracılığıyla imleçler aracılığıyla alınan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="f4dc1-184">Bağlantının sunucuya gönderilme sayısını döndürür ve uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="f4dc1-185">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra kullanılan sonuç kümesi sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="f4dc1-186">Örneğin bu, istemciye döndürülen sonuç kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="f4dc1-187">İmleçler için, her getirme veya engelleme getirme işlemi bağımsız bir sonuç kümesi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="f4dc1-188">Uygulama sağlayıcıyı kullanmaya başladıktan sonra başlatılan kullanıcı işlemleri sayısını döndürür ve geri alma dahil istatistikleri etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="f4dc1-189">Bir bağlantı otomatik işleme ile çalışıyorsa her komut bir işlem olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="f4dc1-190">Bu sayaç, işlemin daha sonra yapılıp yapılmayacağını veya geri döndürülüp döndürülmediğine bakılmaksızın BEGIN TRAN ifadesinin yürütüldüğü anda işlem sayısını artırır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="f4dc1-191">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanmamış deyimlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="f4dc1-192">Değer alma</span><span class="sxs-lookup"><span data-stu-id="f4dc1-192">Retrieving a Value</span></span>  
 <span data-ttu-id="f4dc1-193">Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, dört ayrı istatistiksel değerin nasıl alınacağını ve bunları konsol penceresine nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4dc1-194">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-194">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f4dc1-195">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="f4dc1-196">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-196">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      ' Retrieve a few individual values  
      ' related to the previous command.  
      Dim bytesReceived As Long = _  
          CLng(currentStatistics.Item("BytesReceived"))  
      Dim bytesSent As Long = _  
          CLng(currentStatistics.Item("BytesSent"))  
      Dim selectCount As Long = _  
          CLng(currentStatistics.Item("SelectCount"))  
      Dim selectRows As Long = _  
          CLng(currentStatistics.Item("SelectRows"))  
  
      Console.WriteLine("BytesReceived: " & bytesReceived.ToString())  
      Console.WriteLine("BytesSent: " & bytesSent.ToString())  
      Console.WriteLine("SelectCount: " & selectCount.ToString())  
      Console.WriteLine("SelectRows: " & selectRows.ToString())  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetValue  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =   
          new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
          awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
          currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        // Retrieve a few individual values  
        // related to the previous command.  
        long bytesReceived =  
            (long) currentStatistics["BytesReceived"];  
        long bytesSent =  
            (long) currentStatistics["BytesSent"];  
        long selectCount =  
            (long) currentStatistics["SelectCount"];  
        long selectRows =  
            (long) currentStatistics["SelectRows"];  
  
        Console.WriteLine("BytesReceived: " +  
            bytesReceived.ToString());  
        Console.WriteLine("BytesSent: " +  
            bytesSent.ToString());  
        Console.WriteLine("SelectCount: " +  
            selectCount.ToString());  
        Console.WriteLine("SelectRows: " +  
            selectRows.ToString());  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="f4dc1-197">Tüm değerler alınıyor</span><span class="sxs-lookup"><span data-stu-id="f4dc1-197">Retrieving All Values</span></span>  
 <span data-ttu-id="f4dc1-198">Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, Numaralandırıcının kullanıldığı tüm kullanılabilir istatistik değerlerini almayı ve bunları konsol penceresine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4dc1-199">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-199">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="f4dc1-200">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="f4dc1-201">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-201">Modify the connection string as necessary for your environment.</span></span>  
  
```vb  
Option Strict On  
  
Imports System  
Imports System.Collections  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  Sub Main()  
    Dim connectionString As String = GetConnectionString()  
  
    Using awConnection As New SqlConnection(connectionString)  
      ' StatisticsEnabled is False by default.  
      ' It must be set to True to start the   
      ' statistic collection process.  
      awConnection.StatisticsEnabled = True  
  
      Dim productSQL As String = "SELECT * FROM Production.Product"  
      Dim productAdapter As _  
          New SqlDataAdapter(productSQL, awConnection)  
  
      Dim awDataSet As New DataSet()  
  
      awConnection.Open()  
  
      productAdapter.Fill(awDataSet, "ProductTable")  
  
      ' Retrieve the current statistics as  
      ' a collection of values at this point  
      ' and time.  
      Dim currentStatistics As IDictionary = _  
          awConnection.RetrieveStatistics()  
  
      Console.WriteLine("Total Counters: " & _  
          currentStatistics.Count.ToString())  
      Console.WriteLine()  
  
      Console.WriteLine("Key Name and Value")  
  
      ' Note the entries are unsorted.  
      For Each entry As DictionaryEntry In currentStatistics  
        Console.WriteLine(entry.Key.ToString() & _  
            ": " & entry.Value.ToString())  
      Next  
  
      Console.WriteLine()  
      Console.WriteLine("Press any key to continue")  
      Console.ReadLine()  
    End Using  
  
  End Sub  
  
  Function GetConnectionString() As String  
    ' To avoid storing the connection string in your code,  
    ' you can retrieve it from a configuration file.  
    Return "Data Source=localhost;Integrated Security=SSPI;" & _  
      "Initial Catalog=AdventureWorks"  
  End Function  
End Module  
```  
  
```csharp  
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace CS_Stats_Console_GetAll  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string connectionString = GetConnectionString();  
  
      using (SqlConnection awConnection =   
        new SqlConnection(connectionString))  
      {  
        // StatisticsEnabled is False by default.  
        // It must be set to True to start the   
        // statistic collection process.  
        awConnection.StatisticsEnabled = true;  
  
        string productSQL = "SELECT * FROM Production.Product";  
        SqlDataAdapter productAdapter =  
            new SqlDataAdapter(productSQL, awConnection);  
  
        DataSet awDataSet = new DataSet();  
  
        awConnection.Open();  
  
        productAdapter.Fill(awDataSet, "ProductTable");  
  
        // Retrieve the current statistics as  
        // a collection of values at this point  
        // and time.  
        IDictionary currentStatistics =  
            awConnection.RetrieveStatistics();  
  
        Console.WriteLine("Total Counters: " +  
            currentStatistics.Count.ToString());  
        Console.WriteLine();  
  
        Console.WriteLine("Key Name and Value");  
  
        // Note the entries are unsorted.  
        foreach (DictionaryEntry entry in currentStatistics)  
        {  
          Console.WriteLine(entry.Key.ToString() +  
              ": " + entry.Value.ToString());  
        }  
  
        Console.WriteLine();  
        Console.WriteLine("Press any key to continue");  
        Console.ReadLine();  
      }  
  
    }  
    private static string GetConnectionString()  
    {  
      // To avoid storing the connection string in your code,  
      // you can retrieve it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4dc1-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4dc1-202">See also</span></span>

- [<span data-ttu-id="f4dc1-203">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f4dc1-203">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="f4dc1-204">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f4dc1-204">ADO.NET Overview</span></span>](../ado-net-overview.md)
