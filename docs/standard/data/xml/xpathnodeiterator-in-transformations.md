---
description: 'Daha fazla bilgi edinin: dönüşümlerdeki XPathNodeIterator'
title: Dönüşümlerde XPathNodeIterator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
ms.openlocfilehash: 5e27ff243e4ca0a609b4d5c28d941ea84ea5b10d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782565"
---
# <a name="xpathnodeiterator-in-transformations"></a>Dönüşümlerde XPathNodeIterator

, Bir <xref:System.Xml.XPath.XPathNodeIterator> XML yol dili (XPath) sorgusunun sonucu olarak oluşturulan bir düğüm kümesi veya düğüm kümesi yöntemi kullanılarak bir düğüm kümesine dönüştürülen bir sonuç ağacı parçasının üzerinde yinelemek için yöntemler sağlar. , <xref:System.Xml.XPath.XPathNodeIterator> Bu düğüm kümesi içindeki düğümleri yinelemenize olanak sağlar. Düğüm kümesi alındıktan sonra, <xref:System.Xml.XPath.XPathNodeIterator> sınıf seçili düğüm kümesine salt okunurdur ve salt ileri bir imleç sağlar. Düğüm kümesi belge sırasıyla oluşturulur, bu nedenle bu yöntemin çağrılması belge düzeninde sonraki düğüme gider. <xref:System.Xml.XPath.XPathNodeIterator> kümedeki tüm düğümlerin düğüm ağacını oluşturmaz. Bunun yerine, veride tek bir düğüm penceresi sağlar ve bu, ağaçta hareket ettiği sırada işaret ettiği temel düğümü ortaya çıkar. Sınıfından kullanılabilir yöntemler ve özellikler, <xref:System.Xml.XPath.XPathNodeIterator> geçerli düğümden bilgi almanızı sağlar. Kullanılabilir yöntemlerin ve özelliklerin listesi için bkz <xref:System.Windows.Forms.ToolBar> ..  
  
 Bir <xref:System.Xml.XPath.XPathNodeIterator> XPath sorgusundan oluşturulmuş bir düğüm kümesi üzerinde hareket ettirildiğinde ve yalnızca ileri hareket ettirildiğinde, taşıma <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> Yöntemi yöntemini kullanmaktır. Bu yöntemin dönüş türü `Boolean` , `true` sonraki Seçili düğüme taşınırsa döndürülür ve `false` daha fazla seçili düğüm yoksa döndürülüyor. Dönerse `true` , aşağıdaki listede kullanılabilen özellikler gösterilmektedir:  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
- <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 İlk kez bir düğüm kümesine baktığınızda, <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> Seçilen küme için ilk düğümde konumlandırmaya yönelik bir çağrı yapılmalıdır <xref:System.Xml.XPath.XPathNodeIterator> . Bu, bir while döngüsünün yazılmasına izin verir.  
  
 Aşağıdaki kod örneği <xref:System.Xml.XPath.XPathNodeIterator> ' de bir öğesine bir parametresi olarak nasıl geçirileceğini gösterir <xref:System.Xml.Xsl.XslTransform> <xref:System.Xml.Xsl.XsltArgumentList> . Kodun girişi **books.xml** ve stil sayfası **Text. xsl** olur. Dosya **test.xml** <xref:System.Xml.XPath.XPathDocument> .  
  
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
  
## <a name="booksxml"></a>books.xml  
  
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
  
## <a name="testxml"></a>test.xml  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a>Çıkış (out.xml)  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XslTransform Sınıfı XSLT İşlemcisini Uygular](xsltransform-class-implements-the-xslt-processor.md)
