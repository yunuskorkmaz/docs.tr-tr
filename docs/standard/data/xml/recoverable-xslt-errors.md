---
title: Kurtarılabilir XSLT Hataları
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 484929b0-fefb-4629-87ee-ebdde70ff1f8
ms.openlocfilehash: e3ff86cc80887d14fdffe50f256409cb70ff2d88
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710381"
---
# <a name="recoverable-xslt-errors"></a>Kurtarılabilir XSLT Hataları
W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi, uygulama sağlayıcısının bir durumu nasıl ele verileceğine karar vermesine olanak tanıyan bölgeleri içerir. Bu alanların kısıtlı davranış olduğu kabul edilir. Örneğin, 7,3 bölümünde Işlem yönergeleri oluşturma bölümünde XSLT 1,0 önerisi, `xsl:processing-instruction` içeriğinin örnekleniyor olması halinde bir hata olduğunu belirtir, metin düğümlerinden başka düğümler oluşturur. Bazı sorunlar için XSLT 1,0 önerisi, işlemcinin hatadan kurtulmak için karar verdiğinde hangi kararın yapılması gerektiğini gösterir. Bölüm 7,3 ' de verilen sorun için, W3C, uygulamanın düğümleri ve bunların içeriğini yoksayarak bu hatadan kurtuyor olduğunu söyler.  
  
## <a name="discretionary-behaviors"></a>İsteğe bağlı davranışlar  
 Aşağıdaki tabloda XSLT 1,0 önerisi tarafından izin verilen her bir isteğe bağlı davranış ve bu davranışların <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı tarafından nasıl işlendiği listelenmiştir.  
  
- Kurtarma <xref:System.Xml.Xsl.XslCompiledTransform> sınıfının bu hatadan kurtarılacağını belirtir. <xref:System.Xml.Xsl.XsltArgumentList.XsltMessageEncountered?displayProperty=nameWithType> olayı XSLT işlemcisinden olayları raporlamak için kullanılabilir.  
  
- Hata bu koşul için bir özel durumun yapıldığını gösteriyor.  
  
- Bölüm başvuruları [W3C XSL dönüştürmeleri (XSLT) sürüm 1,0 önerisi](https://www.w3.org/TR/xslt) ve [W3C XSL dönüşümleri (xslt) sürüm 1,0 belirtimi errat](https://www.w3.org/1999/11/REC-xslt-19991116-errata/)' da bulunabilir.  
  
|XSLT koşulu|Bölüm|XslCompiledTransform davranışı|  
|--------------------|-------------|-----------------------------------|  
|Bir metin düğümü hem `xsl:strip-space` hem de `xsl:preserve-space`ile eşleşir.|3.4|Kurtar|  
|Kaynak düğüm, birden fazla şablon kuralıyla eşleşiyor.|5.5|Kurtar|  
|Bir ad alanı URI 'SI, birden çok ad alanı URI 'si için diğer ad olarak, aynı içeri aktarma önceliğine sahip olacak şekilde bildirilmiştir.|7.1.1|Kurtar|  
|Öznitelik değerinden oluşturulan `xsl:attribute` ve `xsl:element` `name` özniteliği QName değil.|7.1.2, 7.1.3|Hatayla|  
|Aynı içeri ve genişletilmiş ada sahip iki öznitelik kümesi ortak bir özniteliğe sahiptir ve aynı ada sahip ortak özniteliği içeren başka bir öznitelik kümesi yoktur.|7.1.4|Kurtar|  
|Bir öğeye alt öğe eklendikten sonra öznitelik ekleme.|7.1.3|Hatayla|  
|' Xmlns ' adlı bir öznitelik oluşturuluyor|7.1.3|Hatayla|  
|Öğe olmayan bir düğüme öznitelik ekleme.|7.1.3|Hatayla|  
|`xsl:attribute` özniteliğinin içeriğinin örneklenmesi sırasında metin düğümlerinden başka düğümler oluşturma.|7.1.3|Hatayla|  
|Bir `xsl:processing-instruction` `name` özniteliği hem NCName hem de bir işleme yönergesi hedefini göstermez.|7.3|Hatayla|  
|`xsl:processing-instruction` içeriğini örnekleme metin düğümlerinden başka düğümler oluşturuyor.|7.3|Hatayla|  
|`xsl:processing-instruction` içeriğinin örnekleniyor sonucu "? >" dizesini içerir|7.3|Kurtar|  
|`xsl:processing-instruction` içeriğinin örnekleniyor sonucu "--" dizesini içerir veya "-" ile biter.|7.4|Kurtar|  
|`xsl:comment` içeriğinin örneklandığı sonuç metin düğümlerinden başka düğümler oluşturuyor.|7.4|Hatayla|  
|Değişken bağlama öğesi içindeki şablon bir öznitelik düğümü veya bir ad alanı düğümü döndürür.|11.2|Hatayla|  
|Belge işlevine geçilen URI 'den kaynak alınırken bir hata oluştu.|12.1|Hata|  
|Belge işlevindeki URI başvurusu bir parça tanımlayıcısı içeriyor ve parça tanımlayıcısı işlenirken bir hata oluştu.|12.1|Kurtarılamıyor|  
|Aynı ada sahip birden çok öznitelik vardır, ancak aynı içeri aktarma önceliğiyle `xsl:output` CDATA-bölüm öğelerinin adlandırılmayan farklı değerleri vardır.|16|Kurtar|  
|İşlemci, `xsl:output` Encoding özniteliğinde kodlamayı desteklemez.|16.1|Kurtar|  
|Sonuç ağacındaki bir metin düğümü dışında bir öğe için kullanılan bir metin düğümü için çıkış kaçı devre dışı bırakılıyor.|16.4|Kurtarılamıyor|  
|Sonuç ağacı parçası, çıkış kaçış özelliği etkinleştirilmiş bir metin düğümü içeriyorsa, sonuç ağacı parçasını sayıya veya dizeye dönüştürme.|16.4|Kurtarılamıyor|  
|XSLT işlemcisinin çıkış için kullandığı kodlamada temsil edilemeyecek bir karakter için çıkış kaçış devre dışı bırakıldı.|16.4|Kurtarılamıyor|  
|Bir öğeye alt öğe eklendikten sonra veya öznitelikleri eklendikten sonra bir ad alanı düğümü ekleme.|eroyta 25|Hatayla|  
|Bir `xsl:number` `value` özniteliği NAN, sonsuz veya 0,5 küçüktür|eroyta 24|Kurtar|  
|İkinci bağımsız değişken düğümü-belge işlevine ayarlanan boş ve URI başvurusu görelidir.|eroyta 14|Kurtar|  
  
 <sup>*</sup> Bu davranış <xref:System.Xml.Xsl.XslTransform> sınıfından farklıdır. Daha fazla bilgi için bkz. [XslTransform sınıfında Isteğe bağlı davranışları uygulama](../../../../docs/standard/data/xml/implementation-of-discretionary-behaviors-in-the-xsltransform-class.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations.md)
