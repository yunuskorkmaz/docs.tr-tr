---
title: Dönüşümlerdeki düğüm kümeleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 23632a5df10c1ab2d1afa654d5438a4ebd903d5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603046"
---
# <a name="node-sets-in-transformations"></a>Dönüşümlerdeki düğüm kümeleri
Düğüm kümeleri XML Path Language (XPath) ifade döndürülen dört temel veri türlerinden biridir. Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız koleksiyonunun ise, bir stil sayfası bir değişkene atanabilir bir düğüm kümesi.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Düğüm kümeleri XPath ifadeleri döndürülen dört temel veri türlerinden biridir. Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız koleksiyonunun ise, bir stil sayfası bir değişkene atanabilir bir düğüm kümesi. Kullanılan ifade bir XPath bir sonuç bu düğüm kümesi bir `select` Dönüşümde öznitelik, XML belge nesne modeli (DOM) öğesinden ayarlanmış bir düğüm aynı davranışı sahiptir. Düğüm kümesi bir dizi yöntem gösterilen kullanarak gidebilirsiniz [kullanarak düğüm kümesi Gezinti XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), farklı bir sonuç ağacı parçası veya kullanan sonuç ağacı parçası olarak <xref:System.Xml.XPath.XPathNodeIterator> gezinme için.  
  
 Aşağıdaki kod örneği nasıl yineleneceğini gösterir. bir düğüm kümesi üzerinde bir `variable` veya `parameter` bir stil sayfası öğesinde bir düğüm kümesi olarak değerlendirir.  
  
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
  
```  
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
