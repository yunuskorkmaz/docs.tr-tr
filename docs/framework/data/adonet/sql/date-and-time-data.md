---
title: Tarih ve saat verilerini
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
ms.assetid: 6f5ff56a-a57e-49d7-8ae9-bbed697e42e3
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a146cf50639351479d42bff684ea7db21ecf5d3b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="date-and-time-data"></a><span data-ttu-id="8f604-102">Tarih ve saat verilerini</span><span class="sxs-lookup"><span data-stu-id="8f604-102">Date and Time Data</span></span>
<span data-ttu-id="8f604-103">SQL Server 2008, tarih ve saat bilgilerini işleme yeni veri türleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="8f604-103">SQL Server 2008 introduces new data types for handling date and time information.</span></span> <span data-ttu-id="8f604-104">Yeni veri türleri, tarih ve saat için ayrı türleri ve büyük aralık, duyarlık ve saat dilimi tanıma ile genişletilmiş veri türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="8f604-104">The new data types include separate types for date and time, and expanded data types with greater range, precision, and time-zone awareness.</span></span> <span data-ttu-id="8f604-105">İle .NET Framework sürüm 3.5 hizmet paketi (SP) 1, SQL Server için .NET Framework veri sağlayıcısı başlatılıyor (<xref:System.Data.SqlClient>) SQL Server 2008 veritabanı altyapısı için yeni özellikler hakkında tam destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-105">Starting with the .NET Framework version 3.5 Service Pack (SP) 1, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides full support for all the new features of the SQL Server 2008 Database Engine.</span></span> <span data-ttu-id="8f604-106">.NET Framework 3.5 SP1'i yüklemeniz gerekir (veya üstü) bu yeni özellikleri ile SqlClient kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="8f604-106">You must install the .NET Framework 3.5 SP1 (or later) to use these new features with SqlClient.</span></span>  
  
 <span data-ttu-id="8f604-107">İki veri türü yalnızca vardı tarih ve saat değerleri ile çalışmak için SQL Server 2008'den önceki SQL Server sürümleri: `datetime` ve `smalldatetime`.</span><span class="sxs-lookup"><span data-stu-id="8f604-107">Versions of SQL Server earlier than SQL Server 2008 only had two data types for working with date and time values: `datetime` and `smalldatetime`.</span></span> <span data-ttu-id="8f604-108">Bu iki veri türü tarih değeri ve yalnızca tarih veya saat değerleri ile çalışmak zorlaştırır bir saat değeri içerir.</span><span class="sxs-lookup"><span data-stu-id="8f604-108">Both of these data types contain both the date value and a time value, which makes it difficult to work with only date or only time values.</span></span> <span data-ttu-id="8f604-109">Ayrıca, bu veri türleri yalnızca 1753 İngiltere'deki Gregoryen takvim girişte sonra ortaya tarihleri destekler.</span><span class="sxs-lookup"><span data-stu-id="8f604-109">Also, these data types only support dates that occur after the introduction of the Gregorian calendar in England in 1753.</span></span> <span data-ttu-id="8f604-110">Bu eski veri türleri saat dilimi olmayan başka bir kısıtlamadır kullanan, birden çok zaman bölgelerinden kaynaklandığı verilerle çalışmak zorlaştıran.</span><span class="sxs-lookup"><span data-stu-id="8f604-110">Another limitation is that these older data types are not time-zone aware, which makes it difficult to work with data that originates from multiple time zones.</span></span>  
  
 <span data-ttu-id="8f604-111">SQL Server veri türleri için kapsamlı belgeler SQL Server Books Online içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f604-111">Complete documentation for SQL Server data types is available in SQL Server Books Online.</span></span> <span data-ttu-id="8f604-112">Aşağıdaki tabloda, tarih ve saat verilerini için sürüme özgü giriş seviyesi konuları listeler.</span><span class="sxs-lookup"><span data-stu-id="8f604-112">The following table lists the version-specific entry-level topics for date and time data.</span></span>  
  
 <span data-ttu-id="8f604-113">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="8f604-113">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="8f604-114">Tarih ve saat verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="8f604-114">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkID=98361)  
  
## <a name="datetime-data-types-introduced-in-sql-server-2008"></a><span data-ttu-id="8f604-115">Veri türleri SQL Server 2008 ' sunulan tarih</span><span class="sxs-lookup"><span data-stu-id="8f604-115">Date/Time Data Types Introduced in SQL Server 2008</span></span>  
 <span data-ttu-id="8f604-116">Aşağıdaki tabloda yeni tarih ve saat veri türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f604-116">The following table describes the new date and time data types.</span></span>  
  
|<span data-ttu-id="8f604-117">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="8f604-117">SQL Server data type</span></span>|<span data-ttu-id="8f604-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f604-118">Description</span></span>|  
|--------------------------|-----------------|  
|`date`|<span data-ttu-id="8f604-119">`date` Veri türüne sahip bir aralığı 1 Ocak-31 Aralık 01 bir doğruluğu, 1 gün ile 9999.</span><span class="sxs-lookup"><span data-stu-id="8f604-119">The `date` data type has a range of January 1, 01 through December 31, 9999 with an accuracy of 1 day.</span></span> <span data-ttu-id="8f604-120">Varsayılan değer 1 Ocak 1900 ' dir.</span><span class="sxs-lookup"><span data-stu-id="8f604-120">The default value is January 1, 1900.</span></span> <span data-ttu-id="8f604-121">Depolama boyutu 3 bayttır.</span><span class="sxs-lookup"><span data-stu-id="8f604-121">The storage size is 3 bytes.</span></span>|  
|`time`|<span data-ttu-id="8f604-122">`time` Veri türü, 24 saatlik dayalı yalnızca saat değerleri depolar.</span><span class="sxs-lookup"><span data-stu-id="8f604-122">The `time` data type stores time values only, based on a 24-hour clock.</span></span> <span data-ttu-id="8f604-123">`time` Aralığıyla 100 nanosaniye bir doğruluğunu 00:00:00.0000000 23:59:59.9999999 aracılığıyla veri türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="8f604-123">The `time` data type has a range of 00:00:00.0000000 through 23:59:59.9999999 with an accuracy of 100 nanoseconds.</span></span> <span data-ttu-id="8f604-124">00:00:00.0000000 (gece yarısı) varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="8f604-124">The default value is 00:00:00.0000000 (midnight).</span></span> <span data-ttu-id="8f604-125">`time` Veri türü kullanıcı tanımlı kesirli ikinci duyarlık destekler ve depolama boyutu 3 ile 6 bayt cinsinden belirtilen duyarlılık göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f604-125">The `time` data type supports user-defined fractional second precision, and the storage size varies from 3 to 6 bytes, based on the precision specified.</span></span>|  
|`datetime2`|<span data-ttu-id="8f604-126">`datetime2` Veri türü, aralık ve kesinliğini birleştirir `date` ve `time` tek bir veri türüne içine veri türleri.</span><span class="sxs-lookup"><span data-stu-id="8f604-126">The `datetime2` data type combines the range and precision of the `date` and `time` data types into a single data type.</span></span><br /><br /> <span data-ttu-id="8f604-127">Dize değişmez değer biçimleri ve varsayılan değerleri tanımlanan aynıdır `date` ve `time` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="8f604-127">The default values and string literal formats are the same as those defined in the `date` and `time` data types.</span></span>|  
|`datetimeoffset`|<span data-ttu-id="8f604-128">`datetimeoffset` Veri türüne sahip tüm özelliklerini `datetime2` ek saat dilimi konumu ile.</span><span class="sxs-lookup"><span data-stu-id="8f604-128">The `datetimeoffset` data type has all the features of `datetime2` with an additional time zone offset.</span></span> <span data-ttu-id="8f604-129">Saat dilimi konumu olarak temsil edilir [+ &#124;-] hh: mm.</span><span class="sxs-lookup"><span data-stu-id="8f604-129">The time zone offset is represented as [+&#124;-] HH:MM.</span></span> <span data-ttu-id="8f604-130">HH 00-saat dilimi kaymasını saat sayısını temsil eden 14 arasında değişen 2 basamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="8f604-130">HH is 2 digits ranging from 00 to 14 that represent the number of hours in the time zone offset.</span></span> <span data-ttu-id="8f604-131">AA 00-saat dilimi kaymasını ek dakika sayısını temsil eden 59 arasında değişen 2 basamaktan oluşur.</span><span class="sxs-lookup"><span data-stu-id="8f604-131">MM is 2 digits ranging from 00 to 59 that represent the number of additional minutes in the time zone offset.</span></span> <span data-ttu-id="8f604-132">Saat biçimleri 100 nanosaniye desteklenir.</span><span class="sxs-lookup"><span data-stu-id="8f604-132">Time formats are supported to 100 nanoseconds.</span></span> <span data-ttu-id="8f604-133">Zorunlu + veya - saat dilimi kaymasını eklendiğinde veya (Evrensel Saat eşgüdümü veya Greenwich saati) yerel zamanını elde etmek için UTC çıkarılır işareti gösterir.</span><span class="sxs-lookup"><span data-stu-id="8f604-133">The mandatory + or - sign indicates whether the time zone offset is added or subtracted from UTC (Universal Time Coordinate or Greenwich Mean Time) to obtain the local time.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8f604-134">Kullanma hakkında daha fazla bilgi için `Type System Version` anahtar sözcüğü, bkz: <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span><span class="sxs-lookup"><span data-stu-id="8f604-134">For more information about using the `Type System Version` keyword, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
## <a name="date-format-and-date-order"></a><span data-ttu-id="8f604-135">Tarih biçimi ve tarih sırası</span><span class="sxs-lookup"><span data-stu-id="8f604-135">Date Format and Date Order</span></span>  
 <span data-ttu-id="8f604-136">SQL Server tarih ve saat değerleri nasıl ayrıştırır yalnızca türü sistemi sürümü ve sunucu sürümü, aynı zamanda sunucunun varsayılan dil ve biçim ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="8f604-136">How SQL Server parses date and time values depends not only on the type system version and server version, but also on the server's default language and format settings.</span></span> <span data-ttu-id="8f604-137">Farklı dil ve tarih biçimi ayarını kullanan bir tarih dizesi Works tarih biçimleri bir dil için bir bağlantı tarafından sorgu yürütülürse tanınmayan olabilir.</span><span class="sxs-lookup"><span data-stu-id="8f604-137">A date string that works for the date formats of one language might be unrecognizable if the query is executed by a connection that uses a different language and date format setting.</span></span>  
  
 <span data-ttu-id="8f604-138">Transact-SQL Dil Ayarla deyimi tarih kısımlarını sırasını belirleyen DATEFORMAT örtük olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-138">The Transact-SQL SET LANGUAGE statement implicitly sets the DATEFORMAT that determines the order of the date parts.</span></span> <span data-ttu-id="8f604-139">Tarih değerlerini tarih kısımlarını AGY, GAY, YAG'dir, YDM, MYD veya DYM sırada sıralama tarafından belirsizliğini ortadan kaldırmak için bir bağlantı üzerinden AYARLAMAK DATEFORMAT Transact-SQL deyimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="8f604-139">You can use the SET DATEFORMAT Transact-SQL statement on a connection to disambiguate date values by ordering the date parts in MDY, DMY, YMD, YDM, MYD, or DYM order.</span></span>  
  
 <span data-ttu-id="8f604-140">Bağlantı için tüm DATEFORMAT belirtmezseniz, SQL Server bağlantı ile ilişkili varsayılan dilini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8f604-140">If you do not specify any DATEFORMAT for the connection, SQL Server uses the default language associated with the connection.</span></span> <span data-ttu-id="8f604-141">Örneğin, tarih dizisi 02 / ' 01/03 ' İngiliz İngilizce dil ayarı ile bir sunucu üzerinde Amerika Birleşik Devletleri İngilizce dil ayarı olan bir sunucuda AGY (2 Ocak 2003) ve GAY (1 Şubat 2003) olarak yorumlanacağını.</span><span class="sxs-lookup"><span data-stu-id="8f604-141">For example, a date string of '01/02/03' would be interpreted as MDY (January 2, 2003) on a server with a language setting of United States English, and as DMY (February 1, 2003) on a server with a language setting of British English.</span></span> <span data-ttu-id="8f604-142">Yılın century değer atamak için kesme tarihi tanımlar SQL Server'ın kesme yıl kuralı kullanılarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="8f604-142">The year is determined by using SQL Server's cutoff year rule, which defines the cutoff date for assigning the century value.</span></span> <span data-ttu-id="8f604-143">Daha fazla bilgi için bkz: [iki rakamlı yıl kesme seçeneği](http://go.microsoft.com/fwlink/?LinkId=120473) SQL Server Books Online.</span><span class="sxs-lookup"><span data-stu-id="8f604-143">For more information, see [two digit year cutoff Option](http://go.microsoft.com/fwlink/?LinkId=120473) in SQL Server Books Online.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f604-144">Bir dize biçimine dönüştürülürken YDM tarih biçimi desteklenmiyor `date`, `time`, `datetime2`, veya `datetimeoffset`.</span><span class="sxs-lookup"><span data-stu-id="8f604-144">The YDM date format is not supported when converting from a string format to `date`, `time`, `datetime2`, or `datetimeoffset`.</span></span>  
  
 <span data-ttu-id="8f604-145">SQL Server tarih ve saat verilerini yorumlaması hakkında daha fazla bilgi için bkz: [kullanarak tarih ve saat verilerini](http://go.microsoft.com/fwlink/?LinkID=98361) SQL Server 2008 Books Online.</span><span class="sxs-lookup"><span data-stu-id="8f604-145">For more information about how SQL Server interprets date and time data, see [Using Date and Time Data](http://go.microsoft.com/fwlink/?LinkID=98361) in SQL Server 2008 Books Online.</span></span>  
  
## <a name="datetime-data-types-and-parameters"></a><span data-ttu-id="8f604-146">Tarih/saat veri türleri ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="8f604-146">Date/Time Data Types and Parameters</span></span>  
 <span data-ttu-id="8f604-147">Veri türünü belirleyebileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> birini kullanarak <xref:System.Data.SqlDbType> numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="8f604-147">You can specify the data type of a <xref:System.Data.SqlClient.SqlParameter> by using one of the <xref:System.Data.SqlDbType> enumerations.</span></span> <span data-ttu-id="8f604-148">Aşağıdaki sabit listeleri için eklenene <xref:System.Data.SqlDbType> yeni tarih ve saat veri türlerini desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="8f604-148">The following enumerations have been added to <xref:System.Data.SqlDbType> to support the new date and time data types.</span></span>  
  
-   `SqlDbType.Date`  
  
-   `SqlDbType.Time`  
  
-   `SqlDbType.DateTime2`  
  
-   `SqlDbType.DateTimeOffSet`  
  
 <span data-ttu-id="8f604-149">Ayrıca türünü belirtebilirsiniz bir <xref:System.Data.SqlClient.SqlParameter> ayarlayarak genel <xref:System.Data.SqlClient.SqlParameter.DbType%2A> özelliği bir `SqlParameter` belirli bir nesneye <xref:System.Data.DbType> numaralandırma değeri.</span><span class="sxs-lookup"><span data-stu-id="8f604-149">You can also specify the type of a <xref:System.Data.SqlClient.SqlParameter> generically by setting the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> property of a `SqlParameter` object to a particular <xref:System.Data.DbType> enumeration value.</span></span> <span data-ttu-id="8f604-150">Aşağıdaki numaralandırma değerleri için eklenene <xref:System.Data.DbType> desteklemek için `datetime2` ve `datetimeoffset` veri türleri:</span><span class="sxs-lookup"><span data-stu-id="8f604-150">The following enumeration values have been added to <xref:System.Data.DbType> to support the `datetime2` and `datetimeoffset` data types:</span></span>  
  
-   <span data-ttu-id="8f604-151">DbType.DateTime2</span><span class="sxs-lookup"><span data-stu-id="8f604-151">DbType.DateTime2</span></span>  
  
-   <span data-ttu-id="8f604-152">DbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-152">DbType.DateTimeOffset</span></span>  
  
 <span data-ttu-id="8f604-153">Bu yeni numaralandırmalar tamamlayacak `Date`, `Time`, ve `DateTime` .NET Framework'ün önceki sürümlerde var olan numaralandırmalar.</span><span class="sxs-lookup"><span data-stu-id="8f604-153">These new enumerations supplement the `Date`, `Time`, and `DateTime` enumerations, which existed in earlier versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="8f604-154">.NET Framework veri sağlayıcısı türü parameter nesnesinin değerin parametre nesnesinin ya da .NET Framework tür çıkarımı yapılan `DbType` parametre nesnesinin.</span><span class="sxs-lookup"><span data-stu-id="8f604-154">The .NET Framework data provider type of a parameter object is inferred from the .NET Framework type of the value of the parameter object, or from the `DbType` of the parameter object.</span></span> <span data-ttu-id="8f604-155">Yeni <xref:System.Data.SqlTypes> veri türlerine sunulan yeni tarih ve saat veri türlerini desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="8f604-155">No new <xref:System.Data.SqlTypes> data types have been introduced to support the new date and time data types.</span></span> <span data-ttu-id="8f604-156">Aşağıdaki tabloda, SQL Server 2008 tarih ve saat veri türleri ve CLR veri türleri arasındaki eşlemeleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8f604-156">The following table describes the mappings between the SQL Server 2008 date and time data types and the CLR data types.</span></span>  
  
|<span data-ttu-id="8f604-157">SQL Server veri türü</span><span class="sxs-lookup"><span data-stu-id="8f604-157">SQL Server data type</span></span>|<span data-ttu-id="8f604-158">.NET Framework türü</span><span class="sxs-lookup"><span data-stu-id="8f604-158">.NET Framework type</span></span>|<span data-ttu-id="8f604-159">System.Data.SqlDbType</span><span class="sxs-lookup"><span data-stu-id="8f604-159">System.Data.SqlDbType</span></span>|<span data-ttu-id="8f604-160">System.Data.DbType</span><span class="sxs-lookup"><span data-stu-id="8f604-160">System.Data.DbType</span></span>|  
|--------------------------|-------------------------|---------------------------|------------------------|  
|<span data-ttu-id="8f604-161">Tarih</span><span class="sxs-lookup"><span data-stu-id="8f604-161">date</span></span>|<span data-ttu-id="8f604-162">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-162">System.DateTime</span></span>|<span data-ttu-id="8f604-163">Tarih</span><span class="sxs-lookup"><span data-stu-id="8f604-163">Date</span></span>|<span data-ttu-id="8f604-164">Tarih</span><span class="sxs-lookup"><span data-stu-id="8f604-164">Date</span></span>|  
|<span data-ttu-id="8f604-165">zaman</span><span class="sxs-lookup"><span data-stu-id="8f604-165">time</span></span>|<span data-ttu-id="8f604-166">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8f604-166">System.TimeSpan</span></span>|<span data-ttu-id="8f604-167">Zaman</span><span class="sxs-lookup"><span data-stu-id="8f604-167">Time</span></span>|<span data-ttu-id="8f604-168">Zaman</span><span class="sxs-lookup"><span data-stu-id="8f604-168">Time</span></span>|  
|<span data-ttu-id="8f604-169">datetime2</span><span class="sxs-lookup"><span data-stu-id="8f604-169">datetime2</span></span>|<span data-ttu-id="8f604-170">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-170">System.DateTime</span></span>|<span data-ttu-id="8f604-171">DateTime2</span><span class="sxs-lookup"><span data-stu-id="8f604-171">DateTime2</span></span>|<span data-ttu-id="8f604-172">DateTime2</span><span class="sxs-lookup"><span data-stu-id="8f604-172">DateTime2</span></span>|  
|<span data-ttu-id="8f604-173">Datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="8f604-173">datetimeoffset</span></span>|<span data-ttu-id="8f604-174">System.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-174">System.DateTimeOffset</span></span>|<span data-ttu-id="8f604-175">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-175">DateTimeOffset</span></span>|<span data-ttu-id="8f604-176">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-176">DateTimeOffset</span></span>|  
|<span data-ttu-id="8f604-177">datetime</span><span class="sxs-lookup"><span data-stu-id="8f604-177">datetime</span></span>|<span data-ttu-id="8f604-178">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-178">System.DateTime</span></span>|<span data-ttu-id="8f604-179">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-179">DateTime</span></span>|<span data-ttu-id="8f604-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-180">DateTime</span></span>|  
|<span data-ttu-id="8f604-181">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="8f604-181">smalldatetime</span></span>|<span data-ttu-id="8f604-182">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-182">System.DateTime</span></span>|<span data-ttu-id="8f604-183">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-183">DateTime</span></span>|<span data-ttu-id="8f604-184">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-184">DateTime</span></span>|  
  
### <a name="sqlparameter-properties"></a><span data-ttu-id="8f604-185">SqlParameter özellikleri</span><span class="sxs-lookup"><span data-stu-id="8f604-185">SqlParameter Properties</span></span>  
 <span data-ttu-id="8f604-186">Aşağıdaki tabloda açıklanmaktadır `SqlParameter` tarih ve saat veri türleri ile ilgili özellikler.</span><span class="sxs-lookup"><span data-stu-id="8f604-186">The following table describes `SqlParameter` properties that are relevant to date and time data types.</span></span>  
  
|<span data-ttu-id="8f604-187">Özellik</span><span class="sxs-lookup"><span data-stu-id="8f604-187">Property</span></span>|<span data-ttu-id="8f604-188">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f604-188">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.IsNullable%2A>|<span data-ttu-id="8f604-189">Alır veya değer boş değer atanabilir olup olmadığını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-189">Gets or sets whether a value is nullable.</span></span> <span data-ttu-id="8f604-190">Sunucuya bir null parametre değeri gönderdiğinizde belirtmelisiniz <xref:System.DBNull>, yerine `null` (`Nothing` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="8f604-190">When you send a null parameter value to the server, you must specify <xref:System.DBNull>, rather than `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="8f604-191">Veritabanı null değerler hakkında daha fazla bilgi için bkz: [boş değerler işleme](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span><span class="sxs-lookup"><span data-stu-id="8f604-191">For more information about database nulls, see [Handling Null Values](../../../../../docs/framework/data/adonet/sql/handling-null-values.md).</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Precision%2A>|<span data-ttu-id="8f604-192">Alır veya değeri temsil etmek için kullanılan basamak sayısını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-192">Gets or sets the maximum number of digits used to represent the value.</span></span> <span data-ttu-id="8f604-193">Bu ayar, tarih ve saat veri türleri için göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="8f604-193">This setting is ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Scale%2A>|<span data-ttu-id="8f604-194">Alır veya ayarlar için değer saat bölümünü olduğu için çözümlenmiş ondalık basamak sayısını `Time`, `DateTime2`, ve `DateTimeOffset`.</span><span class="sxs-lookup"><span data-stu-id="8f604-194">Gets or sets the number of decimal places to which the time portion of the value is resolved for `Time`, `DateTime2`,and `DateTimeOffset`.</span></span> <span data-ttu-id="8f604-195">Varsayılan değer gerçek ölçek değerinden çıkarımı yapılan ve sunucuya gönderilen anlamına gelir 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="8f604-195">The default value is 0, which means that the actual scale is inferred from the value and sent to the server.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="8f604-196">Tarih ve saat veri türleri için yoksayıldı.</span><span class="sxs-lookup"><span data-stu-id="8f604-196">Ignored for date and time data types.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="8f604-197">Alır veya parametre değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-197">Gets or sets the parameter value.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="8f604-198">Alır veya parametre değeri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-198">Gets or sets the parameter value.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8f604-199">Sıfır veya daha büyük veya eşittir 24 saat küçüktür saat değerleri oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="8f604-199">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="creating-parameters"></a><span data-ttu-id="8f604-200">Parametreleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f604-200">Creating Parameters</span></span>  
 <span data-ttu-id="8f604-201">Oluşturabileceğiniz bir <xref:System.Data.SqlClient.SqlParameter> nesne kendi oluşturucusunu kullanarak veya eklemeyi bir <xref:System.Data.SqlClient.SqlCommand> <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> çağırarak koleksiyonu `Add` yöntemi <xref:System.Data.SqlClient.SqlParameterCollection>.</span><span class="sxs-lookup"><span data-stu-id="8f604-201">You can create a <xref:System.Data.SqlClient.SqlParameter> object by using its constructor, or by adding it to a <xref:System.Data.SqlClient.SqlCommand><xref:System.Data.SqlClient.SqlCommand.Parameters%2A> collection by calling the `Add` method of the <xref:System.Data.SqlClient.SqlParameterCollection>.</span></span> <span data-ttu-id="8f604-202">`Add` Yöntemi olarak sürer oluşturucu bağımsız değişkenleri veya varolan bir parametre nesnesi girin.</span><span class="sxs-lookup"><span data-stu-id="8f604-202">The `Add` method will take as input either constructor arguments or an existing parameter object.</span></span>  
  
 <span data-ttu-id="8f604-203">Bu konunun sonraki bölümlerinde, tarih ve saat parametrelerini belirtmek nasıl örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-203">The next sections in this topic provide examples of how to specify date and time parameters.</span></span> <span data-ttu-id="8f604-204">Parametrelerle çalışma ek örnekler için bkz: [yapılandırma parametreleri ve parametre veri türleri](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) ve [DataAdapter parametreleri](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8f604-204">For additional examples of working with parameters, see [Configuring Parameters and Parameter Data Types](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md) and [DataAdapter Parameters](../../../../../docs/framework/data/adonet/dataadapter-parameters.md).</span></span>  
  
### <a name="date-example"></a><span data-ttu-id="8f604-205">Tarih örneği</span><span class="sxs-lookup"><span data-stu-id="8f604-205">Date Example</span></span>  
 <span data-ttu-id="8f604-206">Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `date` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8f604-206">The following code fragment demonstrates how to specify a `date` parameter.</span></span>  
  
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
  
### <a name="time-example"></a><span data-ttu-id="8f604-207">Saat örneği</span><span class="sxs-lookup"><span data-stu-id="8f604-207">Time Example</span></span>  
 <span data-ttu-id="8f604-208">Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `time` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8f604-208">The following code fragment demonstrates how to specify a `time` parameter.</span></span>  
  
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
  
### <a name="datetime2-example"></a><span data-ttu-id="8f604-209">Datetime2 örneği</span><span class="sxs-lookup"><span data-stu-id="8f604-209">Datetime2 Example</span></span>  
 <span data-ttu-id="8f604-210">Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `datetime2` tarih ve saat bölümleri parametresiyle.</span><span class="sxs-lookup"><span data-stu-id="8f604-210">The following code fragment demonstrates how to specify a `datetime2` parameter with both the date and time parts.</span></span>  
  
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
  
### <a name="datetimeoffset-example"></a><span data-ttu-id="8f604-211">DateTimeOffSet Example</span><span class="sxs-lookup"><span data-stu-id="8f604-211">DateTimeOffSet Example</span></span>  
 <span data-ttu-id="8f604-212">Aşağıdaki kod parçası nasıl belirleneceğini göstermektedir bir `DateTimeOffSet` parametresi bir tarih, bir saat ve saat dilimi uzaklığı 0 ile.</span><span class="sxs-lookup"><span data-stu-id="8f604-212">The following code fragment demonstrates how to specify a `DateTimeOffSet` parameter with a date, a time, and a time zone offset of 0.</span></span>  
  
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
  
### <a name="addwithvalue"></a><span data-ttu-id="8f604-213">AddWithValue</span><span class="sxs-lookup"><span data-stu-id="8f604-213">AddWithValue</span></span>  
 <span data-ttu-id="8f604-214">Kullanarak parametreleri sağlayabilir `AddWithValue` yöntemi bir <xref:System.Data.SqlClient.SqlCommand>, aşağıdaki kod parçasında gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="8f604-214">You can also supply parameters by using the `AddWithValue` method of a <xref:System.Data.SqlClient.SqlCommand>, as shown in the following code fragment.</span></span> <span data-ttu-id="8f604-215">Ancak, `AddWithValue` yöntemi izin vermez belirtmek <xref:System.Data.SqlClient.SqlParameter.DbType%2A> veya <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> parametresi için.</span><span class="sxs-lookup"><span data-stu-id="8f604-215">However, the `AddWithValue` method does not allow you to specify the <xref:System.Data.SqlClient.SqlParameter.DbType%2A> or <xref:System.Data.SqlClient.SqlParameter.SqlDbType%2A> for the parameter.</span></span>  
  
```csharp  
command.Parameters.AddWithValue(   
    "@date", DateTimeOffset.Parse("16660902"));  
```  
  
```vb  
command.Parameters.AddWithValue( _  
    "@date", DateTimeOffset.Parse("16660902"))  
```  
  
 <span data-ttu-id="8f604-216">`@date` Parametresini eşleştirmek için bir `date`, `datetime`, veya `datetime2` sunucudaki veri türü.</span><span class="sxs-lookup"><span data-stu-id="8f604-216">The `@date` parameter could map to a `date`, `datetime`, or `datetime2` data type on the server.</span></span> <span data-ttu-id="8f604-217">Yeni çalışırken `datetime` veri türleri, parametrenin açıkça ayarlamalısınız <xref:System.Data.SqlDbType> örnek veri türü için özellik.</span><span class="sxs-lookup"><span data-stu-id="8f604-217">When working with the new `datetime` data types, you must explicitly set the parameter's <xref:System.Data.SqlDbType> property to the data type of the instance.</span></span> <span data-ttu-id="8f604-218">Kullanarak <xref:System.Data.SqlDbType.Variant> ya da örtük olarak parametre değerlerini sağladığını ile geriye dönük uyumluluk sorunları neden olabilecek `datetime` ve `smalldatetime` veri türleri.</span><span class="sxs-lookup"><span data-stu-id="8f604-218">Using <xref:System.Data.SqlDbType.Variant> or implicitly supplying parameter values can cause problems with backward compatibility with the `datetime` and `smalldatetime` data types.</span></span>  
  
 <span data-ttu-id="8f604-219">Aşağıdaki tabloda gösterir `SqlDbTypes` hangi CLR türlerinden sonuçlandı:</span><span class="sxs-lookup"><span data-stu-id="8f604-219">The following table shows which `SqlDbTypes` are inferred from which CLR types:</span></span>  
  
|<span data-ttu-id="8f604-220">CLR türü</span><span class="sxs-lookup"><span data-stu-id="8f604-220">CLR type</span></span>|<span data-ttu-id="8f604-221">Inferred SqlDbType</span><span class="sxs-lookup"><span data-stu-id="8f604-221">Inferred SqlDbType</span></span>|  
|--------------|------------------------|  
|<span data-ttu-id="8f604-222">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-222">DateTime</span></span>|<span data-ttu-id="8f604-223">SqlDbType.DateTime</span><span class="sxs-lookup"><span data-stu-id="8f604-223">SqlDbType.DateTime</span></span>|  
|<span data-ttu-id="8f604-224">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="8f604-224">TimeSpan</span></span>|<span data-ttu-id="8f604-225">SqlDbType.Time</span><span class="sxs-lookup"><span data-stu-id="8f604-225">SqlDbType.Time</span></span>|  
|<span data-ttu-id="8f604-226">DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-226">DateTimeOffset</span></span>|<span data-ttu-id="8f604-227">SqlDbType.DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="8f604-227">SqlDbType.DateTimeOffset</span></span>|  
  
## <a name="retrieving-date-and-time-data"></a><span data-ttu-id="8f604-228">Tarih ve saat verilerini alma</span><span class="sxs-lookup"><span data-stu-id="8f604-228">Retrieving Date and Time Data</span></span>  
 <span data-ttu-id="8f604-229">Aşağıdaki tabloda, SQL Server 2008 tarih ve saat değerleri almak için kullanılan yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f604-229">The following table describes methods that are used to retrieve SQL Server 2008 date and time values.</span></span>  
  
|<span data-ttu-id="8f604-230">SqlClient yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f604-230">SqlClient method</span></span>|<span data-ttu-id="8f604-231">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f604-231">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTime%2A>|<span data-ttu-id="8f604-232">Belirtilen sütun değeri olarak alır bir <xref:System.DateTime> yapısı.</span><span class="sxs-lookup"><span data-stu-id="8f604-232">Retrieves the specified column value as a <xref:System.DateTime> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetDateTimeOffset%2A>|<span data-ttu-id="8f604-233">Belirtilen sütun değeri olarak alır bir <xref:System.DateTimeOffset> yapısı.</span><span class="sxs-lookup"><span data-stu-id="8f604-233">Retrieves the specified column value as a <xref:System.DateTimeOffset> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>|<span data-ttu-id="8f604-234">Alan için temel alınan sağlayıcıya özgü tür türü döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f604-234">Returns the type that is the underlying provider-specific type for the field.</span></span> <span data-ttu-id="8f604-235">Aynı türlerine döndürür `GetFieldType` yeni tarih ve saat türleri için.</span><span class="sxs-lookup"><span data-stu-id="8f604-235">Returns the same types as `GetFieldType` for new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>|<span data-ttu-id="8f604-236">Belirtilen sütunun değeri alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-236">Retrieves the value of the specified column.</span></span> <span data-ttu-id="8f604-237">Aynı türlerine döndürür `GetValue` yeni tarih ve saat türleri için.</span><span class="sxs-lookup"><span data-stu-id="8f604-237">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>|<span data-ttu-id="8f604-238">Belirtilen dizideki alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-238">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlString%2A>|<span data-ttu-id="8f604-239">Sütun değeri olarak alır bir <xref:System.Data.SqlTypes.SqlString>.</span><span class="sxs-lookup"><span data-stu-id="8f604-239">Retrieves the column value as a <xref:System.Data.SqlTypes.SqlString>.</span></span> <span data-ttu-id="8f604-240">Bir <xref:System.InvalidCastException> veri olarak açıklanamayan saptanmışsa bir `SqlString`.</span><span class="sxs-lookup"><span data-stu-id="8f604-240">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a `SqlString`.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>|<span data-ttu-id="8f604-241">Sütun verileri varsayılan olarak alır `SqlDbType`.</span><span class="sxs-lookup"><span data-stu-id="8f604-241">Retrieves column data as its default `SqlDbType`.</span></span> <span data-ttu-id="8f604-242">Aynı türlerine döndürür `GetValue` yeni tarih ve saat türleri için.</span><span class="sxs-lookup"><span data-stu-id="8f604-242">Returns the same types as `GetValue` for the new date and time types.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>|<span data-ttu-id="8f604-243">Belirtilen dizideki alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-243">Retrieves the values in the specified array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetString%2A>|<span data-ttu-id="8f604-244">Tür sistemi sürümü SQL Server 2005'e ayarlanırsa sütun değeri bir dize olarak alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-244">Retrieves the column value as a string if the Type System Version is set to SQL Server 2005.</span></span> <span data-ttu-id="8f604-245">Bir <xref:System.InvalidCastException> verileri dize olarak açıklanamayan ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="8f604-245">An <xref:System.InvalidCastException> occurs if the data cannot be expressed as a string.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetTimeSpan%2A>|<span data-ttu-id="8f604-246">Belirtilen sütun değeri olarak alır bir <xref:System.TimeSpan> yapısı.</span><span class="sxs-lookup"><span data-stu-id="8f604-246">Retrieves the specified column value as a <xref:System.TimeSpan> structure.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>|<span data-ttu-id="8f604-247">Belirtilen sütun değeri temel CLR türünü alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-247">Retrieves the specified column value as its underlying CLR type.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>|<span data-ttu-id="8f604-248">Bir dizi sütun değerlerini alır.</span><span class="sxs-lookup"><span data-stu-id="8f604-248">Retrieves column values in an array.</span></span>|  
|<xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A>|<span data-ttu-id="8f604-249">Döndürür bir <xref:System.Data.DataTable> sonuç kümesi meta verilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="8f604-249">Returns a <xref:System.Data.DataTable> that describes the metadata of the result set.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8f604-250">Yeni tarih ve saat `SqlDbTypes` işlemdeki SQL Server'da yürütüyor kod için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8f604-250">The new date and time `SqlDbTypes` are not supported for code that is executing in-process in SQL Server.</span></span> <span data-ttu-id="8f604-251">Şu türlerden birine sunucuya aktarılırsa bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8f604-251">An exception will be raised if one of these types is passed to the server.</span></span>  
  
## <a name="specifying-date-and-time-values-as-literals"></a><span data-ttu-id="8f604-252">Tarih ve saat değerleri değişmez değerleri belirtme</span><span class="sxs-lookup"><span data-stu-id="8f604-252">Specifying Date and Time Values as Literals</span></span>  
 <span data-ttu-id="8f604-253">Tarih ve saat veri türleri, çeşitli farklı değişmez değer dize biçimlerde, hangi SQL Server'ı kullanarak belirtebilirsiniz ardından iç tarih yapılara dönüştürme çalışma zamanında değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="8f604-253">You can specify date and time data types by using a variety of different literal string formats, which SQL Server then evaluates at run time, converting them to internal date/time structures.</span></span> <span data-ttu-id="8f604-254">SQL Server (') tek tırnak işaretleri içine tarih ve saat verilerini tanır.</span><span class="sxs-lookup"><span data-stu-id="8f604-254">SQL Server recognizes date and time data that is enclosed in single quotation marks (').</span></span> <span data-ttu-id="8f604-255">Aşağıdaki örnekler, bazı biçimleri göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="8f604-255">The following examples demonstrate some formats:</span></span>  
  
-   <span data-ttu-id="8f604-256">Alfabetik tarih biçimleri, gibi `'October 15, 2006'`.</span><span class="sxs-lookup"><span data-stu-id="8f604-256">Alphabetic date formats, such as `'October 15, 2006'`.</span></span>  
  
-   <span data-ttu-id="8f604-257">Sayısal tarih biçimleri, gibi `'10/15/2006'`.</span><span class="sxs-lookup"><span data-stu-id="8f604-257">Numeric date formats, such as `'10/15/2006'`.</span></span>  
  
-   <span data-ttu-id="8f604-258">Dize biçimleri gibi unseparated `'20061015'`, hangi kabul 15 Ekim 2006 ISO standart tarih biçimi kullanıyorsanız.</span><span class="sxs-lookup"><span data-stu-id="8f604-258">Unseparated string formats, such as `'20061015'`, which would be interpreted as October 15, 2006 if you are using the ISO standard date format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f604-259">Değişmez değer dize biçimleri tümünün ve SQL Server Books Online'da tarih ve saat veri türlerinin diğer özellikler için kapsamlı belgeler bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f604-259">You can find complete documentation for all of the literal string formats and other features of the date and time data types in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="8f604-260">Sıfır veya daha büyük veya eşittir 24 saat küçüktür saat değerleri oluşturur bir <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="8f604-260">Time values that are less than zero or greater than or equal to 24 hours will throw an <xref:System.ArgumentException>.</span></span>  
  
## <a name="resources-in-sql-server-2008-books-online"></a><span data-ttu-id="8f604-261">SQL Server 2008 Çevrimiçi Kitapları kaynakları</span><span class="sxs-lookup"><span data-stu-id="8f604-261">Resources in SQL Server 2008 Books Online</span></span>  
 <span data-ttu-id="8f604-262">SQL Server 2008'deki tarih ve saat değerleri ile çalışma hakkında daha fazla bilgi için SQL Server 2008 Çevrimiçi Kitapları'nda aşağıdaki kaynaklara bakın.</span><span class="sxs-lookup"><span data-stu-id="8f604-262">For more information about working with date and time values in SQL Server 2008, see the following resources in SQL Server 2008 Books Online.</span></span>  
  
|<span data-ttu-id="8f604-263">Konu</span><span class="sxs-lookup"><span data-stu-id="8f604-263">Topic</span></span>|<span data-ttu-id="8f604-264">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f604-264">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8f604-265">Tarih ve saat verilerini türler ve İşlevler (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8f604-265">Date and Time Data Types and Functions (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98360)|<span data-ttu-id="8f604-266">Tüm Transact-SQL tarih ve saat veri türleri ve işlevleri hakkında genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-266">Provides an overview of all Transact-SQL date and time data types and functions.</span></span>|  
|[<span data-ttu-id="8f604-267">Tarih ve saat verilerini kullanma</span><span class="sxs-lookup"><span data-stu-id="8f604-267">Using Date and Time Data</span></span>](http://go.microsoft.com/fwlink/?LinkId=98361)|<span data-ttu-id="8f604-268">Tarih ve saat veri türleri ve işlevleri ve onları kullanma örnekleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-268">Provides information about the date and time data types and functions, and examples of using them.</span></span>|  
|[<span data-ttu-id="8f604-269">Veri türleri (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="8f604-269">Data Types (Transact-SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=98362)|<span data-ttu-id="8f604-270">SQL Server 2008 sistem veri türlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f604-270">Describes system data types in SQL Server 2008.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f604-271">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f604-271">See Also</span></span>  
 [<span data-ttu-id="8f604-272">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="8f604-272">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="8f604-273">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8f604-273">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="8f604-274">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8f604-274">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="8f604-275">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8f604-275">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
