---
title: 'Nasıl yapılır: yansıma kullanarak tür ve üye bilgilerini alma'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130211"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="28d52-102">Nasıl yapılır: yansıma kullanarak tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="28d52-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="28d52-103"><xref:System.Reflection> Ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="28d52-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="28d52-104">Bu makalede, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>aşağıdaki yöntemlerden biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="28d52-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="28d52-105">Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="28d52-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="28d52-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="28d52-106">Example</span></span>

<span data-ttu-id="28d52-107">Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:</span><span class="sxs-lookup"><span data-stu-id="28d52-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="28d52-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28d52-108">See also</span></span>

- [<span data-ttu-id="28d52-109">Uygulama etki alanlarıyla program</span><span class="sxs-lookup"><span data-stu-id="28d52-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="28d52-110">Yansıma</span><span class="sxs-lookup"><span data-stu-id="28d52-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="28d52-111">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="28d52-111">Use application domains</span></span>](../app-domains/use.md)
