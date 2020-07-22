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
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865326"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="0448f-103">Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="0448f-103">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="0448f-104"><xref:System.Reflection>Ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir.</span><span class="sxs-lookup"><span data-stu-id="0448f-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="0448f-105">Bu makalede, aşağıdaki yöntemlerden biri gösterilmektedir <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0448f-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0448f-106">Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="0448f-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="0448f-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0448f-107">Example</span></span>

<span data-ttu-id="0448f-108">Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:</span><span class="sxs-lookup"><span data-stu-id="0448f-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="0448f-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0448f-109">See also</span></span>

- [<span data-ttu-id="0448f-110">Uygulama etki alanlarıyla program</span><span class="sxs-lookup"><span data-stu-id="0448f-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="0448f-111">Yansıma</span><span class="sxs-lookup"><span data-stu-id="0448f-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="0448f-112">Uygulama etki alanlarını kullanma</span><span class="sxs-lookup"><span data-stu-id="0448f-112">Use application domains</span></span>](../app-domains/use.md)
