---
title: Dönüşümlerde XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
ms.openlocfilehash: 240f9ca7a887a4a146437fdef46de776b299705a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709757"
---
# <a name="xpathnavigator-in-transformations"></a>Dönüşümlerde XPathNavigator
Sınıfı <xref:System.Xml.XPath.XPathNavigator> , verilere salt okunurdur ve dönüşümler (XSLT) Için Genişletilebilir Stil sayfası dili girişi olarak kullanılmak üzere tasarlanmıştır. , Ve <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XmlDocument>üzerinde uygulanır. , <xref:System.Xml.XPath.XPathNavigator> XML yol dili (XPath) önerisinin 5. bölümünde açıklandığı gibi world WIDE Web KONSORSIYUMU (W3C) veri modelini temel alır.  
  
 , <xref:System.Xml.XPath.XPathNavigator> Herhangi bir mağaza üzerinde bir imleç modeli tanımlar ve tüm veri depolarındaki hızlı, salt okuma XPath sorguları sağlar. Ayrıca <xref:System.Xml.XPath.XPathNavigator> , sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır.  
  
 API, depodaki geçerli düğümden bilgi almanızı ve bağlantılı düğümlere taşımanızı sağlar. , <xref:System.Xml.XPath.XPathNavigator> Bir **taşıma** yöntemleri kümesi kullanarak bir mağaza üzerinde geçiş yapan bir imleç stil modelidir. , <xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğüm üzerinde konumlandırılır. Başarısız olan herhangi bir **Move** yöntemi <xref:System.Xml.XPath.XPathNavigator> değişmeden bırakılamaz.  
  
 , <xref:System.Xml.XPath.XPathNavigator> Sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır. Aşağıdaki kod örneği, bir stil sayfası içinde, XML içeren parametresiyle `fragment`işlevi çağırarak bir sonuç ağacı parçası oluşturur.  
  
## <a name="testxsl"></a>test. Xsl  
  
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
  
## <a name="testxml"></a>test. xml  
  
```xml  
<root>Some text</root>  
```  
  
 Aşağıdaki kod, **test. xsl** stil sayfası ve **test. xml** giriş verilerini kullanır.  
  
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
  
## <a name="output"></a>Çıktı  
 Dönüşümün sonucu, **out. xml**dosyasında bulunur:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
