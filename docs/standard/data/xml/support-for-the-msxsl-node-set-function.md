---
title: msxsl:node-set() İşlevi Desteği
ms.date: 03/30/2017
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 6c84e3789916e8d842e51e8417cb27505cb5cba6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673403"
---
# <a name="support-for-the-msxslnode-set-function"></a>msxsl:node-set() İşlevi Desteği

`msxsl:node-set`İşlevi, bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar. Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.  
  
> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform>Sınıf .NET Framework 2,0 ' de kullanılmıyor. Sınıfını kullanarak dönüşümler için Genişletilebilir Stil sayfası dili (XSLT) dönüşümleri gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> . Daha fazla bilgi için, bkz. [XslCompiledTransform sınıfını kullanma](using-the-xslcompiledtransform-class.md) ve [XslTransform sınıfından geçiş](migrating-from-the-xsltransform-class.md) .  
  
 `msxsl:node-set`İşlevi, bir sonuç ağacı parçasını bir düğüm kümesine dönüştürmenize olanak sağlar. Sonuçta elde edilen düğüm kümesi her zaman tek bir düğüm içerir ve ağacın kök düğümüdür.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, `$books` stil sayfasındaki düğüm ağacı olan bir değişkendir. İşleviyle birlikte bulunan for-each deyimleri, `node-set` kullanıcının bu düğüm ağacı üzerinde bir düğüm kümesi olarak yinemasına olanak tanır.  
  
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

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
