---
description: 'Daha fazla bilgi edinin: SQL Server için sağlayıcı Istatistikleri'
title: SQL Server için Sağlayıcı İstatistikleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
ms.openlocfilehash: ece5a6214d438ecac64e8738755d5fb5d0ed7245
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767602"
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="12505-103">SQL Server için Sağlayıcı İstatistikleri</span><span class="sxs-lookup"><span data-stu-id="12505-103">Provider Statistics for SQL Server</span></span>

<span data-ttu-id="12505-104">.NET Framework sürüm 2,0 ' den başlayarak, SQL Server için .NET Framework Veri Sağlayıcısı, çalışma zamanı istatistiklerini destekler.</span><span class="sxs-lookup"><span data-stu-id="12505-104">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="12505-105"><xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> <xref:System.Data.SqlClient.SqlConnection> Geçerli bir Connection nesneniz oluşturulduktan sonra nesnesinin özelliğini ayarlayarak istatistikleri etkinleştirmeniz gerekir `True` .</span><span class="sxs-lookup"><span data-stu-id="12505-105">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="12505-106">İstatistikler etkinleştirildikten sonra, <xref:System.Collections.IDictionary> nesnenin yöntemi aracılığıyla bir başvuru alarak bunları bir "anlık görüntü" olarak gözden geçirebilirsiniz <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> .</span><span class="sxs-lookup"><span data-stu-id="12505-106">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="12505-107">Liste/değer çifti sözlüğü girdileri kümesi olarak listeyi numaralandırın.</span><span class="sxs-lookup"><span data-stu-id="12505-107">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="12505-108">Bu ad/değer çiftleri sırasız.</span><span class="sxs-lookup"><span data-stu-id="12505-108">These name/value pairs are unordered.</span></span> <span data-ttu-id="12505-109">İstediğiniz zaman, <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> <xref:System.Data.SqlClient.SqlConnection> sayaçları sıfırlamak için nesnesinin yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12505-109">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="12505-110">İstatistik toplama etkinleştirilmediyse, bir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="12505-110">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="12505-111">Ayrıca, <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ilki çağrılmadan çağrılırsa, alınan değerler her girdinin başlangıç değerleridir.</span><span class="sxs-lookup"><span data-stu-id="12505-111">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="12505-112">İstatistikleri etkinleştirir, uygulamanızı bir süre için çalıştırın ve sonra istatistikleri devre dışı bırakırsanız, alınan değerler istatistiklerin devre dışı bırakıldığı noktaya kadar toplanan değerleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="12505-112">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="12505-113">Toplanan tüm istatistiksel değerler her bağlantı için yapılır.</span><span class="sxs-lookup"><span data-stu-id="12505-113">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="12505-114">İstatistiksel değerler kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="12505-114">Statistical Values Available</span></span>  

 <span data-ttu-id="12505-115">Şu anda Microsoft SQL Server sağlayıcısından 18 farklı öğe mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="12505-115">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="12505-116">Kullanılabilir öğelerin sayısına  <xref:System.Collections.IDictionary> tarafından döndürülen arabirim başvurusunun Count özelliği aracılığıyla erişilebilir <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> .</span><span class="sxs-lookup"><span data-stu-id="12505-116">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="12505-117">Sağlayıcı istatistikleri için tüm sayaçlar, ortak dil çalışma zamanı <xref:System.Int64> türünü (C# ve Visual Basic **uzun** ) kullanır ve bu 64 bit genişliğinde olur.</span><span class="sxs-lookup"><span data-stu-id="12505-117">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="12505-118">Int64 tarafından tanımlanan en büyük **Int64** veri türü değeri **. MaxValue** alanı ((2 ^ 63)-1)).</span><span class="sxs-lookup"><span data-stu-id="12505-118">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="12505-119">Sayaçların değerleri bu en büyük değere ulaştığında, artık doğru olarak değerlendirilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="12505-119">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="12505-120">Bu, söz konusu int64 anlamına gelir **. MaxValue**-1 ((2 ^ 63)-2), herhangi bir istatistiğin en büyük geçerli değeri etkin değildir.</span><span class="sxs-lookup"><span data-stu-id="12505-120">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12505-121">Döndürülen istatistiklerin sayısı, isimleri ve sırası gelecekte değiştirebileceğinden, sağlayıcı istatistiklerini döndürmek için bir sözlük kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12505-121">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="12505-122">Uygulamalar, sözlükte bulunan belirli bir değere güvenmemelidir, ancak bunun yerine değerin aynı ve uygun olup olmadığını kontrol etmelidir.</span><span class="sxs-lookup"><span data-stu-id="12505-122">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="12505-123">Aşağıdaki tabloda mevcut istatistiksel değerler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12505-123">The following table describes the current statistical values available.</span></span> <span data-ttu-id="12505-124">Tek tek değerler için anahtar adlarının, Microsoft .NET çerçevesinin bölgesel sürümlerinde yerelleştirilmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12505-124">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="12505-125">Anahtar adı</span><span class="sxs-lookup"><span data-stu-id="12505-125">Key Name</span></span>|<span data-ttu-id="12505-126">Description</span><span class="sxs-lookup"><span data-stu-id="12505-126">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="12505-127">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra SQL Server sağlayıcı tarafından alınan tablo veri akışı (TDS) paketlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-127">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="12505-128">İstatistikler etkinleştirildikten sonra sağlayıcı tarafından SQL Server gönderilen TDS paketlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-128">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="12505-129">Büyük komutlar, birden çok arabellek gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="12505-129">Large commands can require multiple buffers.</span></span> <span data-ttu-id="12505-130">Örneğin, sunucuya büyük bir komut gönderiliyorsa ve altı paket gerektiriyorsa, `ServerRoundtrips` bunlardan biri ile artırılır ve `BuffersSent` altı ile artırılır.</span><span class="sxs-lookup"><span data-stu-id="12505-130">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="12505-131">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirmişse, SQL Server sağlayıcı tarafından alınan TDS paketlerindeki veri bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-131">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="12505-132">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra TDS paketlerindeki SQL Server gönderilen verilerin bayt sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-132">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="12505-133">İstatistiklerin etkinleştirildikten sonra bağlantının açıldığı süre (milisaniye cinsinden) (bağlantı açılmadan önce istatistiklerin etkinleştirilmesi durumunda toplam bağlantı süresi).</span><span class="sxs-lookup"><span data-stu-id="12505-133">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="12505-134">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir imlecin bağlantı üzerinden kaç kez açık olduğunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-134">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="12505-135">SELECT deyimlerinin döndürdüğü salt okuma/iletme sonuçlarının işaretçiler kabul edilmediğini ve bu nedenle bu sayacı etkilemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="12505-135">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="12505-136">Sağlayıcıdan alınan yanıtların yanı sıra sağlayıcının kendisindeki kodu çalıştırırken harcanan süre dahil olmak üzere, sağlayıcının, istatistikleri etkinleştirildikten sonra işlem harcadığı süreyi (milisaniye cinsinden) döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-136">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="12505-137">Zamanlama kodu içeren sınıflar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="12505-137">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="12505-138">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="12505-138">SqlConnection</span></span><br /><br /> <span data-ttu-id="12505-139">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="12505-139">SqlCommand</span></span><br /><br /> <span data-ttu-id="12505-140">Sýnýfý</span><span class="sxs-lookup"><span data-stu-id="12505-140">SqlDataReader</span></span><br /><br /> <span data-ttu-id="12505-141">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="12505-141">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="12505-142">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="12505-142">SqlTransaction</span></span><br /><br /> <span data-ttu-id="12505-143">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="12505-143">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="12505-144">Performans açısından kritik üyeleri mümkün olduğunca küçük tutmak için aşağıdaki Üyeler zaman aşımına uğramaz:</span><span class="sxs-lookup"><span data-stu-id="12505-144">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="12505-145">Sýnýfý</span><span class="sxs-lookup"><span data-stu-id="12505-145">SqlDataReader</span></span><br /><br /> <span data-ttu-id="12505-146">This [] işleci (tüm aşırı yüklemeler)</span><span class="sxs-lookup"><span data-stu-id="12505-146">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="12505-147">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="12505-147">GetBoolean</span></span><br /><br /> <span data-ttu-id="12505-148">GetChar</span><span class="sxs-lookup"><span data-stu-id="12505-148">GetChar</span></span><br /><br /> <span data-ttu-id="12505-149">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="12505-149">GetDateTime</span></span><br /><br /> <span data-ttu-id="12505-150">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="12505-150">GetDecimal</span></span><br /><br /> <span data-ttu-id="12505-151">GetDouble</span><span class="sxs-lookup"><span data-stu-id="12505-151">GetDouble</span></span><br /><br /> <span data-ttu-id="12505-152">GetFloat</span><span class="sxs-lookup"><span data-stu-id="12505-152">GetFloat</span></span><br /><br /> <span data-ttu-id="12505-153">GetGuid</span><span class="sxs-lookup"><span data-stu-id="12505-153">GetGuid</span></span><br /><br /> <span data-ttu-id="12505-154">Getınt16</span><span class="sxs-lookup"><span data-stu-id="12505-154">GetInt16</span></span><br /><br /> <span data-ttu-id="12505-155">Getınt32</span><span class="sxs-lookup"><span data-stu-id="12505-155">GetInt32</span></span><br /><br /> <span data-ttu-id="12505-156">GetInt64</span><span class="sxs-lookup"><span data-stu-id="12505-156">GetInt64</span></span><br /><br /> <span data-ttu-id="12505-157">GetName</span><span class="sxs-lookup"><span data-stu-id="12505-157">GetName</span></span><br /><br /> <span data-ttu-id="12505-158">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="12505-158">GetOrdinal</span></span><br /><br /> <span data-ttu-id="12505-159">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="12505-159">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="12505-160">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="12505-160">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="12505-161">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="12505-161">GetSqlByte</span></span><br /><br /> <span data-ttu-id="12505-162">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="12505-162">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="12505-163">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="12505-163">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="12505-164">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="12505-164">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="12505-165">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="12505-165">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="12505-166">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="12505-166">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="12505-167">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="12505-167">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="12505-168">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="12505-168">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="12505-169">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="12505-169">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="12505-170">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="12505-170">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="12505-171">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="12505-171">GetSqlString</span></span><br /><br /> <span data-ttu-id="12505-172">GetString</span><span class="sxs-lookup"><span data-stu-id="12505-172">GetString</span></span><br /><br /> <span data-ttu-id="12505-173">IsDBNull</span><span class="sxs-lookup"><span data-stu-id="12505-173">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="12505-174">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin toplam sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-174">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="12505-175">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklere etkinleştikten sonra bağlantı aracılığıyla yürütülen INSERT, DELETE ve UPDATE deyimlerinin etkilediği toplam satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-175">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="12505-176">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistiklerin etkinleştirildiğinden, sağlayıcının sunucudan yanıt bekletmeyi beklediği toplam süreyi (milisaniye cinsinden) döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-176">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="12505-177">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanan komutların sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-177">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="12505-178">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla hazırlanan deyimlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-178">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="12505-179">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen SELECT deyimlerinin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-179">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="12505-180">Bu, imleçlerden satırları almak için FETCH deyimlerini içerir ve sonuna ulaşıldığında SELECT deyimlerinin sayısı güncellenir <xref:System.Data.SqlClient.SqlDataReader> .</span><span class="sxs-lookup"><span data-stu-id="12505-180">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="12505-181">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra seçilen satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-181">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="12505-182">Bu sayaç, SQL deyimleri tarafından oluşturulan ve aslında çağıran tarafından tüketilmemiş olanlar dahil tüm satırları yansıtır.</span><span class="sxs-lookup"><span data-stu-id="12505-182">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="12505-183">Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucuyu kapatmak sayıyı etkilemez.</span><span class="sxs-lookup"><span data-stu-id="12505-183">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="12505-184">Bu, GETIRME deyimleri aracılığıyla imleçler aracılığıyla alınan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="12505-184">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="12505-185">Bağlantının sunucuya gönderilme sayısını döndürür ve uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bir yanıt gönderir.</span><span class="sxs-lookup"><span data-stu-id="12505-185">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="12505-186">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra kullanılan sonuç kümesi sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-186">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="12505-187">Örneğin bu, istemciye döndürülen sonuç kümesini içerir.</span><span class="sxs-lookup"><span data-stu-id="12505-187">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="12505-188">İmleçler için, her getirme veya engelleme getirme işlemi bağımsız bir sonuç kümesi olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="12505-188">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="12505-189">Uygulama sağlayıcıyı kullanmaya başladıktan sonra başlatılan kullanıcı işlemleri sayısını döndürür ve geri alma dahil istatistikleri etkinleştirdi.</span><span class="sxs-lookup"><span data-stu-id="12505-189">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="12505-190">Bir bağlantı otomatik işleme ile çalışıyorsa her komut bir işlem olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="12505-190">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="12505-191">Bu sayaç, işlemin daha sonra yapılıp yapılmayacağını veya geri döndürülüp döndürülmediğine bakılmaksızın BEGIN TRAN ifadesinin yürütüldüğü anda işlem sayısını artırır.</span><span class="sxs-lookup"><span data-stu-id="12505-191">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="12505-192">Uygulama sağlayıcıyı kullanmaya başladıktan ve istatistikleri etkinleştirdikten sonra bağlantı aracılığıyla yürütülen hazırlanmamış deyimlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="12505-192">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="12505-193">Değer alma</span><span class="sxs-lookup"><span data-stu-id="12505-193">Retrieving a Value</span></span>  

 <span data-ttu-id="12505-194">Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, dört ayrı istatistiksel değerin nasıl alınacağını ve bunları konsol penceresine nasıl yazılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="12505-194">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12505-195">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="12505-195">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="12505-196">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="12505-196">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="12505-197">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12505-197">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
### <a name="retrieving-all-values"></a><span data-ttu-id="12505-198">Tüm değerler alınıyor</span><span class="sxs-lookup"><span data-stu-id="12505-198">Retrieving All Values</span></span>  

 <span data-ttu-id="12505-199">Aşağıdaki konsol uygulaması, bir bağlantı üzerinde istatistiklerin nasıl etkinleştirileceğini, Numaralandırıcının kullanıldığı tüm kullanılabilir istatistik değerlerini almayı ve bunları konsol penceresine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="12505-199">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12505-200">Aşağıdaki örnek, SQL Server eklenen örnek **AdventureWorks** veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="12505-200">The following example uses the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="12505-201">Örnek kodda sağlanan bağlantı dizesi, veritabanının yüklü olduğunu ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="12505-201">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="12505-202">Bağlantı dizesini ortamınız için gereken şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="12505-202">Modify the connection string as necessary for your environment.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="12505-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12505-203">See also</span></span>

- [<span data-ttu-id="12505-204">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="12505-204">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="12505-205">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="12505-205">ADO.NET Overview</span></span>](../ado-net-overview.md)
