---
title: LINQ to XML’de Ertelenmiş Yürütme ve Geç Değerlendirme
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 98a5010de6ea7ef46d845c6a921c54d4e7692370
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410818"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>LINQ to XML ertelenmiş yürütme ve geç değerlendirme (Visual Basic)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütmeyi kullanacak şekilde uygulanır. Bu konu, ertelenmiş yürütmenin gereksinimlerini ve avantajlarını ve bazı uygulama konularını açıklamaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Ertelenmiş yürütme, *İstenen değer gerçekten* gerekli olana kadar bir ifadenin değerlendirmesinin gecikildiği anlamına gelir. Ertelenmiş yürütme, özellikle de bir dizi zincirleme sorgu veya işleme içeren programlarda büyük veri koleksiyonlarını işlemek gerektiğinde performansı önemli ölçüde iyileştirebilir. En iyi durumda ertelenmiş yürütme, kaynak koleksiyon aracılığıyla yalnızca tek bir yinelemeyi mümkün bir şekilde sunar.  
  
 LINQ teknolojileri, hem çekirdek sınıfların üyelerinde hem de gibi <xref:System.Linq?displayProperty=nameWithType> ÇEŞITLI LINQ ad alanlarında uzantı yöntemlerinde ertelenmiş yürütmenin yoğun bir şekilde kullanılmasını kolaylaştırır <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> .  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager ve geç değerlendirme karşılaştırması  
 Ertelenmiş yürütmeyi uygulayan bir yöntem yazdığınızda, yavaş değerlendirme veya Eager değerlendirmesi kullanarak yöntemi uygulayıp uygulamamaya de karar vermeniz gerekir.  
  
- *Yavaş değerlendirmede*, her Yineleyici çağrısı sırasında kaynak koleksiyonun tek bir öğesi işlenir. Yineleyicilerin uygulanma tipik yoludur.  
  
- *Eager değerlendirmesi*sırasında, Yineleyici için ilk çağrı, tüm koleksiyonun işlenmesine neden olur. Kaynak koleksiyonun geçici bir kopyası da gerekebilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi ilk öğeyi döndürmadan önce tüm koleksiyonu sıralamak zorunda olur.  
  
 Yavaş değerlendirme genellikle koleksiyonun değerlendirmesi boyunca ek yük işlemeyi eşit bir şekilde dağıttığı ve geçici verilerin kullanımını en aza indirecek için daha iyi performans verir. Tabii ki, bazı işlemler için, ara sonuçları gerçekleştirme dışında başka bir seçenek yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticideki sonraki konu, ertelenmiş yürütmeyi gösterir:  
  
- [Ertelenmiş yürütme örneği (Visual Basic)](deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: ertelenmiş yürütme (Visual Basic)](tutorial-deferred-execution.md)
- [Kavramlar ve terminoloji (Işlevsel dönüşüm) (Visual Basic)](concepts-and-terminology-functional-transformation.md)
- [Toplama Işlemleri (Visual Basic)](aggregation-operations.md)
