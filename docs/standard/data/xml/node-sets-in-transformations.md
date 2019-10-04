---
title: Dönüşümlerdeki Düğüm Kümeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbcd9b93f63d48229c174b0f6518fd0150e98e18
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957026"
---
# <a name="node-sets-in-transformations"></a>Dönüşümlerdeki Düğüm Kümeleri
Düğüm kümeleri, XML yol dili (XPath) ifadelerinden döndürülen dört temel veri türünden biridir. Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir.  
  
> [!NOTE]
> @No__t-0 sınıfı, .NET Framework 2,0 ' de kullanılmıyor. @No__t-0 sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 Düğüm kümeleri, XPath ifadelerinden döndürülen dört temel veri türünden biridir. Belge düzeninde oluşturulan ve yinelenen düğümleri olmayan düğümlerin sıralanmamış bir koleksiyonu olan düğüm kümesi, bir stil sayfasında bir değişkene atanabilir. Dönüşümde `select` özniteliğinde kullanılan bir XPath ifadesinin sonucu olan bu düğüm kümesi, XML Belge Nesne Modeli (DOM) tarafından ayarlanan düğüm ile aynı davranışa sahiptir. Gezinti için <xref:System.Xml.XPath.XPathNodeIterator> ' i kullanan bir sonuç ağacı parçasının veya sonuç ağacı parçasının aksine, bir düğüm [kümesi üzerinde bir](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)Yöntem kümesini kullanarak bir düğüm kümesinde gezinebilirsiniz.  
  
 Aşağıdaki kod örneği, bir stil sayfasındaki `variable` veya `parameter` öğesi düğüm kümesine değerlendirirken bir düğüm kümesi üzerinde nasıl yineleme yapılacağını gösterir.  
  
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
  
## <a name="input"></a>Giriş  
  
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
  
## <a name="output"></a>Çıkış  
  
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
- [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)
- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
