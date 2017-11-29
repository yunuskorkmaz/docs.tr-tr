---
title: "Dönüşümleri XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09f89708607ada18181bc6605994c7908e1dd14b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="xpathnavigator-in-transformations"></a>Dönüşümleri XPathNavigator
<xref:System.Xml.XPath.XPathNavigator> Sınıfı verilerine salt okunur rastgele erişim sağlar ve Genişletilebilir Stil sayfası dili için bir giriş olarak kullanmak için Dönüşümleri (XSLT) için tasarlanmıştır. Üzerinde uygulanan <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, ve <xref:System.Xml.XmlDocument>. <xref:System.Xml.XPath.XPathNavigator> XML Path dili (XPath) öneri 5 bölümünde açıklandığı gibi World Wide Web Konsorsiyumu (W3C) veri modeline dayanır.  
  
 <xref:System.Xml.XPath.XPathNavigator> Bir imleç modeli herhangi bir depolama tanımlar ve hızlı, salt okunur XPath sorguları herhangi bir veri deposu sağlar. <xref:System.Xml.XPath.XPathNavigator> De sonuç ağaç parçaları yineleme için kullanılacak bir sınıftır.  
  
 API, depoda geçerli düğümden bilgi almak ve bağlı düğümlerine taşıma sağlar. <xref:System.Xml.XPath.XPathNavigator> Kümesi kullanılarak bir mağaza çapraz geçişi gerçekleştirir bir imleç stili modeldir **taşıma** yöntemleri. <xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğümde konumlandırıldı. Tüm **taşıma** bırakır başarısız yöntemi <xref:System.Xml.XPath.XPathNavigator> değişmez.  
  
 <xref:System.Xml.XPath.XPathNavigator> Sonuç ağaç parçaları yineleme için kullanılacak bir sınıftır. Aşağıdaki kod örneği bir stil sayfası içinden sonuç ağacı parçası parametresiyle işlevini çağırarak oluşturur `fragment`, XML içeriyor.  
  
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
  
 Aşağıdaki kod **test.xsl** stil sayfası ve **test.xml** giriş verileri.  
  
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
 Dönüşümün sonucunu dosyasında bulunan **out.xml**:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XSLT işlemci çok sınıfı uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
