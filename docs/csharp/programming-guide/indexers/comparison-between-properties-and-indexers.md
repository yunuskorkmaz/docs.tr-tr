---
title: "Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 102a6a97726fa19fcba0e6f19876a3935e8625f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Özellikler ve Dizin Oluşturucular Arasında Karşılaştırma (C# Programlama Kılavuzu)
Dizin oluşturucular gibi özelliklerdir. Aşağıdaki tabloda gösterilen farklar dışında özellik erişimcisi için tanımlanan tüm kurallar dizin oluşturucu erişimciler için de geçerlidir.  
  
|Özellik|Dizin Oluşturucu|  
|--------------|-------------|  
|Genel veri üyelerini değilmiş gibi çağrılacak yöntemleri sağlar.|Bir iç nesne üzerinde dizi gösterim biçimini kullanarak erişilmesi için bir nesne koleksiyonu öğelerinin sağlar.|  
|Basit bir ad erişilir.|Bir dizin erişilir.|  
|Statik veya örnek üyesine olabilir.|Bir örnek üyesi olması gerekir.|  
|A [almak](../../../csharp/language-reference/keywords/get.md) bir özelliğin erişimcisine sahip herhangi bir parametre.|A `get` erişimci bir dizin oluşturucu aynı dizin oluşturucu biçimsel parametresi listesine sahiptir.|  
|A [ayarlamak](../../../csharp/language-reference/keywords/set.md) bir özellik erişimcisi içeren örtük `value` parametresi.|A `set` bir dizin oluşturucu erişimcisine sahip aynı biçimsel parametresi listenin dizin oluşturucu olarak ve ayrıca [değeri](../../../csharp/language-reference/keywords/value.md) parametresi.|  
|Destekler kısaltılmış sözdizimi ile [Auto-Implemented özellikleri](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).|Kısaltılmış sözdizimi desteklemez.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md)  
 [Özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md)
