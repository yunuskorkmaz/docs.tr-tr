---
description: 'Daha fazla bilgi edinin: desteklenmeyen Işlevler'
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5c44dd4aad2d2ee4ec5e00ce42f4de9400cea478
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99680895"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="36c24-103">Desteklenmeyen İşlev</span><span class="sxs-lookup"><span data-stu-id="36c24-103">Unsupported Functionality</span></span>

<span data-ttu-id="36c24-104">LINQ to SQL, aşağıdaki SQL işlevselliği mevcut ortak dil çalışma zamanının (CLR) ve .NET Framework yapılarının çevirisi aracılığıyla sunulamaz:</span><span class="sxs-lookup"><span data-stu-id="36c24-104">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
- `STDDEV`  
  
- `LIKE`  
  
     <span data-ttu-id="36c24-105">`LIKE`Doğrudan çeviri aracılığıyla desteklenmese de, sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="36c24-105">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="36c24-106">Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="36c24-106">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
- `DATEDIFF`  
  
     <span data-ttu-id="36c24-107">LINQ to SQL için sınırlı destek vardır `DATEDIFF` .</span><span class="sxs-lookup"><span data-stu-id="36c24-107">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="36c24-108">Sınıfında benzer işlevler bulunur <xref:System.Data.Linq.SqlClient.SqlMethods> .</span><span class="sxs-lookup"><span data-stu-id="36c24-108">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
- `ROUND`  
  
     <span data-ttu-id="36c24-109">LINQ to SQL için sınırlı destek vardır `ROUND` .</span><span class="sxs-lookup"><span data-stu-id="36c24-109">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="36c24-110">Daha fazla bilgi için bkz. [System. Math yöntemleri](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="36c24-110">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c24-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36c24-111">See also</span></span>

- [<span data-ttu-id="36c24-112">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="36c24-112">Data Types and Functions</span></span>](data-types-and-functions.md)
