---
title: XslTransform sınıfında isteğe bağlı davranışların
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1602479d4986109ffe89a87250297ee5687930ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609583"
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>XslTransform sınıfında isteğe bağlı davranışların

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](migrating-from-the-xsltransform-class.md) daha fazla bilgi için.

İsteğe bağlı davranışların olarak listelenen davranışlar açıklanmıştır [World Wide Web Consortium (W3C) XSLT Dönüşümleri (XSLT) sürüm 1.0 öneri](https://www.w3.org/TR/1999/REC-xslt-19991116), hangi uygulama sağlayıcısı birkaç olası birini seçer, bir durumu işlemek için bir yol olarak seçenekleri. Örneğin, Bölüm 7.3 oluşturma işleme yönergeleri, W3C önerisi bir hata durumunda içeriğinin örnekleme 'un `xsl:processing-instruction` metin düğümleri dışındaki düğümlerde oluşturur. Bazı sorunlar için W3C hangi karar yapılmalıdır işlemci hatadan kurtarmayı karar verirse, söyler. 7.3 bölümde verilen sorun için uygulama bu hatadan düğümleri ve içeriklerini yoksayarak kurtarabilirsiniz W3C diyor.

Bu nedenle, her W3C tarafından izin verilen isteğe bağlı davranışları için aşağıdaki tabloda isteğe bağlı davranışların uygulanması için uygulanan listeler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uygulaması <xref:System.Xml.Xsl.XslTransform> sınıfı ve hangi W3C XSLT 1.0 öneri de bölümünde bu sorunu ele alınmıştır.

|Sorun|Davranış|Bölüm|
|-------------|--------------|-------------|
|Bir metin düğümü her ikisi de eşleşen `xsl:strip-space` ve `xsl:preserve-space`.|Kurtarma|3.4|
|Kaynak düğüm, birden fazla şablon kuralı eşleşir.|Kurtarma|5.5|
|Ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) için birden çok ad alanı URI, tümü aynı alma önceliğe sahip bir diğer ad olarak bildirilir.|Kurtarma|7.1.1|
|Ad özniteliği `xsl:attribute` ve `xsl:element` bir öznitelik değeri şablondan oluşturulmuş geçerli bir tam adı (QName) değil.|Özel durum oluştu|7.1.2 ve 7.1.3'ten|
|Öğe düğümü için alt düğümleri eklendikten sonra bir öznitelik bir öğe ekleme.|Kurtarma|7.1.3|
|Öznitelik, bir öğe düğümü dışındaki herhangi bir şey ekleme.|Kurtarma|7.1.3|
|Örneğinin içeriğini `xsl:attribute` öğesi bir metin düğümü değil.|Kurtarma|7.1.3|
|İki öznitelik kümeleri, genişletilmiş adının ve aynı alma önceliğe sahip. Her ikisi de aynı özniteliğe sahip ve aynı ada sahip genel öznitelik daha yüksek önem derecesiyle içeren başka bir öznitelik kümesi yok.|Kurtarma|7.1.4|
|`xsl:processing-instruction` öznitelik adı bir no-iki nokta üst üste adı (NCName) hem bir işleme yönergesi hedefi vermez.|Kurtarma|7.3|
|İçeriği, örnekleme `xsl:processing-instruction` metin düğümleri dışındaki düğümlerde oluşturur.|Kurtarma|7.3|
|İçeriği, örnekleme sonuçlarını `xsl:processing-instruction` dizesini içeren "`?>`".|Kurtarma|7.3|
|İçeriği, örnekleme sonuçlarını `xsl:comment` dizesini içeren "--", veya ile biter "-".|Kurtarma|7.4|
|İçeriği, örnekleme sonuçlarını `xsl:comment` metin düğümleri dışındaki düğümlerde oluşturur.|Kurtarma|7.4|
|Bir değişkeni bağlama öğenin şablonda bir öznitelik düğümü veya ad alanı düğümü döndürür.|Kurtarma|11.2|
|Belge işleve geçirilen URI'deki kaynağı alınırken bir hata yoktur.|Özel durum oluştu|12.1|
|Bir parça tanımlayıcı belge işlevindeki URI başvuru içeren ve parça tanımlayıcı işlenirken bir hata yoktur.|Özel durum oluştu|12.1|
|Aynı ada sahip adlandırılmamış birden çok öznitelik `cdata-section-elements` içinde `xls:output`, ve bu öznitelikleri aynı alma önceliğe sahip.|Kurtarma|16|
|Verilen değer kodlama karakter işlemci desteklemiyor `encoding` özniteliği `xsl:output` öğesi.|Kurtarma|16.1|
|`disable-output-escaping` bir metin düğümü için kullanılır ve bu metin düğümü sonucu ağacında bir metin düğümü dışında bir şey oluşturmak için kullanılır.|`disable-output-escaping` özniteliği yoksayılıyor|16.4|
|Sonuç ağacı parçası etkin çıkış kaçış ile bir metin düğümü içeriyorsa, bir sayı veya dize bir sonuç ağacı parçası dönüştürülüyor.|Yoksayıldı|16.4|
|Çıkış kaçış XSLT işlemci için çıkış kullandığını kodlama temsil edilemeyen karakterler için devre dışı bırakıldı.|Yoksayıldı|16.4|
|Alt öğeler veya öznitelikleri eklendikten sonra onu eklendikten sonra bir ad alanı düğümü bir öğe ekleme|Kurtarma|Errata e25|
|`xsl:number` NaN, sonsuz veya 0,5 değerinden ' dir.|Kurtarma|Errata e24|
|Düğüm kümesi belge işleve ikinci bağımsız değişken boş ve göreli URI başvurusu|Kurtarma|Errata e14|

W3C errata bölümlerinden bulunabilir [XSLT Dönüşümleri (XSLT) sürüm 1.0 belirtimi Errata](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).

## <a name="custom-defined-implementation-behaviors"></a>Uygulama özel tanımlı davranışlar

Davranışları için benzersiz <xref:System.Xml.Xsl.XslTransform> sınıfı uygulaması. Bu bölümde ele alınmaktadır sağlayıcıya özel uygulanışı `xsl:sort` ve tarafından desteklenen isteğe bağlı özellikler <xref:System.Xml.Xsl.XslTransform> sınıfı.

## <a name="xslsort"></a>Sort

Bir dönüştürme sıralamak için kullanılırken, bazı gözlemler W3C XSLT 1.0 önerisi sağlar. Bunlar:

- İki XSLT işlemci işlemcilerin uygun, ancak hala farklı sıralama yapılabilir.

- Tüm XSLT işlemci ile aynı dilleri destekler.

- Diller onaylamaz, farklı işlemcilerin sıralama kendi üzerinde belirtilmemiş belirli bir dil değişebilir `xsl:sort.`

Aşağıdaki tablo her bir veri türü dönüştürme kullanarak bir .NET Framework uygulamasında için uygulanan sıralama davranışını gösterir <xref:System.Xml.Xsl.XslTransform>:

|Veri türü|Sıralama davranışını|
|---------------|----------------------|
|Metin|Veriler, ortak dil çalışma zamanı (CLR) String.Compare yöntemi ve kültürel bir yerel ayar kullanılarak sıralanır. Equals "metin" veri türü, sıralamayı <xref:System.Xml.Xsl.XslTransform> sınıfı CLR dize karşılaştırma davranışlarını aynı şekilde davranır.|
|Sayı|Sayısal değerlerin XML Path Language (XPath) sayı olarak kabul edilir ve W3C ana hatlarıyla belirtilen ayrıntılara göre sıralanır [XML Path Language (XPath) sürüm 1.0 öneri, Bölüm 3.5](https://www.w3.org/TR/1999/REC-xpath-19991116/#numbers).|

## <a name="optional-features-supported"></a>Desteklenen isteğe bağlı özellikler

Bir XSLT işlemci uygulamak isteğe bağlıdır ve uygulanan özellikler aşağıdaki tabloda gösterilmektedir <xref:System.Xml.Xsl.XslTransform> sınıfı.

|Özellik|Başvuru konum|Notlar|
|-------------|------------------------|-----------|
|`disable-output-escaping` özniteliği `<xsl:text...>` ve `<xsl:value-of...>` etiketler.|W3C XSLT 1.0 öneri,<br /><br /> Bölüm 16.4|`disable-output-escaping` Özniteliği göz ardı edilir olduğunda `xsl:text` veya `xsl:value-of` öğeleri kullanıldığı bir `xsl:comment`, `xsl:processing-instruction`, veya `xsl:attribute` öğesi.<br /><br /> Metin ve kaçış metin çıktısı içeren sonucu ağacı parçalarını desteklenmez.<br /><br /> İçin dönüştürme yaparken disable-çıkış kaçış özniteliği yoksayılıyor bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesne.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Xsl.XslTransform>
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [Dönüşümlerde XPathNavigator](xpathnavigator-in-transformations.md)
- [Dönüşümlerde XPathNodeIterator](xpathnodeiterator-in-transformations.md)
- [XslTransform’a XPathDocument Girişi](xpathdocument-input-to-xsltransform.md)
- [XslTransform’a XmlDataDocument Girişi](xmldatadocument-input-to-xsltransform.md)
- [XslTransform’a XmlDocument Girişi](xmldocument-input-to-xsltransform.md)
