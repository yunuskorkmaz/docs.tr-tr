---
title: "System.DateTimeOffset yöntemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 81d80cfa69d5afcd39bb1cf78ab3b42aaee06aed
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="systemdatetimeoffset-methods"></a><span data-ttu-id="3d8dd-102">System.DateTimeOffset yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3d8dd-102">System.DateTimeOffset Methods</span></span>
<span data-ttu-id="3d8dd-103">Nesne modeli ya da dış eşleme dosyası eşlenen sonra LINQ-SQL çoğunu çağrı sayesinde <xref:System.DateTimeOffset?displayProperty=nameWithType> yöntemleri, işleçler ve özelliklerinden, LINQ to SQL sorguları.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-103">Once mapped in the object model or external mapping file, LINQ to SQL allows you to call most of the <xref:System.DateTimeOffset?displayProperty=nameWithType> methods, operators, and properties from within your LINQ to SQL queries.</span></span>  
  
 <span data-ttu-id="3d8dd-104">Desteklenmeyen yalnızca bu devralınan gelen yöntemlerdir <xref:System.Object?displayProperty=nameWithType> , yapmayın algılama LINQ bağlamında SQL sorguları gibi: `Finalize`, `GetHashCode`, `GetType`, ve `MemberwiseClone`.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-104">The only methods not supported are those inherited from <xref:System.Object?displayProperty=nameWithType> that do not make sense in the context of LINQ to SQL queries, such as: `Finalize`, `GetHashCode`, `GetType`, and `MemberwiseClone`.</span></span> <span data-ttu-id="3d8dd-105">LINQ-SQL bunları SQL Server üzerine yürütülmek çeviremez çünkü bu yöntemleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-105">These methods are not supported because LINQ to SQL cannot translate them for execution on the SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d8dd-106">Ortak dil çalışma zamanı (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> yapısı ve bir SQL eşleme özelliğini `DATETIMEOFFSET` LINQ-SQL, sütunla .NET Framework 3.5 SP1 gerektirir veya sonrasını.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-106">The common language runtime (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> structure, and the ability to map it to a SQL `DATETIMEOFFSET` column with LINQ to SQL, requires the .NET Framework 3.5 SP1 or beyond.</span></span> <span data-ttu-id="3d8dd-107">SQL `DATETIMEOFFSET` sütundur yalnızca Microsoft SQL Server 2008 ve sonrasındaki kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-107">The SQL `DATETIMEOFFSET` column is only available in Microsoft SQL Server 2008 and beyond.</span></span>  
  
## <a name="sqlmethods-date-and-time-methods"></a><span data-ttu-id="3d8dd-108">SQLMethods tarih ve saat yöntemleri</span><span class="sxs-lookup"><span data-stu-id="3d8dd-108">SQLMethods Date and Time Methods</span></span>  
 <span data-ttu-id="3d8dd-109">Tarafından sunulan yöntemleri yanı sıra <xref:System.DateTimeOffset> yapısı, LINQ-SQL, aşağıdaki tabloda listelenen yöntemleri sunar <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tarih ve saat ile çalışmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-109">In addition to the methods offered by the <xref:System.DateTimeOffset> structure, LINQ to SQL offers the methods listed in the following table from the <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> class for working with date and time.</span></span>  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="3d8dd-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d8dd-110">See Also</span></span>  
 [<span data-ttu-id="3d8dd-111">Sorgu Kavramları</span><span class="sxs-lookup"><span data-stu-id="3d8dd-111">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [<span data-ttu-id="3d8dd-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3d8dd-112">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [<span data-ttu-id="3d8dd-113">SQL-CLR Tür Eşlemesi</span><span class="sxs-lookup"><span data-stu-id="3d8dd-113">SQL-CLR Type Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
