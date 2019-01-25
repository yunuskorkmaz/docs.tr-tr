---
title: System.DateTimeOffset yöntemleri
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 46b1622cdc8a38544f1c8a8104abb935c9ff1269
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637209"
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="6bca2-102">System.DateTimeOffset yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6bca2-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="6bca2-103">Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ to SQL çoğunu çağırmanızı sağlar <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemleri, işleçler ve LINQ içinde özellikleri SQL sorguları.</span><span class="sxs-lookup"><span data-stu-id="6bca2-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="6bca2-104">Desteklenmeyen yalnızca bu devralınan gelen yöntemlerdir <xref:System.Object?displayProperty=nameWithType> , mantıklı değildir LINQ bağlamında SQL sorguları gibi: `Finalize`, `GetHashCode`, `GetType`, ve `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="6bca2-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="6bca2-105">LINQ to SQL için SQL Server üzerinde yürütme çevirmek olamaz çünkü bu yöntemler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="6bca2-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6bca2-106">Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve bir SQL eşleme özelliğini `DATETIMEOFFSET` sütun LINQ to SQL ile .NET Framework 3.5 SP1 gerektirir veya sonrasını.</span><span class="sxs-lookup"><span data-stu-id="6bca2-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="6bca2-107">SQL `DATETIMEOFFSET` sütundur yalnızca Microsoft SQL Server 2008'de ve sonrasında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bca2-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="6bca2-108">SQLMethods tarih ve saat yöntemleri</span><span class="sxs-lookup"><span data-stu-id="6bca2-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="6bca2-109">Tarafından sunulan yöntemlerine ek olarak <xref:System.DateTimeOffset> yapısı, LINQ to SQL sunar ve aşağıdaki tablodan listelenen yöntemleri <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="6bca2-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="6bca2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bca2-110">See also</span></span>
- [<span data-ttu-id="6bca2-111">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="6bca2-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [<span data-ttu-id="6bca2-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6bca2-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="6bca2-113">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="6bca2-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
