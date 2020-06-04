---
title: Kavramlar ve Terimler (İşlevsel Dönüşüm)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 4a63630d431a0972fb1a61981306a41e6f4926e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410870"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Kavramlar ve terminoloji (Işlevsel dönüşüm) (Visual Basic)
Bu konu, saf işlevsel dönüştürmelerin kavramlarını ve terminolojisini tanıtır. Veri dönüştürme yaklaşımı, genellikle programa, daha ayrıntılı bir şekilde daha hızlı ve hata ayıklama ve daha geleneksel, kesinlik temelli programlama açısından daha kolay olan kodu verir.

Bu bölümdeki konuların işlevsel programlamayı tam olarak açıklamak için düşünülmediğini unutmayın. Bunun yerine, bu konular XML 'i bir şekilden diğerine dönüştürmeyi kolaylaştıran bazı işlevsel programlama özelliklerini belirler.

## <a name="what-is-pure-functional-transformation"></a>Saf Işlevsel dönüştürme nedir?

*Saf işlevsel dönüşümde*, *saf işlevler*olarak adlandırılan bir işlevler kümesi, bir dizi yapısal veriyi özgün formdan başka bir biçime dönüştürmeyi tanımlar. "Saf" sözcüğü, işlevlerin *birleştirilebilen*şekilde olduğunu belirtir ve şunları gerektirir:

- *Kendi kendine dahil*olmak üzere, bağımsız olarak sıralanmış ve daha sonra programın geri kalanı olmadan bir arada ve yeniden düzenlenecek şekilde yeniden düzenlenebilir. Saf dönüşümler, ortamları hakkında bilgi sahibi değildir veya etkilemez. Diğer bir deyişle, dönüşümde kullanılan işlevlerin *yan etkileri*yoktur.

- *Durum bilgisiz*, aynı veya aynı girişte aynı işlevin veya belirli bir işlev kümesinin yürütülmesi her zaman aynı çıkışa neden olur. Saf dönüşümlerinin önceki kullanımları belleği yoktur.

> [!IMPORTANT]
> Bu öğreticinin geri kalanında, "saf işlev" terimi, belirli bir dil özelliği değil, programlama yaklaşımını göstermek için genel anlamda kullanılır.
>
> Saf işlevlerin Visual Basic işlev olarak uygulanması gerektiğini unutmayın.
>
> Ayrıca, saf işlevleri C++ ' da saf sanal yöntemlerle karıştırmayın. İkincisi, kapsayan sınıfın soyut olduğunu ve hiçbir Yöntem gövdesinin sağlanmadığını gösterir.

### <a name="functional-programming"></a>Fonksiyonel programlama

*Fonksiyonel programlama* , saf işlevsel dönüştürmeyi doğrudan destekleyen bir programlama yaklaşımıdır.

Geçmişte, genel amaçlı işlevsel programlama dilleri, örneğin ML, düzen, Haskell ve F #, birincil olarak akademik toplulukla ilgilenmiştir. Visual Basic saf işlevsel dönüştürmeleri yazmak her zaman mümkün olsa da, bunu yapmanın zorluğunu çoğu programcıya etkileyici bir seçenek yapmamıştır. Daha sonraki Visual Basic sürümleriyle, lambda ifadeleri ve tür çıkarımı gibi yeni dil yapıları BT programlamanın çok daha kolay ve daha üretken olmasını sağlar.

İşlevsel programlama hakkında daha fazla bilgi için bkz. [fonksiyonel programlama vs. kesinlik programlama (Visual Basic)](functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Etki alanına özgü FP dilleri

Genel fonksiyonel programlama dilleri çok daha fazla benimsemese de, etki alanına özgü belirli işlevsel programlama dillerinin başarısı daha iyidir. Örneğin, birçok Web sayfasının görünümünü ve kullanımını belirlemede Geçişli Stil Sayfaları (CSS) kullanılır ve Genişletilebilir Stil sayfası dil dönüşümleri (XSLT) stil sayfaları, XML veri işleme açısından kapsamlı olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz. [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminoloji

Aşağıdaki tabloda, işlevsel dönüşümlerle ilgili bazı terimler tanımlanmaktadır.

daha yüksek sıralı (birinci sınıf) işlev \
Programlı bir nesne olarak değerlendirilenebilir bir işlev. Örneğin, daha yüksek sıralı bir işlev başka işlevlere geçirilebilir veya bu işlevlerden döndürülebilir. Visual Basic, temsilciler ve lambda ifadeleri, daha yüksek sıralı işlevleri destekleyen dil özelliklerdir. Daha yüksek sıralı bir işlev yazmak için temsilcileri almak üzere bir veya daha fazla bağımsız değişken bildirir ve genellikle bunu çağırırken Lambda ifadelerini kullanırsınız. Standart sorgu işleçlerinin birçoğu daha yüksek sıralı işlevlerdir.

Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](standard-query-operators-overview.md).

Lambda ifadesi \
Temelde, bir temsilci türünün beklendiği her yerde kullanılabilecek bir satır içi anonim işlev. Bu, lambda ifadelerinin basitleştirilmiş bir tanımıdır, ancak Bu öğreticinin amaçları doğrultusunda yeterlidir.

Hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../language-features/procedures/lambda-expressions.md).

koleksiyon
Genellikle tek biçimli bir tür için yapılandırılmış bir veri kümesi. LINQ ile uyumlu olmak için bir koleksiyonun <xref:System.Collections.IEnumerable> arabirimini veya <xref:System.Linq.IQueryable> arabirimini (ya da kendi genel karşılıklarından birini veya) uygulaması gerekir <xref:System.Collections.Generic.IEnumerator%601> <xref:System.Linq.IQueryable%601> .

tanımlama grubu (anonim türler) \
Bir matematiksel kavram olan tanımlama grubu, belirli bir türün her biri için sınırlı bir nesne dizisidir. Bir tanımlama grubu sıralı liste olarak da bilinir. Anonim türler, bu kavramın bir dil uygulamasıdır. Bu, adlandırılmamış bir sınıf türünün bildirilmesini ve bu türden bir nesnenin aynı anda oluşturulmasını sağlar.

Daha fazla bilgi için bkz. [anonim türler](../../language-features/objects-and-classes/anonymous-types.md).

Tür çıkarımı (örtük yazma) \
Bir derleyicinin açık tür bildirimi yokluğunda bir değişkenin türünü belirleme özelliği.

Daha fazla bilgi için bkz. [Yerel tür çıkarımı](../../language-features/variables/local-type-inference.md).

ertelenmiş yürütme ve geç değerlendirme \
Çözümlenmiş değeri gerçekten gerekli olana kadar bir ifadenin değerlendirilme ertelenmesi. Ertelenmiş yürütme, koleksiyonlarda desteklenir.

Daha fazla bilgi için bkz. [temel sorgu işlemleri (Visual Basic)](basic-query-operations.md) ve [ertelenmiş yürütme ve yavaş değerlendirme LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Bu dil özellikleri, bu bölümün tamamında kod örneklerinde kullanılacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel dönüşümlere giriş (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Fonksiyonel programlama ile kesinlik temelli programlama (Visual Basic)](functional-programming-vs-imperative-programming.md)
