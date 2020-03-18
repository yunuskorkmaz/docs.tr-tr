---
title: Kavramlar ve Terminoloji (Fonksiyonel Dönüşüm) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 3e2ecc4c2f70700ae92ee36b6f122059b922332e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70040628"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Kavramlar ve Terminoloji (Fonksiyonel Dönüşüm) (C#)

Bu konu, saf işlevsel dönüşümlerin kavramlarını ve terminolojisini tanımaktadır. Veri dönüştürmeiçin işlevsel dönüşüm yaklaşımı, genellikle programa daha hızlı, daha anlamlı ve hata ayıklama ve daha geleneksel, zorunlu programlama daha korumak daha kolay kod verir.

Bu bölümdeki konuların işlevsel programlamayı tam olarak açıklamak için tasarlanmadığını unutmayın. Bunun yerine, bu konular, XML'i bir şekilden diğerine dönüştürmeyi kolaylaştıran bazı işlevsel programlama özelliklerini tanımlar.

## <a name="what-is-pure-functional-transformation"></a>Saf Fonksiyonel Dönüşüm Nedir?

*Saf işlevsel dönüşümde,* *saf işlevler*olarak adlandırılan bir dizi işlev, yapılandırılmış bir veri kümesinin orijinal formundan başka bir forma nasıl dönüştürüldüğünü tanımlar. "Saf" sözcüğü, işlevlerin *birleştirilebilir*olduğunu ve bunların bir arada olduğunu gösterir:

- *Kendi kendine yeten*, böylece serbestçe sipariş ve programın geri kalanı ile dolaşıklık veya karşılıklı bağımlılık olmadan yeniden düzenlenebilir. Saf dönüşümlerin çevreleri hakkında hiçbir bilgisi veya etkisi yoktur. Yani dönüşümde kullanılan işlevlerin *hiçbir yan etkisi*yoktur.

- *Stateless*, böylece aynı işlev veya aynı giriş üzerinde işlevleri belirli bir dizi yürütme her zaman aynı çıktı neden olur. Saf dönüşümler, önceki kullanımları hakkında hiçbir belleğe sahip değildir.

> [!IMPORTANT]
> Bu öğreticinin geri kalanında, "saf işlev" terimi, belirli bir dil özelliğini değil, programlama yaklaşımını belirtmek için genel anlamda kullanılır.
>
> Saf işlevlerin C#'da yöntem olarak uygulanması gerektiğini unutmayın.
>
> Ayrıca, saf işlevleri C++'da saf sanal yöntemlerle karıştırmamalısınız. İkincisi, içeren sınıfın soyut olduğunu ve hiçbir yöntem gövdesinin sağlanolmadığını gösterir.

### <a name="functional-programming"></a>Fonksiyonel Programlama

*İşlevsel programlama,* saf işlevsel dönüşümü doğrudan destekleyen bir programlama yaklaşımıdır.

Tarihsel olarak, ML, Scheme, Haskell ve F# gibi genel amaçlı işlevsel programlama dilleri öncelikle akademik topluluğun ilgisini çekebilir. C#'da saf işlevsel dönüşümler yazmak her zaman mümkün olsa da, bunu yapmanın zorluğu onu çoğu programcı için cazip bir seçenek haline getirmiyor. Ancak C#'ın son sürümlerinde lambda ifadeleri ve tür çıkarımı gibi yeni dil yapıları işlevsel programlamayı çok daha kolay ve üretken hale getirir.

İşlevsel programlama hakkında daha fazla bilgi için [Bkz. İşlevsel Programlama ve Zorunlu Programlama (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Etki Alanına Özel FP Dilleri

Genel işlevsel programlama dilleri yaygın olarak benimsenmese de, etki alanına özgü belirli işlevsel programlama dilleri daha başarılı olmuştur. Örneğin, Basamaklı Stil Sayfaları (CSS) birçok Web sayfasının görünümünü ve hissini belirlemek için kullanılır ve Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) stil sayfaları XML veri işlemede yaygın olarak kullanılır. XSLT hakkında daha fazla bilgi için [Bkz. XSLT Dönüşümleri.](../../../../standard/data/xml/xslt-transformations.md)

## <a name="terminology"></a>Terminoloji

Aşağıdaki tabloda işlevsel dönüşümlerle ilgili bazı terimler tanımlanmaktadır.

üst düzey (birinci sınıf) fonksiyonu \
Programlı bir nesne olarak kabul edilebilen bir işlev. Örneğin, daha yüksek bir sıra işlevi diğer işlevlere geçirilebilir veya döndürülebilir. C#c'de, temsilciler ve lambda ifadeleri üst düzey işlevleri destekleyen dil özellikleridir. Daha yüksek bir sıralı işlev yazmak için, bir veya daha fazla bağımsız değişkeni temsilci almak için bildirirsiniz ve genellikle arama yaparken lambda ifadeleri kullanırsınız. Standart sorgu işleçlerinin çoğu daha yüksek sıralı işlevlerdir.

Daha fazla bilgi için, [Bkz. Standart Sorgu Operatörleri Genel Bakış (C#)](./standard-query-operators-overview.md).

lambda ifade \
Esasen, temsilci türünün beklendiği her yerde kullanılabilecek satır lı anonim bir işlev. Bu lambda ifadelerin basitleştirilmiş bir tanımıdır, ancak bu öğretici amaçları için yeterlidir.

Hakkında daha fazla bilgi için [Lambda İfadeleri'ne](../../statements-expressions-operators/lambda-expressions.md)bakın.

toplama \
Genellikle tek tipte yapılandırılmış bir veri kümesi. LINQ ile uyumlu olması için, <xref:System.Collections.IEnumerable> bir koleksiyonun arabirimi veya <xref:System.Linq.IQueryable> arabirimi <xref:System.Collections.Generic.IEnumerator%601> (veya genel karşılıklarından birini veya). <xref:System.Linq.IQueryable%601>

tuple (anonim türleri) \
Matematiksel bir kavram, bir tuple nesnelerin sınırlı bir dizi, belirli bir tür her. Bir tuple sıralı liste olarak da bilinir. Anonim türler, bu kavramın, adsız bir sınıf türünün bildirilmesini ve bu tür bir nesnenin aynı anda anlık olarak görüntülemesini sağlayan bir dil uygulamasıdır.

Daha fazla bilgi için [Bkz. Anonim Türler.](../../classes-and-structs/anonymous-types.md)

tür çıkarım (örtülü yazma) \
Derleyicinin açık bir tür bildirimi yokluğunda bir değişkenin türünü belirleme yeteneği.

Daha fazla bilgi için [bkz.](../../classes-and-structs/implicitly-typed-local-variables.md)

ertelenmiş yürütme ve tembel değerlendirme \
Bir ifadenin çözümlenen değerine kadar değerlendirilmesinin geciktirilmesi gerçekten gereklidir. Ertelenmiş yürütme koleksiyonlarda desteklenir.

Daha fazla bilgi için [linq sorgularına giriş (C#)](./introduction-to-linq-queries.md) ve [Linq'te Ertelenmiş Yürütme ve Tembel Değerlendirme ile XML (C#) bölümüne](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)bakın.

Bu dil özellikleri bu bölüm boyunca kod örneklerinde kullanılacaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Saf İşlevsel Dönüşümlere Giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [Fonksiyonel Programlama ve Zorunlu Programlama (C#)](./functional-programming-vs-imperative-programming.md)
