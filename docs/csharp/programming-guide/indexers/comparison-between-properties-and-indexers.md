---
title: Özellikler ve Dizinleyiciler Arasında Karşılaştırma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712136"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin leyiciler özellikler gibidir. Aşağıdaki tabloda gösterilen farklar dışında, özellik erişime girenler için tanımlanan tüm kurallar dizinleyici erişime girenler için de geçerlidir.  
  
|Özellik|Dizin Oluşturucu|  
|--------------|-------------|  
|Yöntemlerin genel veri üyesi gibi çağrılmasını sağlar.|Nesnenin iç koleksiyonunun öğelerine, nesnenin kendisinde dizi gösterimi kullanılarak erişilmesine izin verir.|  
|Basit bir isimle erişildi.|Bir dizin üzerinden erişilir.|  
|Statik veya örnek üye olabilir.|Örnek üye olmalı.|  
|Bir özelliğin [erişime](../../language-reference/keywords/get.md) erişiminin parametreleri yoktur.|Bir `get` dizinleyicinin erişimi, dizinleyiciyle aynı resmi parametre listesine sahiptir.|  
|Bir özelliğin [ayarlanmış](../../language-reference/keywords/set.md) bir erişimcisi örtük `value` parametre içerir.|Bir `set` dizin leyicinin erişicisi, dizinleyiciyle ve [değer](../../language-reference/keywords/value.md) parametresi ile aynı resmi parametre listesine sahiptir.|  
|[Otomatik Uygulanan Özellikler](../classes-and-structs/auto-implemented-properties.md)ile kısaltılmış sözdizimini destekler.|Yalnızca dizin oluşturma için ifade gövdeli üyeleri destekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
