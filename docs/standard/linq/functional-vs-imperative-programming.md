---
title: Fonksiyonel programlama ve kesinlik temelli programlama-LINQ to XML
description: Fonksiyonel programlama hakkında bilgi edinin ve bunun geleneksel olarak kesinlik (yordamsal) programlamadan farklı olduğunu öğrenin.
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: d6dddab9b288cfa820aa4ed9d800c29136edf772
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553010"
---
# <a name="functional-programming-vs-imperative-programming-linq-to-xml"></a>Fonksiyonel programlama ile kesinlik temelli programlama (LINQ to XML)

Bu makalede, daha geleneksel kesinlik (yordamsal) programlamaya yönelik fonksiyonel programlama karşılaştırılır ve karşıtlıkları gösterilmiştir.

## <a name="functional-programming-vs-imperative-programming"></a>Fonksiyonel programlama ve kesinlik temelli programlama karşılaştırması

*İşlevsel programlama* paradigması, sorun çözmeye yönelik saf işlevsel bir yaklaşımı desteklemek üzere açıkça oluşturulmuştur. Fonksiyonel programlama bir *bildirim temelli programlama*biçimidir. Buna karşılık, C#, Visual Basic, C++ ve Java gibi nesne odaklı programlama (OOP) dilleri de dahil olmak üzere çoğu temel dil, öncelikle *kesinlik* (yordamsal) programlamayı destekleyecek şekilde tasarlanmıştır.

Bir geliştirici, bir zorunlu yaklaşımla birlikte, bilgisayarın hedefi başarmak için gerçekleştirmesi gereken adımları belirten kodu yazar. Bu, bazen *algoritmik* programlama olarak adlandırılır. Buna karşılık, işlevsel bir yaklaşım, sorunu yürütülecek bir işlevler kümesi olarak oluşturmayı içerir. Her işleve yönelik girişi dikkatle tanımlarsınız ve her bir işlevin ne getirir. Aşağıdaki tabloda, bu iki yaklaşım arasındaki genel farklılıklar açıklanmaktadır.

|Özellik|Kesinlik temelli yaklaşım|İşlevsel yaklaşım|
|--------------------|-------------------------|-------------------------|
|Programcı odağı|Görevleri (algoritmalar) gerçekleştirme ve durumu değişiklikleri izleme.|Hangi bilgiler istenir ve hangi dönüşümler gereklidir?|
|Durum değişiklikleri|Önemli.|Mevcut değil.|
|Yürütme sırası|Önemli.|Düşük önem derecesi.|
|Birincil akış denetimi|Döngüler, conditionals ve function (Yöntem) çağrıları.|Özyineleme dahil işlev çağrıları.|
|Birincil işleme birimi|Yapıların veya sınıfların örnekleri.|Birinci sınıf nesneler ve veri koleksiyonları olarak işlevler.|

Çoğu dil belirli bir programlama paradigmasını destekleyecek şekilde tasarlansa da birçok genel dil birden çok paradigmalarına desteklemek için yeterince esnektir. Örneğin, işlev işaretçileri içeren çoğu dil işlevsel programlamayı güvenilir bir şekilde desteklemek için kullanılabilir. Ayrıca, C# ve Visual Basic lambda ifadeleri ve tür çıkarımı dahil olmak üzere işlevsel programlamayı desteklemek için açık dil uzantıları içerir. LINQ teknolojisi, bildirime dayalı, işlevsel programlama biçimidir.

## <a name="functional-programming-using-xslt"></a>XSLT kullanarak işlevsel programlama

Birçok XSLT geliştiricisi, saf işlevsel yaklaşımla tanıdık gelecektir. XSLT stil sayfası geliştirmenin en etkili yolu, her bir şablonu yalıtılmış, birleştirilebilir bir dönüşüm olarak değerlendirmektir. Yürütmenin sırası tamamen vurgulandı. XSLT yan etkilere izin vermez (yordamsal kodu yürütmeye yönelik kaçış mekanizmalarının hariç olması, işlevsel bir sorun oluşmasına neden olan yan etkileri ortaya çıkarabilir). Ancak XSLT etkin bir araç olsa da bazı özellikleri en uygun değildir. Örneğin, XML 'de programlama yapılarını ifade etmek, kod görece ayrıntılıdır ve bu nedenle devam etmek zordur. Ayrıca, akış denetimi için özyineleme açısından ağır güvenilme, okunması zor olan koda neden olabilir. XSLT hakkında daha fazla bilgi için bkz. [XSLT dönüştürmeleri](../../standard/data/xml/xslt-transformations.md).

Ancak XSLT, XML 'yi bir şekilden diğerine dönüştürmek için saf işlevsel bir yaklaşım kullanma değerini uzamıştır. LINQ to XML ile saf işlevsel programlama, XSLT 'nin birçok yolu ile benzerdir. Ancak, LINQ to XML, C# ve Visual Basic tarafından tanıtılan programlama yapıları, XSLT 'den daha okunaklı ve sürdürülebilir saf işlevsel dönüşümler yazmanızı sağlar.

## <a name="advantages-of-pure-functions"></a>Saf işlevlerin avantajları

İşlev dönüştürmelerinin saf işlevler olarak uygulanması için asıl neden, saf işlevlerin birleştirilamasıdır: Yani, kendi içinde ve durumsuz. Bu özellikler, aşağıdakiler de dahil olmak üzere çeşitli avantajlar getirir:

- Daha fazla okunabilirlik ve bakımma. Bunun nedeni, her işlevin bağımsız değişkenleri verilen belirli bir görevi gerçekleştirmek için tasarlanmalıdır. İşlev herhangi bir dış duruma bağlı değildir.
- Daha kolay yeniden yinelemeli geliştirme. Kodun yeniden düzenlenmesi daha kolay olduğundan, tasarımın değişikliklerinin uygulanması genellikle daha kolay olur. Örneğin, karmaşık bir dönüşüm yazdığınızı ve sonra bazı kodların dönüşümde birkaç kez tekrarlanmış olduğunu fark edelim. Saf bir yöntemde yeniden düzenleme yaparsanız, yan etkileri konusunda endişelenmenize gerek kalmadan saf yönteminizi ' de çağırabilirsiniz.
- Daha kolay test ve hata ayıklama. Saf işlevlerin yalıtımda daha kolay test edileceği için, saf işlevi çağıran test kodunu tipik değerlerle, geçerli kenar çalışmalarından ve geçersiz kenar durumları ile yazabilirsiniz.

## <a name="transitioning-for-oop-developers"></a>OOP geliştiricileri için geçiş

Geleneksel nesne odaklı programlamada (OOP), çoğu geliştirici, zorunlu/yordamsal stilde programlanması için tasarlanmıştır. Saf işlevsel stilde geliştirmeye geçiş yapmak için, düşünmelerde ve geliştirme yaklaşımında bir geçiş yapması gerekir.

Sorunları gidermek için, OOP geliştiricileri sınıf hiyerarşilerini tasarlar, doğru kapsülleme üzerine odaklanmak ve sınıf sözleşmeleri açısından düşünün. Nesne türlerinin davranışı ve durumu Paramount ve sınıflar, arabirimler, devralma ve çok biçimlilik gibi dil özellikleri bu sorunları ele almak için sağlanır.

Buna karşılık, fonksiyonel programlama, veri koleksiyonlarının saf işlevsel dönüştürmelerinin değerlendirmesinde bir alıştırma olarak sorun giderme konusunda yaklaşımlar. Fonksiyonel programlama durum ve değişebilir verileri önler ve bunun yerine işlevlerin uygulamasını vurgular.

Neyse ki, C# ve Visual Basic, hem zorunlu hem de işlevsel programlama yaklaşımlarını desteklediklerinden, işlevsel programlamaya tam olarak gerek kalmaz. Geliştirici, belirli bir senaryo için en uygun yaklaşımı seçebilir. Aslında, programlar genellikle her iki yaklaşımı de birleştirir.

## <a name="see-also"></a>Ayrıca bkz.

- [Saf işlevsel dönüşümlere giriş](introduction-pure-functional-transformations.md)
- [XSLT Dönüşümleri](/../../standard/data/xml/xslt-transformations.md)
- [Saf işlevlerde yeniden düzenleme](refactor-pure-functions.md)
