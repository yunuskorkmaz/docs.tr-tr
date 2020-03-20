---
title: Tarih ve Saat Verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: d7a016b8911cee3091dec24bc26d1f1965f54749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148770"
---
# <a name="date-and-time-data"></a><span data-ttu-id="b1f00-102">Tarih ve Saat Verileri</span><span class="sxs-lookup"><span data-stu-id="b1f00-102">Date and Time Data</span></span>
<span data-ttu-id="b1f00-103">SQL Server 2008 tarih ve saat bilgilerini işlemek için yeni veri türleri sunar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="b1f00-104">Yeni veri türleri, tarih ve saat için ayrı türler ve daha geniş aralık, kesinlik ve saat dilimi farkındalığı yla genişletilmiş veri türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="b1f00-105">.NET Framework sürüm 3.5 Service Pack (SP) 1 ile başlayan SQL<xref:System.Data.SqlClient>Server için .NET Framework Data Provider ( ) SQL Server 2008 Veritabanı Motoru'nun tüm yeni özellikleri için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="b1f00-106">SqlClient ile bu yeni özellikleri kullanmak için .NET Framework 3.5 SP1 (veya sonraki) yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="b1f00-107">SQL Server 2008'den önceki SQL Server sürümlerinde tarih ve saat `datetime` `smalldatetime`değerleriyle çalışmak için yalnızca iki veri türü vardı: ve .</span><span class="sxs-lookup"><span data-stu-id="b1f00-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="b1f00-108">Bu veri türlerinin her ikisi de hem tarih değeri hem de bir saat değeri içerir, bu da yalnızca tarih veya yalnızca saat değerleriyle çalışmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="b1f00-109">Ayrıca, bu veri türleri yalnızca 1753 yılında İngiltere'de Gregoryen takviminin piyasaya sürülmesinden sonra oluşan tarihleri destekler.</span><span class="sxs-lookup"><span data-stu-id="b1f00-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="b1f00-110">Başka bir sınırlama, bu eski veri türlerinin saat dilimi farkında olmamasıdır, bu da birden çok saat diliminden kaynaklanan verilerle çalışmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="b1f00-111">SQL Server veri türleri için eksiksiz belgeler SQL Server Books Online'da mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b1f00-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="b1f00-112">Aşağıdaki tabloda, tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listeleneb.r.</span><span class="sxs-lookup"><span data-stu-id="b1f00-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="b1f00-113">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="b1f00-113">**SQL Server documentation**</span></span>  
  
1. <span data-ttu-id="b1f00-114">[Tarih ve Saat Verilerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="b1f00-114">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="b1f00-115">SQL Server 2008'de Tanıtılan Tarih/Saat Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="b1f00-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="b1f00-116">Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="b1f00-117">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="b1f00-117">SQL Server data type</span></span>|<span data-ttu-id="b1f00-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f00-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="b1f00-119">Veri `date` türü 1 gün doğruluk ile 31 Aralık 9999 1 Ocak 01 ile 9999 bir dizi vardır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="b1f00-120">Varsayılan değer 1 Ocak 1900'dür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="b1f00-121">Depolama boyutu 3 bayt.</span><span class="sxs-lookup"><span data-stu-id="b1f00-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="b1f00-122">Veri `time` türü, 24 saatlik bir saate bağlı olarak yalnızca zaman değerlerini depolar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="b1f00-123">Veri `time` türü 100 nanosaniye doğruluk ile 23:59:59:99999999 00:00:0000000 00:00.0000000 bir dizi vardır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="b1f00-124">Varsayılan değer 00:00:00.0000000 (gece yarısı) olur.</span><span class="sxs-lookup"><span data-stu-id="b1f00-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="b1f00-125">`time` Veri türü kullanıcı tanımlı kısmi ikinci kesinliği destekler ve depolama boyutu belirtilen duyarlıkbağlı olarak 3 ile 6 bayt arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="b1f00-126">Veri `datetime2` türü, ve veri türlerinin `date` `time` aralığını ve kesinliğini tek bir veri türünde birleştirir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="b1f00-127">Varsayılan değerler ve dize gerçek biçimleri, `date` `time` veri türlerinde tanımlananlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="b1f00-128">Veri `datetimeoffset` türü ek bir `datetime2` saat dilimi mahsup ile tüm özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="b1f00-129">Saat dilimi mahsulü [+&#124;-] HH:MM olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="b1f00-130">HH, saat dilimi mahsupundaki saat sayısını temsil eden 00 ile 14 arasında değişen 2 basamaktır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="b1f00-131">MM, saat dilimi mahsupundaki ek dakika sayısını temsil eden 00 ile 59 arasında değişen 2 basamaktır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="b1f00-132">Zaman biçimleri 100 nanosaniye ye desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="b1f00-133">Zorunlu + veya - işareti, yerel saati elde etmek için saat dilimi mahsulünün UTC'den (Evrensel Zaman Koordinatı veya Greenwich Ortalama Saati) eklenip eklenmediğini veya çıkarılıp çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b1f00-134">Anahtar kelimeyi `Type System Version` kullanma hakkında daha <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>fazla bilgi için bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="b1f00-135">Tarih Biçimi ve Tarih Sırası</span><span class="sxs-lookup"><span data-stu-id="b1f00-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="b1f00-136">SQL Server'ın tarih ve saat değerlerini nasıl ayrıştırdığı yalnızca tür sistemi sürümüne ve sunucu sürümüne değil, aynı zamanda sunucunun varsayılan dil ve biçim ayarlarına da bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="b1f00-137">Sorgu farklı bir dil ve tarih biçimi ayarı kullanan bir bağlantı tarafından yürütülürse, bir dilin tarih biçimleri için çalışan bir tarih dizesi tanınmaz olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="b1f00-138">Transact-SQL SET LANGUAGE deyimi, tarih parçalarının sırasını belirleyen DATEFORMAT'ı zımni olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="b1f00-139">MDY, DMY, YMD, YDM, MYD veya DYM siparişindeki tarih parçalarını sıralayarak, disambiguate tarih değerlerine bağlantı da SET DATEFORMAT Transact-SQL deyimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="b1f00-140">Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantıyla ilişkili varsayılan dili kullanır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="b1f00-141">Örneğin, '01/02/03' tarih dizesi, ABD İngilizcesi dil ayarlı bir sunucuda MDY (2 Ocak 2003) ve İngiliz İngilizcesi dil ayarlı bir sunucuda DMY (1 Şubat 2003) olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="b1f00-142">Yıl, sql server'ın yüzyıl değerini atamak için kesme tarihini tanımlayan kesme yılı kuralı kullanılarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="b1f00-143">Daha fazla bilgi için [iki basamaklı yıl kesme Seçeneği'ne](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option)bakın.</span><span class="sxs-lookup"><span data-stu-id="b1f00-143">For more information, see [two digit year cutoff Option](/sql/database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1f00-144">YDM tarih biçimi, dize `date`biçiminden , , `time` `datetime2`veya `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="b1f00-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="b1f00-145">SQL Server'ın tarih ve saat verilerini nasıl yorumladığı hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="b1f00-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100)).</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="b1f00-146">Tarih/Saat Veri Türleri ve Parametreleri</span><span class="sxs-lookup"><span data-stu-id="b1f00-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="b1f00-147">Yeni tarih ve saat veri <xref:System.Data.SqlDbType> türlerini desteklemek için aşağıdaki eklemeler eklendi.</span><span class="sxs-lookup"><span data-stu-id="b1f00-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="b1f00-148">Önceki <xref:System.Data.SqlDbType> tümumerasyonlardan <xref:System.Data.SqlClient.SqlParameter> birini kullanarak a'nın veri türünü belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span>

> [!NOTE]
> <span data-ttu-id="b1f00-149">Bir `DbType` `SqlParameter` özelliği ni 'ye `SqlDbType.Date`ayarlayamazsınız.</span><span class="sxs-lookup"><span data-stu-id="b1f00-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="b1f00-150">Ayrıca, bir nesnenin <xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> özelliğini belirli `SqlParameter` <xref:System.Data.DbType> bir numaralandırma değerine ayarlayarak genel olarak bir tür belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="b1f00-151">Veri türlerini desteklemek <xref:System.Data.DbType> `datetime2` `datetimeoffset` için aşağıdaki numaralandırma değerleri eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="b1f00-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="b1f00-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="b1f00-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="b1f00-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="b1f00-154">Bu yeni sayılar,.NET Framework'ün `Date`önceki sürümlerinde bulunan , `Time`ve `DateTime` sayılmaları tamamlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b1f00-155">Bir parametre nesnesinin .NET Framework veri sağlayıcısı türü, parametre nesnesinin değerinin .NET Framework türünden veya parametre `DbType` nesnesinin değerinden çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="b1f00-156">Yeni <xref:System.Data.SqlTypes> tarih ve saat veri türlerini desteklemek için yeni veri türleri kullanılmadı.</span><span class="sxs-lookup"><span data-stu-id="b1f00-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="b1f00-157">Aşağıdaki tabloda SQL Server 2008 tarih ve saat veri türleri ile CLR veri türleri arasındaki eşlemeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="b1f00-158">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="b1f00-158">SQL Server data type</span></span>|<span data-ttu-id="b1f00-159">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="b1f00-159">.NET Framework type</span></span>|<span data-ttu-id="b1f00-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="b1f00-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="b1f00-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="b1f00-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="b1f00-162">date</span><span class="sxs-lookup"><span data-stu-id="b1f00-162">date</span></span>|<span data-ttu-id="b1f00-163">Datetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-163">System.DateTime</span></span>|<span data-ttu-id="b1f00-164">Tarih</span><span class="sxs-lookup"><span data-stu-id="b1f00-164">Date</span></span>|<span data-ttu-id="b1f00-165">Tarih</span><span class="sxs-lookup"><span data-stu-id="b1f00-165">Date</span></span>|  
|<span data-ttu-id="b1f00-166">time</span><span class="sxs-lookup"><span data-stu-id="b1f00-166">time</span></span>|<span data-ttu-id="b1f00-167">Timespan</span><span class="sxs-lookup"><span data-stu-id="b1f00-167">System.TimeSpan</span></span>|<span data-ttu-id="b1f00-168">Zaman</span><span class="sxs-lookup"><span data-stu-id="b1f00-168">Time</span></span>|<span data-ttu-id="b1f00-169">Zaman</span><span class="sxs-lookup"><span data-stu-id="b1f00-169">Time</span></span>|  
|<span data-ttu-id="b1f00-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="b1f00-170">datetime2</span></span>|<span data-ttu-id="b1f00-171">Datetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-171">System.DateTime</span></span>|<span data-ttu-id="b1f00-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="b1f00-172">DateTime2</span></span>|<span data-ttu-id="b1f00-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="b1f00-173">DateTime2</span></span>|  
|<span data-ttu-id="b1f00-174">Datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-174">datetimeoffset</span></span>|<span data-ttu-id="b1f00-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-175">System.DateTimeOffset</span></span>|<span data-ttu-id="b1f00-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-176">DateTimeOffset</span></span>|<span data-ttu-id="b1f00-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="b1f00-178">datetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-178">datetime</span></span>|<span data-ttu-id="b1f00-179">Datetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-179">System.DateTime</span></span>|<span data-ttu-id="b1f00-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-180">DateTime</span></span>|<span data-ttu-id="b1f00-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-181">DateTime</span></span>|  
|<span data-ttu-id="b1f00-182">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-182">smalldatetime</span></span>|<span data-ttu-id="b1f00-183">Datetime</span><span class="sxs-lookup"><span data-stu-id="b1f00-183">System.DateTime</span></span>|<span data-ttu-id="b1f00-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-184">DateTime</span></span>|<span data-ttu-id="b1f00-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="b1f00-186">SqlParameter Özellikleri</span><span class="sxs-lookup"><span data-stu-id="b1f00-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="b1f00-187">Aşağıdaki tabloda `SqlParameter` tarih ve saat veri türleri ile ilgili özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="b1f00-188">Özellik</span><span class="sxs-lookup"><span data-stu-id="b1f00-188">Property</span></span>|<span data-ttu-id="b1f00-189">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f00-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="b1f00-190">Bir değerin nullable olup olmadığını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="b1f00-191">Sunucuya null parametre değeri gönderdiğinde, (Visual <xref:System.DBNull> `null` `Nothing` Basic'te) yerine belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="b1f00-192">Veritabanı nulls hakkında daha fazla bilgi için [bkz.](handling-null-values.md)</span><span class="sxs-lookup"><span data-stu-id="b1f00-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="b1f00-193">Değeri temsil etmek için kullanılan en büyük basamak sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="b1f00-194">Bu ayar, tarih ve saat veri türleri için yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="b1f00-195">Değerin zaman bölümünün ,, `Time` `DateTime2`ve `DateTimeOffset`. için çözüldüğü ondalık basamak sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="b1f00-196">Varsayılan değer 0'dır, bu da gerçek ölçeğin değerden çıkarıldığı ve sunucuya gönderildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="b1f00-197">Tarih ve saat veri türleri için yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="b1f00-198">Parametre değerini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="b1f00-199">Parametre değerini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b1f00-200">Sıfırdan az veya 24 saatten büyük veya eşit olan <xref:System.ArgumentException>zaman değerleri bir .</span><span class="sxs-lookup"><span data-stu-id="b1f00-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="b1f00-201">Parametreler oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1f00-201">Creating Parameters</span></span>  
 <span data-ttu-id="b1f00-202">Bir <xref:System.Data.SqlClient.SqlParameter> nesneyi oluşturucusu kullanarak veya bir <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> koleksiyona `Add` ekleyerek . <xref:System.Data.SqlClient.SqlParameterCollection></span><span class="sxs-lookup"><span data-stu-id="b1f00-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="b1f00-203">Yöntem, `Add` kurucu bağımsız değişkenler veya varolan bir parametre nesnesi olarak kabul edilecektir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="b1f00-204">Bu konudaki sonraki bölümlerde tarih ve saat parametrelerinin nasıl belirtilen örnekler verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="b1f00-205">Parametrelerle çalışma ek örnekleri için, [Parametreleri ve Parametre Veri Türlerini ve](../configuring-parameters-and-parameter-data-types.md) [DataAdapter Parametrelerini](../dataadapter-parameters.md)Yapılandırma bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b1f00-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="b1f00-206">Tarih Örneği</span><span class="sxs-lookup"><span data-stu-id="b1f00-206">Date Example</span></span>  
 <span data-ttu-id="b1f00-207">Aşağıdaki kod parçası, bir `date` parametrenin nasıl belirtilen nasıl olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Date";  
parameter.SqlDbType = SqlDbType.Date;  
parameter.Value = "2007/12/1";  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Date"  
parameter.SqlDbType = SqlDbType.Date  
parameter.Value = "2007/12/1"  
```  
  
### <a name="time-example"></a><span data-ttu-id="b1f00-208">Zaman Örneği</span><span class="sxs-lookup"><span data-stu-id="b1f00-208">Time Example</span></span>  
 <span data-ttu-id="b1f00-209">Aşağıdaki kod parçası, bir `time` parametrenin nasıl belirtilen nasıl olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@time";  
parameter.SqlDbType = SqlDbType.Time;  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Time"  
parameter.SqlDbType = SqlDbType.Time  
parameter.Value = DateTime.Parse("23:59:59").TimeOfDay;  
```  
  
### <a name="datetime2-example"></a><span data-ttu-id="b1f00-210">Datetime2 Örneği</span><span class="sxs-lookup"><span data-stu-id="b1f00-210">Datetime2 Example</span></span>  
 <span data-ttu-id="b1f00-211">Aşağıdaki kod parçası, hem tarih `datetime2` hem de saat parçalarıyla bir parametrenin nasıl belirtilen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@Datetime2";  
parameter.SqlDbType = SqlDbType.DateTime2;  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@Datetime2"  
parameter.SqlDbType = SqlDbType.DateTime2  
parameter.Value = DateTime.Parse("1666-09-02 1:00:00");  
```  
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="b1f00-212">DateTimeOffSet Örneği</span><span class="sxs-lookup"><span data-stu-id="b1f00-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="b1f00-213">Aşağıdaki kod parçası, tarih, `DateTimeOffSet` saat ve saat dilimi ofset 0 olan bir parametrenin nasıl belirtilen olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
```csharp  
SqlParameter parameter = new SqlParameter();  
parameter.ParameterName = "@DateTimeOffSet";  
parameter.SqlDbType = SqlDbType.DateTimeOffSet;  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
```vb  
Dim parameter As New SqlParameter()  
parameter.ParameterName = "@DateTimeOffSet"  
parameter.SqlDbType = SqlDbType.DateTimeOffSet  
parameter.Value = DateTimeOffset.Parse("1666-09-02 1:00:00+0");  
```  
  
### <a name="addwithvalue"></a><span data-ttu-id="b1f00-214">Katma Değer</span><span class="sxs-lookup"><span data-stu-id="b1f00-214">AddWithValue</span></span>  
 <span data-ttu-id="b1f00-215">Aşağıdaki kod parçasında `AddWithValue` gösterildiği gibi, <xref:System.Data.SqlClient.SqlCommand>bir , yöntemini kullanarak parametreleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="b1f00-216">Ancak, `AddWithValue` yöntem parametreyi <xref:System.Data.SqlClient.SqlParameter.DbType%2A> belirtmenize <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b1f00-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="b1f00-217">`@date` Parametre, sunucudaki `date`bir `datetime`, `datetime2` veya veri türüyle eşleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="b1f00-218">Yeni `datetime` veri türleri ile çalışırken, <xref:System.Data.SqlDbType> parametrenin özelliğini açıkça örneğin veri türüne ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="b1f00-219">Parametre değerlerinin kullanılması <xref:System.Data.SqlDbType.Variant> veya dolaylı olarak sağlanması, parametre değerleri `datetime` ve `smalldatetime` veri türleri ile geriye dönük uyumluluk la ilgili sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="b1f00-220">Aşağıdaki tablo, `SqlDbTypes` hangi CLR türlerinden çıkarılan ları gösterir:</span><span class="sxs-lookup"><span data-stu-id="b1f00-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="b1f00-221">CLR türü</span><span class="sxs-lookup"><span data-stu-id="b1f00-221">CLR type</span></span>|<span data-ttu-id="b1f00-222">Çıkarılan SqlDbType</span><span class="sxs-lookup"><span data-stu-id="b1f00-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="b1f00-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-223">DateTime</span></span>|<span data-ttu-id="b1f00-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="b1f00-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="b1f00-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="b1f00-225">TimeSpan</span></span>|<span data-ttu-id="b1f00-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="b1f00-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="b1f00-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-227">DateTimeOffset</span></span>|<span data-ttu-id="b1f00-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="b1f00-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="b1f00-229">Tarih ve Saat Verilerini Alma</span><span class="sxs-lookup"><span data-stu-id="b1f00-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="b1f00-230">Aşağıdaki tabloda SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="b1f00-231">SqlClient yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1f00-231">SqlClient method</span></span>|<span data-ttu-id="b1f00-232">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f00-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="b1f00-233">Bir <xref:System.DateTime> yapı olarak belirtilen sütun değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="b1f00-234">Bir <xref:System.DateTimeOffset> yapı olarak belirtilen sütun değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="b1f00-235">Alan için temel sağlayıcıya özgü türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="b1f00-236">Yeni tarih ve `GetFieldType` saat türleri ile aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="b1f00-237">Belirtilen sütunun değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="b1f00-238">Yeni tarih ve `GetValue` saat türleri ile aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="b1f00-239">Belirtilen dizideki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="b1f00-240">Sütun değerini ' <xref:System.Data.SqlTypes.SqlString>olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="b1f00-241">Veriler <xref:System.InvalidCastException> bir `SqlString`. olarak ifade edilemiyorsa oluşur</span><span class="sxs-lookup"><span data-stu-id="b1f00-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="b1f00-242">Sütun verilerini varsayılan `SqlDbType`olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="b1f00-243">Yeni tarih ve `GetValue` saat türleri ile aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="b1f00-244">Belirtilen dizideki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="b1f00-245">Tip Sistem Sürümü SQL Server 2005 olarak ayarlanmışsa sütun değerini dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="b1f00-246">Veriler <xref:System.InvalidCastException> dize olarak ifade edilemiyorsa oluşur.</span><span class="sxs-lookup"><span data-stu-id="b1f00-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="b1f00-247">Bir <xref:System.TimeSpan> yapı olarak belirtilen sütun değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="b1f00-248">Belirtilen sütun değerini temel CLR türü olarak alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="b1f00-249">Bir dizideki sütun değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="b1f00-250">Sonuç <xref:System.Data.DataTable> kümesinin meta verilerini açıklayan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="b1f00-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="b1f00-251">Yeni tarih ve `SqlDbTypes` saat, SQL Server'da işlem içinde yürütülen kod için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b1f00-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="b1f00-252">Bu türlerden biri sunucuya aktarılırsa bir özel durum yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="b1f00-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="b1f00-253">Tarih ve Saat Değerlerini Literal olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="b1f00-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="b1f00-254">SQL Server'ın çalışma zamanında değerlendirdiği çeşitli gerçek dize biçimlerini kullanarak tarih ve saat veri türlerini belirterek bunları dahili tarih/saat yapılarına dönüştürebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="b1f00-255">SQL Server, tek tırnak işaretleri (') ile kapatılan tarih ve saat verilerini tanır.</span><span class="sxs-lookup"><span data-stu-id="b1f00-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="b1f00-256">Aşağıdaki örnekler bazı biçimleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="b1f00-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="b1f00-257">Alfabetik tarih biçimleri, `'October 15, 2006'`gibi .</span><span class="sxs-lookup"><span data-stu-id="b1f00-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="b1f00-258">Gibi sayısal tarih biçimleri, `'10/15/2006'`</span><span class="sxs-lookup"><span data-stu-id="b1f00-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="b1f00-259">ISO standart tarih biçimini `'20061015'`kullanıyorsanız, 15 Ekim 2006 olarak yorumlanacak olan ayrılmamış dize biçimleri.</span><span class="sxs-lookup"><span data-stu-id="b1f00-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1f00-260">SQL Server Books Online'da tüm gerçek dize biçimleri ve tarih ve saat veri türlerinin diğer özellikleri için tam dokümantasyon bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b1f00-261">Sıfırdan az veya 24 saatten büyük veya eşit olan <xref:System.ArgumentException>zaman değerleri bir .</span><span class="sxs-lookup"><span data-stu-id="b1f00-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-books-online"></a><span data-ttu-id="b1f00-262">SQL Server Books Online'daki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="b1f00-262">Resources in SQL Server Books Online</span></span>  
 <span data-ttu-id="b1f00-263">SQL Server'da tarih ve saat değerleriyle çalışma hakkında daha fazla bilgi için SQL Server Books Online'da aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="b1f00-263">For more information about working with date and time values in SQL Server, see the following resources in SQL Server Books Online.</span></span>  
  
|<span data-ttu-id="b1f00-264">Konu başlığı</span><span class="sxs-lookup"><span data-stu-id="b1f00-264">Topic</span></span>|<span data-ttu-id="b1f00-265">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1f00-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b1f00-266">Tarih ve Saat Veri Türleri ve Fonksiyonları (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b1f00-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)|<span data-ttu-id="b1f00-267">Tüm Transact-SQL tarih ve saat veri türlerine ve işlevlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|<span data-ttu-id="b1f00-268">[Tarih ve Saat Verilerini Kullanma](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="b1f00-268">[Using Date and Time Data](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms180878(v=sql.100))</span></span>|<span data-ttu-id="b1f00-269">Tarih ve saat veri türleri ve işlevleri ve bunları kullanma örnekleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="b1f00-270">Veri Türleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="b1f00-270">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)|<span data-ttu-id="b1f00-271">SQL Server'daki sistem veri türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b1f00-271">Describes system data types in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1f00-272">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1f00-272">See also</span></span>

- [<span data-ttu-id="b1f00-273">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="b1f00-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="b1f00-274">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b1f00-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="b1f00-275">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b1f00-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="b1f00-276">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1f00-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
