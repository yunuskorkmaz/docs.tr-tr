---
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: d4fe3d91b80197d962989cd2d3bc9bb2df6e3ffe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164161"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="2e077-102">Desteklenmeyen İşlev</span><span class="sxs-lookup"><span data-stu-id="2e077-102">Unsupported Functionality</span></span>

<span data-ttu-id="2e077-103">LINQ to SQL, aşağıdaki SQL işlevselliği mevcut ortak dil çalışma zamanının (CLR) ve .NET Framework yapılarının çevirisi aracılığıyla sunulamaz:</span><span class="sxs-lookup"><span data-stu-id="2e077-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="2e077-104">`LIKE`Doğrudan çeviri aracılığıyla desteklenmese de, sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="2e077-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="2e077-105">Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e077-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="2e077-106">LINQ to SQL için sınırlı destek vardır `DATEDIFF` .</span><span class="sxs-lookup"><span data-stu-id="2e077-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="2e077-107">Sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="2e077-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="2e077-108">LINQ to SQL için sınırlı destek vardır `ROUND` .</span><span class="sxs-lookup"><span data-stu-id="2e077-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="2e077-109">Daha fazla bilgi için bkz. [System. Math yöntemleri](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="2e077-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e077-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e077-110">See also</span></span>

- [<span data-ttu-id="2e077-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="2e077-111">Data Types and Functions</span></span>](data-types-and-functions.md)
