---
title: msxsl:node-set() İşlevi Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a37220816ab320340b2dd5c048cc4ff2ad9724a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026919"
---
# <a name="support-for-the-msxslnode-set-function"></a>msxsl:node-set() İşlevi Desteği
`msxsl:node-set` İşlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar. Sonuç olarak oluşan düğüm her zaman tek bir düğüm içeriyor ve ağaç kök düğümü.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil Sayfası Dil Dönüşümleri (XSLT) dönüştürmeleri için kullanarak gerçekleştirebileceğiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [geçirme gelen XslTransform sınıfı](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 `msxsl:node-set` İşlevi bir sonuç ağacı parçası düğümünü kümeyi dönüştürmek sağlar. Sonuç olarak oluşan düğüm her zaman tek bir düğüm içeriyor ve ağaç kök düğümü.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `$var` stil sayfası düğümü ağacında bir değişkendir. For-each ifadesinin birlikte `node-set` işlevi bu düğüm ağacı bir düğüm kümesi olarak gezinilen kullanıcının sağlar.  
  
## <a name="nodesetxsl"></a>NodeSet.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">   
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Çıkış  
 Dönüşümün çıkış  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
