---
title: "Düğüm dönüşümler ayarlar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad034f0e-ff8b-4a71-9a4c-528c754263c4
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 95df2f2888899093943feda35768694bf414de84
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="node-sets-in-transformations"></a>Düğüm dönüşümler ayarlar
Düğüm kümeleri gelen XML Path dili (XPath) ifadeleri döndürülen dört temel veri türlerini biridir. Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız bir koleksiyonudur, stil sayfası bir değişkende atanmış bir düğüm kümesi.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 Düğüm kümeleri gelen XPath ifadeleri döndürülen dört temel veri türlerini biridir. Belge sırada oluşturulan yinelemeleri olmadan düğümler sırasız bir koleksiyonudur, stil sayfası bir değişkende atanmış bir düğüm kümesi. XPath ifadesi kullanılan sonucu bu düğüm kümesi bir `select` özniteliği bir dönüşüm, XML belge nesne modeli (DOM) gelen ayarlanmış bir düğümü aynı davranışı sahiptir. Bir dizi gösterilen yöntem kullanılarak ayarlanan bir düğüm gidebilirsiniz [düğüm kümesi Gezinti kullanarak XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md), farklı sonuç ağacı parçası veya kullanan sonuç ağacı parçası olarak <xref:System.Xml.XPath.XPathNodeIterator> gezinti için.  
  
 Aşağıdaki kod örneği, yinelemek gösterilmiştir bir düğüm kümesi üzerinde bir `variable` veya `parameter` bir stil sayfası öğesinde düğüm kümesi olarak değerlendirilir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XPath.XPathNodeIterator>  
 [XslTransform Sınıfı ile XSLT Dönüşümleri](../../../../docs/standard/data/xml/xslt-transformations-with-the-xsltransform-class.md)  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
