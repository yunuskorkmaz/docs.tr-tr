---
title: LINQ to XML ertelenmiş yürütme ve geç değerlendirme (C#)
description: Sorgu ve eksen işlemleri, C# ' de ertelenmiş yürütmeyi kullanabilir. Ertelenmiş yürütmenin ve uygulama konularının gereksinimleri ve avantajları hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 8559505572404f895d75e0d9895f9ae2c07b795e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105466"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>LINQ to XML ertelenmiş yürütme ve geç değerlendirme (C#)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütmeyi kullanacak şekilde uygulanır. Bu konu, ertelenmiş yürütmenin gereksinimlerini ve avantajlarını ve bazı uygulama konularını açıklamaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Ertelenmiş yürütme, *İstenen değer gerçekten* gerekli olana kadar bir ifadenin değerlendirmesinin gecikildiği anlamına gelir. Ertelenmiş yürütme, özellikle de bir dizi zincirleme sorgu veya işleme içeren programlarda büyük veri koleksiyonlarını işlemek gerektiğinde performansı önemli ölçüde iyileştirebilir. En iyi durumda ertelenmiş yürütme, kaynak koleksiyon aracılığıyla yalnızca tek bir yinelemeyi mümkün bir şekilde sunar.  
  
 LINQ teknolojileri, hem çekirdek sınıfların üyelerinde hem de gibi <xref:System.Linq?displayProperty=nameWithType> ÇEŞITLI LINQ ad alanlarında uzantı yöntemlerinde ertelenmiş yürütmenin yoğun bir şekilde kullanılmasını kolaylaştırır <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> .  
  
 Ertelenmiş yürütme, [yield](../../../language-reference/keywords/yield.md) `yield-return` bir yineleyici bloğunda kullanılan yield anahtar sözcüğü (deyimin biçiminde) tarafından doğrudan C# dilinde desteklenir. Bu tür bir yineleyici, <xref:System.Collections.IEnumerator> ya da <xref:System.Collections.Generic.IEnumerator%601> (ya da türetilmiş bir tür) bir koleksiyon döndürmelidir.  
  
## <a name="eager-vs-lazy-evaluation"></a>Eager ve geç değerlendirme karşılaştırması  
 Ertelenmiş yürütmeyi uygulayan bir yöntem yazdığınızda, yavaş değerlendirme veya Eager değerlendirmesi kullanarak yöntemi uygulayıp uygulamamaya de karar vermeniz gerekir.  
  
- *Yavaş değerlendirmede*, her Yineleyici çağrısı sırasında kaynak koleksiyonun tek bir öğesi işlenir. Yineleyicilerin uygulanma tipik yoludur.  
  
- *Eager değerlendirmesi*sırasında, Yineleyici için ilk çağrı, tüm koleksiyonun işlenmesine neden olur. Kaynak koleksiyonun geçici bir kopyası da gerekebilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi ilk öğeyi döndürmadan önce tüm koleksiyonu sıralamak zorunda olur.  
  
 Yavaş değerlendirme genellikle koleksiyonun değerlendirmesi boyunca ek yük işlemeyi eşit bir şekilde dağıttığı ve geçici verilerin kullanımını en aza indirecek için daha iyi performans verir. Tabii ki, bazı işlemler için, ara sonuçları gerçekleştirme dışında başka bir seçenek yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticideki sonraki konu, ertelenmiş yürütmeyi gösterir:  
  
- [Ertelenmiş yürütme örneği (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: sorguları birlikte zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Kavramlar ve terminoloji (Işlevsel dönüşüm) (C#)](./concepts-and-terminology-functional-transformation.md)
- [Toplama Işlemleri (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
