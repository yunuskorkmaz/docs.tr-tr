---
title: LINQ to XML’de Ertelenmiş Yürütme ve Geç Değerlendirme
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 8e94b9133a2d2dd287fba91600c94460a5204b2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346402"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütmeyi kullanacak şekilde uygulanır. Bu konu, ertelenmiş yürütmenin gereksinimlerini ve avantajlarını ve bazı uygulama konularını açıklamaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Ertelenmiş yürütme, *İstenen değer gerçekten* gerekli olana kadar bir ifadenin değerlendirmesinin gecikildiği anlamına gelir. Ertelenmiş yürütme, özellikle de bir dizi zincirleme sorgu veya işleme içeren programlarda büyük veri koleksiyonlarını işlemek gerektiğinde performansı önemli ölçüde iyileştirebilir. En iyi durumda ertelenmiş yürütme, kaynak koleksiyon aracılığıyla yalnızca tek bir yinelemeyi mümkün bir şekilde sunar.  
  
 LINQ teknolojileri, hem çekirdek <xref:System.Linq?displayProperty=nameWithType> sınıfların üyelerinde hem de <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>gibi çeşitli LINQ ad alanlarında uzantı yöntemlerinde ertelenen yürütmenin kapsamlı bir şekilde kullanılmasını kolaylaştırır.  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager ve geç değerlendirme karşılaştırması  
 Ertelenmiş yürütmeyi uygulayan bir yöntem yazdığınızda, yavaş değerlendirme veya Eager değerlendirmesi kullanarak yöntemi uygulayıp uygulamamaya de karar vermeniz gerekir.  
  
- *Yavaş değerlendirmede*, her Yineleyici çağrısı sırasında kaynak koleksiyonun tek bir öğesi işlenir. Yineleyicilerin uygulanma tipik yoludur.  
  
- *Eager değerlendirmesi*sırasında, Yineleyici için ilk çağrı, tüm koleksiyonun işlenmesine neden olur. Kaynak koleksiyonun geçici bir kopyası da gerekebilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yönteminin, ilk öğeyi döndürmadan önce tüm koleksiyonu sıralaması gerekir.  
  
 Yavaş değerlendirme genellikle koleksiyonun değerlendirmesi boyunca ek yük işlemeyi eşit bir şekilde dağıttığı ve geçici verilerin kullanımını en aza indirecek için daha iyi performans verir. Tabii ki, bazı işlemler için, ara sonuçları gerçekleştirme dışında başka bir seçenek yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticideki sonraki konu, ertelenmiş yürütmeyi gösterir:  
  
- [Ertelenmiş yürütme örneği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Kavramlar ve terminoloji (Işlevsel dönüşüm) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Toplama Işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
