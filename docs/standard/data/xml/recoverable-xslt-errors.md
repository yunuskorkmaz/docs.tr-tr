---
title: Kurtarılabilir XSLT hataları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ef88add49cb4a269612965d14dfbca6b3263533
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="recoverable-xslt-errors"></a>Kurtarılabilir XSLT hataları
W3C XSL Dönüşümleri (XSLT) sürüm 1.0 öneri uygulama sağlayıcısı bir durumu işlemek nasıl karar verebilir alanları içerir. Bu alanlar isteğe bağlı davranış olduğu kabul edilir. Örneğin, Bölüm 7.3 oluşturma işleme yönergelerde XSLT 1.0 öneri, bir hata içeriğinin başlatmasını varsa bildiren `xsl:processing-instruction` metin düğümleri dışında düğümleri oluşturur. Hatadan kurtarmak işlemci karar verirse ne karar öneri gösterir XSLT 1.0 bazı sorunlar için yapılması gerekir. 7.3 bölümünde verilen sorun için uygulama bu hatadan düğümleri ve bunların içeriği yoksayılıyor kurtarabilirsiniz W3C söyler.  
  
## <a name="discretionary-behaviors"></a>İsteğe bağlı davranışları  
 Aşağıdaki tabloda her XSLT 1.0 öneri ve bu davranışların tarafından nasıl işleneceğini tarafından izin verilen isteğe bağlı davranışlar listelenmektedir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı.  
  
-   Kurtarma gösterir <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı bu hatadan kurtarmak. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> Olay XSLT işlemci tüm olayları raporlamak için kullanılabilir.  
  
-   Bu koşul için bir özel durum tetiklenir hata gösterir.  
  
-   Bölüm başvurular bulunabilir [W3C XSL Dönüşümleri (XSLT) sürüm 1.0 öneri](http://www.w3.org/TR/xslt) ve [W3C XSL Dönüşümleri (XSLT) sürüm 1.0 belirtimi ayrıntıyla açıklayan hata bilgilerini](https://www.w3.org/1999/11/REC-xslt-19991116-errata/).  
  
|XSLT koşulu|Bölüm|XslCompiledTransform davranışı|  
|--------------------|-------------|-----------------------------------|  
|Bir metin düğümü hem eşleşen `xsl:strip-space` ve `xsl:preserve-space`.|3.4|Kurtarma|  
|Bir kaynak düğüm birden fazla şablon kuralla eşleşir.|5.5|Kurtarma|  
|Bir ad alanı URI tüm aynı alma önceliğe sahip birden çok ad alanı URI, bir diğer ad olarak bildirildi.|7.1.1|Kurtarma|  
|`name` Özniteliğini `xsl:attribute` ve `xsl:element` bir öznitelik değerinden oluşturulan bir QName değil.|7.1.2, 7.1.3|Hata *|  
|İki öznitelik aynı alma işlemi kümeleriyle ve genişletilmiş ada sahip bir öznitelik ortak ve daha yüksek önem düzeyine sahip aynı ada sahip sık kullanılan özniteliği içeren hiçbir öznitelik kümesi yok.|7.1.4|Kurtarma|  
|Alt eklendikten sonra bir özniteliği bir öğe olarak ekleniyor.|7.1.3|Hata *|  
|Bir öznitelik adı 'xmlns' ile oluşturma|7.1.3|Hata *|  
|Öznitelik bir öğe değil bir düğüm ekleme.|7.1.3|Hata *|  
|Metin düğümleri dışında düğümlerini içeriğini örnek oluşturma sırasında oluşturma `xsl:attribute` özniteliği.|7.1.3|Hata *|  
|`name` Özniteliği bir `xsl:processing-instruction` NCName ve bir işleme yönergesi hedefi vermez.|7.3|Hata *|  
|İçeriği başlatmasını `xsl:processing-instruction` metin düğümleri dışında düğümleri oluşturur.|7.3|Hata *|  
|İçeriği başlatmasını sonucunu `xsl:processing-instruction` dizesini içeren "? >"|7.3|Kurtarma|  
|İçeriği başlatmasını sonucunu `xsl:processing-instruction` dizesini içeren "--" veya ile biten "-".|7.4|Kurtarma|  
|İçeriği başlatmasını sonucunu `xsl:comment` metin düğümleri dışında düğümleri oluşturur.|7.4|Hata *|  
|Değişken bağlama öğesi şablonda bir öznitelik düğümü veya bir ad alanı düğümü döndürür.|11.2|Hata *|  
|Kaynak belge işlevdeki geçirilen URI alınırken bir hata var.|12.1|Hata|  
|Belge işlevi URI başvurusunda parça tanımlayıcısı içeriyor ve parça tanımlayıcısı işlenirken bir hata oluştu.|12.1|Kurtarma *|  
|Aynı adlı ancak içinde cdata bölümünün öğeleri adlı değil farklı değerler, birden çok öznitelik `xsl:output` ile aynı öncelik içeri aktarın.|16|Kurtarma|  
|İşlemci içinde kodlamasını desteklemediğini `xsl:output` kodlama özniteliği.|16.1|Kurtarma|  
|Sonuç ağacındaki bir metin düğümü dışında bir şey için kullanılan bir metin düğümü için çıktı kaçış devre dışı bırakılıyor.|16.4|Kurtarma *|  
|Sonuç ağacı parçası etkin çıkış kaçış ile bir metin düğümü içeriyorsa sonuç ağacı parçası bir sayı veya dize dönüştürme.|16.4|Kurtarma *|  
|Çıktı kaçış XSLT işlemci çıktı için kullandığını kodlama temsil edilemeyen karakterler devre dışı bırakılmıştır.|16.4|Kurtarma *|  
|Alt ona veya öznitelikleri eklendikten sonra eklendikten sonra bir ad alanı düğümü bir öğe olarak ekleniyor.|ayrıntıyla açıklayan hata bilgilerini 25|Hata *|  
|`value` Özniteliği bir `xsl:number` NAN, sonsuz veya daha az 0,5 olup|ayrıntıyla açıklayan hata bilgilerini 24|Kurtarma|  
|Düğüm kümesi belge işlevi ikinci bağımsız değişkeni boş ve göreli URI başvurudur.|ayrıntıyla açıklayan hata bilgilerini 14|Kurtarma|  
  
 <sup>*</sup> Bu davranış farklı <xref:System.Xml.Xsl.XslTransform> sınıfı. Daha fazla bilgi için bkz: [uygulama, isteğe bağlı davranışları çok sınıfında](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
