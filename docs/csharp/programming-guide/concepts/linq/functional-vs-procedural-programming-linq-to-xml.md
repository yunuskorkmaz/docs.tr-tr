---
title: İşlev vs. Yordam programlama (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: 16d78e967fd5379940ac93c82e3bb59c60941e58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33328220"
---
# <a name="functional-vs-procedural-programming-linq-to-xml-c"></a>İşlev vs. Yordam programlama (LINQ-XML) (C#)
XML uygulamaları çeşitli türleri şunlardır:  
  
-   Bazı uygulamalar kaynak XML belgelerini almak ve kaynak belgeleri değerinden farklı bir şeklinde olan yeni XML belgeleri oluşturabilir.  
  
-   Bazı uygulamalar kaynak XML belgelerini ayırın ve HTML veya CSV metin dosyaları gibi tamamen farklı bir form sonuç belgelerde üretir.  
  
-   Bazı uygulamalar kaynak XML belgelerini almak ve bir veritabanına kayıtları ekleyin.  
  
-   Bazı uygulamalar, bir veritabanı gibi başka bir kaynaktan veri almak ve XML belgeleri oluşturun.  
  
 Bu tüm XML uygulama türlerini değildir, ancak bunlar temsilcisi uygulamak için bir XML Programcı sahip işlevselliği türlerini kümesidir.  
  
 Tüm bu tür uygulamalar, bir geliştirici sürebilir karşıt iki yaklaşım vardır:  
  
-   Bildirim temelli bir yaklaşım kullanarak işlev oluşturma.  
  
-   Bellek içi XML ağaç değişikliği yordam kodu kullanarak.  
  
 LINQ-XML her iki yaklaşımın destekler.  
  
 İşlev yaklaşımı kullanarak, kaynak belgeleri yapan ve oluşturmak istediğiniz şekli tamamen yeni sonuç belgelerle dönüşümleri yazma.  
  
 Bir XML ağacı yerinde değiştirirken, ekleme, silme ve gerektiğinde düğümleri değiştirme erişir ve bir bellek içi XML ağacında düğümler üzerinden gider kod yazın.  
  
 LINQ-XML her iki yaklaşım ile kullanabilirsiniz. Aynı sınıflarını kullanın ve bazı durumlarda aynı yöntemleri. Ancak, iki yaklaşım, hedefler ve yapısı çok farklı değildir. Örneğin, farklı durumlarda bir ya da bir yaklaşım genellikle daha iyi performans sahip ve fazla veya az bellek kullanır. Ayrıca, bir ya da bir yaklaşım yazmak ve daha fazla Bakımı yapılabilir kodu elde etmek daha kolay olacaktır.  
  
 Contrasted iki yaklaşım görmek için bkz: [bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).  
  
 İşlev dönüşümleri yazma bir öğretici için bkz: [saf işlevsel dönüşümleri XML (C#)](../../../../csharp/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
