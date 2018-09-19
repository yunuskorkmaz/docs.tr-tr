---
title: Dönüşümlerde XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57290af1df8d370c928a97aba1622e41a6a33589
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003990"
---
# <a name="xpathnavigator-in-transformations"></a>Dönüşümlerde XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Sınıfı veri salt okunur rastgele erişim sağlar ve Genişletilebilir Stil sayfası dili için giriş olarak kullanmak için Dönüşümleri (XSLT) için tasarlanmıştır. Üzerinde uygulanan <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, ve <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> XML Path Language (XPath) öneri 5. bölümünde anlatıldığı gibi World Wide Web Consortium (W3C) veri modeline dayanır.  
  
 <xref:System.Xml.XPath.XPathNavigator> Hiçbir depo üzerinde bir imleç modeli tanımlar ve XPath sorgularını hızlı ve salt okunur herhangi bir veri deposu sağlar. <xref:System.Xml.XPath.XPathNavigator> Ayrıca sonucu ağacı parçalarını yineleme için kullanılacak bir sınıftır.  
  
 API, depodaki geçerli düğüm öğrenmesini ve bağlı düğümleri için taşıma sağlar. <xref:System.Xml.XPath.XPathNavigator> Kümesini kullanan bir depo üzerinde çapraz geçişi gerçekleştirir imleç stil modelidir **taşıma** yöntemleri. <xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğümde konumlandırılır. Tüm **taşıma** bırakır başarısız yöntemi <xref:System.Xml.XPath.XPathNavigator> değişmez.  
  
 <xref:System.Xml.XPath.XPathNavigator> Sonucu ağacı parçalarını yineleme için kullanılacak sınıftır. Aşağıdaki kod örneği, işlev parametresi ile çağırarak bir stil sayfası içinde bir sonuç ağacı parçası oluşturur `fragment`, XML içeriyor.  
  
## <a name="testxsl"></a>Test.xsl  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl ="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.adventure-works.com"  
                version="1.0">  
  
<xsl:variable name="fragment">  
    <authorlist>  
       <author>Joe</author>  
    </authorlist>  
</xsl:variable>  
  
<msxsl:script language="C#" implements-prefix="user">  
<![CDATA[  
   string NodeFragment(XPathNavigator nav)  
   {  
      if (nav.HasChildren)  
        return nav.Value;  
      else  
        return "";  
   }  
]]>  
</msxsl:script>  
  
<xsl:template match="/">  
     <xsl:value-of select="user:NodeFragment($fragment)"/>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>Test.XML  
  
```xml  
<root>Some text</root>  
```  
  
 Aşağıdaki kod **test.xsl** stil sayfası ve **test.xml** veri girişi.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
Public Class sample  
  
    Public Shared Sub Main()  
        Dim xslt As New XslTransform()  
        xslt.Load("test.xsl")  
  
        Dim xd As New XPathDocument("test.xml")  
  
        Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
        xslt.Transform(xd, Nothing, strmTemp, Nothing)  
    End Sub 'Main  
End Class 'sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Xsl;  
using System.Xml.XPath;  
using System.Text;  
  
public class sample  
{  
    public static void Main()  
    {  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, null, strmTemp, null);  
    }  
}  
```  
  
## <a name="output"></a>Çıkış  
 Dönüştürme sonucunu dosyasında bulunan **out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
