---
title: Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: eade2fe987ecbc399c2e2a8a65e74e3beab5e123
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Ertelenmiş yürütme ve geç değerlendirme LINQ-XML (Visual Basic)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır. Bu konuda, ertelenmiş yürütme ve bazı uygulama konuları avantajları ve gereksinimleri açıklanmaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Bir ifadenin değerlendirmesine kadar Gecikmeli yürütme anlamına gelir ertelenmiş kendi *gerçekleşen* değeri gerçekte gereklidir. Bir dizi zincirleme sorguları ya da işlemeleri içeren programlarda özellikle büyük veri koleksiyonları yönlendirme olduğunda ertelenmiş yürütme önemli ölçüde performansını iyileştirebilir. En iyi durumda yalnızca tek bir yineleme kaynak koleksiyonu aracılığıyla ertelenmiş yürütme sağlar.  
  
 LINQ teknolojileri ertelenmiş yürütme kapsamlı kullanımını her iki çekirdek üyelerinde olun <xref:System.Linq?displayProperty=nameWithType> sınıfları ve çeşitli LINQ ad alanlarında genişletme yöntemleri gibi <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>İstekli vs. Geç değerlendirme  
 Ertelenmiş yürütme uygulayan bir yöntem yazdığınızda, ayrıca geç değerlendirme veya istekli değerlendirme kullanarak yöntemini uygulamak karar vermeniz gerekir.  
  
-   İçinde *geç değerlendirme*, tek bir öğeye kaynak koleksiyonunun yineleyici yapılan her çağrı sırasında işlenir. Bu, hangi yineleyiciler uygulanan tipik yoludur.  
  
-   İçinde *istekli değerlendirme*, yineleyici ilk çağrıda işlenmekte olan tüm koleksiyonunda neden olur. Kaynak koleksiyonu geçici bir kopyasını de gerekli olabilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi sahip ilk öğe döndürmeden önce tüm koleksiyon sıralamak.  
  
 Ek görevlerin işlenmesi koleksiyon Değerlendirme boyunca eşit olarak dağıtır ve geçici verileri kullanımını en aza indirir çünkü geç değerlendirme genellikle daha iyi performans sağlar. Elbette, bazı işlemler için Ara sonuçların gerçekleştirmeye üzere daha diğer bir seçenek yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticide sonraki konu ertelenmiş yürütme gösterilmektedir:  
  
-   [Ertelenmiş yürütme örneği (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öğretici: Ertelenmiş yürütme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [Kavramları ve terminolojiyi (işlev dönüştürme) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Toplama işlemleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
