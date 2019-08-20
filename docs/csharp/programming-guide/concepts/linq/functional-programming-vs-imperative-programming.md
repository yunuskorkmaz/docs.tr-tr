---
title: İşlevsel Programlama ve Kesinlik temelli programlamaC#()
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: a163a62912ed2a44d6ea8cad5bc536f03343f15c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594319"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>İşlevsel Programlama ve Kesinlik temelli programlamaC#()
Bu konu, daha geleneksel kesinlik (yordamsal) programlamaya yönelik fonksiyonel programlamayı karşılaştırır ve karşıtın.  
  
## <a name="functional-programming-vs-imperative-programming"></a>İşlevsel Programlama ve Kesin Programlama Karşılaştırması  
 *İşlevsel programlama* paradigması, sorun çözmeye yönelik saf işlevsel bir yaklaşımı desteklemek üzere açıkça oluşturulmuştur. Fonksiyonel programlama bir *bildirim temelli programlama*biçimidir. Buna karşılık, Visual Basic, C# C++ve Java gibi nesne odaklı programlama (OOP) dilleri de dahil olmak üzere çoğu temel dil, öncelikli olarak (yordamsal) programlama desteği sağlayacak şekilde tasarlanmıştır.  
  
 Bir geliştirici, bir zorunlu yaklaşım ile, exacting detaylı olarak, bilgisayarın hedefi başarmak için gerçekleştirmesi gereken adımları yazarak bu kodu yazar. Bu, bazen *algoritmik* programlama olarak adlandırılır. Buna karşılık, işlevsel bir yaklaşım, sorunu yürütülecek bir işlevler kümesi olarak oluşturmayı içerir. Her işleve yönelik girişi dikkatle tanımlarsınız ve her bir işlevin ne getirir. Aşağıdaki tabloda, bu iki yaklaşım arasındaki genel farklılıklar açıklanmaktadır.  
  
|Özellik|Kesinlik temelli yaklaşım|İşlevsel yaklaşım|  
|--------------------|-------------------------|-------------------------|  
|Programcı odağı|Görevleri (algoritmalar) gerçekleştirme ve durumu değişiklikleri izleme.|Hangi bilgiler istenir ve hangi dönüşümler gereklidir?|  
|Durum değişiklikleri|Önemli.|Mevcut değil.|  
|Yürütme sırası|Önemli.|Düşük önem derecesi.|  
|Birincil akış denetimi|Döngüler, conditionals ve function (Yöntem) çağrıları.|Özyineleme dahil işlev çağrıları.|  
|Birincil işleme birimi|Yapıların veya sınıfların örnekleri.|Birinci sınıf nesneler ve veri koleksiyonları olarak işlevler.|  
  
 Çoğu dil belirli bir programlama paradigmasını destekleyecek şekilde tasarlansa da birçok genel dil birden çok paradigmalarına desteklemek için yeterince esnektir. Örneğin, işlev işaretçileri içeren çoğu dil işlevsel programlamayı güvenilir bir şekilde desteklemek için kullanılabilir. Ayrıca, C# lambda ifadeleri ve tür çıkarımı dahil olmak üzere fonksiyonel programlamayı desteklemek için açık dil uzantıları içerir. LINQ teknolojisi, bildirime dayalı, işlevsel programlama biçimidir.  
  
## <a name="functional-programming-using-xslt"></a>XSLT kullanarak işlevsel programlama  
 Birçok XSLT geliştiricisi, saf işlevsel yaklaşımla tanıdık gelecektir. XSLT stil sayfası geliştirmenin en etkili yolu, her bir şablonu yalıtılmış, birleştirilebilir bir dönüşüm olarak değerlendirmektir. Yürütmenin sırası tamamen vurgulandı. XSLT yan etkilere izin vermez (yordamsal kodu yürütmeye yönelik kaçış mekanizmalarının özel durumu, işlevsel bir sorun oluşmasına neden olan yan etkileri ortaya çıkarabilir). Ancak XSLT etkin bir araç olsa da, bazı özellikleri en uygun değildir. Örneğin, XML 'de programlama yapılarını ifade etmek, kod görece ayrıntılıdır ve bu nedenle devam etmek zordur. Ayrıca, akış denetimi için özyineleme açısından ağır güvenilme, okunması zor olan koda neden olabilir. XSLT hakkında daha fazla bilgi için bkz. [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).  
  
 Ancak XSLT, XML 'yi bir şekilden diğerine dönüştürmek için saf işlevsel bir yaklaşım kullanma değerini uzamıştır. LINQ to XML ile saf işlevsel programlama, XSLT 'nin birçok yolu ile benzerdir. Ancak, LINQ to XML tarafından tanıtılan programlama yapıları, XSLT C# 'den daha okunaklı ve sürdürülebilir saf işlevsel dönüşümler yazmanızı sağlar.  
  
## <a name="advantages-of-pure-functions"></a>Saf Işlevlerin avantajları  
 İşlev dönüştürmelerinin saf işlevler olarak uygulanması için asıl neden, saf işlevlerin birleştirilamasıdır: Yani, kendi içinde ve durumsuz. Bu özellikler, aşağıdakiler de dahil olmak üzere çeşitli avantajlar getirir:  
  
- Daha fazla okunabilirlik ve bakımma. Bunun nedeni, her işlevin bağımsız değişkenleri verilen belirli bir görevi gerçekleştirmek için tasarlanmalıdır. İşlev herhangi bir dış duruma bağlı değil.  
  
- Daha kolay yeniden yinelemeli geliştirme. Kodun yeniden düzenlenmesi daha kolay olduğundan, tasarımın değişikliklerinin uygulanması genellikle daha kolay olur. Örneğin, karmaşık bir dönüşüm yazdığınızı ve sonra bazı kodların dönüşümde birkaç kez tekrarlanmış olduğunu fark edelim. Saf bir yöntemde yeniden düzenleme yaparsanız, yan etkileri konusunda endişelenmenize gerek kalmadan saf yönteminizi ' de çağırabilirsiniz.  
  
- Daha kolay test ve hata ayıklama. Saf işlevlerin yalıtımda daha kolay test edileceği için, saf işlevi çağıran test kodunu tipik değerlerle, geçerli kenar çalışmalarından ve geçersiz kenar durumları ile yazabilirsiniz.  
  
## <a name="transitioning-for-oop-developers"></a>OOP geliştiricileri için geçiş  
 Geleneksel nesne odaklı programlamada (OOP), çoğu geliştirici, zorunlu/yordamsal stilde programlanması için tasarlanmıştır. Saf işlevsel stilde geliştirmeye geçiş yapmak için, düşünmelerde ve geliştirme yaklaşımında bir geçiş yapması gerekir.  
  
 Sorunları gidermek için, OOP geliştiricileri sınıf hiyerarşilerini tasarlar, doğru kapsülleme üzerine odaklanmak ve sınıf sözleşmeleri açısından düşünün. Nesne türlerinin davranışı ve durumu Paramount ve sınıflar, arabirimler, devralma ve çok biçimlilik gibi dil özellikleri bu sorunları ele almak için sağlanır.  
  
 Buna karşılık, fonksiyonel programlama, veri koleksiyonlarının saf işlevsel dönüştürmelerinin değerlendirmesinde bir alıştırma olarak sorun giderme konusunda yaklaşımlar. Fonksiyonel programlama durum ve değişebilir verileri önler ve bunun yerine işlevlerin uygulamasını vurgular.  
  
 Neyse ki C# , hem zorunlu hem de işlevsel programlama yaklaşımlarını desteklediğinden işlevsel programlamaya tam olarak gerek yoktur. Geliştirici, belirli bir senaryo için en uygun yaklaşımı seçebilir. Aslında, programlar genellikle her iki yaklaşımı de birleştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf Işlevsel Dönüştürmelere giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [XSLT Dönüşümleri](../../../../standard/data/xml/xslt-transformations.md)
- [Saf IŞLEVLERE yeniden düzenleme (C#)](./refactoring-into-pure-functions.md)
