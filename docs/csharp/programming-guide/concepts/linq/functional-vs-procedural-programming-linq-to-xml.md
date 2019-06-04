---
title: İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 1f713e54cefed5b1fcf8c29cd88aa7587a737327
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486952"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)
XML uygulama çeşitli türleri şunlardır:  
  
- Bazı uygulamalar kaynak XML belgelerini alın ve kaynak belgeleri değerinden farklı bir şekil olan yeni XML belgeleri oluşturmak.  
  
- Bazı uygulamalar kaynak XML belgelerini alın ve sonuç belgeleri, HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde üretmek.  
  
- Bazı uygulamalar kaynak XML belgelerini alın ve kayıtları bir veritabanına Ekle.  
  
- Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri almak ve XML belgeleri oluşturun.  
  
 Bu XML uygulama türleri tümünün değildir, ancak bir temsilci uygulamak için bir XML Programcı olan işlevselliği türleri kümesini şunlardır.  
  
 Tüm bu tür uygulamalar, bir geliştirici alabilir ve karşıt iki yaklaşım vardır:  
  
- Bildirim temelli bir yaklaşım kullanarak işlevsel oluşturma.  
  
- Yordam kodu kullanarak bellek içi XML ağacı değişikliği.  
  
 LINQ to XML her iki yaklaşım destekler.  
  
 İşlevsel yaklaşım kullanırken, kaynak belgelerini alın ve istediğiniz şekli ile tamamen yeni sonucu belgeleri oluşturmak dönüşümleri yazın.  
  
 Bir XML ağacı yerinde değiştirirken, ekleme, silme ve düğümleri gerektiği şekilde değiştirme erişir ve bir bellek içi XML ağacı düğümler üzerinden gider kod yazın.  
  
 LINQ to XML ile her iki yöntemle kullanabilirsiniz. Aynı sınıfları kullanın ve bazı durumlarda aynı yöntemleri. Ancak, iki yaklaşım, hedefler ve yapısı çok farklıdır. Örneğin, farklı durumlarda, bir ya da diğer bir yaklaşım genellikle daha iyi performans sunar ve daha fazla veya daha az bellek kullanır. Ayrıca, bir ya da diğer bir yaklaşım yazma ve daha fazla sürdürülebilir kod yield daha kolay olacaktır.  
  
 Karşıtlıklar iki yaklaşım için bkz [bellek içi XML ağacı değişikliği ve. İşlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 İşlevsel dönüşümlere yazma ilişkin bir öğretici için bkz. [saf işlevsel dönüşümleri XML (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
