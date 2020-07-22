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
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini alma
<xref:System.Reflection>Ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir. Bu makalede, aşağıdaki yöntemlerden biri gösterilmektedir <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla program](../app-domains/application-domains.md#programming-with-application-domains)
- [Yansıma](reflection.md)
- [Uygulama etki alanlarını kullanma](../app-domains/use.md)
