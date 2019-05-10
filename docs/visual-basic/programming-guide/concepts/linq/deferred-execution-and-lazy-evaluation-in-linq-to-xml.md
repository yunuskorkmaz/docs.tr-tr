---
title: Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: a8d3bec16fa8ca7f5c587a9fdbb6caac53b74efe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641994"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (Visual Basic)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır. Bu konuda, ertelenmiş yürütme ve bazı uygulama konuları avantajları ve gereksinimleri açıklanmaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Bir ifadenin değerlendirmesine kadar Gecikmeli yürütme anlamına gelir ertelenmiş kendi *gerçekleşen* değeri gerçekten gereklidir. İçeren bir dizi zincirleme sorguları veya işlemeleri programlarda özellikle büyük veri koleksiyonları yönlendirme olduğunda ertelenmiş yürütme performansı büyük ölçüde artırabilir. En iyi durumda, yalnızca tek bir yineleme kaynak koleksiyonu aracılığıyla ertelenmiş yürütme sağlar.  
  
 LINQ teknolojileri kapsamlı ertelenmiş yürütme iki çekirdek üyelerinde kullanabilmesine <xref:System.Linq?displayProperty=nameWithType> sınıflarını ve çeşitli LINQ ad alanında uzantı yöntemlerini gibi <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>İstekli vs. Geç değerlendirme  
 Ertelenmiş yürütme uygulayan bir Metoda yazdığınızda, ayrıca uygulanmayacağını geç değerlendirme veya istekli değerlendirme kullanarak yöntemini karar vermeniz gerekir.  
  
- İçinde *geç değerlendirme*, tek bir kaynak koleksiyonu öğesinin yineleyici yapılan her çağrı sırasında işlenir. Yineleyiciler uygulanan normal şekilde budur.  
  
- İçinde *istekli değerlendirme*, yineleyici yapılan ilk çağrı işlenmekte olan tüm koleksiyonda neden olur. Kaynak koleksiyonu geçici bir kopyası gerekli olabilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> ilk öğeyi döndürür önce tüm koleksiyon sıralama yöntemi vardır.  
  
 Geç değerlendirme genellikle daha iyi performans verir, çünkü ek yükü işleme koleksiyon Değerlendirme boyunca eşit olarak dağıtır ve geçici veri kullanımını en aza indirir. Elbette, bazı işlemler için Ara sonuçlar gerçekleştirmek üzere daha diğer seçeneği yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticide bir sonraki konu ertelenmiş yürütme gösterilmektedir:  
  
- [Ertelenmiş yürütme örneği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Kavramlar ve terimler (işlevsel dönüşüm) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Toplama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
