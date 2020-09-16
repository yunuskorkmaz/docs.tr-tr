---
title: Kavramlar ve terminoloji (işlevsel dönüşüm)-LINQ to XML
description: Saf işlevsel dönüştürmelerin kavramlarını ve terminolojisini öğrenin.
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 0ecdbdf88ee9f868143f466222fa06f0ccf641d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558113"
---
# <a name="concepts-and-terminology-functional-transformation-linq-to-xml"></a>Kavramlar ve terminoloji (işlevsel dönüşüm) (LINQ to XML)

Bu makale, saf işlevsel dönüştürmelerin kavramlarını ve terminolojisini tanıtır. Verileri dönüştürmek için işlevsel dönüştürme yaklaşımı, programlama, daha ayrıntılı ve daha kolay bir şekilde hata ayıklama ve daha kolay ve kesinlik sağlamak için daha hızlı bir kod verir.

Bu bölümdeki makalelerin işlevsel programlamayı tam olarak açıklamak amaçlanmadığını unutmayın. Bunun yerine, bu makaleler XML 'i bir şekilden diğerine dönüştürmeyi kolaylaştıran bazı işlevsel programlama özelliklerini belirler.

## <a name="what-is-pure-functional-transformation"></a>Saf işlevsel dönüştürme nedir?

*Saf işlevsel dönüşümde*, *saf işlevler*olarak adlandırılan bir işlevler kümesi, bir dizi yapısal veriyi özgün formdan başka bir biçime dönüştürmeyi tanımlar. "Saf" sözcüğü, işlevlerin *birleştirilebilen*, ancak şunları gerektirdiğini belirtir:

- *Kendi kendine dahil*olmak üzere, bağımsız olarak sıralanmış ve daha sonra programın geri kalanı olmadan bir arada ve yeniden düzenlenecek şekilde yeniden düzenlenebilir. Saf dönüşümler, ortamları hakkında bilgi sahibi değildir veya etkilemez. Diğer bir deyişle, dönüşümde kullanılan işlevlerin *yan etkileri*yoktur.
- *Durum bilgisiz*, aynı veya aynı girişte aynı işlevin veya belirli bir işlev kümesinin yürütülmesi her zaman aynı çıkışa neden olur. Saf dönüşümlerinin önceki kullanımları belleği yoktur.

> [!IMPORTANT]
> Bu öğreticinin geri kalanında, "saf işlev" terimi, belirli bir dil özelliği değil, programlama yaklaşımını göstermek için genel anlamda kullanılır.
>
> Saf işlevlerin C# dilinde yöntemler olarak ve Visual Basic işlevler olarak uygulanması gerektiğini unutmayın.
>
> Saf işlevleri C++ ' da saf sanal yöntemlerle karıştırmayın. İkincisi, kapsayan sınıfın soyut olduğunu ve hiçbir Yöntem gövdesinin sağlanmadığını gösterir.

### <a name="functional-programming"></a>İşlevsel programlama

*Fonksiyonel programlama* , saf işlevsel dönüştürmeyi doğrudan destekleyen bir programlama yaklaşımıdır.

Geçmişte, genel amaçlı işlevsel programlama dilleri, örneğin ML, düzen, Haskell ve F #, birincil olarak akademik toplulukla ilgilenmiştir. C# ve Visual Basic saf işlevsel dönüşümler yazmak her zaman mümkün olsa da, bunu yapmanın zorluğunu çoğu programcıya etkileyici bir seçenek yapmamıştır. Ancak, bu dillerin son sürümlerinde, lambda ifadeleri ve tür çıkarımı gibi yeni dil yapıları fonksiyonel programlamayı çok daha kolay ve daha üretken hale getirir.

Fonksiyonel programlama hakkında daha fazla bilgi için bkz. [fonksiyonel programlama vs. kesinlik programlama](functional-vs-imperative-programming.md).

#### <a name="domain-specific-functional-programming-languages"></a>Etki alanına özgü işlevsel programlama dilleri

Genel fonksiyonel programlama dilleri yaygın olarak benimsenmese de, bazı etki alanına özgü işlevsel programlama dilleri daha başarılı oldu. Örneğin, birçok Web sayfasının görünümünü ve kullanımını belirlemede Geçişli Stil Sayfaları (CSS) kullanılır ve Genişletilebilir Stil sayfası dil dönüşümleri (XSLT) stil sayfaları, XML veri işleme açısından kapsamlı olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz. [XSLT dönüştürmeleri](../data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminoloji

Aşağıdaki listede, işlevsel dönüşümlerle ilgili bazı terimler tanımlanmaktadır.

daha yüksek sıralı (birinci sınıf) işlev \
Programlı bir nesne olarak değerlendirilenebilir bir işlev. Örneğin, daha yüksek sıralı bir işlev başka işlevlere geçirilebilir veya bu işlevlerden döndürülebilir. C# ve Visual Basic, temsilciler ve lambda ifadeleri, daha yüksek sıralı işlevleri destekleyen dil özelliklerdir. Daha yüksek sıralı bir işlev yazmak için temsilcileri almak üzere bir veya daha fazla bağımsız değişken bildirir ve genellikle bunu çağırırken Lambda ifadelerini kullanırsınız. Standart sorgu işleçlerinin birçoğu daha yüksek sıralı işlevlerdir.

Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ve [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

Lambda ifadesi \
Temelde, bir temsilci türünün beklendiği her yerde kullanılabilecek bir satır içi anonim işlev. Bu, lambda ifadelerinin basitleştirilmiş bir tanımıdır, ancak Bu öğreticinin amaçları doğrultusunda yeterlidir.

Daha fazla bilgi için bkz. [lambda ifadeleri (C# Programlama Kılavuzu)](../../csharp/language-reference/operators/lambda-expressions.md) ve [lambda ifadeleri (Visual Basic))](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

koleksiyon
Genellikle tek biçimli bir tür için yapılandırılmış bir veri kümesi. LINQ ile uyumlu olmak için bir koleksiyonun <xref:System.Collections.IEnumerable> arabirimini veya <xref:System.Linq.IQueryable> arabirimini (ya da kendi genel karşılıklarından birini veya) uygulaması gerekir <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601> .

tanımlama grubu (anonim türler) \
Bir matematiksel kavram olan tanımlama grubu, belirli bir türün her biri için sınırlı bir nesne dizisidir. Bir tanımlama grubu sıralı liste olarak da bilinir. Anonim türler, bu kavramın bir dil uygulamasıdır. Bu, adlandırılmamış bir sınıf türünün bildirilmesini ve bu türden bir nesnenin aynı anda oluşturulmasını sağlar.

Daha fazla bilgi için bkz. [anonim türler (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md) ve [anonim türler (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

Tür çıkarımı (örtük yazma) \
Bir derleyicinin açık tür bildirimi yokluğunda bir değişkenin türünü belirleme özelliği.

Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler (C# Programlama Kılavuzu)](../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [Yerel tür çıkarımı (Visual Basic)](../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

ertelenmiş yürütme ve geç değerlendirme \
Çözümlenmiş değeri gerçekten gerekli olana kadar bir ifadenin değerlendirilme ertelenmesi. Ertelenmiş yürütme, koleksiyonlarda desteklenir.

Daha fazla C# bilgisi için bkz. [LINQ to XML (C#) ' de](./deferred-execution-lazy-evaluation.md) [LINQ Sorgularına Giriş (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) ve ertelenmiş yürütme ve yavaş değerlendirme.

Daha fazla bilgi Visual Basic için bkz. [temel sorgu işlemleri (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) ve [ertelenmiş yürütme ve LINQ to XML (Visual Basic)](./deferred-execution-lazy-evaluation.md).

Bu dil özellikleri, bu bölümün tamamında kod örneklerinde kullanılacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md)
- [Fonksiyonel programlama ile kesin programlama karşılaştırması](functional-vs-imperative-programming.md)
