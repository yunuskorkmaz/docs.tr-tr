---
title: System.DateTimeOffset Yöntemleri
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 2e29cf02d4f7e8004782264bf940bb1faf393269
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781555"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="3cf41-102">System.DateTimeOffset Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3cf41-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="3cf41-103">Nesne modelinde veya dış eşleme dosyasında eşlendikten sonra LINQ to SQL, LINQ to SQL Sorgularınızdaki <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemlerin, işleçlerin ve özelliklerin çoğunu çağırabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="3cf41-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="3cf41-104">Desteklenmeyen tek Yöntemler <xref:System.Object?displayProperty=nameWithType> ,: `Finalize`, `GetHashCode` `GetType`, ve`MemberwiseClone`gibi LINQ to SQL sorgularının bağlamında anlamayan Devralınanlar.</span><span class="sxs-lookup"><span data-stu-id="3cf41-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="3cf41-105">LINQ to SQL SQL Server yürütülmek üzere çevrilemediğinden bu yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3cf41-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cf41-106">Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve LINQ to SQL ile bir SQL `DATETIMEOFFSET` sütunuyla eşleme özelliği .NET Framework 3,5 SP1 veya daha fazlasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3cf41-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="3cf41-107">SQL `DATETIMEOFFSET` sütunu yalnızca Microsoft SQL Server 2008 ve sonraki bir sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cf41-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="3cf41-108">SQLMethods tarih ve saat yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3cf41-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="3cf41-109"><xref:System.DateTimeOffset> Yapı tarafından sunulan yöntemlerin yanı sıra, LINQ to SQL tarih ve saat ile çalışmaya yönelik <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> sınıftan aşağıdaki tabloda listelenen yöntemleri sunar.</span><span class="sxs-lookup"><span data-stu-id="3cf41-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3cf41-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cf41-110">See also</span></span>

- [<span data-ttu-id="3cf41-111">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="3cf41-111">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="3cf41-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3cf41-112">Creating the Object Model</span></span>](creating-the-object-model.md)
- [<span data-ttu-id="3cf41-113">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="3cf41-113">SQL-CLR Type Mapping</span></span>](sql-clr-type-mapping.md)
