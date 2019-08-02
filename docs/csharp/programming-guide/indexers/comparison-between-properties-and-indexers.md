---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671676"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin oluşturucular Özellikler gibidir. Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.  
  
|Özellik|Dizinleyic|  
|--------------|-------------|  
|Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.|Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.|  
|Basit bir ad üzerinden erişilir.|Bir dizin üzerinden erişilir.|  
|Statik veya örnek üyesi olabilir.|Örnek üye olmalıdır.|  
|Özelliğin [Get](../../../csharp/language-reference/keywords/get.md) erişimcisinin parametresi yok.|Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine sahiptir. `get`|  
|Bir özelliğin [set](../../../csharp/language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.|Bir dizin oluşturucunun [](../../../csharp/language-reference/keywords/value.md) erişimcisi,DizinOluşturucuileaynıbiçimselparametrelistesineveayrıcadeğerparametresine`set` sahiptir.|  
|[Otomatik uygulanan özelliklerle](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.|Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Dizin Oluşturucular](../../../csharp/programming-guide/indexers/index.md)
- [Özellikler](../../../csharp/programming-guide/classes-and-structs/properties.md)
