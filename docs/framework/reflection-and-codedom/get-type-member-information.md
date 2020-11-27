---
title: 'Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini alma'
description: System. Reflection ad alanını kullanarak, yansıma ile tür ve üye bilgilerini almayı öğrenin.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 771917bb2ae5cae56c775ae23119d5eda9701df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266330"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="9a9cd-103">Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="9a9cd-103">How to: Get type and member information by using reflection</span></span>

<span data-ttu-id="9a9cd-104"><xref:System.Reflection>Ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="9a9cd-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="9a9cd-105">Bu makalede, aşağıdaki yöntemlerden biri gösterilmektedir <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9a9cd-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9a9cd-106">Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="9a9cd-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="9a9cd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9a9cd-107">Example</span></span>

<span data-ttu-id="9a9cd-108">Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:</span><span class="sxs-lookup"><span data-stu-id="9a9cd-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="9a9cd-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a9cd-109">See also</span></span>

- [<span data-ttu-id="9a9cd-110">Uygulama etki alanlarıyla program</span><span class="sxs-lookup"><span data-stu-id="9a9cd-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="9a9cd-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="9a9cd-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="9a9cd-112">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="9a9cd-112">Use application domains</span></span>](../app-domains/use.md)
