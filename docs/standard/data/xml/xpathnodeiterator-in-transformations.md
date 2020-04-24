---
title: Dönüşümlerde XPathNodeIterator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 63beeb3ca9d3f3cb6e6bde418e99ee2bd0a12e20
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709744"
---
# <a name="xpathnodeiterator-in-transformations"></a>Dönüşümlerde XPathNodeIterator
, <xref:System.Xml.XPath.XPathNodeIterator> Bir XML yol dili (XPath) sorgusunun sonucu olarak oluşturulan bir düğüm kümesi veya düğüm kümesi yöntemi kullanılarak bir düğüm kümesine dönüştürülen bir sonuç ağacı parçasının üzerinde yinelemek için yöntemler sağlar. , <xref:System.Xml.XPath.XPathNodeIterator> Bu düğüm kümesi içindeki düğümleri yinelemenize olanak sağlar. Düğüm kümesi alındıktan sonra, <xref:System.Xml.XPath.XPathNodeIterator> sınıf seçili düğüm kümesine salt okunurdur ve salt ileri bir imleç sağlar. Düğüm kümesi belge sırasıyla oluşturulur, bu nedenle bu yöntemin çağrılması belge düzeninde sonraki düğüme gider. <xref:System.Xml.XPath.XPathNodeIterator>kümedeki tüm düğümlerin düğüm ağacını oluşturmaz. Bunun yerine, veride tek bir düğüm penceresi sağlar ve bu, ağaçta hareket ettiği sırada işaret ettiği temel düğümü ortaya çıkar. <xref:System.Xml.XPath.XPathNodeIterator> Sınıfından kullanılabilir yöntemler ve özellikler, geçerli düğümden bilgi almanızı sağlar. Kullanılabilir yöntemlerin ve özelliklerin listesi için bkz <xref:System.Windows.Forms.ToolBar>..  
  
 Bir <xref:System.Xml.XPath.XPathNodeIterator> XPath sorgusundan oluşturulmuş bir düğüm kümesi üzerinde hareket ettirildiğinde ve yalnızca ileri hareket ettirildiğinde, taşıma <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> Yöntemi yöntemini kullanmaktır. Bu yöntemin dönüş türü, sonraki seçili `Boolean`düğüme taşınırsa `true` döndürülür ve `false` daha fazla seçili düğüm yoksa döndürülüyor. Dönerse `true`, aşağıdaki listede kullanılabilen özellikler gösterilmektedir:  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 İlk kez bir düğüm kümesine baktığınızda, seçilen küme için ilk düğümde konumlandırmaya <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> <xref:System.Xml.XPath.XPathNodeIterator> yönelik bir çağrı yapılmalıdır. Bu, bir while döngüsünün yazılmasına izin verir.  
  
 Aşağıdaki kod örneği ' de bir <xref:System.Xml.XPath.XPathNodeIterator> öğesine bir parametresi <xref:System.Xml.Xsl.XslTransform> olarak nasıl geçirileceğini gösterir. <xref:System.Xml.Xsl.XsltArgumentList> Kodun girişi **Books. xml**' dir ve stil sayfası **Text. xsl**' dir. **Test. xml** dosyası <xref:System.Xml.XPath.XPathDocument>.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Xsl  
Imports System.Xml.XPath  
Imports System.Text  
  
Public Class sample  
  
   Public Shared Sub Main()  
      Dim Doc As New XPathDocument("books.xml")  
      Dim nav As XPathNavigator = Doc.CreateNavigator()  
      Dim Iterator As XPathNodeIterator = nav.Select("/bookstore/book")  
  
      Dim arg As New XsltArgumentList()  
      arg.AddParam("param1", "", Iterator)  
  
      Dim xslt As New XslTransform()  
      xslt.Load("test.xsl")  
  
      Dim xd As New XPathDocument("test.xml")  
  
      Dim strmTemp = New FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite)  
      xslt.Transform(xd, arg, strmTemp, Nothing)  
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
        XPathDocument Doc = new XPathDocument("books.xml");  
        XPathNavigator nav = Doc.CreateNavigator();  
        XPathNodeIterator Iterator = nav.Select("/bookstore/book");  
  
        XsltArgumentList arg = new XsltArgumentList();  
        arg.AddParam("param1", "", Iterator);  
  
        XslTransform xslt = new XslTransform();  
        xslt.Load("test.xsl");  
  
        XPathDocument xd = new XPathDocument("test.xml");  
  
        Stream strmTemp = new FileStream("out.xml", FileMode.Create, FileAccess.ReadWrite);  
        xslt.Transform(xd, arg, strmTemp, null);  
    }  
}  
```  
  
## <a name="booksxml"></a>Books. xml  
  
```xml  
<?xml version='1.0'?>  
<!-- This file represents a fragment of a book store inventory database. -->  
<bookstore specialty="novel">  
    <book style="autobiography">  
    <title>Seven Years in Trenton</title>  
        <author>  
            <first-name>Jay</first-name>  
            <last-name>Adams</last-name>  
            <award>Trenton Literary Review Honorable Mention</award>  
            <country>USA</country>  
        </author>  
        <price>12</price>  
    </book>  
    <book style="textbook">  
        <title>History of Trenton</title>  
        <author>  
            <first-name>Kim</first-name>  
            <last-name>Akers</last-name>  
            <publication>  
                Selected Short Stories of  
                <first-name>Scott</first-name>  
                <last-name>Bishop</last-name>  
                <country>US</country>  
            </publication>  
        </author>  
        <price>55</price>  
    </book>  
</bookstore>  
```  
  
## <a name="testxsl"></a>test. Xsl  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
xmlns:msxsl="urn:schemas-microsoft-com:xslt" exclude-result-prefixes="msxsl">  
  
<xsl:output method="xml" indent="yes"/>  
<xsl:param name="param1"/>  
  
<xsl:template match="/">  
    <out>  
        <xsl:for-each select="$param1/title">  
            <title><xsl:value-of select="."/></title>  
        </xsl:for-each>  
    </out>  
</xsl:template>  
  
</xsl:stylesheet>  
```  
  
## <a name="testxml"></a>test. xml  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Output (out. xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
