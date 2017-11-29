---
title: "İşlev vs. Yordam programlama (LINQ-XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea1015a5-d4c8-4d79-8e1e-ba17a40a4f39
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e47ff583146ab4258e219537cdc01821009e965
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="functional-vs-procedural-programming-linq-to-xml-visual-basic"></a>İşlev vs. Yordam programlama (LINQ-XML) (Visual Basic)
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
  
 Contrasted iki yaklaşım görmek için bkz: [bellek içi XML ağaç değişikliği vs. İşlev yapımı (LINQ-XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/in-memory-xml-tree-modification-vs-functional-construction.md).  
  
 İşlev dönüşümleri yazma bir öğretici için bkz: [saf işlevsel dönüşümleri XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/pure-functional-transformations-of-xml.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
