---
title: İsteğe bağlı davranışları çok sınıfında uygulaması
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d2758ea1-03f6-47bd-88d2-0fb7ccdb2fab
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3c2ffa755c642b2a3c7dd47d7007bff7239f500f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="implementation-of-discretionary-behaviors-in-the-xsltransform-class"></a>İsteğe bağlı davranışları çok sınıfında uygulaması
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Davranışları World Wide Web Konsorsiyumu (W3C) XSL Dönüşümleri (XSLT) sürümü 1.0 öneri, uygulama sağlayıcısı olası seçeneklerden biri bir şekilde seçer (www.w3.org/TR/xslt) listelendiği gibi isteğe bağlı davranışları açıklanmaktadır bir durumu işlemek için. Örneğin, Bölüm 7.3 oluşturma işleme yönergelerde W3C önerisi hata içeriğinin başlatmasını varsa 'un `xsl:processing-instruction` metin düğümleri dışında düğümleri oluşturur. Bazı sorunlar için W3C hangi karar yapılmalıdır işlemci hatadan kurtarmak karar olmadığını bildirir. 7.3 bölümünde verilen sorun için uygulama bu hatadan düğümleri ve bunların içeriği yoksayılıyor kurtarabilirsiniz W3C söyler.  
  
 Bu nedenle, her W3C tarafından izin verilen isteğe bağlı davranışları için aşağıdaki tabloda uyguladığı için isteğe bağlı davranışları listeler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uyarlamasını <xref:System.Xml.Xsl.XslTransform> sınıfı ve ne W3C XSLT 1.0 öneri bölümünde bu sorunu ele alınmıştır.  
  
|Sorun|Davranış|Bölüm|  
|-------------|--------------|-------------|  
|Bir metin düğümü hem eşleşen `xsl:strip-space` ve `xsl:preserve-space`.|Kurtarma|3.4|  
|Bir kaynak düğüm birden fazla şablon kuralla eşleşir.|Kurtarma|5.5|  
|Ad alanı Tekdüzen Kaynak Tanımlayıcısı (URI) birden çok ad alanı URI, tümü aynı alma önceliğe sahip olmak için diğer ad olarak bildirilir.|Kurtarma|7.1.1|  
|Adı özniteliği `xsl:attribute` ve `xsl:element` bir öznitelik değeri şablondan oluşturulan geçerli bir tam adı (QName) değil.|Özel durum oluştu|7.1.2 ve 7.1.3'ten|  
|Alt düğümler öğesi düğüme zaten eklendikten sonra bir özniteliği bir öğe olarak ekleniyor.|Kurtarma|7.1.3|  
|Öznitelik, bir öğe düğümü dışında her şey ekleme.|Kurtarma|7.1.3|  
|Örnek oluşturma içeriğinin `xsl:attribute` öğesi bir metin düğümü değil.|Kurtarma|7.1.3|  
|İki öznitelik kümesi aynı alma öncelik ve genişletilmiş ada sahip. Her ikisi de aynı özniteliğine sahip ve aynı ada sahip sık kullanılan öznitelik daha yüksek öncelikli olarak içeren başka bir öznitelik kümesi yok.|Kurtarma|7.1.4|  
|`xsl:processing-instruction` ad özniteliği yok iki nokta üst üste adı (NCName) ve bir işleme yönergesi hedefi vermez.|Kurtarma|7.3|  
|İçeriği başlatmasını `xsl:processing-instruction` metin düğümleri dışında düğümleri oluşturur.|Kurtarma|7.3|  
|İçeriği başlatmasını sonuçlarını `xsl:processing-instruction` dizesini içeren "`?>`".|Kurtarma|7.3|  
|İçeriği başlatmasını sonuçlarını `xsl:comment` dizesini içeren "--", veya ile biten "-".|Kurtarma|7.4|  
|İçeriği başlatmasını sonuçlarını `xsl:comment` metin düğümleri dışında düğümleri oluşturur.|Kurtarma|7.4|  
|Değişken bağlama öğesi şablonda bir öznitelik düğümü veya bir ad alanı düğümü döndürür.|Kurtarma|11.2|  
|Kaynak belge işlevdeki geçirilen URI alınırken bir hata var.|Özel durum oluştu|12.1|  
|Parça tanımlayıcısı işlenirken bir hata oluştu ve bir parça tanımlayıcı belge işlevinde URI başvuru içeriyor.|Özel durum oluştu|12.1|  
|Adlandırılmamış aynı ada sahip birden çok öznitelik `cdata-section-elements` içinde `xls:output`, ve bu öznitelikler aynı alma önceliklidir.|Kurtarma|16|  
|İşlemci verilen değer kodlama karakter desteklemiyor `encoding` özniteliği `xsl:output` öğesi.|Kurtarma|16.1|  
|`disable-output-escaping` bir metin düğümü için kullanılır ve bu metin düğümü, bir metin düğümü dışında bir şey sonuç ağacında oluşturmak için kullanılır.|`disable-output-escaping` öznitelik göz ardı edilir|16.4|  
|Sonuç ağacı parçası etkin çıkış kaçış ile bir metin düğümü içeriyorsa sonuç ağacı parçası bir sayı veya dize dönüştürme.|Yoksayıldı|16.4|  
|Çıktı kaçış XSLT işlemci çıktı için kullandığını kodlama temsil edilemeyen karakterler için devre dışı bırakılır.|Yoksayıldı|16.4|  
|Alt ona veya öznitelikleri eklendikten sonra eklendikten sonra bir öğe için bir ad alanı düğüm ekleme|Kurtarma|Ayrıntıyla açıklayan hata bilgilerini e25|  
|`xsl:number` NaN, sonsuz veya 0,5'den daha az olur.|Kurtarma|Ayrıntıyla açıklayan hata bilgilerini e24|  
|Düğüm kümesi belge işlevi ikinci bağımsız değişkeni boş ve göreli URI başvurusu|Kurtarma|Ayrıntıyla açıklayan hata bilgilerini e14|  
  
 Ayrıntıyla açıklayan hata bilgilerini bölümlerinden www.w3.org/1999/11/REC-xslt-19991116-errata bulunan World Wide Web Konsorsiyumu (W3C) XSL Dönüşümleri (XSLT) sürüm 1.0 belirtimi ayrıntıyla açıklayan hata bilgilerini, bulunabilir.  
  
## <a name="custom-defined-implementation-behaviors"></a>Özel tanımlı bir uygulama davranışları  
 Davranışları benzersiz <xref:System.Xml.Xsl.XslTransform> sınıfı uygulama. Bu bölümde, sağlayıcıya özgü uyarlamasını anlatılmaktadır `xsl:sort` ve tarafından desteklenen isteğe bağlı özellikler <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
## <a name="xslsort"></a>Sort  
 Bir dönüşüm sıralamak için kullanırken, W3C XSLT 1.0 öneri bazı gözlemleri yapar. Bunlar:  
  
-   İki XSLT işlemci işlemciler uyumsuz, ancak hala farklı sıralama yapılabilir.  
  
-   Tüm XSLT işlemcileri dillerini destekler.  
  
-   Dilleri göre sıralama kendi üzerinde belirtilmemiş belirli bir dil farklı işlemcilere değişebilir `xsl:sort.`  
  
 Aşağıdaki tabloda her bir veri türü dönüşümü kullanarak .NET Framework uygulamasında için uygulanan sıralama davranışı gösterilmektedir <xref:System.Xml.Xsl.XslTransform>.  
  
|Veri türü|Sıralama davranışı|  
|---------------|----------------------|  
|Metin|Ortak dil çalışma zamanı (CLR) String.Compare yöntemi ve kültürel yerel ayarını kullanarak veri sıralanır. Eşittir "metin" veri türü, sıralamayı <xref:System.Xml.Xsl.XslTransform> sınıfı aynı şekilde davrandığını CLR dize karşılaştırma davranışlarını.|  
|Sayı|Sayısal değerler XML Path dili (XPath) sayı olarak kabul edilir ve W3C XML Path dili (XPath) sürüm 1.0 öneri, Bölüm 3.5 (www.w3.org/TR/xpath.html#numbers) özetlenen ayrıntılara göre sıralanır.|  
  
## <a name="optional-features-supported"></a>Desteklenen isteğe bağlı özellikler  
 Aşağıdaki tabloda, bir XSLT işlemcisi uygulamak isteğe bağlıdır ve içinde uygulanan özellikleri gösterilmektedir <xref:System.Xml.Xsl.XslTransform> sınıfı.  
  
|Özellik|Başvuru konumu|Notlar|  
|-------------|------------------------|-----------|  
|`disable-output-escaping` özniteliği `<xsl:text...>` ve `<xsl:value-of...>` etiketler.|W3C XSLT 1.0 öneri,<br /><br /> Bölüm 16.4|`disable-output-escaping` Özniteliği göz ardı edilir zaman `xsl:text` veya `xsl:value-of` öğeleri kullanıldığı bir `xsl:comment`, `xsl:processing-instruction`, veya `xsl:attribute` öğesi.<br /><br /> Metin ve atlanan metin çıktısı içeren sonuç ağaç parçaları desteklenmez.<br /><br /> Devre dışı bırak çıkış kaçış öznitelik için dönüştürülürken yoksayılır bir <xref:System.Xml.XmlReader> veya <xref:System.Xml.XmlWriter> nesnesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Xsl.XslTransform>  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)  
 [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [Dönüşümlerde XPathNavigator](../../../../docs/standard/data/xml/xpathnavigator-in-transformations.md)  
 [Dönüşümlerde XPathNodeIterator](../../../../docs/standard/data/xml/xpathnodeiterator-in-transformations.md)  
 [XslTransform’a XPathDocument Girişi](../../../../docs/standard/data/xml/xpathdocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDataDocument Girişi](../../../../docs/standard/data/xml/xmldatadocument-input-to-xsltransform.md)  
 [XslTransform’a XmlDocument Girişi](../../../../docs/standard/data/xml/xmldocument-input-to-xsltransform.md)
