---
title: Dönüşümlerdeki Düğüm Kümeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
ms.openlocfilehash: 33cbae05cf35904903189ce767090d3d3cca8e4d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288751"
---
# <a name="node-sets-in-transformations"></a>Dönüşümlerdeki Düğüm Kümeleri
Düğüm kümeleri, XML yol dili (XPath) ifadelerinden döndürülen dört temel veri türünden biridir. Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 Düğüm kümeleri, XPath ifadelerinden döndürülen dört temel veri türünden biridir. Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir. Dönüşümdeki bir öznitelikte kullanılan bir XPath ifadesinin sonucu olan bu düğüm kümesi, `select` XML belge nesne modeli (DOM) bir düğüm kümesiyle aynı davranışa sahiptir. Bir düğüm kümesinde gezinme için, bir sonuç ağacı parçasının veya sonuç ağacı parçasının aksine (örneğin, gezinti için) bir düğüm [kümesi gezinmede](node-set-navigation-using-xpathnavigator.md)gösterilen bir yöntem kümesini kullanarak gidebilirsiniz <xref:System.Xml.XPath.XPathNodeIterator> .  
  
 Aşağıdaki kod örneği, bir `variable` `parameter` stil sayfasındaki bir veya öğesinin bir düğüm kümesini değerlendirirken bir düğüm kümesi üzerinde nasıl yineleceğini gösterir.  
  
## <a name="style-sheet"></a>Stil sayfası  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0">  
  
    <xsl:variable name="x" select="bookstore/book/title"></xsl:variable>  
  
    <xsl:template match="/">  
        <xsl:for-each select="$x">  
            ******  
            <xsl:value-of select="."></xsl:value-of>  
            ******  
        </xsl:for-each>  
    </xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="input"></a>Girdi  
  
```xml  
<bookstore>  
   <book style="autobiography">  
      <title>Seven Years in Trenton</title>  
   </book>  
  
   <book style="autobiography">  
      <title>Seven Years in Trenton2</title>  
   </book>  
  
   <book style="textbook">  
      <title>History of Trenton Vol 3</title>  
   </book>  
</bookstore>  
```  
  
## <a name="output"></a>Çıktı  
  
```output  
******  
Seven Years in Trenton  
******  
  
******  
Seven Years in Trenton2  
******  
  
******  
History of Trenton Vol 3  
******  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XPath.XPathNodeIterator>
- [XslTransform Sınıfı ile XSLT Dönüşümleri](xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
