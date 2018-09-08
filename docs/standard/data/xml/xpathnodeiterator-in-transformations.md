---
title: Dönüşümlerde XPathNodeIterator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2bc6ddc6-674a-4f75-b264-abc35e4e5857
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f71d409729707f4af93fd7f8d5b82a99404579b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129271"
---
# <a name="xpathnodeiterator-in-transformations"></a><span data-ttu-id="702a8-102">Dönüşümlerde XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="702a8-102">XPathNodeIterator in Transformations</span></span>
<span data-ttu-id="702a8-103"><xref:System.Xml.XPath.XPathNodeIterator> Düğüm kümesi yöntemi kullanarak bir XML yolu dil (XPath) sorgusu veya bir düğüme dönüştürülen bir sonuç ağacı parçası olarak oluşturulan düğümleri kümesi üzerinden yineleme yapmak için yöntemler kümesi sağlar.</span><span class="sxs-lookup"><span data-stu-id="702a8-103">The <xref:System.Xml.XPath.XPathNodeIterator> provides methods to iterate over a set of nodes created as the result of an XML Path Language (XPath) query or a result tree fragment converted to a node set by use of the node-set method.</span></span> <span data-ttu-id="702a8-104"><xref:System.Xml.XPath.XPathNodeIterator> , Düğüm kümesi içindeki düğümler üzerinden yineleme yapma sağlar.</span><span class="sxs-lookup"><span data-stu-id="702a8-104">The <xref:System.Xml.XPath.XPathNodeIterator> enables you to iterate over the nodes within that node set.</span></span> <span data-ttu-id="702a8-105">Bir düğüm kümesi alındıktan sonra <xref:System.Xml.XPath.XPathNodeIterator> seçili düğümleri kümesini için salt okunur, salt iletme imleç sınıf sağlar.</span><span class="sxs-lookup"><span data-stu-id="702a8-105">Once a node set is retrieved, the <xref:System.Xml.XPath.XPathNodeIterator> class provides a read-only, forward-only cursor to the selected set of nodes.</span></span> <span data-ttu-id="702a8-106">Bu yöntemin çağrılması belge sırayla bir sonraki düğüme taşınmasını belge sırayla düğüm kümesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="702a8-106">The node set is created in document order, so calling this method moves to the next node in document order.</span></span> <span data-ttu-id="702a8-107"><xref:System.Xml.XPath.XPathNodeIterator> bir düğüm ağacı kümedeki tüm düğümlerin oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="702a8-107"><xref:System.Xml.XPath.XPathNodeIterator> does not build a node tree of all the nodes in the set.</span></span> <span data-ttu-id="702a8-108">Bunun yerine, temel alınan düğümü ağacında gezinme gibi işaret gösterme, verilerin bir tek düğümlü penceresi sağlar.</span><span class="sxs-lookup"><span data-stu-id="702a8-108">Instead, it provides a single node window into the data, exposing the underlying node it points to as you move around in the tree.</span></span> <span data-ttu-id="702a8-109">Kullanılabilir özellikleri ve yöntemleri <xref:System.Xml.XPath.XPathNodeIterator> sınıfını geçerli düğüm bilgi almak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="702a8-109">The methods and properties available from the <xref:System.Xml.XPath.XPathNodeIterator> class enable you to get information from the current node.</span></span> <span data-ttu-id="702a8-110">Kullanılabilir yöntemlerin ve özelliklerin listesi için bkz. <xref:System.Windows.Forms.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="702a8-110">For a list of the available methods and properties, see <xref:System.Windows.Forms.ToolBar>.</span></span>  
  
 <span data-ttu-id="702a8-111">Bu yana bir <xref:System.Xml.XPath.XPathNodeIterator> taşır bir dizi düğümü üzerinden bir XPath sorgudan oluşturulan ve yalnızca ileri taşır, taşımak için yolu kullanmaktır <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="702a8-111">Since an <xref:System.Xml.XPath.XPathNodeIterator> moves over a set of nodes created from an XPath query and moves forward only, the way to move is by using the <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> method.</span></span> <span data-ttu-id="702a8-112">Bu yöntemin dönüş türü `Boolean`, döndürme `true` sonraki Seçili düğüme geçerse ve `false` artık seçilen düğüm varsa.</span><span class="sxs-lookup"><span data-stu-id="702a8-112">The return type of this method is `Boolean`, returning `true` if it moves to the next selected node, and `false` if there are no more selected nodes.</span></span> <span data-ttu-id="702a8-113">Döndürürse `true`, aşağıdaki listede kullanılabilir özellikleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="702a8-113">If it returns `true`, the following list shows the properties available:</span></span>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Current%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.CurrentPosition%2A>  
  
-   <xref:System.Xml.XPath.XPathNodeIterator.Count%2A>  
  
 <span data-ttu-id="702a8-114">Bir düğümde, aradığınız ayarlamak ilk kez, bir çağrı <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> konumlandırmak için yapılmalıdır <xref:System.Xml.XPath.XPathNodeIterator> seçili kümenin ilk düğümü üzerinde.</span><span class="sxs-lookup"><span data-stu-id="702a8-114">When you are looking at a node set for the first time, a call to <xref:System.Xml.XPath.XPathNodeIterator.MoveNext%2A> must be made to position the <xref:System.Xml.XPath.XPathNodeIterator> on the first node of the selected set.</span></span> <span data-ttu-id="702a8-115">Bu işlem biraz sağlar yazılacak döngü.</span><span class="sxs-lookup"><span data-stu-id="702a8-115">This allows a while loop to be written.</span></span>  
  
 <span data-ttu-id="702a8-116">Aşağıdaki kod örneğinde nasıl geçirileceğini gösterir. bir <xref:System.Xml.XPath.XPathNodeIterator> için bir <xref:System.Xml.Xsl.XslTransform> bir parametre olarak <xref:System.Xml.Xsl.XsltArgumentList>.</span><span class="sxs-lookup"><span data-stu-id="702a8-116">The following code example shows how to pass an <xref:System.Xml.XPath.XPathNodeIterator> to an <xref:System.Xml.Xsl.XslTransform> as a parameter in the <xref:System.Xml.Xsl.XsltArgumentList>.</span></span> <span data-ttu-id="702a8-117">Kod giriştir **books.xml**, ve stil sayfası **text.xsl**.</span><span class="sxs-lookup"><span data-stu-id="702a8-117">The input to the code is **books.xml**, and the style sheet is **text.xsl**.</span></span> <span data-ttu-id="702a8-118">Dosya **test.xml** olduğu <xref:System.Xml.XPath.XPathDocument>.</span><span class="sxs-lookup"><span data-stu-id="702a8-118">The file **test.xml** is the <xref:System.Xml.XPath.XPathDocument>.</span></span>  
  
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
  
## <a name="booksxml"></a><span data-ttu-id="702a8-119">Books.XML</span><span class="sxs-lookup"><span data-stu-id="702a8-119">books.xml</span></span>  
  
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
  
## <a name="testxsl"></a><span data-ttu-id="702a8-120">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="702a8-120">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="702a8-121">Test.XML</span><span class="sxs-lookup"><span data-stu-id="702a8-121">test.xml</span></span>  
  
```xml  
<Title attr="Test">this is a test</Title>  
```  
  
## <a name="output-outxml"></a><span data-ttu-id="702a8-122">Çıkış (out.xml)</span><span class="sxs-lookup"><span data-stu-id="702a8-122">Output (out.xml)</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<out>  
  <title>Seven Years in Trenton</title>  
  <title>History of Trenton</title>  
</out>  
```  
  
## <a name="see-also"></a><span data-ttu-id="702a8-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="702a8-123">See also</span></span>

- [<span data-ttu-id="702a8-124">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="702a8-124">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
