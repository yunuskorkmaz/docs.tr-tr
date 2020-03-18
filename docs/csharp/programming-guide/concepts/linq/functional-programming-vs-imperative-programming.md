---
title: Fonksiyonel Programlama ve Zorunlu Programlama (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: a163a62912ed2a44d6ea8cad5bc536f03343f15c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594319"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Fonksiyonel Programlama ve Zorunlu Programlama (C#)
Bu konu, işlevsel programlamayı daha geleneksel zorunlu (yordamsal) programlama ile karşılaştırır ve karşılaştırır.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Fonksiyonel Programlama ve Zorunlu Programlama  
 *İşlevsel programlama* paradigması, problem çözmeye saf işlevsel bir yaklaşımı desteklemek için açıkça oluşturulmuştur. Fonksiyonel programlama *bildirimsel programlama*biçimidir. Buna karşılık, C#, Visual Basic, C++ve Java gibi nesne yönelimli programlama (OOP) dilleri de dahil olmak üzere çoğu ana dil, öncelikle *zorunlu* (yordamsal) programlamayı destekleyecek şekilde tasarlanmıştır.  
  
 Zorunlu bir yaklaşımla, geliştirici, bilgisayarın hedefi gerçekleştirmek için atması gereken adımları ayrıntılı olarak açıklayan kod yazar. Bu bazen *algoritmik* programlama olarak adlandırılır. Buna karşılık, işlevsel bir yaklaşım yürütülecek işlevler kümesi olarak sorun oluşturma içerir. Her işlevin girişini ve her işlevin ne döndürür olduğunu dikkatle tanımlarsınız. Aşağıdaki tabloda, bu iki yaklaşım arasındaki genel farklardan bazıları açıklanmaktadır.  
  
|Özellik|Zorunlu yaklaşım|Fonksiyonel yaklaşım|  
|--------------------|-------------------------|-------------------------|  
|Programcı odak|Görevlerin (algoritmaların) nasıl gerçekleştirildirilen ve durum daki değişikliklerin nasıl izlenir.|Hangi bilgilerin istendiği ve hangi dönüşümlerin gerekli olduğu.|  
|Durum değişiklikleri|Önemli.|Var olmayan bir şey.|  
|Yürütme emri|Önemli.|Düşük öneme sahip.|  
|Birincil akış kontrolü|Döngüler, koşullular ve işlev (yöntem) çağrıları.|Özyineleme de dahil olmak üzere işlev çağrıları.|  
|Birincil manipülasyon ünitesi|Yapı veya sınıf örnekleri.|Birinci sınıf nesneler ve veri koleksiyonları olarak işlev görür.|  
  
 Çoğu dil belirli bir programlama paradigmasını destekleyecek şekilde tasarlanmış olsa da, birçok genel dil birden çok paradigmayı destekleyecek kadar esnektir. Örneğin, işlev işaretçileri içeren çoğu dil işlevsel programlamayı güvenilir bir şekilde desteklemek için kullanılabilir. Ayrıca, C# lambda ifadeleri ve tür çıkarımı da dahil olmak üzere işlevsel programlamayı desteklemek için açık dil uzantıları içerir. LINQ teknolojisi bildirimsel, işlevsel programlama biçimidir.  
  
## <a name="functional-programming-using-xslt"></a>XSLT Kullanarak Fonksiyonel Programlama  
 Birçok XSLT geliştiricisi saf işlevsel yaklaşıma aşinadır. Bir XSLT stil sayfası geliştirmenin en etkili yolu, her şablonu yalıtılmış, birleştirilebilir dönüşüm olarak ele almaktır. İdam emri tamamen vurgulanır. XSLT yan etkilere izin vermez (prosedür kodunun yürütülmesi için mekanizmaların kaçış işlevsel kirlilik neden yan etkileri tanıtmak dışında). Ancak, XSLT etkili bir araç olmasına rağmen, bazı özellikleri en iyi değildir. Örneğin, XML programlama yapıları ifade kodu nispeten ayrıntılı hale getirir ve bu nedenle bakımı zor. Ayrıca, akış denetimi için özyinelemeye duyulan ağır güven, okunması zor bir kodla sonuçlanabilir. XSLT hakkında daha fazla bilgi için [Bkz. XSLT Dönüşümleri.](../../../../standard/data/xml/xslt-transformations.md)  
  
 Ancak XSLT, XML'i bir şekilden diğerine dönüştürmek için saf işlevsel bir yaklaşım kullanmanın değerini kanıtlamıştır. LINQ ile XML arasında saf işlevsel programlama birçok yönden XSLT'ye benzer. Ancak, LINQ tarafından XML ve C# ile tanıtılan programlama yapıları, XSLT'den daha okunabilir ve korunabilen saf işlevsel dönüşümler yazmanızı sağlar.  
  
## <a name="advantages-of-pure-functions"></a>Saf Fonksiyonların Avantajları  
 İşlevsel dönüşümleri saf işlevler olarak uygulamanın temel nedeni, saf işlevlerin birleştirilebilir olmasıdır: yani, bağımsız ve devletsiz. Bu özellikler, aşağıdakiler de dahil olmak üzere bir dizi avantaj sağlar:  
  
- Artırılabilirlik ve bakım. Bunun nedeni, her işlevin bağımsız değişkenleri göz önüne alındığında belirli bir görevi gerçekleştirmek üzere tasarlanmış olmasıdır. İşlev herhangi bir dış duruma dayanmaz.  
  
- Daha kolay yinelemeli geliştirme. Kodu yeniden düzenlemek daha kolay olduğundan, tasarım değişiklikleri genellikle uygulanması daha kolaydır. Örneğin, karmaşık bir dönüşüm yazdığınızı ve dönüşümde bazı kodların birkaç kez yinelediğini fark ettiğinizi varsayalım. Eğer saf bir yöntem ile refactor, yan etkileri hakkında endişelenmeden istediğiniz saf yöntemi arayabilirsiniz.  
  
- Daha kolay test ve hata ayıklama. Saf işlevler daha kolay yalıtımda sınanabileceğinden, saf işlevi tipik değerler, geçerli kenar örnekleri ve geçersiz kenar durumlarıyla çağıran test kodu yazabilirsiniz.  
  
## <a name="transitioning-for-oop-developers"></a>OOP Geliştiricileri için Geçiş  
 Geleneksel nesne yönelimli programlamada (OOP), çoğu geliştirici zorunlu/yordam tarzında programlamaya alışkındır. Saf işlevsel bir tarzda gelişmeye geçmek için, onların düşünce ve gelişim e yaklaşımlarında bir geçiş yapmak zorunda.  
  
 Sorunları çözmek için, OOP geliştiricileri sınıf hiyerarşileri tasarlar, uygun kapsülleme üzerine odaklanır ve sınıf sözleşmeleri açısından düşünür. Nesne türlerinin davranışı ve durumu çok önemlidir ve bu endişeleri gidermek için sınıflar, arabirimler, kalıtım ve çok biçimlilik gibi dil özellikleri sağlanır.  
  
 Buna karşılık, fonksiyonel programlama veri koleksiyonlarının saf işlevsel dönüşümlerinin değerlendirilmesinde bir alıştırma olarak hesaplama lı sorunlara yaklaşır. İşlevsel programlama durum ve mutable verileri önler ve bunun yerine işlevlerin uygulanmasını vurgular.  
  
 Neyse ki, C# işlevsel programlamaya tam sıçrama gerektirmez, çünkü hem zorunlu hem de işlevsel programlama yaklaşımlarını destekler. Geliştirici, belirli bir senaryo için en uygun yaklaşımı seçebilir. Aslında, programlar genellikle her iki yaklaşımı birleştirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Saf İşlevsel Dönüşümlere Giriş (C#)](./introduction-to-pure-functional-transformations.md)
- [XSLT Dönüşümleri](../../../../standard/data/xml/xslt-transformations.md)
- [Saf Fonksiyonlara Yeniden Düzenleme (C#)](./refactoring-into-pure-functions.md)
