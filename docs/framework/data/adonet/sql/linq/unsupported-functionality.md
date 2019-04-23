---
title: Desteklenmeyen İşlev
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: 18a1a8f33a9360b4299648bcd329f4c5f2e7de88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097879"
---
# <a name="unsupported-functionality"></a><span data-ttu-id="275d8-102">Desteklenmeyen İşlev</span><span class="sxs-lookup"><span data-stu-id="275d8-102">Unsupported Functionality</span></span>
<span data-ttu-id="275d8-103">LINQ to SQL'de aşağıdaki SQL işlevleri var olan ortak dil çalışma zamanının (CLR) çeviri sunulamaz ve .NET Framework oluşturur:</span><span class="sxs-lookup"><span data-stu-id="275d8-103">In LINQ to SQL, the following SQL functionality cannot be exposed through translation of existing common language runtime (CLR) and .NET Framework constructs:</span></span>  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     <span data-ttu-id="275d8-104">Ancak `LIKE` desteklenmeyen benzer işlevselliği doğrudan çeviri var. <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="275d8-104">Although `LIKE` is not supported through direct translation, similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span> <span data-ttu-id="275d8-105">Daha fazla bilgi için bkz. <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="275d8-105">For more information, see <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.</span></span>  
  
-   `DATEDIFF`  
  
     <span data-ttu-id="275d8-106">LINQ to SQL desteği sınırlı `DATEDIFF`.</span><span class="sxs-lookup"><span data-stu-id="275d8-106">LINQ to SQL has limited support for `DATEDIFF`.</span></span> <span data-ttu-id="275d8-107">Benzer bir işlevsellik mevcut <xref:System.Data.Linq.SqlClient.SqlMethods> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="275d8-107">Similar functionality exists in the <xref:System.Data.Linq.SqlClient.SqlMethods> class.</span></span>  
  
-   `ROUND`  
  
     <span data-ttu-id="275d8-108">LINQ to SQL desteği sınırlı `ROUND`.</span><span class="sxs-lookup"><span data-stu-id="275d8-108">LINQ to SQL has limited support for `ROUND`.</span></span> <span data-ttu-id="275d8-109">Daha fazla bilgi için [System.Math yöntemleri](system-math-methods.md).</span><span class="sxs-lookup"><span data-stu-id="275d8-109">For more information, see [System.Math Methods](system-math-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275d8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="275d8-110">See also</span></span>

- [<span data-ttu-id="275d8-111">Veri Türleri ve İşlevleri</span><span class="sxs-lookup"><span data-stu-id="275d8-111">Data Types and Functions</span></span>](data-types-and-functions.md)
