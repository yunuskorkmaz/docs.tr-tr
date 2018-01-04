---
title: "System.DateTime yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 50fe660a84dcb75c12655f2b60c7e5969a07a839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="ad7ad-102">System.DateTime yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-102">System.DateTime Methods</span></span>
<span data-ttu-id="ad7ad-103">LINQ SQL sorguları kullanmak, aşağıdaki LINQ SQL desteklenen yöntem, işleçler ve özellikler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-103">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="ad7ad-104">Yöntemi, işleci veya özelliği desteklenmeyen olduğunda LINQ-SQL üye SQL Server üzerinde yürütme için çeviremez.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-104">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="ad7ad-105">Kodunuzda bu üyeleri kullanabilir, sorgu Transact-SQL veya veritabanından sonuçları alındıktan sonra çevrilmesi önce ancak, bunlar değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-105">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="ad7ad-106">Desteklenen System.DateTime üyeleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-106">Supported System.DateTime Members</span></span>  
 <span data-ttu-id="ad7ad-107">Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ-SQL aşağıdaki çağrı sayesinde <xref:System.DateTime?displayProperty=nameWithType> SQL sorguları LINQ içinde üyelerine.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-107">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="ad7ad-108">Desteklenen <xref:System.DateTime> yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-108">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="ad7ad-109">Desteklenen <xref:System.DateTime> işleçleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-109">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="ad7ad-110">Desteklenen <xref:System.DateTime> özellikleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-110">Supported <xref:System.DateTime> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Add%2A>|<xref:System.DateTime.op_Addition%2A>|<xref:System.DateTime.Date%2A>|  
|<xref:System.DateTime.AddDays%2A>|<xref:System.DateTime.op_Equality%2A>|<xref:System.DateTime.Day%2A>|  
|<xref:System.DateTime.AddHours%2A>|<xref:System.DateTime.op_GreaterThan%2A>|<xref:System.DateTime.DayOfWeek%2A>|  
|<xref:System.DateTime.AddMilliseconds%2A>|<xref:System.DateTime.op_GreaterThanOrEqual%2A>|<xref:System.DateTime.DayOfYear%2A>|  
|<xref:System.DateTime.AddMinutes%2A>|<xref:System.DateTime.op_Inequality%2A>|<xref:System.DateTime.Hour%2A>|  
|<xref:System.DateTime.AddMonths%2A>|<xref:System.DateTime.op_LessThan%2A>|<xref:System.DateTime.Millisecond%2A>|  
|<xref:System.DateTime.AddSeconds%2A>|<xref:System.DateTime.op_LessThanOrEqual%2A>|<xref:System.DateTime.Minute%2A>|  
|<xref:System.DateTime.AddTicks%2A>|<xref:System.DateTime.op_Subtraction%2A>|<xref:System.DateTime.Month%2A>|  
|<xref:System.DateTime.AddYears%2A>||<xref:System.DateTime.Now%2A>|  
|<xref:System.DateTime.Compare%2A>||<xref:System.DateTime.Second%2A>|  
|<xref:System.DateTime.CompareTo%28System.DateTime%29>||<xref:System.DateTime.TimeOfDay%2A>|  
|<xref:System.DateTime.Equals%28System.DateTime%29>||<xref:System.DateTime.Today%2A>|  
|||<xref:System.DateTime.Year%2A>|  
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="ad7ad-111">LINQ-SQL tarafından desteklenmeyen üyeleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-111">Members Not Supported by LINQ to SQL</span></span>  
 <span data-ttu-id="ad7ad-112">Aşağıdaki üyeleri içinde LINQ SQL sorguları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-112">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
|||  
|-|-|  
|<xref:System.DateTime.IsDaylightSavingTime%2A>|<xref:System.DateTime.IsLeapYear%2A>|  
|<xref:System.DateTime.DaysInMonth%2A>|<xref:System.DateTime.ToBinary%2A>|  
|<xref:System.DateTime.ToFileTime%2A>|<xref:System.DateTime.ToFileTimeUtc%2A>|  
|<xref:System.DateTime.ToLongDateString%2A>|<xref:System.DateTime.ToLongTimeString%2A>|  
|<xref:System.DateTime.ToOADate%2A>|<xref:System.DateTime.ToShortDateString%2A>|  
|<xref:System.DateTime.ToShortTimeString%2A>|<xref:System.DateTime.ToUniversalTime%2A>|  
|<xref:System.DateTime.FromBinary%2A>|<xref:System.DateTime.UtcNow%2A>|  
|<xref:System.DateTime.FromFileTime%2A>|<xref:System.DateTime.FromFileTimeUtc%2A>|  
|<xref:System.DateTime.FromOADate%2A>|<xref:System.DateTime.GetDateTimeFormats%2A>|  
  
## <a name="method-translation-example"></a><span data-ttu-id="ad7ad-113">Yöntemi çevirisi örneği</span><span class="sxs-lookup"><span data-stu-id="ad7ad-113">Method Translation Example</span></span>  
 <span data-ttu-id="ad7ad-114">SQL Server'a gönderilmeden önce LINQ-SQL tarafından desteklenen tüm yöntemleri için Transact-SQL çevrilir.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-114">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="ad7ad-115">Örneğin, aşağıdaki düzeni göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-115">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="ad7ad-116">Tanınan, SQL Server doğrudan bir çağrı çevrilir `DATEDIFF` gibi işlev:</span><span class="sxs-lookup"><span data-stu-id="ad7ad-116">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="ad7ad-117">SQLMethods tarih ve saat yöntemleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-117">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="ad7ad-118">Tarafından sunulan yöntemleri yanı sıra <xref:System.DateTime> yapısı, LINQ-SQL, aşağıdaki tabloda listelenen yöntemleri sunar <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-118">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="ad7ad-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ad7ad-119">See Also</span></span>  
 [<span data-ttu-id="ad7ad-120">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="ad7ad-120">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="ad7ad-121">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ad7ad-121">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="ad7ad-122">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="ad7ad-122">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [<span data-ttu-id="ad7ad-123">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="ad7ad-123">Data Types and Functions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
