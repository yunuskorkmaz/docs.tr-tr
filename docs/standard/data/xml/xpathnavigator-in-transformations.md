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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026749"
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="67d9d-102">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="67d9d-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="67d9d-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı veri salt okunur rastgele erişim sağlar ve Genişletilebilir Stil sayfası dili için giriş olarak kullanmak için Dönüşümleri (XSLT) için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="67d9d-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="67d9d-104">Üzerinde uygulanan <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, ve <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="67d9d-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="67d9d-105"><xref:System.Xml.XPath.XPathNavigator> XML Path Language (XPath) öneri 5. bölümünde anlatıldığı gibi World Wide Web Consortium (W3C) veri modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="67d9d-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="67d9d-106"><xref:System.Xml.XPath.XPathNavigator> Hiçbir depo üzerinde bir imleç modeli tanımlar ve XPath sorgularını hızlı ve salt okunur herhangi bir veri deposu sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d9d-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="67d9d-107"><xref:System.Xml.XPath.XPathNavigator> Ayrıca sonucu ağacı parçalarını yineleme için kullanılacak bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="67d9d-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="67d9d-108">API, depodaki geçerli düğüm öğrenmesini ve bağlı düğümleri için taşıma sağlar.</span><span class="sxs-lookup"><span data-stu-id="67d9d-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="67d9d-109"><xref:System.Xml.XPath.XPathNavigator> Kümesini kullanan bir depo üzerinde çapraz geçişi gerçekleştirir imleç stil modelidir **taşıma** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="67d9d-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="67d9d-110"><xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğümde konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="67d9d-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="67d9d-111">Tüm **taşıma** bırakır başarısız yöntemi <xref:System.Xml.XPath.XPathNavigator> değişmez.</span><span class="sxs-lookup"><span data-stu-id="67d9d-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="67d9d-112"><xref:System.Xml.XPath.XPathNavigator> Sonucu ağacı parçalarını yineleme için kullanılacak sınıftır.</span><span class="sxs-lookup"><span data-stu-id="67d9d-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="67d9d-113">Aşağıdaki kod örneği, işlev parametresi ile çağırarak bir stil sayfası içinde bir sonuç ağacı parçası oluşturur `fragment`, XML içeriyor.</span><span class="sxs-lookup"><span data-stu-id="67d9d-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="67d9d-114">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="67d9d-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="67d9d-115">test.xml</span><span class="sxs-lookup"><span data-stu-id="67d9d-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="67d9d-116">Aşağıdaki kod **test.xsl** stil sayfası ve **test.xml** veri girişi.</span><span class="sxs-lookup"><span data-stu-id="67d9d-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="67d9d-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="67d9d-117">Output</span></span>  
 <span data-ttu-id="67d9d-118">Dönüştürme sonucunu dosyasında bulunan **out.xml**:</span><span class="sxs-lookup"><span data-stu-id="67d9d-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="67d9d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="67d9d-119">See also</span></span>

- [<span data-ttu-id="67d9d-120">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="67d9d-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
