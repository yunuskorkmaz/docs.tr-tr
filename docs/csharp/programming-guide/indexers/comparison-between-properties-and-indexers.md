---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712136"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin oluşturucular Özellikler gibidir. Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.  
  
|Özellik|Dizin Oluşturucu|  
|--------------|-------------|  
|Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.|Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.|  
|Basit bir ad üzerinden erişilir.|Bir dizin üzerinden erişilir.|  
|Statik veya örnek üyesi olabilir.|Örnek üye olmalıdır.|  
|Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.|Bir dizin oluşturucunun `get` erişimcisi, Indexer ile aynı biçimsel parametre listesine sahiptir.|  
|Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.|Bir dizin oluşturucunun `set` erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine ve ayrıca [değer](../../language-reference/keywords/value.md) parametresine sahiptir.|  
|[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.|Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Veri Erişimi](../classes-and-structs/properties.md)
