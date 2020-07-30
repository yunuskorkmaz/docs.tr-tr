---
title: Özellikler ve Dizin oluşturucular arasında karşılaştırma-C# Programlama Kılavuzu
description: C# içindeki dizin oluşturucularının özellikler gibi nasıl olduğunu karşılaştırın. Bazı farklılıklar haricinde, özellik erişimcileri için tanımlanan kurallar Dizin Oluşturucu erişimcileri için geçerlidir.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: b83ce3db3d4b53fb7bcc5f3b3cd603a375d5d473
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299181"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin oluşturucular Özellikler gibidir. Aşağıdaki tabloda gösterilen farklar dışında, özellik erişimcileri için tanımlanan tüm kurallar Dizin Oluşturucu erişimcileri için de geçerlidir.  
  
|Özellik|Dizin Oluşturucu|  
|--------------|-------------|  
|Yöntemlerin ortak veri üyeleri gibi çağrılmasına izin verir.|Nesne üzerinde dizi gösterimi kullanılarak bir nesne iç koleksiyonunun öğelerine erişilmesine izin verir.|  
|Basit bir ad üzerinden erişilir.|Bir dizin üzerinden erişilir.|  
|Statik veya örnek üyesi olabilir.|Örnek üye olmalıdır.|  
|Özelliğin [Get](../../language-reference/keywords/get.md) erişimcisinin parametresi yok.|`get`Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine sahiptir.|  
|Bir özelliğin [set](../../language-reference/keywords/set.md) erişimcisi örtük `value` parametresi içerir.|`set`Bir dizin oluşturucunun erişimcisi, Dizin Oluşturucu ile aynı biçimsel parametre listesine ve ayrıca [değer](../../language-reference/keywords/value.md) parametresine sahiptir.|  
|[Otomatik uygulanan özelliklerle](../classes-and-structs/auto-implemented-properties.md)kısaltılmış sözdizimini destekler.|Yalnızca Get Dizin oluşturucular için ifade gövdeli üyelerini destekler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
