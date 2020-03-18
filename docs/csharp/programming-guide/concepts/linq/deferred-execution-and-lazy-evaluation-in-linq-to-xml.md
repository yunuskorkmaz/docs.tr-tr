---
title: Linq'te Ertelenmiş Yürütme ve Tembel Değerlendirme XML 'ye (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 9cf28afb5b7b8b3047c8b1b21915ffe7409eb25e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594559"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Linq'te Ertelenmiş Yürütme ve Tembel Değerlendirme XML 'ye (C#)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır. Bu konu, ertelenmiş yürütmenin gereklerini ve avantajlarını ve bazı uygulama hususlarını açıklar.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Ertelenmiş yürütme, bir ifadenin değerlendirilmesinin *gerçekleşen* değeri gerçekten gerekli olana kadar geciktiği anlamına gelir. Ertelenmiş yürütme, özellikle zincirlenmiş sorgular veya işlemeler içeren programlarda büyük veri toplamaları işlemek zorunda olduğunuzda performansı büyük ölçüde artırabilir. En iyi durumda, ertelenmiş yürütme kaynak koleksiyonu üzerinden yalnızca tek bir yineleme sağlar.  
  
 LINQ teknolojileri, hem çekirdek <xref:System.Linq?displayProperty=nameWithType> sınıfların üyeleri hem de çeşitli LINQ ad alanlarındaki uzantı yöntemlerinde <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>ertelenmiş yürütmeyi kapsamlı bir şekilde kullanır.  
  
 Ertelenmiş yürütme, bir yineleyici bloğu içinde kullanıldığında [verim](../../../language-reference/keywords/yield.md) anahtar sözcüğü `yield-return` (deyim biçiminde) tarafından doğrudan C# dilinde desteklenir. Böyle bir yineleyici, tür <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> (veya türetilmiş tür) bir koleksiyon döndürmelidir.  
  
## <a name="eager-vs-lazy-evaluation"></a>Istekli vs Tembel Değerlendirme  
 Ertelenmiş yürütmeyi uygulayan bir yöntem yazdığınızda, yöntemi tembel değerlendirme veya istekli değerlendirme kullanarak uygulayıp uygulamayacağınıza da karar vermeniz gerekir.  
  
- *Tembel değerlendirmede,* kaynak koleksiyonun tek bir öğesi her çağrı sırasında yineleyiciye işlenir. Bu, yineleyicilerin uygulanabın tipik yoludur.  
  
- *Istekli değerlendirmede,* yineleyiciye yapılan ilk çağrı, tüm koleksiyonun işlenmesiyle sonuçlanır. Kaynak koleksiyonun geçici bir kopyası da gerekebilir. Örneğin, yöntemin <xref:System.Linq.Enumerable.OrderBy%2A> ilk öğeyi döndürmeden önce tüm koleksiyonu sıralaması gerekiyor.  
  
 Denetim, yükün değerlendirilmesi boyunca genel bilgileri eşit olarak dağıttığı ve geçici verilerin kullanımını en aza indirdiği için genellikle daha iyi performans sağlar. Tabii ki, bazı işlemler için, ara sonuçları hayata getirmekten başka bir seçenek yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticideki bir sonraki konu ertelenmiş yürütmeyi göstermektedir:  
  
- [Ertelenmiş Yürütme Örneği (C#)](./deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları Birlikte Zincirleme (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
- [Kavramlar ve Terminoloji (Fonksiyonel Dönüşüm) (C#)](./concepts-and-terminology-functional-transformation.md)
- [Toplama İşlemleri (C#)](./aggregation-operations.md)
- [yield](../../../language-reference/keywords/yield.md)
