---
title: İşlevsel ve yordamsal programlama (LINQ to XML) (C#)
description: XML işlemek için LINQ to XML hem yordamsal, hem de bellek içi XML ağacı değişikliğini ve bildirim temelli bir yaklaşım kullanan işlevsel oluşturmayı destekler.
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: e19f9311c56f4fe2c5e7e5f228aca6c03c6fe04d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103660"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>İşlevsel ve yordamsal programlama (LINQ to XML) (C#)
Çeşitli türlerdeki XML uygulamaları vardır:  
  
- Bazı uygulamalar kaynak XML belgelerini alır ve kaynak belgelerden farklı bir şekilde yeni XML belgeleri oluşturur.  
  
- Bazı uygulamalar kaynak XML belgelerini alır ve sonuç belgelerini HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde oluşturur.  
  
- Bazı uygulamalar kaynak XML belgelerini alır ve bir veritabanına kayıt ekler.  
  
- Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri alır ve bundan XML belgesi oluşturur.  
  
 Bunlar, XML uygulaması türlerinin hepsi değildir, ancak bunlar bir XML Programlayıcısının uygulamak zorunda olduğu işlevsellik türlerinin temsili bir kümesidir.  
  
 Bu tür uygulamaların tümünde, bir geliştiricinin uygulayabileceğiniz iki yaklaşım vardır:  
  
- Bildirim temelli bir yaklaşım kullanılarak işlevsel oluşturma.  
  
- Yordamsal kodu kullanarak bellek içi XML ağacı değişikliği.  
  
 LINQ to XML her iki yaklaşımı destekler.  
  
 İşlevsel yaklaşımı kullanırken, kaynak belgeleri alan ve istenen şekle sahip tamamen yeni sonuç belgeleri oluşturan dönüşümler yazarsınız.  
  
 Bir XML ağacını yerinde değiştirirken, düğüm içi bir XML ağacındaki düğümlerde geçen ve gezinen, düğümleri ekleme, silme ve değiştirme gibi bir kod yazın.  
  
 LINQ to XML iki yaklaşımla de kullanabilirsiniz. Aynı sınıfları ve bazı durumlarda aynı yöntemleri kullanırsınız. Ancak, iki yaklaşımdan oluşan yapı ve hedefler çok farklıdır. Örneğin, farklı durumlarda, bir veya diğer yaklaşım genellikle daha iyi performansa sahip olur ve daha fazla veya daha az bellek kullanır. Buna ek olarak, bir veya başka bir yaklaşım daha fazla erişilebilir kod yazmak ve sağlamak daha kolay olacaktır.  
  
 Bu iki yaklaşımı görmek için bkz. [bellek ıçı XML ağacı değişikliği ve Işlevsel oluşturma (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 İşlev dönüştürmeleri yazma hakkında bir öğretici için bkz. [XML 'In saf Işlevsel dönüştürmeleri (C#)](./introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](./linq-to-xml-overview.md)
