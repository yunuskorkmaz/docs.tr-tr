---
title: XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
ms.openlocfilehash: b37cb0f4bf9a85053d70d549ae005c7d50a50bc0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710810"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>XslTransform Sınıfında İsteğe Bağlı Davranışların Uygulanması

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> sınıfı, .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .

İsteğe bağlı davranışlar, [World Wide Web Konsorsiyumu (W3C) XSL dönüşümleri (XSLT) sürüm 1,0 önerisi](https://www.w3.org/TR/1999/REC-xslt-19991116)altında listelenen davranışlar olarak tanımlanır ve bu, uygulama sağlayıcısının bir durumu işlemek için kullanılabilecek birkaç seçenekten birini seçtiği bir yöntemdir. Örneğin, 7,3 bölümünde Işlem yönergeleri oluşturulurken W3C önerisi, `xsl:processing-instruction` içeriğinin örnekleniyor olması halinde, metin düğümlerinden başka düğümler oluşturduğunda hata olduğunu belirtir. Bazı sorunlar için, işlemciler, işlemcinin hatadan kurtulmak için karar verdiğinde hangi kararların yapılması gerektiğini söyler. Bölüm 7,3 ' de verilen sorun için, W3C, uygulamanın düğümleri ve bunların içeriğini yoksayarak bu hatadan kurtuyor olduğunu söyler.

Bu nedenle, W3C tarafından izin verilen her bir isteğe bağlı davranış için aşağıdaki tabloda, <xref:System.Xml.Xsl.XslTransform> sınıfının .NET Framework uygulamasına uygulanan isteğe bağlı davranışlar ve bu sorunun ele alındığı W3C XSLT 1,0 önerisine ilişkin bölüm listelenmektedir.

|Sorun|Davranış|Bölüm|
|-------------|--------------|-------------|
|Bir metin düğümü hem `xsl:strip-space` hem de `xsl:preserve-space`ile eşleşir.|Kurtar|3.4|
|Kaynak düğüm, birden fazla şablon kuralıyla eşleşiyor.|Kurtar|5.5|
|Ad alanı Tekdüzen Kaynak tanımlayıcısı (URI), birden çok ad alanı URI 'si için bir diğer ad olarak, hepsi aynı içeri aktarma önceliğine sahip olacak şekilde bildirilmiştir.|Kurtar|7.1.1|
|Öznitelik değeri şablonundan oluşturulan `xsl:attribute` ve `xsl:element` ad özniteliği geçerli bir nitelenmiş ad (QName) değil.|Özel durum oluştu|7.1.2 ve 7.1.3|
|Alt düğümler zaten öğe düğümüne eklendikten sonra bir öğeye öznitelik ekleme.|Kurtar|7.1.3|
|Bir özniteliği, öğe düğümü dışında bir şeye ekleme.|Kurtar|7.1.3|
|`xsl:attribute` öğesinin içeriğinin örneklenmesi bir metin düğümü değil.|Kurtar|7.1.3|
|İki öznitelik kümesi aynı içeri aktarma önceliğine ve genişletilmiş ada sahiptir. Her ikisi de aynı özniteliğe sahiptir ve aynı ada sahip ortak özniteliği içeren, daha yüksek önem taşıyan başka bir öznitelik kümesi yoktur.|Kurtar|7.1.4|
|`xsl:processing-instruction` Name özniteliği hem bir iki nokta üst üste adı (NCName) hem de bir Işleme yönergesi hedefi sağlamıyor.|Kurtar|7.3|
|`xsl:processing-instruction` içeriğini örnekleme metin düğümlerinden başka düğümler oluşturuyor.|Kurtar|7.3|
|`xsl:processing-instruction` içeriğin örneğini oluşturma sonuçları "`?>`" dizesini içerir.|Kurtar|7.3|
|`xsl:comment` içeriğin örneğini oluşturma sonuçları "--" dizesini içerir veya "-" ile biter.|Kurtar|7.4|
|`xsl:comment` içeriğinin örneğini oluşturma sonuçları metin düğümlerinden başka düğümler oluşturuyor.|Kurtar|7.4|
|Değişken bağlama öğesi içindeki şablon bir öznitelik düğümü veya bir ad alanı düğümü döndürür.|Kurtar|11.2|
|Belge işlevine geçilen URI 'den kaynak alınırken bir hata oluştu.|Özel durum oluştu|12.1|
|Belge işlevindeki URI başvurusu bir parça tanımlayıcısı içeriyor ve parça tanımlayıcısı işlenirken bir hata oluştu.|Özel durum oluştu|12.1|
|`xls:output``cdata-section-elements` adlı aynı ada sahip birden çok öznitelik vardır ve bu özniteliklerin aynı içeri aktarma önceliği vardır.|Kurtar|16|
|İşlemci, `xsl:output` öğesinin `encoding` özniteliğinde verilen karakter kodlama değerini desteklemiyor.|Kurtar|16.1|
|`disable-output-escaping` bir metin düğümü için kullanılır ve bu metin düğümü, sonuç ağacındaki bir metin düğümü dışında bir şey oluşturmak için kullanılır.|`disable-output-escaping` öznitelik yoksayıldı|16.4|
|Sonuç ağacı parçası, çıkış kaçış özelliği etkinleştirilmiş bir metin düğümü içeriyorsa, sonuç ağacı parçasını sayıya veya dizeye dönüştürme.|Yoksayıldı|16.4|
|XSLT işlemcisinin çıktı için kullandığı kodlamada temsil edilemeyecek karakterler için çıkış kaçış devre dışı bırakıldı.|Yoksayıldı|16.4|
|Bir öğeye alt öğe eklendikten sonra veya öznitelikleri eklendikten sonra bir ad alanı düğümü ekleme|Kurtar|Errampae25|
|`xsl:number` NaN, Infinite veya 0,5 ' den küçük.|Kurtar|Errampae24|
|İkinci bağımsız değişken düğümü-belge işlevine ayarlanan boş ve URI başvurusu göreli|Kurtar|Errampae14|

Errampadaki bölümler W3C [XSL dönüştürmeleri (XSLT) sürüm 1,0 belirtiminde Erminta](https://www.w3.org/1999/11/REC-xslt-19991116-errata/)bulunabilir.

## <a name="custom-defined-implementation-behaviors"></a>Özel tanımlı uygulama davranışları

<xref:System.Xml.Xsl.XslTransform> sınıfı uygulamasına özel davranışlar vardır. Bu bölümde, <xref:System.Xml.Xsl.XslTransform> sınıfı tarafından desteklenen `xsl:sort` ve isteğe bağlı özelliklerin sağlayıcıya özgü uygulamaları açıklanmaktadır.

## <a name="xslsort"></a>Sort

Sıralamak için bir dönüşüm kullanılırken, W3C XSLT 1,0 önerisi bazı gözlemlerin olmasını sağlar. Bunlar:

- İki XSLT işlemcisi uyumlu işlemciler olabilir, ancak yine de farklı şekilde sıralama yapılabilir.

- XSLT işlemcilerin hepsi aynı dilleri desteklemez.

- Diller açısından, farklı işlemciler `xsl:sort.` belirtilen belirli bir dilde sıralama üzerinde farklılık gösterebilir

Aşağıdaki tabloda, <xref:System.Xml.Xsl.XslTransform>kullanarak bir dönüştürmenin .NET Framework uygulamasındaki her bir veri türü için uygulanan sıralama davranışı gösterilmektedir:

|Veri türü|Sıralama davranışı|
|---------------|----------------------|
|Metin|Veriler, ortak dil çalışma zamanı (CLR) dizesi. Compare yöntemi ve kültürel yerel ayarı kullanılarak sıralanır. Veri türü "metin" değerine eşitse, <xref:System.Xml.Xsl.XslTransform> sınıfında sıralama CLR 'nin dize karşılaştırma davranışları ile aynı şekilde davranır.|
|Sayı|Sayısal değerler, XML yol dili (XPath) numaraları olarak değerlendirilir ve W3C [XML Path Language (XPath) sürüm 1,0 önerisi, bölüm 3,5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers)' de özetlenen ayrıntılara göre sıralanır.|

## <a name="optional-features-supported"></a>Desteklenen isteğe bağlı özellikler

Aşağıdaki tabloda, bir XSLT işlemcisinin uygulanması ve <xref:System.Xml.Xsl.XslTransform> sınıfında uygulanması için isteğe bağlı özellikler gösterilmektedir.

|Özellik|Başvuru konumu|Notlar|
|-------------|------------------------|-----------|
|`<xsl:text...>` ve `<xsl:value-of...>` etiketlerindeki `disable-output-escaping` özniteliği.|W3C XSLT 1,0 önerisi,<br /><br /> Bölüm 16,4|`xsl:text` veya `xsl:value-of` öğeleri bir `xsl:comment`, `xsl:processing-instruction`veya `xsl:attribute` öğesi kullanılırken `disable-output-escaping` özniteliği yoksayılır.<br /><br /> Metin ve kaçışlı metin çıktısı içeren sonuç ağacı parçaları desteklenmez.<br /><br /> Bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesnesine dönüştürülürken Disable-output-kaçış özniteliği yok sayılır.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
