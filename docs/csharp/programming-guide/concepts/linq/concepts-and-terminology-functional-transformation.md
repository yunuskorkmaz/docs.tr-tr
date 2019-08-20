---
title: Kavramlar ve terminoloji (Işlevsel dönüşüm) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: bf340b960a6770f972f545b23bd857afd4cb9ede
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594589"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Kavramlar ve terminoloji (Işlevsel dönüşüm) (C#)
Bu konu, saf işlevsel dönüştürmelerin kavramlarını ve terminolojisini tanıtır. Veri dönüştürme yaklaşımı, genellikle programa, daha ayrıntılı bir şekilde daha hızlı ve hata ayıklama ve daha geleneksel, kesinlik temelli programlama açısından daha kolay olan kodu verir.  
  
 Bu bölümdeki konuların işlevsel programlamayı tam olarak açıklamak için düşünülmediğini unutmayın. Bunun yerine, bu konular XML 'i bir şekilden diğerine dönüştürmeyi kolaylaştıran bazı işlevsel programlama özelliklerini belirler.  
  
## <a name="what-is-pure-functional-transformation"></a>Saf Işlevsel dönüştürme nedir?  
 *Saf işlevsel dönüşümde*, *saf işlevler*olarak adlandırılan bir işlevler kümesi, bir dizi yapısal veriyi özgün formdan başka bir biçime dönüştürmeyi tanımlar. "Saf" sözcüğü, işlevlerin birleştirilebilen şekilde olduğunubelirtir ve şunları gerektirir:  
  
- *Kendi kendine dahil*olmak üzere, bağımsız olarak sıralanmış ve daha sonra programın geri kalanı olmadan bir arada ve yeniden düzenlenecek şekilde yeniden düzenlenebilir. Saf dönüşümler, ortamları hakkında bilgi sahibi değildir veya etkilemez. Diğer bir deyişle, dönüşümde kullanılan işlevlerin *yan etkileri*yoktur.  
  
- *Durum bilgisiz*, aynı veya aynı girişte aynı işlevin veya belirli bir işlev kümesinin yürütülmesi her zaman aynı çıkışa neden olur. Saf dönüşümlerinin önceki kullanımları belleği yoktur.  
  
> [!IMPORTANT]
>  Bu öğreticinin geri kalanında, "saf işlev" terimi, belirli bir dil özelliği değil, programlama yaklaşımını göstermek için genel anlamda kullanılır.  
>   
>  Saf işlevlerin ' de C#Yöntem olarak uygulanması gerektiğini unutmayın.  
>   
>  Ayrıca, saf işlevleri içinde C++saf sanal yöntemlerle karıştırmayın. İkincisi, kapsayan sınıfın soyut olduğunu ve hiçbir Yöntem gövdesinin sağlanmadığını gösterir.  
  
### <a name="functional-programming"></a>Fonksiyonel programlama  
 *Fonksiyonel programlama* , saf işlevsel dönüştürmeyi doğrudan destekleyen bir programlama yaklaşımıdır.  
  
 Geçmişte, genel amaçlı işlevsel programlama dilleri, örneğin, ML, düzen, Haskell ve F#, birincil olarak akademik topluluk ile ilgilenmiştir. Üzerinde C#saf işlevsel dönüşümler yazmak her zaman mümkün olsa da, bunu yapmanın zorluğunu çoğu programcıya etkileyici bir seçenek yapmamıştır. Ancak, ' nin C#son sürümlerinde, lambda ifadeleri ve tür çıkarımı gibi yeni dil yapıları BT programlamanın çok daha kolay ve daha üretken olmasını sağlar.  
  
 Fonksiyonel programlama hakkında daha fazla bilgi için bkz [. fonksiyonel programlama vs. Kesinlik temelli programlamaC#(](./functional-programming-vs-imperative-programming.md)).  
  
#### <a name="domain-specific-fp-languages"></a>Etki alanına özgü FP dilleri  
 Genel fonksiyonel programlama dilleri çok daha fazla benimsemese de, etki alanına özgü belirli işlevsel programlama dillerinin başarısı daha iyidir. Örneğin, birçok Web sayfasının görünümünü ve kullanımını belirlemede Geçişli Stil Sayfaları (CSS) kullanılır ve Genişletilebilir Stil sayfası dil dönüşümleri (XSLT) stil sayfaları, XML veri işleme açısından kapsamlı olarak kullanılır. XSLT hakkında daha fazla bilgi için bkz. [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminoloji  
 Aşağıdaki tabloda, işlevsel dönüşümlerle ilgili bazı terimler tanımlanmaktadır.  
  
 daha yüksek sıralı (birinci sınıf) işlev  
 Programlı bir nesne olarak değerlendirilenebilir bir işlev. Örneğin, daha yüksek sıralı bir işlev başka işlevlere geçirilebilir veya bu işlevlerden döndürülebilir. C # c 'de temsilciler ve lambda ifadeleri, daha yüksek sıralı işlevleri destekleyen dil özelliklerdir. Daha yüksek sıralı bir işlev yazmak için temsilcileri almak üzere bir veya daha fazla bağımsız değişken bildirir ve genellikle bunu çağırırken Lambda ifadelerini kullanırsınız. Standart sorgu işleçlerinin birçoğu daha yüksek sıralı işlevlerdir.  
  
 Daha fazla bilgi için bkz. [Standart sorgu IşleçlerineC#genel bakış ()](./standard-query-operators-overview.md).  
  
 Lambda ifadesi  
 Temelde, bir temsilci türünün beklendiği her yerde kullanılabilecek bir satır içi anonim işlev. Bu, lambda ifadelerinin basitleştirilmiş bir tanımıdır, ancak Bu öğreticinin amaçları doğrultusunda yeterlidir.  
  
 Hakkında daha fazla bilgi için bkz. [lambda ifadeleri](../../statements-expressions-operators/lambda-expressions.md).  
  
 koleksiyonu  
 Genellikle tek biçimli bir tür için yapılandırılmış bir veri kümesi. LINQ ile uyumlu olmak için bir <xref:System.Collections.IEnumerable> koleksiyonun arabirimini <xref:System.Linq.IQueryable> veya arabirimini (ya da <xref:System.Linq.IQueryable%601>kendi genel karşılıklarından <xref:System.Collections.Generic.IEnumerator%601> birini veya) uygulaması gerekir.  
  
 tanımlama grubu (anonim türler)  
 Bir matematiksel kavram olan tanımlama grubu, belirli bir türün her biri için sınırlı bir nesne dizisidir. Bir tanımlama grubu sıralı liste olarak da bilinir. Anonim türler, bu kavramın bir dil uygulamasıdır. Bu, adlandırılmamış bir sınıf türünün bildirilmesini ve bu türden bir nesnenin aynı anda oluşturulmasını sağlar.  
  
 Daha fazla bilgi için bkz. [anonim türler](../../classes-and-structs/anonymous-types.md).  
  
 Tür çıkarımı (örtük yazma)  
 Bir derleyicinin açık tür bildirimi yokluğunda bir değişkenin türünü belirleme özelliği.  
  
 Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
 ertelenmiş yürütme ve geç değerlendirme  
 Çözümlenmiş değeri gerçekten gerekli olana kadar bir ifadenin değerlendirilme ertelenmesi. Ertelenmiş yürütme, koleksiyonlarda desteklenir.  
  
 Daha fazla bilgi için bkz. [LINQ Sorgularına Giriş (C#)](./introduction-to-linq-queries.md) ve [LINQ to XML (C#) içinde ertelenmiş yürütme ve geç değerlendirme](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Bu dil özellikleri, bu bölümün tamamında kod örneklerinde kullanılacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel Dönüştürmelere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [İşlevsel Programlama ve Kesinlik temelli programlamaC#()](./functional-programming-vs-imperative-programming.md)
