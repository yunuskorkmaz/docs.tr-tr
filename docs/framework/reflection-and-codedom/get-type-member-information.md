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
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Nasıl yapılır: yansıma kullanarak tür ve üye bilgilerini alma
<xref:System.Reflection> ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir. Bu makalede, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>bu yöntemlerden biri gösterilmektedir. Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla program](../app-domains/application-domains.md#programming-with-application-domains)
- [Yansıma](reflection.md)
- [Uygulama etki alanlarını kullanma](../app-domains/use.md)
