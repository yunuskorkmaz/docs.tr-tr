---
title: İşlevsel ve Yordamsal Programlama (LINQ - XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e87114d2edcda4b2df14eb2d84f62ebe9638b5eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594254"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>İşlevsel ve Yordamsal Programlama (LINQ - XML) (C#)
Çeşitli XML uygulamaları vardır:  
  
- Bazı uygulamalar kaynak XML belgeleri alır ve kaynak belgelerden farklı bir biçimde yeni XML belgeleri üretir.  
  
- Bazı uygulamalar kaynak XML belgeleri alır ve html veya CSV metin dosyaları gibi tamamen farklı bir biçimde sonuç belgeleri üretir.  
  
- Bazı uygulamalar kaynak XML belgelerini alır ve kayıtları veritabanına ekler.  
  
- Bazı uygulamalar veritabanı gibi başka bir kaynaktan veri alır ve bu kaynaktan XML belgeleri oluşturur.  
  
 Bunlar XML uygulama türlerinin tümü değildir, ancak bunlar bir XML programcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili kümesidir.  
  
 Bu tür uygulamaların tümlerinde, bir geliştiricinin kaldırabileceği iki zıt yaklaşım vardır:  
  
- Bildirimsel bir yaklaşım la fonksiyonel yapı.  
  
- Yordam kodu kullanarak bellek tesisi XML ağaç modifikasyonu.  
  
 LINQ to XML her iki yaklaşımı da destekler.  
  
 İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekille tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.  
  
 Bir XML ağacını yerinde değiştirirken, bellek içi bir XML ağacında düğümler arasında geçiş yapan ve gezinen kod yazar, düğümleri gerektiği gibi ekler, siler ve değiştirir.  
  
 Her iki yaklaşımla LINQ xml kullanabilirsiniz. Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız. Ancak, iki yaklaşımın yapısı ve hedefleri çok farklıdır. Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olacak ve daha fazla veya daha az bellek kullanır. Buna ek olarak, bir veya diğer yaklaşım yazmak ve daha sadaabilir kod verim daha kolay olacaktır.  
  
 Zıt iki yaklaşımı görmek için Bellek [Içi XML Ağaç Modifikasyonu ve Fonksiyonel Yapı (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)bakın.  
  
 İşlevsel dönüşümleri yazma konusunda bir öğretici için Bkz. [XML'in Saf İşlevsel Dönüşümleri (C#)](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Programlamaya Genel Bakış (C#)](./linq-to-xml-overview.md)
