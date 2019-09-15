---
title: 'Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini al'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: da71845ea276267220636cfd661465ea02b2b50d
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972923"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a>Nasıl yapılır: Yansıma kullanarak tür ve üye bilgilerini al
<xref:System.Reflection> Ad alanı türler ve üyeleri hakkında bilgi almak için birçok yöntem içerir. Bu makalede, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>aşağıdaki yöntemlerden biri gösterilmektedir. Daha fazla bilgi için bkz. [yansımaya genel bakış](reflection.md).
  
## <a name="example"></a>Örnek

Aşağıdaki örnek, yansıma kullanarak tür ve üye bilgilerini edinir:

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama etki alanlarıyla program](../app-domains/application-domains.md#programming-with-application-domains)
- [Yansıma](reflection.md)
- [Uygulama etki alanlarını kullanma](../app-domains/use.md)
