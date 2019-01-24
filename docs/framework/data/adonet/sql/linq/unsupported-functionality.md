---
title: Desteklenmeyen işlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 5022c9011c2aac5b3272e359f991c40236a5673f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686711"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="657b3-102">Desteklenmeyen işlev</span><span class="sxs-lookup"><span data-stu-id="657b3-102">Unsupported Functionality</span></span>
<span data-ttu-id="657b3-103">LINQ to SQL'de aşağıdaki SQL işlevleri var olan ortak dil çalışma zamanının (CLR) çeviri sunulamaz ve .NET Framework oluşturur:</span><span class="sxs-lookup"><span data-stu-id="657b3-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="657b3-104">Ancak `LIKE` desteklenmeyen benzer işlevselliği doğrudan çeviri var. <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="657b3-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="657b3-105">Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="657b3-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="657b3-106">LINQ to SQL desteği sınırlı `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="657b3-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="657b3-107">Benzer bir işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="657b3-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="657b3-108">LINQ to SQL desteği sınırlı `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="657b3-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="657b3-109">Daha fazla bilgi için [System.Math yöntemleri](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="657b3-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="657b3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="657b3-110">See also</span></span>
- [<span data-ttu-id="657b3-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="657b3-111">Data Types and Functions</span></span>](data-types-and-functions.md)
