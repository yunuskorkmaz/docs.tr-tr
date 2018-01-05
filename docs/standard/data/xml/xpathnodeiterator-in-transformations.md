---
title: "Dönüşümleri XPathNodeIterator"
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
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 523a4774de9975812838b22bbb5193e59cd58130
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="811e8-102">Dönüşümleri XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="811e8-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="811e8-103"><xref:System.Xml.XPath.XPathNodeIterator> Küme düğümlerinin bir XML Path dili (XPath) sorgusu veya bir düğüme dönüştürülen sonuç ağacı parçası sonucu olarak oluşturulan üzerinde yinelemek için yöntemler kümesi düğüm kümesi yöntemi kullanarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="811e8-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="811e8-104"><xref:System.Xml.XPath.XPathNodeIterator> Bu düğüm kümesi içindeki düğümler üzerinden yineleme olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="811e8-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="811e8-105">Bir düğüm kümesi alındıktan sonra <xref:System.Xml.XPath.XPathNodeIterator> sınıfı düğümleri seçilen kümesi için salt okunur, yalnızca ileri yönlü bir imleç sağlar.</span><span class="sxs-lookup"><span data-stu-id="811e8-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="811e8-106">Bu yöntemin çağrılması belge sırayla bir sonraki düğüme taşınmasını düğüm kümesi belge sırayla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="811e8-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="811e8-107"><xref:System.Xml.XPath.XPathNodeIterator>Kümedeki tüm düğümler düğüm ağacının oluşmuyor.</span><span class="sxs-lookup"><span data-stu-id="811e8-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="811e8-108">Bunun yerine, ağacında hareket etme gibi işaret temel düğüm gösterme veri, bir tek düğümlü pencere sağlar.</span><span class="sxs-lookup"><span data-stu-id="811e8-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="811e8-109">Kullanılabilir özellikler ve yöntemler <xref:System.Xml.XPath.XPathNodeIterator> sınıfı, geçerli düğümden bilgi almak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="811e8-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="811e8-110">Kullanılabilir yöntemleri ve özellikleri listesi için bkz: <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="811e8-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="811e8-111">Bu yana bir <xref:System.Xml.XPath.XPathNodeIterator> taşır küme düğümleri üzerinde oluşturulan bir XPath sorgusu ve taşır iletmek yalnızca, taşıma kullanarak yoludur <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="811e8-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="811e8-112">Bu yöntemin dönüş türü `Boolean`, döndürme `true` sonraki Seçili düğüme geçerse ve `false` artık seçili düğümler varsa.</span><span class="sxs-lookup"><span data-stu-id="811e8-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="811e8-113">Döndürürse `true`, aşağıdaki listede kullanılabilir özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="811e8-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="811e8-114">Bir düğümde zaman aradığınız ayarlamak ilk kez bir çağrı <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> konumlandırmak için yapılmalıdır <xref:System.Xml.XPath.XPathNodeIterator> seçili kümenin ilk düğümü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="811e8-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="811e8-115">Bu işlem biraz zaman verir döngü yazılacak.</span><span class="sxs-lookup"><span data-stu-id="811e8-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="811e8-116">Aşağıdaki kod örneğinde nasıl iletileceğini gösterir bir <xref:System.Xml.XPath.XPathNodeIterator> için bir <xref:System.Xml.Xsl.XslTransform> bir parametresi olarak <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="811e8-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="811e8-117">Giriş kodu **books.xml**, ve stil sayfası **text.xsl**.</span><span class="sxs-lookup"><span data-stu-id="811e8-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="811e8-118">Dosya **test.xml** olan <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="811e8-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
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
  
## <a name="booksxml"></a><span data-ttu-id="811e8-119">Books.XML</span><span class="sxs-lookup"><span data-stu-id="811e8-119">books.xml</span></span>  
  
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
  
## <a name="testxsl"></a><span data-ttu-id="811e8-120">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="811e8-120">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="811e8-121">Test.XML</span><span class="sxs-lookup"><span data-stu-id="811e8-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="811e8-122">Çıktı (out.xml)</span><span class="sxs-lookup"><span data-stu-id="811e8-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="811e8-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="811e8-123">See Also</span></span>  
 [<span data-ttu-id="811e8-124">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="811e8-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
