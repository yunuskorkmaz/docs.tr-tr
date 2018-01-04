---
title: "SQL Server için sağlayıcı istatistikleri"
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
ms.assetid: 429c9d09-92ac-46ec-829a-fbff0a9575a2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 87f3dfbb3af6e638207d68540217f7134b95c354
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="provider-statistics-for-sql-server"></a><span data-ttu-id="7958b-102">SQL Server için sağlayıcı istatistikleri</span><span class="sxs-lookup"><span data-stu-id="7958b-102">Provider Statistics for SQL Server</span></span>
<span data-ttu-id="7958b-103">.NET Framework sürüm 2.0 ile başlayarak, SQL Server için .NET Framework veri sağlayıcısı çalışma zamanı istatistikleri destekler.</span><span class="sxs-lookup"><span data-stu-id="7958b-103">Starting with the .NET Framework version 2.0, the .NET Framework Data Provider for SQL Server supports run-time statistics.</span></span> <span data-ttu-id="7958b-104">Ayarlayarak istatistikleri etkinleştirmelisiniz <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> nesnesine `True` oluşturulan geçerli bir bağlantı nesnesi sonra.</span><span class="sxs-lookup"><span data-stu-id="7958b-104">You must enable statistics by setting the <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> property of the <xref:System.Data.SqlClient.SqlConnection> object to `True` after you have a valid connection object created.</span></span> <span data-ttu-id="7958b-105">İstatistikleri etkinleştirildikten sonra bunları "anlık görüntü olarak zaman içinde" alarak gözden geçirebilirsiniz bir <xref:System.Collections.IDictionary> aracılığıyla başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="7958b-105">After statistics are enabled, you can review them as a "snapshot in time" by retrieving an <xref:System.Collections.IDictionary> reference via the <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="7958b-106">Ad/değer çifti dictionary girişlerinin bir dizi listesini numaralandırır.</span><span class="sxs-lookup"><span data-stu-id="7958b-106">You enumerate through the list as a set of name/value pair dictionary entries.</span></span> <span data-ttu-id="7958b-107">Bu ad/değer çiftleri sırasız şunlardır.</span><span class="sxs-lookup"><span data-stu-id="7958b-107">These name/value pairs are unordered.</span></span> <span data-ttu-id="7958b-108">Herhangi bir zamanda çağırabilirsiniz <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> yöntemi <xref:System.Data.SqlClient.SqlConnection> sayaçları sıfırlamak için nesne.</span><span class="sxs-lookup"><span data-stu-id="7958b-108">At any time, you can call the <xref:System.Data.SqlClient.SqlConnection.ResetStatistics%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to reset the counters.</span></span> <span data-ttu-id="7958b-109">Toplama istatistiği etkin değil, bir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="7958b-109">If statistic gathering has not been enabled, an exception is not generated.</span></span> <span data-ttu-id="7958b-110">Ayrıca, varsa <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> olmadan adlı <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> ilk çağrılmış alınan her giriş için başlangıç değerlerini değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7958b-110">In addition, if <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A> is called without <xref:System.Data.SqlClient.SqlConnection.StatisticsEnabled%2A> having been called first, the values retrieved are the initial values for each entry.</span></span> <span data-ttu-id="7958b-111">İstatistikleri etkinleştirirseniz, bir süre için uygulamanızı çalıştırın ve istatistikleri devre dışı bırakmak, alınan değerleri nerede istatistikleri devre dışı bırakılan noktaya kadar toplanan değerleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7958b-111">If you enable statistics, run your application for a while, and then disable statistics, the values retrieved will reflect the values collected up to the point where statistics were disabled.</span></span> <span data-ttu-id="7958b-112">Toplanan tüm istatistiksel bir bağlantı başına temelinde değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="7958b-112">All statistical values gathered are on a per-connection basis.</span></span>  
  
## <a name="statistical-values-available"></a><span data-ttu-id="7958b-113">İstatistiksel kullanılabilir değerler</span><span class="sxs-lookup"><span data-stu-id="7958b-113">Statistical Values Available</span></span>  
 <span data-ttu-id="7958b-114">Şu anda 18 farklı öğeler Microsoft SQL Server sağlayıcıdan kullanılabilir yok.</span><span class="sxs-lookup"><span data-stu-id="7958b-114">Currently there are 18 different items available from the Microsoft SQL Server provider.</span></span> <span data-ttu-id="7958b-115">Kullanılabilir öğelerin sayısı üzerinden erişilen **sayısı** özelliği <xref:System.Collections.IDictionary> arabirim tarafından döndürülen başvuru <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span><span class="sxs-lookup"><span data-stu-id="7958b-115">The number of items available can be accessed via the **Count** property of the <xref:System.Collections.IDictionary> interface reference returned by <xref:System.Data.SqlClient.SqlConnection.RetrieveStatistics%2A>.</span></span> <span data-ttu-id="7958b-116">Tüm sayaçları sağlayıcı istatistikler için ortak dil çalışma zamanı kullanmak <xref:System.Int64> türü (**uzun** C# ve Visual Basic), 64 bit uzunluğunda olduğunu.</span><span class="sxs-lookup"><span data-stu-id="7958b-116">All of the counters for provider statistics use the common language runtime <xref:System.Int64> type (**long** in C# and Visual Basic), which is 64 bits wide.</span></span> <span data-ttu-id="7958b-117">En büyük değerini **Int64** tarafından tanımlanan veri türü, **Int64. MaxValue** alan, ((2^63)-1.)).</span><span class="sxs-lookup"><span data-stu-id="7958b-117">The maximum value of the **int64** data type, as defined by the **int64.MaxValue** field, is ((2^63)-1)).</span></span> <span data-ttu-id="7958b-118">Sayaç değerlerini bu en büyük değer ulaştığında, bunlar artık doğru dikkate alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7958b-118">When the values for the counters reach this maximum value, they should no longer be considered accurate.</span></span> <span data-ttu-id="7958b-119">Bunun anlamı **Int64. MaxValue**-1((2^63)-2) olan etkili bir şekilde tüm istatistiği için geçerli en büyük değer.</span><span class="sxs-lookup"><span data-stu-id="7958b-119">This means that **int64.MaxValue**-1((2^63)-2) is effectively the greatest valid value for any statistic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7958b-120">Bir sözlük sayısı, adları ve döndürülen istatistikleri sırasını gelecekte değişebilir çünkü sağlayıcı istatistikleri döndürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7958b-120">A dictionary is used for returning provider statistics because the number, names and order of the returned statistics may change in the future.</span></span> <span data-ttu-id="7958b-121">Uygulamaları sözlükte bulunan belirli bir değerin güvenmemelisiniz, ancak bunun yerine değeri vardır ve buna göre dal denetlemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="7958b-121">Applications should not rely on a specific value being found in the dictionary, but should instead check whether the value is there and branch accordingly.</span></span>  
  
 <span data-ttu-id="7958b-122">Aşağıdaki tabloda kullanılabilir geçerli istatistiksel değerleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7958b-122">The following table describes the current statistical values available.</span></span> <span data-ttu-id="7958b-123">Bölgesel Microsoft .NET Framework sürümleri arasında değerlerini ayrı ayrı anahtar adları yerelleştirilmiş değil unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7958b-123">Note that the key names for the individual values are not localized across regional versions of the Microsoft .NET Framework.</span></span>  
  
|<span data-ttu-id="7958b-124">Anahtar adı</span><span class="sxs-lookup"><span data-stu-id="7958b-124">Key Name</span></span>|<span data-ttu-id="7958b-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7958b-125">Description</span></span>|  
|--------------|-----------------|  
|`BuffersReceived`|<span data-ttu-id="7958b-126">Tablo veri akışı (TDS) paketleri uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sağlayıcının SQL Server tarafından alınan döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-126">Returns the number of tabular data stream (TDS) packets received by the provider from SQL Server after the application has started using the provider and has enabled statistics.</span></span>|  
|`BuffersSent`|<span data-ttu-id="7958b-127">İstatistikleri etkinleştirdikten sonra SQL Server'a sağlayıcı tarafından gönderilen TDS paketlerin sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-127">Returns the number of TDS packets sent to SQL Server by the provider after statistics have been enabled.</span></span> <span data-ttu-id="7958b-128">Büyük komutları birden çok arabellek gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="7958b-128">Large commands can require multiple buffers.</span></span> <span data-ttu-id="7958b-129">Örneğin, büyük bir komut sunucuya gönderilir ve altı paketleri gerektiriyorsa `ServerRoundtrips` bir artırılır ve `BuffersSent` altı tarafından artırılır.</span><span class="sxs-lookup"><span data-stu-id="7958b-129">For example, if a large command is sent to the server and it requires six packets, `ServerRoundtrips` is incremented by one and `BuffersSent` is incremented by six.</span></span>|  
|`BytesReceived`|<span data-ttu-id="7958b-130">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra SQL Server'ın sağlayıcısı tarafından alınan TDS paketlerde veri baytlarının miktarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-130">Returns the number of bytes of data in the TDS packets received by the provider from SQL Server once the application has started using the provider and has enabled statistics.</span></span>|  
|`BytesSent`|<span data-ttu-id="7958b-131">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra SQL Server'a TDS paketlerinde gönderilen veri baytı sayısı sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-131">Returns the number of bytes of data sent to SQL Server in TDS packets after the application has started using the provider and has enabled statistics.</span></span>|  
|`ConnectionTime`|<span data-ttu-id="7958b-132">Bağlantı kaldırıldı süre (milisaniye olarak) miktarını istatistikleri etkinleştirdikten sonra açılan (toplam bağlantı süresi istatistikleri bağlantı açmadan önce etkinleştirilmişse).</span><span class="sxs-lookup"><span data-stu-id="7958b-132">The amount of time (in milliseconds) that the connection has been opened after statistics have been enabled (total connection time if statistics were enabled before opening the connection).</span></span>|  
|`CursorOpens`|<span data-ttu-id="7958b-133">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bir imleç bağlantı üzerinden açık sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-133">Returns the number of times a cursor was open through the connection once the application has started using the provider and has enabled statistics.</span></span><br /><br /> <span data-ttu-id="7958b-134">SELECT deyimleri tarafından döndürülen yalnızca/ileri-salt okunur sonuçları imleçler dikkate alınmaz ve bu nedenle bu sayaç etkilemez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7958b-134">Note that read-only/forward-only results returned by SELECT statements are not considered cursors and thus do not affect this counter.</span></span>|  
|`ExecutionTime`|<span data-ttu-id="7958b-135">Toplam süreyi (milisaniye cinsinden) sağlayıcı istatistikleri etkinleştirildikten sonra işleme harcanan, saatin yanı sıra, sunucunun yanıt beklerken harcanan süre dahil olmak üzere sağlayıcı kod çalıştırırken harcadığı döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-135">Returns the cumulative amount of time (in milliseconds) that the provider has spent processing once statistics have been enabled, including the time spent waiting for replies from the server as well as the time spent executing code in the provider itself.</span></span><br /><br /> <span data-ttu-id="7958b-136">Zamanlama kod dahil sınıfları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7958b-136">The classes that include timing code are:</span></span><br /><br /> <span data-ttu-id="7958b-137">SqlConnection</span><span class="sxs-lookup"><span data-stu-id="7958b-137">SqlConnection</span></span><br /><br /> <span data-ttu-id="7958b-138">SqlCommand</span><span class="sxs-lookup"><span data-stu-id="7958b-138">SqlCommand</span></span><br /><br /> <span data-ttu-id="7958b-139">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="7958b-139">SqlDataReader</span></span><br /><br /> <span data-ttu-id="7958b-140">SqlDataAdapter</span><span class="sxs-lookup"><span data-stu-id="7958b-140">SqlDataAdapter</span></span><br /><br /> <span data-ttu-id="7958b-141">SqlTransaction</span><span class="sxs-lookup"><span data-stu-id="7958b-141">SqlTransaction</span></span><br /><br /> <span data-ttu-id="7958b-142">SqlCommandBuilder</span><span class="sxs-lookup"><span data-stu-id="7958b-142">SqlCommandBuilder</span></span><br /><br /> <span data-ttu-id="7958b-143">Performans açısından kritik üyeleri olabildiğince küçük tutmak için aşağıdaki üyeleri zamanlanır değil:</span><span class="sxs-lookup"><span data-stu-id="7958b-143">To keep performance-critical members as small as possible, the following members are not timed:</span></span><br /><br /> <span data-ttu-id="7958b-144">SqlDataReader</span><span class="sxs-lookup"><span data-stu-id="7958b-144">SqlDataReader</span></span><br /><br /> <span data-ttu-id="7958b-145">Bu [] işleci (tüm aşırı)</span><span class="sxs-lookup"><span data-stu-id="7958b-145">this[] operator (all overloads)</span></span><br /><br /> <span data-ttu-id="7958b-146">GetBoolean</span><span class="sxs-lookup"><span data-stu-id="7958b-146">GetBoolean</span></span><br /><br /> <span data-ttu-id="7958b-147">GetChar</span><span class="sxs-lookup"><span data-stu-id="7958b-147">GetChar</span></span><br /><br /> <span data-ttu-id="7958b-148">GetDateTime</span><span class="sxs-lookup"><span data-stu-id="7958b-148">GetDateTime</span></span><br /><br /> <span data-ttu-id="7958b-149">GetDecimal</span><span class="sxs-lookup"><span data-stu-id="7958b-149">GetDecimal</span></span><br /><br /> <span data-ttu-id="7958b-150">GetDouble</span><span class="sxs-lookup"><span data-stu-id="7958b-150">GetDouble</span></span><br /><br /> <span data-ttu-id="7958b-151">GetFloat</span><span class="sxs-lookup"><span data-stu-id="7958b-151">GetFloat</span></span><br /><br /> <span data-ttu-id="7958b-152">GetGuid</span><span class="sxs-lookup"><span data-stu-id="7958b-152">GetGuid</span></span><br /><br /> <span data-ttu-id="7958b-153">Getınt16</span><span class="sxs-lookup"><span data-stu-id="7958b-153">GetInt16</span></span><br /><br /> <span data-ttu-id="7958b-154">Getınt32</span><span class="sxs-lookup"><span data-stu-id="7958b-154">GetInt32</span></span><br /><br /> <span data-ttu-id="7958b-155">GetInt64</span><span class="sxs-lookup"><span data-stu-id="7958b-155">GetInt64</span></span><br /><br /> <span data-ttu-id="7958b-156">GetName</span><span class="sxs-lookup"><span data-stu-id="7958b-156">GetName</span></span><br /><br /> <span data-ttu-id="7958b-157">GetOrdinal</span><span class="sxs-lookup"><span data-stu-id="7958b-157">GetOrdinal</span></span><br /><br /> <span data-ttu-id="7958b-158">GetSqlBinary</span><span class="sxs-lookup"><span data-stu-id="7958b-158">GetSqlBinary</span></span><br /><br /> <span data-ttu-id="7958b-159">GetSqlBoolean</span><span class="sxs-lookup"><span data-stu-id="7958b-159">GetSqlBoolean</span></span><br /><br /> <span data-ttu-id="7958b-160">GetSqlByte</span><span class="sxs-lookup"><span data-stu-id="7958b-160">GetSqlByte</span></span><br /><br /> <span data-ttu-id="7958b-161">GetSqlDateTime</span><span class="sxs-lookup"><span data-stu-id="7958b-161">GetSqlDateTime</span></span><br /><br /> <span data-ttu-id="7958b-162">GetSqlDecimal</span><span class="sxs-lookup"><span data-stu-id="7958b-162">GetSqlDecimal</span></span><br /><br /> <span data-ttu-id="7958b-163">GetSqlDouble</span><span class="sxs-lookup"><span data-stu-id="7958b-163">GetSqlDouble</span></span><br /><br /> <span data-ttu-id="7958b-164">GetSqlGuid</span><span class="sxs-lookup"><span data-stu-id="7958b-164">GetSqlGuid</span></span><br /><br /> <span data-ttu-id="7958b-165">GetSqlInt16</span><span class="sxs-lookup"><span data-stu-id="7958b-165">GetSqlInt16</span></span><br /><br /> <span data-ttu-id="7958b-166">GetSqlInt32</span><span class="sxs-lookup"><span data-stu-id="7958b-166">GetSqlInt32</span></span><br /><br /> <span data-ttu-id="7958b-167">GetSqlInt64</span><span class="sxs-lookup"><span data-stu-id="7958b-167">GetSqlInt64</span></span><br /><br /> <span data-ttu-id="7958b-168">GetSqlMoney</span><span class="sxs-lookup"><span data-stu-id="7958b-168">GetSqlMoney</span></span><br /><br /> <span data-ttu-id="7958b-169">GetSqlSingle</span><span class="sxs-lookup"><span data-stu-id="7958b-169">GetSqlSingle</span></span><br /><br /> <span data-ttu-id="7958b-170">GetSqlString</span><span class="sxs-lookup"><span data-stu-id="7958b-170">GetSqlString</span></span><br /><br /> <span data-ttu-id="7958b-171">GetString</span><span class="sxs-lookup"><span data-stu-id="7958b-171">GetString</span></span><br /><br /> <span data-ttu-id="7958b-172">IsDbNull</span><span class="sxs-lookup"><span data-stu-id="7958b-172">IsDBNull</span></span>|  
|`IduCount`|<span data-ttu-id="7958b-173">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen ekleme, silme ve güncelleştirme deyimleri toplam sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-173">Returns the total number of INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`IduRows`|<span data-ttu-id="7958b-174">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen ekleme, silme ve güncelleştirme deyimleri tarafından etkilenen satırların toplam sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-174">Returns the total number of rows affected by INSERT, DELETE, and UPDATE statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`NetworkServerTime`|<span data-ttu-id="7958b-175">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sağlayıcının'ın sunucudan yanıt beklerken harcanan süre (milisaniye cinsinden) toplu miktarını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-175">Returns the cumulative amount of time (in milliseconds) that the provider spent waiting for replies from the server once the application has started using the provider and has enabled statistics.</span></span>|  
|`PreparedExecs`|<span data-ttu-id="7958b-176">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlıklı komutlarını sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-176">Returns the number of prepared commands executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`Prepares`|<span data-ttu-id="7958b-177">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden prepared deyimleri sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-177">Returns the number of statements prepared through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
|`SelectCount`|<span data-ttu-id="7958b-178">SELECT deyimi sonra uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkin olduğundan bağlantı üzerinden yürütülen sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-178">Returns the number of SELECT statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7958b-179">Bu imleçler satır almak için FETCH deyimleri içerir ve SELECT deyimi için sayısı güncelleştirilir zaman sonuna bir <xref:System.Data.SqlClient.SqlDataReader> ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="7958b-179">This includes FETCH statements to retrieve rows from cursors, and the count for SELECT statements is updated when the end of a <xref:System.Data.SqlClient.SqlDataReader> is reached.</span></span>|  
|`SelectRows`|<span data-ttu-id="7958b-180">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra seçilen satır sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-180">Returns the number of rows selected once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7958b-181">Bu sayaç, aslında çağıran tarafından tüketilmeyen olanlar bile SQL deyimleri tarafından oluşturulan tüm satırları yansıtır.</span><span class="sxs-lookup"><span data-stu-id="7958b-181">This counter reflects all the rows generated by SQL statements, even those that were not actually consumed by the caller.</span></span> <span data-ttu-id="7958b-182">Örneğin, tüm sonuç kümesini okumadan önce bir veri okuyucu kapatma sayısı onaydan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="7958b-182">For example, closing a data reader before reading the entire result set would not affect the count.</span></span> <span data-ttu-id="7958b-183">Bu, imleçler FETCH deyimlerinin üzerinden alınan satırları içerir.</span><span class="sxs-lookup"><span data-stu-id="7958b-183">This includes the rows retrieved from cursors through FETCH statements.</span></span>|  
|`ServerRoundtrips`|<span data-ttu-id="7958b-184">Bağlantının komutları ve sunucuya gönderilen ve uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bir yanıtı geri alındı sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-184">Returns the number of times the connection sent commands to the server and got a reply back once the application has started using the provider and has enabled statistics.</span></span>|  
|`SumResultSets`|<span data-ttu-id="7958b-185">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra sonuç sayısını ayarlar veya döndürür kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="7958b-185">Returns the number of result sets that have been used once the application has started using the provider and has enabled statistics.</span></span> <span data-ttu-id="7958b-186">Bu istemciye döndürülen herhangi bir sonuç kümesi örneğin içerir.</span><span class="sxs-lookup"><span data-stu-id="7958b-186">For example this would include any result set returned to the client.</span></span> <span data-ttu-id="7958b-187">İmleçler için her getirme veya blok getirme işlemi bağımsız sonuç kümesi olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7958b-187">For cursors, each fetch or block-fetch operation is considered an independent result set.</span></span>|  
|`Transactions`|<span data-ttu-id="7958b-188">Uygulama sağlayıcısını kullanarak başlatıldığından ve istatistikler, geri alma dahil olmak üzere etkinleştirilmiş bir kez başlatılan kullanıcı işlemleri sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-188">Returns the number of user transactions started once the application has started using the provider and has enabled statistics, including rollbacks.</span></span> <span data-ttu-id="7958b-189">Bağlantı otomatik tamamlama üzerinde çalışıyorsa, her komutun bir işlem olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="7958b-189">If a connection is running with auto commit on, each command is considered a transaction.</span></span><br /><br /> <span data-ttu-id="7958b-190">Olup işlem yürütülmeli veya geri daha sonra bağımsız olarak başlamak TRAN deyimine yürütüldükten hemen sonra Bu sayaç işlem sayısını artırır.</span><span class="sxs-lookup"><span data-stu-id="7958b-190">This counter increments the transaction count as soon as a BEGIN TRAN statement is executed, regardless of whether the transaction is committed or rolled back later.</span></span>|  
|`UnpreparedExecs`|<span data-ttu-id="7958b-191">Uygulama sağlayıcısını kullanarak başlatıldı ve istatistikleri etkinleştirilmiş sonra bağlantı üzerinden yürütülen hazırlıksız deyimleri sayısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="7958b-191">Returns the number of unprepared statements executed through the connection once the application has started using the provider and has enabled statistics.</span></span>|  
  
### <a name="retrieving-a-value"></a><span data-ttu-id="7958b-192">Bir değer alma</span><span class="sxs-lookup"><span data-stu-id="7958b-192">Retrieving a Value</span></span>  
 <span data-ttu-id="7958b-193">Aşağıdaki konsol uygulaması, bir bağlantı istatistiklerle etkinleştirmek, dört tekil istatistik değerleri almak ve konsol penceresine yazamadı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7958b-193">The following console application shows how to enable statistics on a connection, retrieve four individual statistic values, and write them out to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7958b-194">Aşağıdaki örnek, örnek kullanır **AdventureWorks** ile birlikte gelen veritabanı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7958b-194">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7958b-195">Örnek kodda sağlanan bağlantı dizesi veritabanına yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7958b-195">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="7958b-196">Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7958b-196">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
### <a name="retrieving-all-values"></a><span data-ttu-id="7958b-197">Tüm değerleri alma</span><span class="sxs-lookup"><span data-stu-id="7958b-197">Retrieving All Values</span></span>  
 <span data-ttu-id="7958b-198">Aşağıdaki konsol uygulaması, bir bağlantı istatistiklerle etkinleştirmek, numaralandırıcı kullanarak tüm kullanılabilir istatistik değerleri almak ve konsol penceresine yazma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7958b-198">The following console application shows how to enable statistics on a connection, retrieve all available statistic values using the enumerator, and write them to the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7958b-199">Aşağıdaki örnek, örnek kullanır **AdventureWorks** ile birlikte gelen veritabanı [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7958b-199">The following example uses the sample **AdventureWorks** database included with [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="7958b-200">Örnek kodda sağlanan bağlantı dizesi veritabanına yüklenir ve yerel bilgisayarda kullanılabilir olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7958b-200">The connection string provided in the sample code assumes the database is installed and available on the local computer.</span></span> <span data-ttu-id="7958b-201">Bağlantı dizesi, ortamınız için gerektiği gibi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7958b-201">Modify the connection string as necessary for your environment.</span></span>  
  
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
    ' you can retrive it from a configuration file.  
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
      // you can retrive it from a configuration file.  
      return "Data Source=localhost;Integrated Security=SSPI;" +   
        "Initial Catalog=AdventureWorks";  
    }  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7958b-202">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7958b-202">See Also</span></span>  
 [<span data-ttu-id="7958b-203">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7958b-203">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="7958b-204">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="7958b-204">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
