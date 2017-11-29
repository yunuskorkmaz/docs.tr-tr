---
title: "İşlevsel Programlama vs. Kesinlik temelli programlama (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c57d89120eee8c7f84d6e87b14f038378a0b3d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="functional-programming-vs-imperative-programming-c"></a>İşlevsel Programlama vs. Kesinlik temelli programlama (C#)
Bu konuda karşılaştırır ve işlevsel programlama daha geleneksel kesinlik temelli (yordam) programlama ile karşılaştırır.  
  
## <a name="functional-programming-vs-imperative-programming"></a>İşlevsel Programlama vs. Kesinlik temelli programlama  
 *İşlevsel programlama* sorunu çözmeye saf bir işlev yaklaşım desteklemek için açıkça kip oluşturuldu. İşlevsel programlama biçimi olan *bildirim temelli programlama*. Buna karşılık, nesne odaklı programlama (OOP) dil C#, Visual Basic, C++ ve Java gibi dahil olmak üzere çoğu temel dil öncelikle desteklemek için tasarlanmış olan *kesinlik temelli* (yordam) programlama.  
  
 Kesinlik temelli bir yaklaşım ile bir geliştirici açıklayan kod ayrıntı kesin bilgisayarı hedef gerçekleştirmek için uygulamanız gereken adımlar yazar. Bu bazen olarak adlandırılır *algoritmik* programlama. Buna karşılık, işlevsel bir yaklaşım sorun yürütülecek işlevler kümesi olarak oluşturmayı kapsar. Her işlev giriş ve her hangi bir işlev döndürür dikkatle tanımlarsınız. Aşağıdaki tabloda bu iki yaklaşım genel farklarını bazıları açıklanmaktadır.  
  
|Özelliği|Kesinlik temelli bir yaklaşım|İşlevsel bir yaklaşım|  
|--------------------|-------------------------|-------------------------|  
|Programcı odak|(Algoritmaları) görevlerin nasıl gerçekleştirileceği ve durumunda değişikliklerin nasıl izleneceği.|Hangi bilgilerin istenen ve hangi dönüşümleri gereklidir.|  
|Durum değişiklikleri|Önemli.|Varolmayan.|  
|Yürütme sırasını|Önemli.|Düşük önem.|  
|Birincil akış denetimi|Döngüler, koşulları ve işlev (yöntem) çağrıları.|Özyineleme dahil olmak üzere işlevi çağırır.|  
|Birincil işleme birimi|Yapıları veya sınıfların örnekleri.|İlk sınıf nesneleri ve veri koleksiyonları görür.|  
  
 Çoğu dil belirli bir programlama standardı desteklemek için tasarlanmış olsa da, birçok genel diller birden fazla örneklerinde desteklemek için yeterince esnektir. Örneğin, işlev işaretçileri içeren çoğu dil credibly işlevsel programlama desteklemek için kullanılabilir. Ayrıca, C# ve tür çıkarımı lambda ifadeleri de dahil olmak üzere işlevsel programlama desteklemek için açık dil uzantıları içerir. LINQ teknolojisi bildirim temelli, işlevsel programlama biçimidir.  
  
## <a name="functional-programming-using-xslt"></a>İşlev XSLT kullanarak programlama  
 Birçok XSLT geliştiricilerine saf işlevsel yaklaşımda biliyorsunuzdur. XSLT stil sayfasını geliştirmek için en etkili her şablon bir yalıtılmış, birleştirilebilir dönüşümü işlemek için bir yoludur. Yürütme tamamen XML'deki vurgulanmış sırasıdır. XSLT yan etkileri (ile yordam kod yürütmek için mekanizmalar kaçış içinde işlev impurity neden yan etkileri yaratabilir özel durum) izin vermiyor. XSLT etkili bir aracı olsa da, ancak bazıları onun özelliklerini en iyi değil. Örneğin, XML programlama yapıları ifade kod görece ayrıntılı ve korumak bu nedenle zor hale getirir. Ayrıca, akış denetimi için özyineleme ağır bağımlılık okunması zor kodda neden olabilir. XSLT hakkında daha fazla bilgi için bkz: [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md).  
  
 Ancak, XSLT XML bir şekli'ndan diğerine dönüştürme için saf işlevsel bir yaklaşım kullanarak değerini oluyor uygulamasına yol açıyordu. Saf işlevsel LINQ-XML ile programlama XSLT birçok yönden benzer. Ancak, XML ve C# üzerinde LINQ tarafından sunulan programlama yapıları daha okunabilir ve sürdürülebilir XSLT daha saf işlevsel dönüşümleri yazmanıza izin verir.  
  
## <a name="advantages-of-pure-functions"></a>Saf işlevleri avantajları  
 Saf işlev olarak işlev dönüştürmeleri uygulamak için birincil saf işlevleri birleştirilebilir nedeni: başka bir deyişle, kendi içinde bulunan ve durum bilgisiz. Bu özelliklere aşağıdakiler de dahil olmak üzere avantajları getirin:  
  
-   Artan okunabilirlik ve bakımı. Belirli bir görevi gerçekleştirmek için her işlevi tasarlandığından bu değişkenlerinin verilir. İşlev üzerinde herhangi bir dış durum bağlı değildir.  
  
-   Daha kolay reiterative geliştirme. Kod düzenleme için daha kolay olduğundan, tasarım değişiklikleri genellikle uygulamak daha kolaydır. Örneğin, karmaşık bir dönüşüm yazma ve bazı kodlar dönüşümünde birkaç kez yinelenen fark varsayalım. Saf bir yöntem yeniden düzenlemeniz varsa, yan etkileri hakkında endişelenmeden gerçekleştirilse, saf yöntemini çağırabilirsiniz.  
  
-   Daha kolay test ve hata ayıklama. Saf işlevleri yalıtım modunda daha kolayca sınanabilir çünkü tipik değerleri, geçerli sınır durumları ve geçersiz kenar durumlarda saf işlev çağrıları test kod yazabilirsiniz.  
  
## <a name="transitioning-for-oop-developers"></a>OOP geliştiriciler için geçiş  
 Geleneksel nesne odaklı programlama (OOP), çoğu Geliştirici kesinliği/yordam stili programlamada bilirsiniz. Saf işlevsel stilde geliştirmek için geçiş yapmak için bunlar kendi düşünmeye ve bunların yaklaşımı geliştirme için bir geçiş yapmanız gerekir.  
  
 Sorunları çözmek için OOP geliştiriciler sınıfı hiyerarşi tasarımı, üzerinde uygun kapsülleme odaklanmanıza ve sınıf sözleşmeleri açısından düşünün. Nesne türlerinin durumu ve davranış en önemli ve bu sorunları çözmek için sınıflar, arabirimler, devralma ve çok biçimlilik, gibi dil özellikleri sağlanır.  
  
 Buna karşılık, işlevsel programlama veri koleksiyonları saf işlevsel dönüşümleri değerlendirilmesinde bir alıştırma olarak hesaplama sorunları yaklaşıyor. İşlevsel programlama durumu ve değişebilir veri engeller ve bunun yerine uygulama işlevlerin vurgular.  
  
 Kesinlik temelli ve işlevsel programlama yaklaşımlar desteklediğinden Neyse ki, C# işlevsel programlama için tam artık gerektirmez. Bir geliştirici, hangi yaklaşımın belirli bir senaryo için en uygun olan seçebilirsiniz. Aslında, programlar genellikle her iki yaklaşımı birleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Giriş saf işlevsel Dönüşümleri (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [XSLT dönüştürmeleri](../../../../standard/data/xml/xslt-transformations.md)  
 [Saf işlevlerini (C#) yeniden düzenleme](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
