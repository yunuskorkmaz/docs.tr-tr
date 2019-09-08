---
title: Tarih ve Saat Verileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
ms.openlocfilehash: 90a70eaa2b5aeb8ef1f1659d7912b9ae5abc4eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794242"
---
# <a name="date-and-time-data"></a><span data-ttu-id="6e7a6-102">Tarih ve Saat Verileri</span><span class="sxs-lookup"><span data-stu-id="6e7a6-102">Date and Time Data</span></span>
<span data-ttu-id="6e7a6-103">SQL Server 2008, tarih ve saat bilgilerini işlemeye yönelik yeni veri türlerini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="6e7a6-104">Yeni veri türleri tarih ve saat için ayrı türler, daha fazla Aralık, duyarlık ve saat dilimi tanıma ile genişletilmiş veri türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="6e7a6-105">.NET Framework sürüm 3,5 hizmet paketi (SP) 1 ' den başlayarak, SQL Server (<xref:System.Data.SqlClient>) için .NET Framework veri sağlayıcısı, SQL Server 2008 veritabanı altyapısının tüm yeni özellikleri için tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="6e7a6-106">Bu yeni özellikleri SqlClient kullanmak için .NET Framework 3,5 SP1 (veya sonraki bir sürümü) yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="6e7a6-107">SQL Server 2008 ' den önceki SQL Server sürümlerinde yalnızca tarih ve saat değerleriyle çalışma için iki veri türü vardı: `datetime` ve. `smalldatetime`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="6e7a6-108">Bu veri türlerinin her ikisi de tarih değerini ve bir saat değerini içerir. Bu, yalnızca tarih veya yalnızca saat değerleriyle çalışmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="6e7a6-109">Ayrıca, bu veri türleri yalnızca 1753 içinde England 'da Gregoryen takvime giriş sonrasında oluşan tarihleri destekler.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="6e7a6-110">Diğer bir sınırlama, bu eski veri türlerinin zaman dilimi açısından farkında olmamasıdır ve bu sayede birden çok saat diliminden kaynaklanan verilerle çalışmayı zorlaştırır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="6e7a6-111">SQL Server veri türleri için tüm belgeler, çevrimiçi SQL Server Books Online 'da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="6e7a6-112">Aşağıdaki tabloda tarih ve saat verileri için sürüme özgü giriş düzeyi konuları listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="6e7a6-113">**Books Online SQL Server**</span><span class="sxs-lookup"><span data-stu-id="6e7a6-113">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="6e7a6-114">Tarih ve saat verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6e7a6-114">Using Date and Time Data</span></span>](https://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="6e7a6-115">SQL Server 2008 ' de tanıtılan tarih/saat veri türleri</span><span class="sxs-lookup"><span data-stu-id="6e7a6-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="6e7a6-116">Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="6e7a6-117">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="6e7a6-117">SQL Server data type</span></span>|<span data-ttu-id="6e7a6-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e7a6-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="6e7a6-119">`date` Veri türü 1 Ocak 01 ile 31 Aralık 9999 arasında bir aralığa sahiptir ve 1 gün doğruluk sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="6e7a6-120">Varsayılan değer 1 Ocak 1900 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="6e7a6-121">Depolama boyutu 3 bayttır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="6e7a6-122">`time` Veri türü yalnızca saat değerlerini, 24 saatlik bir saate göre depolar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="6e7a6-123">`time` Veri türü 00:00:00.0000000 ila 23:59:59.9999999 ile 100 nanosaniye arasında bir aralığa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="6e7a6-124">Varsayılan değer 00:00:00.0000000 (gece yarısı) olur.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="6e7a6-125">`time` Veri türü, Kullanıcı tanımlı kesirli ikinci duyarlığı destekler ve depolama boyutu, belirtilen duyarlığa göre 3 ile 6 bayt arasında değişir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="6e7a6-126">Veri türü, `date` ve`time` veri türlerinin aralığını ve duyarlığını tek bir veri türünde birleştirir. `datetime2`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="6e7a6-127">Varsayılan değerler ve dize değişmez biçimleri, `date` ve `time` veri türlerinde tanımlananlarla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="6e7a6-128">Veri türünün tüm `datetime2` özellikleri ek saat dilimi farkına sahiptir. `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="6e7a6-129">Saat dilimi boşluğu [+&#124;-] hh: mm olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="6e7a6-130">SS, saat dilimi kaydırmasında saat sayısını temsil eden 00 ile 14 arasında 2 basamaklı bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="6e7a6-131">Aa, saat dilimi kaydırmasında ek dakika sayısını temsil eden 00 ila 59 arasında 2 basamaklı bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="6e7a6-132">Zaman biçimleri 100 nanosaniye için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="6e7a6-133">Zorunlu + veya-imzala, saat dilimi kaydırın UTC (evrensel saat koordinatı veya Greenwich saati) ile yerel saati elde edilip edilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6e7a6-134">`Type System Version` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için bkz <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="6e7a6-135">Tarih biçimi ve tarih sırası</span><span class="sxs-lookup"><span data-stu-id="6e7a6-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="6e7a6-136">SQL Server Tarih ve saat değerlerini nasıl ayrıştırdığı, yalnızca sistem sürümüne ve sunucu sürümüne değil, ayrıca sunucunun varsayılan diline ve biçim ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="6e7a6-137">Sorgu farklı bir dil ve tarih biçimi ayarı kullanan bir bağlantı tarafından yürütülürse, bir dilin tarih biçimleri için çalıştırılan bir tarih dizesi tanınmıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="6e7a6-138">Transact-SQL SET LANGUAGE deyimleri, tarih bölümlerinin sırasını belirleyen DATEFORMAT öğesini örtülü olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="6e7a6-139">Tarih değerlerini MDY, DMY, YıMD, YıDM, MYD veya DYM Order içindeki Tarih kısımlarını sıralamaya göre ayırt etmek için bir bağlantıda DATEFORMAT Transact-SQL ifadesini ayarla ' yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="6e7a6-140">Bağlantı için herhangi bir DATEFORMAT belirtmezseniz, SQL Server bağlantıyla ilişkili varsayılan dili kullanır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="6e7a6-141">Örneğin, bir tarih dizesi ' 01/02/03 ', dil Birleşik Devletler ayarı olan bir sunucu üzerinde MDY (2 Ocak 2003) ve Ingiliz Ingilizcesi dil ayarı olan bir sunucuda DMY (1 Şubat 2003) olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="6e7a6-142">Yıl, yüzyıl değerini atamak için kesme tarihini tanımlayan SQL Server kesme yılı kuralı kullanılarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="6e7a6-143">Daha fazla bilgi için SQL Server Books Online 'da [iki basamaklı yıl kesme seçeneği](https://go.microsoft.com/fwlink/?LinkId=120473) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-143">For more information, see [two digit year cutoff Option](https://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e7a6-144">Bir `date`dize biçiminden `time` ,`datetime2`, veya`datetimeoffset`olarak dönüştürülürken, yıdm tarih biçimi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="6e7a6-145">SQL Server Tarih ve saat verilerini yorumlama hakkında daha fazla bilgi için, bkz. SQL Server 2008 Books Online 'da [Tarih ve saat verileri kullanma](https://go.microsoft.com/fwlink/?LinkID=98361) .</span><span class="sxs-lookup"><span data-stu-id="6e7a6-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](https://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="6e7a6-146">Tarih/saat veri türleri ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="6e7a6-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="6e7a6-147">Yeni tarih ve saat veri türlerini desteklemek <xref:System.Data.SqlDbType> için aşağıdaki numaralandırmalar eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-147">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
- `SqlDbType.Date`  
  
- `SqlDbType.Time`  
  
- `SqlDbType.DateTime2`  
  
- `SqlDbType.DateTimeOffSet`  

<span data-ttu-id="6e7a6-148">Bir <xref:System.Data.SqlClient.SqlParameter> öğesinin veri türünü, önceki <xref:System.Data.SqlDbType> Numaralandırmalardan birini kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-148">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the preceding <xref:System.Data.SqlDbType> enumerations.</span></span> 

> [!NOTE]
> <span data-ttu-id="6e7a6-149">Öğesinin `DbType`özelliğini olarak`SqlDbType.Date`ayarlayamazsınız. `SqlParameter`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-149">You cannot set the `DbType` property of a `SqlParameter` to `SqlDbType.Date`.</span></span>

 <span data-ttu-id="6e7a6-150"><xref:System.Data.SqlClient.SqlParameter> <xref:System.Data.SqlClient.SqlParameter.DbType%2A> Bir nesnenin`SqlParameter` özelliğini belirli<xref:System.Data.DbType> bir numaralandırma değerine ayarlayarak, bir genel olarak türünü de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-150">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="6e7a6-151">`datetime2` <xref:System.Data.DbType> Ve`datetimeoffset` veri türlerini desteklemek için aşağıdaki numaralandırma değerleri eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="6e7a6-151">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
- <span data-ttu-id="6e7a6-152">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="6e7a6-152">DbType.DateTime2</span></span>  
  
- <span data-ttu-id="6e7a6-153">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-153">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="6e7a6-154">Bu yeni numaralandırmalar, `Date`.NET Framework `Time`önceki sürümlerinde `DateTime` mevcut olan, ve Numaralandırmalar için ek niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-154">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="6e7a6-155">Parametre nesnesinin .NET Framework veri sağlayıcısı türü, parametre nesnesinin değerinin .NET Framework türünden veya parametre nesnesinin öğesinden `DbType` çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-155">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="6e7a6-156">Yeni tarih <xref:System.Data.SqlTypes> ve saat veri türlerini desteklemek için yeni veri türleri tanıtılmadı.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-156">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="6e7a6-157">Aşağıdaki tabloda SQL Server 2008 tarih ve saat veri türleri ile CLR veri türleri arasındaki eşlemeler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-157">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="6e7a6-158">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="6e7a6-158">SQL Server data type</span></span>|<span data-ttu-id="6e7a6-159">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="6e7a6-159">.NET Framework type</span></span>|<span data-ttu-id="6e7a6-160">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="6e7a6-160">System.Data.SqlDbType</span></span>|<span data-ttu-id="6e7a6-161">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="6e7a6-161">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="6e7a6-162">Tarih</span><span class="sxs-lookup"><span data-stu-id="6e7a6-162">date</span></span>|<span data-ttu-id="6e7a6-163">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-163">System.DateTime</span></span>|<span data-ttu-id="6e7a6-164">Tarih</span><span class="sxs-lookup"><span data-stu-id="6e7a6-164">Date</span></span>|<span data-ttu-id="6e7a6-165">Tarih</span><span class="sxs-lookup"><span data-stu-id="6e7a6-165">Date</span></span>|  
|<span data-ttu-id="6e7a6-166">zaman</span><span class="sxs-lookup"><span data-stu-id="6e7a6-166">time</span></span>|<span data-ttu-id="6e7a6-167">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6e7a6-167">System.TimeSpan</span></span>|<span data-ttu-id="6e7a6-168">Zaman</span><span class="sxs-lookup"><span data-stu-id="6e7a6-168">Time</span></span>|<span data-ttu-id="6e7a6-169">Zaman</span><span class="sxs-lookup"><span data-stu-id="6e7a6-169">Time</span></span>|  
|<span data-ttu-id="6e7a6-170">datetime2</span><span class="sxs-lookup"><span data-stu-id="6e7a6-170">datetime2</span></span>|<span data-ttu-id="6e7a6-171">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-171">System.DateTime</span></span>|<span data-ttu-id="6e7a6-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="6e7a6-172">DateTime2</span></span>|<span data-ttu-id="6e7a6-173">DateTime2</span><span class="sxs-lookup"><span data-stu-id="6e7a6-173">DateTime2</span></span>|  
|<span data-ttu-id="6e7a6-174">türünde</span><span class="sxs-lookup"><span data-stu-id="6e7a6-174">datetimeoffset</span></span>|<span data-ttu-id="6e7a6-175">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-175">System.DateTimeOffset</span></span>|<span data-ttu-id="6e7a6-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-176">DateTimeOffset</span></span>|<span data-ttu-id="6e7a6-177">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-177">DateTimeOffset</span></span>|  
|<span data-ttu-id="6e7a6-178">datetime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-178">datetime</span></span>|<span data-ttu-id="6e7a6-179">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-179">System.DateTime</span></span>|<span data-ttu-id="6e7a6-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-180">DateTime</span></span>|<span data-ttu-id="6e7a6-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-181">DateTime</span></span>|  
|<span data-ttu-id="6e7a6-182">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-182">smalldatetime</span></span>|<span data-ttu-id="6e7a6-183">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-183">System.DateTime</span></span>|<span data-ttu-id="6e7a6-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-184">DateTime</span></span>|<span data-ttu-id="6e7a6-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-185">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="6e7a6-186">SqlParameter özellikleri</span><span class="sxs-lookup"><span data-stu-id="6e7a6-186">SqlParameter Properties</span></span>  
 <span data-ttu-id="6e7a6-187">Aşağıdaki tabloda tarih ve `SqlParameter` saat veri türleriyle ilgili özellikler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-187">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="6e7a6-188">Özellik</span><span class="sxs-lookup"><span data-stu-id="6e7a6-188">Property</span></span>|<span data-ttu-id="6e7a6-189">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e7a6-189">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="6e7a6-190">Değerin null yapılabilir olup olmayacağını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-190">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="6e7a6-191">Sunucuya null bir parametre değeri gönderdiğinizde, <xref:System.DBNull> `null` (`Nothing` Visual Basic) yerine belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-191">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="6e7a6-192">Veritabanı boş değerleri hakkında daha fazla bilgi için bkz. [null değerlerini işleme](handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="6e7a6-192">For more information about database nulls, see [Handling Null Values](handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="6e7a6-193">Değeri temsil etmek için kullanılan en fazla basamak sayısını alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-193">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="6e7a6-194">Tarih ve saat veri türleri için bu ayar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-194">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="6e7a6-195">, `Time` `DateTime2`Ve içindeğerinsaatkısmınınçözümlendiğiondalıkbasamaklarınsayısınıalırveyaayarlar.`DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-195">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="6e7a6-196">Varsayılan değer 0 ' dır. Bu, gerçek ölçeğin değerden çıkarılan ve sunucuya gönderildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-196">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="6e7a6-197">Tarih ve saat veri türleri için yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-197">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="6e7a6-198">Parametre değerini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-198">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="6e7a6-199">Parametre değerini alır veya ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-199">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6e7a6-200">Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir <xref:System.ArgumentException>oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-200">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="6e7a6-201">Parametreleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e7a6-201">Creating Parameters</span></span>  
 <span data-ttu-id="6e7a6-202"><xref:System.Data.SqlClient.SqlParameter> Yapıcısını kullanarak veya metodunu`Add` <xref:System.Data.SqlClient.SqlCommand> çağırarakbirkoleksiyonaekleyerek<xref:System.Data.SqlClient.SqlCommand.Parameters%2A> bir nesne oluşturabilirsiniz. <xref:System.Data.SqlClient.SqlParameterCollection></span><span class="sxs-lookup"><span data-stu-id="6e7a6-202">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="6e7a6-203">Yöntemi `Add` , Oluşturucu bağımsız değişkenleri ya da varolan bir parametre nesnesi olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-203">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="6e7a6-204">Bu konunun sonraki bölümlerinde tarih ve saat parametrelerinin nasıl belirtilme örnekleri verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-204">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="6e7a6-205">Parametrelerle çalışma hakkında daha fazla örnek için bkz. [parametreleri ve parametre veri türlerini](../configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametrelerini](../dataadapter-parameters.md)yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-205">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="6e7a6-206">Tarih örneği</span><span class="sxs-lookup"><span data-stu-id="6e7a6-206">Date Example</span></span>  
 <span data-ttu-id="6e7a6-207">Aşağıdaki kod parçası, bir `date` parametrenin nasıl belirtileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-207">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="6e7a6-208">Zaman örneği</span><span class="sxs-lookup"><span data-stu-id="6e7a6-208">Time Example</span></span>  
 <span data-ttu-id="6e7a6-209">Aşağıdaki kod parçası, bir `time` parametrenin nasıl belirtileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-209">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="6e7a6-210">Datetime2 örneği</span><span class="sxs-lookup"><span data-stu-id="6e7a6-210">Datetime2 Example</span></span>  
 <span data-ttu-id="6e7a6-211">Aşağıdaki kod parçası, hem tarih hem de saat `datetime2` parçalarıyla bir parametrenin nasıl belirtileceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-211">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="6e7a6-212">DateTimeOffSet örneği</span><span class="sxs-lookup"><span data-stu-id="6e7a6-212">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="6e7a6-213">Aşağıdaki kod parçası, bir `DateTimeOffSet` parametrenin Tarih, saat ve saat dilimi fark değeri olan 0 ' ı nasıl belirteceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-213">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="6e7a6-214">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="6e7a6-214">AddWithValue</span></span>  
 <span data-ttu-id="6e7a6-215">Ayrıca, aşağıdaki kod parçasında gösterildiği gibi, `AddWithValue` bir <xref:System.Data.SqlClient.SqlCommand>öğesinin yöntemini kullanarak parametreler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-215">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="6e7a6-216">Ancak, `AddWithValue` yöntemi parametresi için <xref:System.Data.SqlClient.SqlParameter.DbType%2A> veya <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> belirtmenize izin vermez.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-216">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="6e7a6-217">Parametresi, sunucusundaki bir `date`, `datetime`veya `datetime2` veri türüyle eşleşgelebilir. `@date`</span><span class="sxs-lookup"><span data-stu-id="6e7a6-217">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="6e7a6-218">Yeni `datetime` veri türleriyle çalışırken, <xref:System.Data.SqlDbType> parametrenin özelliğini, örneğin veri türüne açık olarak ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-218">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="6e7a6-219">Parametre <xref:System.Data.SqlDbType.Variant> değerlerini kullanmak veya örtük olarak sağlamak, `datetime` ve `smalldatetime` veri türleriyle geriye dönük uyumlulukla ilgili sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-219">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="6e7a6-220">Aşağıdaki tabloda, hangi CLR `SqlDbTypes` türlerinden çıkarılan gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6e7a6-220">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="6e7a6-221">CLR türü</span><span class="sxs-lookup"><span data-stu-id="6e7a6-221">CLR type</span></span>|<span data-ttu-id="6e7a6-222">Çıkarılan SqlDbType</span><span class="sxs-lookup"><span data-stu-id="6e7a6-222">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="6e7a6-223">DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-223">DateTime</span></span>|<span data-ttu-id="6e7a6-224">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="6e7a6-224">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="6e7a6-225">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="6e7a6-225">TimeSpan</span></span>|<span data-ttu-id="6e7a6-226">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="6e7a6-226">SqlDbType.Time</span></span>|  
|<span data-ttu-id="6e7a6-227">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-227">DateTimeOffset</span></span>|<span data-ttu-id="6e7a6-228">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="6e7a6-228">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="6e7a6-229">Tarih ve saat verilerini alma</span><span class="sxs-lookup"><span data-stu-id="6e7a6-229">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="6e7a6-230">Aşağıdaki tabloda SQL Server 2008 tarih ve saat değerlerini almak için kullanılan yöntemler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-230">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="6e7a6-231">SqlClient yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e7a6-231">SqlClient method</span></span>|<span data-ttu-id="6e7a6-232">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e7a6-232">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="6e7a6-233">Belirtilen sütun değerini bir <xref:System.DateTime> yapı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-233">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="6e7a6-234">Belirtilen sütun değerini bir <xref:System.DateTimeOffset> yapı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-234">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="6e7a6-235">Alan için sağlayıcıya özgü temel tür olan türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-235">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="6e7a6-236">Yeni tarih ve saat türleri `GetFieldType` için aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-236">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="6e7a6-237">Belirtilen sütunun değerini alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-237">Retrieves the value of the specified column.</span></span> <span data-ttu-id="6e7a6-238">Yeni tarih ve saat türleri `GetValue` için aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-238">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="6e7a6-239">Belirtilen dizideki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-239">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="6e7a6-240">Sütun değerini bir <xref:System.Data.SqlTypes.SqlString>olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-240">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="6e7a6-241">Veriler bir`SqlString`olarak ifade edilenemediğinde oluşur.<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="6e7a6-241">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="6e7a6-242">Sütun verilerini varsayılan `SqlDbType`olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-242">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="6e7a6-243">Yeni tarih ve saat türleri `GetValue` için aynı türleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-243">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="6e7a6-244">Belirtilen dizideki değerleri alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-244">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="6e7a6-245">Tür sistemi sürümü SQL Server 2005 olarak ayarlandıysa, sütun değerini bir dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-245">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="6e7a6-246">Veriler bir dize olarak ifade edilenemediğinde oluşur.<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="6e7a6-246">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="6e7a6-247">Belirtilen sütun değerini bir <xref:System.TimeSpan> yapı olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-247">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="6e7a6-248">Belirtilen sütun değerini temel alınan CLR türü olarak alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-248">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="6e7a6-249">Bir dizideki sütun değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-249">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="6e7a6-250">Sonuç kümesinin <xref:System.Data.DataTable> meta verilerini açıklayan bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-250">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="6e7a6-251">Yeni tarih ve saat `SqlDbTypes` , SQL Server içinde işlem sırasında yürütülen kod için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-251">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="6e7a6-252">Bu türlerden biri sunucuya geçirilirse bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-252">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="6e7a6-253">Tarih ve saat değerlerini değişmez değer olarak belirtme</span><span class="sxs-lookup"><span data-stu-id="6e7a6-253">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="6e7a6-254">Tarih ve saat veri türlerini SQL Server, daha sonra çalışma zamanında değerlendiren ve bunları iç tarih/saat yapılarına dönüştüren çeşitli farklı değişmez dize biçimlerini kullanarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-254">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="6e7a6-255">SQL Server, tek tırnak işareti (') içine alınmış tarih ve saat verilerini tanır.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-255">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="6e7a6-256">Aşağıdaki örneklerde bazı biçimler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="6e7a6-256">The following examples demonstrate some formats:</span></span>  
  
- <span data-ttu-id="6e7a6-257">Alfabetik tarih biçimleri, `'October 15, 2006'`örneğin.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-257">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
- <span data-ttu-id="6e7a6-258">Gibi sayısal Tarih biçimleri `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-258">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
- <span data-ttu-id="6e7a6-259">ISO standart tarih biçimini kullanıyorsanız, örneğin `'20061015'`, 15 Ekim 2006 olarak yorumlanabilecek, gibi ayrılmamış dize biçimleri.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-259">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e7a6-260">Tüm sabit dize biçimlerinin ve SQL Server Books Online 'daki tarih ve saat veri türlerinin diğer özelliklerine ilişkin tüm belgeleri bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-260">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="6e7a6-261">Sıfırdan küçük veya 24 saatten büyük veya buna eşit olan saat değerleri bir <xref:System.ArgumentException>oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-261">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="6e7a6-262">SQL Server 2008 Books Online 'daki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6e7a6-262">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="6e7a6-263">SQL Server 2008 ' de tarih ve saat değerleriyle çalışma hakkında daha fazla bilgi için SQL Server 2008 Books Online 'da aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-263">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="6e7a6-264">Konu</span><span class="sxs-lookup"><span data-stu-id="6e7a6-264">Topic</span></span>|<span data-ttu-id="6e7a6-265">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e7a6-265">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6e7a6-266">Tarih ve saat veri türleri ve Işlevleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6e7a6-266">Date and Time Data Types and Functions (Transact-SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="6e7a6-267">Tüm Transact-SQL tarih ve saat veri türleri ve işlevlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-267">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="6e7a6-268">Tarih ve saat verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="6e7a6-268">Using Date and Time Data</span></span>](https://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="6e7a6-269">Tarih ve saat veri türleri ve işlevleri hakkında bilgi ve bunları kullanma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-269">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="6e7a6-270">Veri türleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6e7a6-270">Data Types (Transact-SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="6e7a6-271">SQL Server 2008 ' de sistem veri türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-271">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e7a6-272">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e7a6-272">See also</span></span>

- [<span data-ttu-id="6e7a6-273">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="6e7a6-273">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="6e7a6-274">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6e7a6-274">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="6e7a6-275">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6e7a6-275">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)
- [<span data-ttu-id="6e7a6-276">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6e7a6-276">ADO.NET Overview</span></span>](../ado-net-overview.md)
