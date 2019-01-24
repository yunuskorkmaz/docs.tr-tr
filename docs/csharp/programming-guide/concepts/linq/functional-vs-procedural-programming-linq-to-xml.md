---
title: İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 0f45efabd0e2092325ac18c7fbf195c3338acf87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536717"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>İşlevsel ve Yordam programlama karşılaştırması (LINQ to XML) (C#)
XML uygulama çeşitli türleri şunlardır:  
  
-   Bazı uygulamalar kaynak XML belgelerini alın ve kaynak belgeleri değerinden farklı bir şekil olan yeni XML belgeleri oluşturmak.  
  
-   Bazı uygulamalar kaynak XML belgelerini alın ve sonuç belgeleri, HTML veya CSV metin dosyaları gibi tamamen farklı bir biçimde üretmek.  
  
-   Bazı uygulamalar kaynak XML belgelerini alın ve kayıtları bir veritabanına Ekle.  
  
-   Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri almak ve XML belgeleri oluşturun.  
  
 Bu XML uygulama türleri tümünün değildir, ancak bir temsilci uygulamak için bir XML Programcı olan işlevselliği türleri kümesini şunlardır.  
  
 Tüm bu tür uygulamalar, bir geliştirici alabilir ve karşıt iki yaklaşım vardır:  
  
-   Bildirim temelli bir yaklaşım kullanarak işlevsel oluşturma.  
  
-   Yordam kodu kullanarak bellek içi XML ağacı değişikliği.  
  
 LINQ to XML her iki yaklaşım destekler.  
  
 İşlevsel yaklaşım kullanırken, kaynak belgelerini alın ve istediğiniz şekli ile tamamen yeni sonucu belgeleri oluşturmak dönüşümleri yazın.  
  
 Bir XML ağacı yerinde değiştirirken, ekleme, silme ve düğümleri gerektiği şekilde değiştirme erişir ve bir bellek içi XML ağacı düğümler üzerinden gider kod yazın.  
  
 LINQ to XML ile her iki yöntemle kullanabilirsiniz. Aynı sınıfları kullanın ve bazı durumlarda aynı yöntemleri. Ancak, iki yaklaşım, hedefler ve yapısı çok farklıdır. Örneğin, farklı durumlarda, bir ya da diğer bir yaklaşım genellikle daha iyi performans sunar ve daha fazla veya daha az bellek kullanır. Ayrıca, bir ya da diğer bir yaklaşım yazma ve daha fazla sürdürülebilir kod yield daha kolay olacaktır.  
  
 Karşıtlıklar iki yaklaşım için bkz [bellek içi XML ağacı değişikliği ve. İşlevsel oluşturma (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 İşlevsel dönüşümlere yazma ilişkin bir öğretici için bkz. [saf işlevsel dönüşümleri XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
