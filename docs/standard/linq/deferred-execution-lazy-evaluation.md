---
title: Ertelenmiş yürütme ve geç değerlendirme-LINQ to XML
description: Ertelenmiş yürütmenin olumlu ve gereksinimlerini ve sorgu ve eksen işlemlerini kullanarak nasıl uygulanacağını öğrenin.
ms.date: 07/20/2015
ms.assetid: 8683d1b4-b7ec-407b-be12-906ebe958a09
ms.openlocfilehash: 21b1c7b7d54e7f787919f1e1601fc36bc8c1caff
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552920"
---
# <a name="deferred-execution-and-lazy-evaluation-linq-to-xml"></a>Ertelenmiş yürütme ve geç değerlendirme (LINQ to XML)

Sorgu ve eksen işlemleri genellikle ertelenmiş yürütmeyi kullanacak şekilde uygulanır. Bu makalede ertelenmiş yürütmenin gereksinimleri ve avantajları ve bazı uygulama konuları açıklanmaktadır.

## <a name="deferred-execution"></a>Ertelenmiş yürütme

Ertelenmiş yürütme, *İstenen değer gerçekten* gerekli olana kadar bir ifadenin değerlendirmesinin gecikildiği anlamına gelir. Ertelenmiş yürütme, özellikle de bir dizi zincirleme sorgu veya işleme içeren programlarda büyük veri koleksiyonlarını işlemek gerektiğinde performansı önemli ölçüde iyileştirebilir. En iyi durumda ertelenmiş yürütme, kaynak koleksiyon aracılığıyla yalnızca tek bir yinelemeyi mümkün bir şekilde sunar.

LINQ teknolojileri, hem çekirdek sınıfların üyelerinde hem de gibi <xref:System.Linq?displayProperty=nameWithType> ÇEŞITLI LINQ ad alanlarında uzantı yöntemlerinde ertelenmiş yürütmenin yoğun bir şekilde kullanılmasını kolaylaştırır <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType> .

Ertelenmiş yürütme, bir yineleyici bloğunda kullanılan [yield (C# Reference)](../../csharp/language-reference/keywords/yield.md) anahtar sözcüğü (deyimin biçiminde) tarafından doğrudan C# dilinde desteklenir `yield-return` . Bu tür bir yineleyici, <xref:System.Collections.IEnumerator> ya da <xref:System.Collections.Generic.IEnumerator%601> (ya da türetilmiş bir tür) bir koleksiyon döndürmelidir.

## <a name="eager-vs-lazy-evaluation"></a>Eager ve geç değerlendirme karşılaştırması

Ertelenmiş yürütmeyi uygulayan bir yöntem yazdığınızda, yavaş değerlendirme veya Eager değerlendirmesi kullanarak yöntemi uygulayıp uygulamamaya de karar vermeniz gerekir.

- *Yavaş değerlendirmede*, her Yineleyici çağrısı sırasında kaynak koleksiyonun tek bir öğesi işlenir. Yineleyicilerin uygulanma tipik yoludur.
- *Eager değerlendirmesi*sırasında, Yineleyici için ilk çağrı, tüm koleksiyonun işlenmesine neden olur. Kaynak koleksiyonun geçici bir kopyası da gerekebilir. Örneğin, <xref:System.Linq.Enumerable.OrderBy%2A> yöntemi ilk öğeyi döndürmadan önce tüm koleksiyonu sıralamak zorunda olur.

Yavaş değerlendirme genellikle koleksiyonun değerlendirmesi boyunca ek yük işlemeyi eşit bir şekilde dağıttığı ve geçici verilerin kullanımını en aza indirecek için daha iyi performans verir. Tabii ki, bazı işlemler için, ara sonuçları gerçekleştirme dışında başka bir seçenek yoktur.

C# ve Visual Basic ertelenmiş yürütmeyi programlama örneği için bkz. [ertelenmiş yürütme örneği](deferred-execution-example.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: sorguları C 'de birlikte Zinciri #](chain-queries-example.md)
- [Kavramlar ve terminoloji (işlevsel dönüştürme)](concepts-terminology-functional-transformation.md)
- [Toplama Işlemleri (C#)](../../csharp/programming-guide/concepts/linq/aggregation-operations.md)
- [Toplama Işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
- [yield (C# Başvurusu)](../../csharp/language-reference/keywords/yield.md)
