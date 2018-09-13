---
title: İşlevsel programlama ve Kesin programlama karşılaştırması (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: 01be2758147b84af3410709aab62a0ca89b0c9cf
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44706271"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>İşlevsel programlama ve Kesin programlama karşılaştırması (C#)
Bu konuda karşılaştırır ve işlevsel programlama daha geleneksel buyurgan (yordamsal) programlamaya ile karşılaştırır.  
  
## <a name="functional-programming-vs-imperative-programming"></a>İşlevsel programlama ve Kesin programlama karşılaştırması  
 *İşlevsel programlama* paradigma sorunu çözmek için saf işlevsel yaklaşım desteklemek için açıkça oluşturuldu. İşlevsel programlama, çeşit *bildirime dayalı programlama*. Buna karşılık, nesne odaklı programlama (OOP) dilleri gibi C#, Visual Basic, C++ ve Java dahil olmak üzere çoğu temel dil öncelikle desteklemek için tasarlanmış *kesinlik temelli* (yordamsal) programlamaya.  
  
 Kesinlik temelli bir yaklaşım ile bir geliştirici açıklayan kod ayrıntı kesin bilgisayar ve hedefe ulaşmak için gerçekleştirmeniz gereken adımlar yazar. Bu bazen olarak adlandırılır *algoritmik* programlama. Buna karşılık, işlevsel bir yaklaşım sorun yürütülecek işlevler bir dizi oluşturmayı kapsar. Her işlev girişi ve her hangi bir işlevi döndürür dikkatli bir şekilde tanımlarsınız. Aşağıdaki tabloda, bu iki yaklaşımı genel farklılıklardan bazıları açıklanmaktadır.  
  
|Özelliği|Kesinlik temelli yaklaşımın|İşlevsel yaklaşım|  
|--------------------|-------------------------|-------------------------|  
|Programcı odağı|(Algoritmaları) görevlerin nasıl gerçekleştirileceği ve durum değişiklikleri izlemek nasıl.|Hangi bilgilerin istenen ve hangi dönüştürmeleri gereklidir.|  
|Durum değişiklikleri|Önemli.|Varolmayan.|  
|Yürütme sırası|Önemli.|Düşük önem derecesi.|  
|Birincil akış denetimi|Döngüler, koşullular ve (yöntem) işlev çağrıları.|Özyineleme dahil olmak üzere, işlev çağrıları.|  
|Birincil işleme birimi|Yapıların veya sınıfların örneklerini.|Birinci sınıf nesneleri ve veri koleksiyonları görür.|  
  
 Birçok programlama dili, belirli bir programlama modelini desteklemek için tasarlanmış olsa da, birçok genel dil birden çok paradigmalarını destekleme kadar esnektir. Örneğin, işlev işaretçileri içeren çoğu dil credibly işlevsel programlama desteği için kullanılabilir. Ayrıca, C# lambda ifadeleri de dahil olmak üzere, işlevsel programlama desteği ve tür çıkarımı açık dil uzantılarını içerir. LINQ teknolojisi, bildirim temelli, işlevsel programlama şeklidir.  
  
## <a name="functional-programming-using-xslt"></a>İşlevsel programlama XSLT kullanma  
 Saf işlevsel yaklaşım ile birçok XSLT geliştiricilerine sahibisiniz. Her şablon bir yalıtılmış, birleştirilebilir dönüştürme değerlendirilecek bir XSLT stil sayfası geliştirmek için en etkili yolu var. Tamamen devre dışı bırakmak vurgulanmış yürütme sırasıdır. XSLT yan etkileri (ile yordam kodu yürütmek mekanizmaları kaçış yan etkileri işlevsel impurity neden ortaya çıkarabilir özel durum) izin vermez. XSLT etkili bir araçtır, ancak bazı özelliklerine en uygun değildir. Örneğin, XML programlama yapıları ifade kod oldukça ayrıntılı ve bu nedenle sürdürülmesi zor hale getirir. Ayrıca, akış denetimi için özyineleme ağır güvenme okunması zor olan kodu neden olabilir. XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüşümleri](../../../../standard/data/xml/xslt-transformations.md).  
  
 Ancak, XSLT XML bir şekilden diğerine dönüştürme için saf işlevsel bir yaklaşım kullanarak değerini kanıtladılar. Saf işlevsel LINQ to XML programlama XSLT birçok açıdan benzer. Ancak LINQ to XML ve C# tarafından sunulan programlama yapıları daha okunabilir ve XSLT daha sürdürülebilir saf işlevsel dönüşümlere yazmanıza olanak sağlar.  
  
## <a name="advantages-of-pure-functions"></a>Saf işlevler avantajları  
 Saf işlevler olarak işlevsel dönüşümlere uygulamak için birincil saf işlevler birleştirilebilir nedeni: başka bir deyişle, bağımsızdır ve durum bilgisi olmayan. Bu özelliklere birtakım avantajlar, aşağıdakiler dahil olmak üzere getirin:  
  
-   Okunurluğu ve sürdürülebilirliği. Bu, her işlevin belirli bir görevi gerçekleştirmek için tasarlandığından bağımsız değişkenlerinden verilir. İşlevi, tüm dış durumuna bağımlı kalmayacak.  
  
-   Daha kolay reiterative geliştirme. Kod yeniden düzenlenmesi daha kolay olduğundan, değişiklikleri tasarlamak için genellikle uygulamak daha kolaydır. Örneğin, karmaşık bir dönüştürme yazın ve sonra biraz kod dönüşümünde birkaç kez yinelenir fark varsayalım. Saf bir yöntem aracılığıyla yeniden düzenlerseniz, yan etkileri hakkında endişelenmenize gerek kalmadan dilediğiniz zaman saf yönteminizi çağırabilir.  
  
-   Daha kolay test ve hata ayıklama. Saf işlevler daha kolay yalıtım modunda test edilebilir olduğundan, normal değerler, geçerli istisnai durumlara ve geçersiz istisnai durumlara saf işlev çağıran test kodu yazabilirsiniz.  
  
## <a name="transitioning-for-oop-developers"></a>Geçiş OOP geliştiricileri için  
 Geleneksel nesne yönelimli programlama, (OOP) çoğu Geliştirici kesinliği/yordam stili programlamada bilirsiniz. Saf işlevsel stilde geliştirmeye geçiş yapmak için bunlar kendi düşünmek ve yaklaşımları geliştirme için bir geçiş yapmanız gerekir.  
  
 Sorunları çözmek için OOP geliştiriciler sınıf Hiyerarşiler tasarım, uygun kapsülleme üzerinde odaklanın ve sınıf sözleşmeleri açısından düşünebilirsiniz. Nesne türleri durumunu ve davranışını güvenilirliği ve sınıfları, arabirimleri, devralma ve çok biçimlilik, gibi dil özellikleri bu sorunları çözmek için sağlanır.  
  
 Buna karşılık, işlevsel programlama, saf işlevsel dönüşümlere veri koleksiyonlarının evrimi bir alıştırma olarak işlem sorunları yaklaşıyor. İşlevsel programlama, durum ve değişebilir veri önler ve bunun yerine uygulama işlevlerin vurgular.  
  
 Hem zorunlu hem de işlevsel programlama yaklaşımları desteklediğinden Neyse ki, C# işlevsel programlamaya, tam artık gerektirmez. Bir geliştirici, hangi yaklaşımın belirli bir senaryo için en uygun seçebilirsiniz. Aslında, programlar genellikle iki yaklaşımı birleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Giriş saf işlevsel dönüşümlere (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
- [XSLT Dönüşümleri](../../../../standard/data/xml/xslt-transformations.md)  
- [Saf işlevler halinde (C#) yeniden düzenleme](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
