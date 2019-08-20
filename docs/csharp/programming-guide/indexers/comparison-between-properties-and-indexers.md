---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589473"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin oluşturucular Özellikler gibidir. Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.  
  
|Özellik|Dizinleyic|  
|--------------|-------------|  
|Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.|Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.|  
|Basit bir ad üzerinden erişilir.|Bir dizin üzerinden erişilir.|  
|Statik veya örnek üyesi olabilir.|Örnek üye olmalıdır.|  
|Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.|Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine sahiptir. `get`|  
|Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.|Bir dizin oluşturucunun [](../../language-reference/keywords/value.md) erişimcisi,DizinOluşturucuileaynıbiçimselparametrelistesineveayrıcadeğerparametresine`set` sahiptir.|  
|[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.|Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
