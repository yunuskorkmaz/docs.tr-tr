---
description: ': System. TimeSpan yöntemleri hakkında daha fazla bilgi'
title: System.TimeSpan Yöntemleri
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: fa3192d18a59e589f2c7510776f8510b2c12cac4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681194"
---
# <a name="systemtimespan-methods"></a><span data-ttu-id="6d407-103">System.TimeSpan Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6d407-103">System.TimeSpan Methods</span></span>

<span data-ttu-id="6d407-104">İçin üye desteği <xref:System.TimeSpan?displayProperty=nameWithType> büyük ölçüde kullandığınız .NET Framework ve Microsoft SQL Server sürümlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6d407-104">Member support for <xref:System.TimeSpan?displayProperty=nameWithType> greatly depends on the versions of the .NET Framework and Microsoft SQL Server that you are using.</span></span>  
  
 <span data-ttu-id="6d407-105">Bir yöntem, işleç veya özellik desteklenmiyorsa; LINQ to SQL, SQL Server yürütme için üyeyi çeviremediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6d407-105">When a method, operator, or property is unsupported; it means that LINQ to SQL cannot translate the member for execution on the SQL Server.</span></span> <span data-ttu-id="6d407-106">Kodunuzda bu üyeleri yine de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d407-106">You may still be able to use these members in your code.</span></span> <span data-ttu-id="6d407-107">Ancak, sorgu Transact-SQL ' e çevrilmeden veya sonuçlar veritabanından alındıktan sonra değerlendirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6d407-107">However, they must be evaluated before the query is translated to Transact-SQL or after the results have been retrieved from the database.</span></span>  
  
## <a name="previous-limitations"></a><span data-ttu-id="6d407-108">Önceki sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="6d407-108">Previous Limitations</span></span>  

 <span data-ttu-id="6d407-109">.NET Framework 3,5 SP1 'den önceki .NET Framework sürümleriyle LINQ to SQL kullanırken, SQL Server veritabanı alanlarını ile eşleyemezsiniz <xref:System.TimeSpan?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6d407-109">When using LINQ to SQL with versions of the .NET Framework prior to .NET Framework 3.5 SP1, you cannot map SQL Server database fields to <xref:System.TimeSpan?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d407-110">Ancak, <xref:System.TimeSpan> <xref:System.TimeSpan> değerler çıkarma işleminden döndürülebilecek <xref:System.DateTime> veya bir ifadenin bir sabit değer ya da bağlı değişken olarak tanıtıldığı için üzerinde işlemler desteklenir.</span><span class="sxs-lookup"><span data-stu-id="6d407-110">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
## <a name="supported-systemtimespan-member-support"></a><span data-ttu-id="6d407-111">Desteklenen System. TimeSpan üye desteği</span><span class="sxs-lookup"><span data-stu-id="6d407-111">Supported System.TimeSpan member support</span></span>

 <span data-ttu-id="6d407-112">Aşağıdaki LINQ to SQL desteklenen yöntemler, işleçler ve Özellikler LINQ to SQL sorgularda kullanabileceğiniz şekilde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d407-112">The following LINQ to SQL-supported methods, operators, and properties are available for you to use in your LINQ to SQL queries.</span></span> <span data-ttu-id="6d407-113">Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra, LINQ to SQL LINQ to SQL Sorgularınızdaki birçok üyeyi çağırabilmeniz için izin verir <xref:System.TimeSpan?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6d407-113">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call many of the <xref:System.TimeSpan?displayProperty=nameWithType> members inside your LINQ to SQL queries.</span></span>  
  
|<span data-ttu-id="6d407-114">Desteklenen <xref:System.TimeSpan> Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6d407-114">Supported <xref:System.TimeSpan> Methods</span></span>|<span data-ttu-id="6d407-115">Desteklenen <xref:System.TimeSpan> işleçler</span><span class="sxs-lookup"><span data-stu-id="6d407-115">Supported <xref:System.TimeSpan> Operators</span></span>|<span data-ttu-id="6d407-116">Desteklenen <xref:System.TimeSpan> Özellikler</span><span class="sxs-lookup"><span data-stu-id="6d407-116">Supported <xref:System.TimeSpan> Properties</span></span>|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> <span data-ttu-id="6d407-117"><xref:System.TimeSpan?displayProperty=nameWithType>LINQ to SQL ile BIR SQL sütunuyla eşleme özelliği, `TIME` .NET Framework 3,5 SP1 ve daha fazlasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6d407-117">The ability to map <xref:System.TimeSpan?displayProperty=nameWithType> to a SQL `TIME` column with LINQ to SQL requires the .NET Framework 3.5 SP1 and beyond.</span></span> <span data-ttu-id="6d407-118">SQL `TIME` veri türü yalnızca Microsoft SQL Server 2008 ve daha ötesi bir sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6d407-118">The SQL `TIME` data type is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
### <a name="addition-and-subtraction"></a><span data-ttu-id="6d407-119">Toplama ve çıkarma</span><span class="sxs-lookup"><span data-stu-id="6d407-119">Addition and Subtraction</span></span>  

 <span data-ttu-id="6d407-120">CLR <xref:System.TimeSpan?displayProperty=nameWithType> türü ekleme ve çıkarma desteği sağlasa da, SQL `TIME` türü değildir.</span><span class="sxs-lookup"><span data-stu-id="6d407-120">Although the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type does support addition and subtraction, the SQL `TIME` type does not.</span></span> <span data-ttu-id="6d407-121">Bu nedenle, LINQ to SQL sorgularınız, SQL türüne eşlendiklerinde ekleme ve çıkarma işlemi gerçekleştirmeye çalıştıklarında hatalar oluşturur `TIME` .</span><span class="sxs-lookup"><span data-stu-id="6d407-121">Because of this, your LINQ to SQL queries will generate errors if they attempt addition and subtraction when they are mapped to the SQL `TIME` type.</span></span> <span data-ttu-id="6d407-122">SQL [-CLR tür EŞLEMESINDE](sql-clr-type-mapping.md)SQL tarih ve saat türleriyle çalışmaya yönelik başka hususlar bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6d407-122">You can find other considerations for working with SQL date and time types in [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d407-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6d407-123">See also</span></span>

- [<span data-ttu-id="6d407-124">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="6d407-124">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="6d407-125">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6d407-125">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="6d407-126">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="6d407-126">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
- [<span data-ttu-id="6d407-127">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6d407-127">Data Types and Functions</span></span>](data-types-and-functions.md)
