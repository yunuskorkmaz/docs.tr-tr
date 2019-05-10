---
title: Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 940885d6499bd2730c0bd4a5e15a490a9e85deab
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64597439"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-c"></a>Ertelenmiş yürütme ve geç değerlendirme LINQ to XML (C#)
Sorgu ve eksen işlemleri genellikle ertelenmiş yürütme kullanmak için uygulanır. Bu konuda, ertelenmiş yürütme ve bazı uygulama konuları avantajları ve gereksinimleri açıklanmaktadır.  
  
## <a name="deferred-execution"></a>Ertelenmiş Yürütme  
 Bir ifadenin değerlendirmesine kadar Gecikmeli yürütme anlamına gelir ertelenmiş kendi *gerçekleşen* değeri gerçekten gereklidir. İçeren bir dizi zincirleme sorguları veya işlemeleri programlarda özellikle büyük veri koleksiyonları yönlendirme olduğunda ertelenmiş yürütme performansı büyük ölçüde artırabilir. En iyi durumda, yalnızca tek bir yineleme kaynak koleksiyonu aracılığıyla ertelenmiş yürütme sağlar.  
  
 LINQ teknolojileri kapsamlı ertelenmiş yürütme iki çekirdek üyelerinde kullanabilmesine <xref:System.Linq?displayProperty=nameWithType> sınıflarını ve çeşitli LINQ ad alanında uzantı yöntemlerini gibi <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
 Ertelenmiş yürütme, C# dil tarafından doğrudan içerisinde desteklendiği [yield](../../../../csharp/language-reference/keywords/yield.md) anahtar sözcüğü (biçiminde `yield-return` deyimi) yineleyici bloğu içinde kullanıldığında. Böyle bir yineleyici türü koleksiyonu döndürmelidir <xref:System.Collections.IEnumerator> veya <xref:System.Collections.Generic.IEnumerator%601> (veya türetilmiş bir tür).  
  
## <a name="eager-vs-lazy-evaluation"></a>İstekli vs. Geç değerlendirme  
 Ertelenmiş yürütme uygulayan bir Metoda yazdığınızda, ayrıca uygulanmayacağını geç değerlendirme veya istekli değerlendirme kullanarak yöntemini karar vermeniz gerekir.  
  
- İçinde *geç değerlendirme*, tek bir kaynak koleksiyonu öğesinin yineleyici yapılan her çağrı sırasında işlenir. Yineleyiciler uygulanan normal şekilde budur.  
  
- İçinde *istekli değerlendirme*, yineleyici yapılan ilk çağrı işlenmekte olan tüm koleksiyonda neden olur. Kaynak koleksiyonu geçici bir kopyası gerekli olabilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> ilk öğeyi döndürür önce tüm koleksiyon sıralama yöntemi vardır.  
  
 Geç değerlendirme genellikle daha iyi performans verir, çünkü ek yükü işleme koleksiyon Değerlendirme boyunca eşit olarak dağıtır ve geçici veri kullanımını en aza indirir. Elbette, bazı işlemler için Ara sonuçlar gerçekleştirmek üzere daha diğer seçeneği yoktur.  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bu öğreticide bir sonraki konu ertelenmiş yürütme gösterilmektedir:  
  
- [Ertelenmiş yürütme örneği (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Sorguları birbirine zincirleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)
- [Kavramlar ve terimler (işlevsel dönüşüm) (C#)](../../../../csharp/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Toplama işlemleri (C#)](../../../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [yield](../../../../csharp/language-reference/keywords/yield.md)
