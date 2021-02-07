---
description: 'Daha fazla bilgi edinin: XslTransform sınıfında Isteğe bağlı davranışların uygulanması'
title: XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması
ms.date: 03/30/2017
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
ms.openlocfilehash: 56936183f635a002d2226bd8e91a6539308259e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713760"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

İsteğe bağlı davranışlar, [World Wide Web Konsorsiyumu (W3C) XSL dönüşümleri (XSLT) sürüm 1,0 önerisi](https://www.w3.org/TR/1999/REC-xslt-19991116)altında listelenen davranışlar olarak tanımlanır ve bu, uygulama sağlayıcısının bir durumu işlemek için kullanılabilecek birkaç seçenekten birini seçtiği bir yöntemdir. Örneğin, 7,3 bölümünde Işlem yönergeleri oluşturulurken W3C önerisi, `xsl:processing-instruction` metin düğümlerinden farklı düğüm oluşturur içeriği örneklerse bir hata olduğunu belirtir. Bazı sorunlar için, işlemciler, işlemcinin hatadan kurtulmak için karar verdiğinde hangi kararların yapılması gerektiğini söyler. Bölüm 7,3 ' de verilen sorun için, W3C, uygulamanın düğümleri ve bunların içeriğini yoksayarak bu hatadan kurtuyor olduğunu söyler.

Bu nedenle, W3C tarafından izin verilen her bir isteğe bağlı davranış için aşağıdaki tabloda, sınıfının .NET Framework uygulamasına uygulanan isteğe bağlı davranışlar <xref:System.Xml.Xsl.XslTransform> ve bu sorunun ele alındığı W3C XSLT 1,0 önerisi listelenmiştir.

|Sorun|Davranış|Section|
|-------------|--------------|-------------|
|Bir metin düğümü `xsl:strip-space` ve ile eşleşir `xsl:preserve-space` .|Kurtar|3.4|
|Kaynak düğüm, birden fazla şablon kuralıyla eşleşiyor.|Kurtar|5.5|
|Ad alanı Tekdüzen Kaynak tanımlayıcısı (URI), birden çok ad alanı URI 'si için bir diğer ad olarak, hepsi aynı içeri aktarma önceliğine sahip olacak şekilde bildirilmiştir.|Kurtar|7.1.1|
|' Deki `xsl:attribute` ve `xsl:element` öznitelik değeri şablonundan oluşturulan ad özniteliği geçerli bir nitelenmiş ad (QName) değil.|Özel durum oluştu|7.1.2 ve 7.1.3|
|Alt düğümler zaten öğe düğümüne eklendikten sonra bir öğeye öznitelik ekleme.|Kurtar|7.1.3|
|Bir özniteliği, öğe düğümü dışında bir şeye ekleme.|Kurtar|7.1.3|
|Öğe içeriğinin örneklenmesi `xsl:attribute` bir metin düğümü değil.|Kurtar|7.1.3|
|İki öznitelik kümesi aynı içeri aktarma önceliğine ve genişletilmiş ada sahiptir. Her ikisi de aynı özniteliğe sahiptir ve aynı ada sahip ortak özniteliği içeren, daha yüksek önem taşıyan başka bir öznitelik kümesi yoktur.|Kurtar|7.1.4|
|`xsl:processing-instruction` Name özniteliği hem bir iki nokta üst üste adı (NCName) hem de bir Işleme yönergesi hedefi getirmiyor.|Kurtar|7.3|
|`xsl:processing-instruction`Metin düğümleri dışındaki düğüm oluşturur içeriğinin örneği oluşturuluyor.|Kurtar|7.3|
|İçeriği örneği oluşturma sonuçları `xsl:processing-instruction` "" dizesini içerir `?>` .|Kurtar|7.3|
|İçeriğinin örneğini oluşturma sonuçları `xsl:comment` "--" dizesini içerir veya "-" ile biter.|Kurtar|7.4|
|`xsl:comment`Metin düğümlerinden farklı oluşturulan düğümlerin içeriğini örnekleniyor sonuçları.|Kurtar|7.4|
|Değişken bağlama öğesi içindeki şablon bir öznitelik düğümü veya bir ad alanı düğümü döndürür.|Kurtar|11,2|
|Belge işlevine geçilen URI 'den kaynak alınırken bir hata oluştu.|Özel durum oluştu|12.1|
|Belge işlevindeki URI başvurusu bir parça tanımlayıcısı içeriyor ve parça tanımlayıcısı işlenirken bir hata oluştu.|Özel durum oluştu|12.1|
|İçinde adlandırılmayan aynı ada sahip birden çok öznitelik vardır `cdata-section-elements` `xls:output` ve bu özniteliklerin aynı içeri aktarma önceliği vardır.|Kurtar|16|
|İşlemci, öğesinin özniteliğinde verilen karakter kodlama değerini desteklemiyor `encoding` `xsl:output` .|Kurtar|16,1|
|`disable-output-escaping` bir metin düğümü için kullanılır ve bu metin düğümü, sonuç ağacındaki bir metin düğümü dışında bir öğe oluşturmak için kullanılır.|`disable-output-escaping` öznitelik yoksayıldı|16.4|
|Sonuç ağacı parçası, çıkış kaçış özelliği etkinleştirilmiş bir metin düğümü içeriyorsa, sonuç ağacı parçasını sayıya veya dizeye dönüştürme.|Yoksayıldı|16.4|
|XSLT işlemcisinin çıktı için kullandığı kodlamada temsil edilemeyecek karakterler için çıkış kaçış devre dışı bırakıldı.|Yoksayıldı|16.4|
|Bir öğeye alt öğe eklendikten sonra veya öznitelikleri eklendikten sonra bir ad alanı düğümü ekleme|Kurtar|Errampae25|
|`xsl:number` NaN, Infinite veya 0,5 ' den küçük.|Kurtar|Errampae24|
|İkinci bağımsız değişken düğümü-belge işlevine ayarlanan boş ve URI başvurusu göreli|Kurtar|Errampae14|

Errampadaki bölümler W3C [XSL dönüştürmeleri (XSLT) sürüm 1,0 belirtiminde Erminta](https://www.w3.org/1999/11/REC-xslt-19991116-errata/)bulunabilir.

## <a name="custom-defined-implementation-behaviors"></a>Custom-Defined uygulama davranışları

Sınıf uygulamasına özel davranışlar vardır <xref:System.Xml.Xsl.XslTransform> . Bu bölümde, `xsl:sort` sınıfı tarafından desteklenen ve isteğe bağlı özelliklerin sağlayıcıya özgü uygulamaları ele alınmaktadır <xref:System.Xml.Xsl.XslTransform> .

## <a name="xslsort"></a>Sort

Sıralamak için bir dönüşüm kullanılırken, W3C XSLT 1,0 önerisi bazı gözlemlerin olmasını sağlar. Bunlar:

- İki XSLT işlemcisi uyumlu işlemciler olabilir, ancak yine de farklı şekilde sıralama yapılabilir.

- XSLT işlemcilerin hepsi aynı dilleri desteklemez.

- Dillere göre farklı işlemciler, belirli bir dildeki sıralama üzerinde belirtilen bir dilde farklılık gösterebilir `xsl:sort.`

Aşağıdaki tabloda, kullanarak bir dönüşümün .NET Framework uygulamasındaki her bir veri türü için uygulanan sıralama davranışı gösterilmektedir <xref:System.Xml.Xsl.XslTransform> :

|Veri türü|Sıralama davranışı|
|---------------|----------------------|
|Metin|Veriler, ortak dil çalışma zamanı (CLR) dizesi. Compare yöntemi ve kültürel yerel ayarı kullanılarak sıralanır. Veri türü "metin" değerine eşitse, <xref:System.Xml.Xsl.XslTransform> sınıftaki SıRALAMA clr 'nin dize karşılaştırma davranışları ile aynı şekilde davranır.|
|Sayı|Sayısal değerler, XML yol dili (XPath) numaraları olarak değerlendirilir ve W3C [XML Path Language (XPath) sürüm 1,0 önerisi, bölüm 3,5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers)' de özetlenen ayrıntılara göre sıralanır.|

## <a name="optional-features-supported"></a>Desteklenen isteğe bağlı özellikler

Aşağıdaki tabloda, bir XSLT işlemcisinin uygulanması ve sınıfında uygulanması için isteğe bağlı özellikler gösterilmektedir <xref:System.Xml.Xsl.XslTransform> .

|Öne çıkan özelliği|Başvuru konumu|Notlar|
|-------------|------------------------|-----------|
|`disable-output-escaping``<xsl:text...>`ve etiketlerinin özniteliği `<xsl:value-of...>` .|W3C XSLT 1,0 önerisi,<br /><br /> Bölüm 16,4|, Veya `disable-output-escaping` `xsl:text` `xsl:value-of` öğeleri bir `xsl:comment` , `xsl:processing-instruction` veya `xsl:attribute` öğesinde kullanıldığında özniteliği yok sayılır.<br /><br /> Metin ve kaçışlı metin çıktısı içeren sonuç ağacı parçaları desteklenmez.<br /><br /> Bir veya nesnesine dönüştürülürken Disable-output-kaçış özniteliği yok sayılır <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> .|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
