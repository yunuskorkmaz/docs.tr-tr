---
title: msxsl:node-set() İşlevi Desteği
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3670803ff20351fd9ff6892a0cef48b9caa70199
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939519"
---
# <a name="support-for-the-msxslnode-set-function"></a>msxsl:node-set() İşlevi Desteği
İşlevi `msxsl:node-set` , bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar. Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> Sınıf .NET Framework 2,0 ' de kullanılmıyor. <xref:System.Xml.Xsl.XslCompiledTransform> Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz. Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) .  
  
 İşlevi `msxsl:node-set` , bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar. Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `$var` stil sayfasındaki düğüm ağacı olan bir değişkendir. `node-set` İşleviyle birlikte bulunan for-each deyimleri, kullanıcının bu düğüm ağacı üzerinde bir düğüm kümesi olarak yinemasına olanak tanır.  
  
## <a name="nodesetxsl"></a>nodeset. Xsl  
  
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
 Dönüşümün çıktısı  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
