---
description: Daha fazla bilgi için bkz. System. DateTime yöntemleri
title: System.DateTime Yöntemleri
ms.date: 03/30/2017
ms.assetid: 4f80700c-e83f-4ab6-af0f-1c9a606e1133
ms.openlocfilehash: b4b732bf41be2a943610a26f5abc33d1bb080d2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681389"
---
# <a name="systemdatetime-methods"></a><span data-ttu-id="a04be-103">System.DateTime Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a04be-103">System.DateTime Methods</span></span>

<span data-ttu-id="a04be-104">Aşağıdaki LINQ to SQL desteklenen yöntemler, işleçler ve Özellikler LINQ to SQL sorgularda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a04be-104">The following LINQ to SQL-supported methods, operators, and properties are available to use in LINQ to SQL queries.</span></span> <span data-ttu-id="a04be-105">Bir yöntem, işleç veya özellik desteklenmiyorsa LINQ to SQL, üyeyi SQL Server yürütme için çeviremez.</span><span class="sxs-lookup"><span data-stu-id="a04be-105">When a method, operator or property is unsupported, LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="a04be-106">Kodunuzda bu üyeleri kullanabilirsiniz, ancak sorgu Transact-SQL ' e çevrilmeden veya sonuçlar veritabanından alındıktan sonra değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="a04be-106">You may use these members in your code, however, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="supported-systemdatetime-members"></a><span data-ttu-id="a04be-107">Desteklenen System. DateTime üyeleri</span><span class="sxs-lookup"><span data-stu-id="a04be-107">Supported System.DateTime Members</span></span>  

 <span data-ttu-id="a04be-108">Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra LINQ to SQL, aşağıdaki <xref:System.DateTime?displayProperty=nameWithType> üyeleri LINQ to SQL sorguları içinde çağırabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="a04be-108">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call the following <xref:System.DateTime?displayProperty=nameWithType> members inside LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="a04be-109">Desteklenen <xref:System.DateTime> Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a04be-109">Supported <xref:System.DateTime> Methods</span></span>|<span data-ttu-id="a04be-110">Desteklenen <xref:System.DateTime> işleçler</span><span class="sxs-lookup"><span data-stu-id="a04be-110">Supported <xref:System.DateTime> Operators</span></span>|<span data-ttu-id="a04be-111">Desteklenen <xref:System.DateTime> Özellikler</span><span class="sxs-lookup"><span data-stu-id="a04be-111">Supported <xref:System.DateTime> Properties</span></span>|  
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
  
## <a name="members-not-supported-by-linq-to-sql"></a><span data-ttu-id="a04be-112">LINQ to SQL tarafından desteklenmeyen Üyeler</span><span class="sxs-lookup"><span data-stu-id="a04be-112">Members Not Supported by LINQ to SQL</span></span>  

 <span data-ttu-id="a04be-113">LINQ to SQL sorgularda aşağıdaki Üyeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a04be-113">The following members are not supported inside LINQ to SQL queries.</span></span>  
  
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
  
## <a name="method-translation-example"></a><span data-ttu-id="a04be-114">Yöntem çevirisi örneği</span><span class="sxs-lookup"><span data-stu-id="a04be-114">Method Translation Example</span></span>  

 <span data-ttu-id="a04be-115">LINQ to SQL tarafından desteklenen tüm yöntemler, SQL Server gönderilmeden önce Transact-SQL ' e çevrilir.</span><span class="sxs-lookup"><span data-stu-id="a04be-115">All methods supported by LINQ to SQL are translated to Transact-SQL before they are sent to   SQL Server.</span></span> <span data-ttu-id="a04be-116">Örneğin, aşağıdaki kalıbı göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="a04be-116">For example, consider the following pattern.</span></span>  
  
 `(dateTime1 – dateTime2).{Days, Hours, Milliseconds, Minutes, Months, Seconds, Years}`  
  
 <span data-ttu-id="a04be-117">Tanındığında, aşağıdaki şekilde SQL Server işlevine doğrudan bir çağrıya çevrilir `DATEDIFF` :</span><span class="sxs-lookup"><span data-stu-id="a04be-117">When it is recognized, it is translated into a direct call to the SQL Server `DATEDIFF` function, as follows:</span></span>  
  
 `DATEDIFF({DatePart}, @dateTime1, @dateTime2)`  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="a04be-118">SQLMethods tarih ve saat yöntemleri</span><span class="sxs-lookup"><span data-stu-id="a04be-118">SQLMethods Date and Time Methods</span></span>  

 <span data-ttu-id="a04be-119">Yapı tarafından sunulan yöntemlerin yanı sıra <xref:System.DateTime> , LINQ to SQL <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> Tarih ve saat ile çalışmaya yönelik sınıftan aşağıdaki tabloda listelenen yöntemleri sunar.</span><span class="sxs-lookup"><span data-stu-id="a04be-119">In addition to the methods offered by the <xref:System.DateTime> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="a04be-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a04be-120">See also</span></span>

- [<span data-ttu-id="a04be-121">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="a04be-121">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="a04be-122">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a04be-122">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="a04be-123">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="a04be-123">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="a04be-124">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="a04be-124">Data Types and Functions</span></span>](data-types-and-functions.md)
