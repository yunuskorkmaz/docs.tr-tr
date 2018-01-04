---
title: "Msxsl: node-set() işlevi için destek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7cd79acbdef09acb0a05c818d8358cd612c3bcdf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="support-for-the-msxslnode-set-function"></a>Msxsl: node-set() işlevi için destek
`msxsl:node-set` İşlevi bir düğüm kümesine sonuç ağacı parçası dönüştürmenize olanak sağlar. Her zaman ortaya çıkan düğümü tek bir düğüm içerir ve ağacı kök düğümü olur.  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> Sınıftır'te eski [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]. Genişletilebilir Stil sayfası dili kullanarak Dönüşümleri (XSLT) dönüştürmeleri için gerçekleştirebilirsiniz <xref:System.Xml.Xsl.XslCompiledTransform> sınıfı. Bkz: [XslCompiledTransform sınıfını kullanarak](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) ve [çok sınıfı geçirme](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) daha fazla bilgi için.  
  
 `msxsl:node-set` İşlevi bir düğüm kümesine sonuç ağacı parçası dönüştürmenize olanak sağlar. Her zaman ortaya çıkan düğümü tek bir düğüm içerir ve ağacı kök düğümü olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `$var` stil sayfası düğümü ağaçtaki bir değişkendir. İçin-each deyimi birlikte `node-set` işlevi bu düğüm ağacına bir düğüm kümesi olarak üzerinden yineleme kullanıcıya izin verir.  
  
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
                <author><xsl:value-of select="@author"/)</author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a>Çıkış  
 Dönüştürme çıktısı  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
