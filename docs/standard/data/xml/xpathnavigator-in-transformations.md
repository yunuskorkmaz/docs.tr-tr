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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c492d470fe29041f32039d98ecb854e18f40423c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="f1ccf-102">Dönüşümleri XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f1ccf-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="f1ccf-103"><xref:System.Xml.XPath.XPathNavigator> Sınıfı verilerine salt okunur rastgele erişim sağlar ve Genişletilebilir Stil sayfası dili için bir giriş olarak kullanmak için Dönüşümleri (XSLT) için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="f1ccf-104">Üzerinde uygulanan <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, ve <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="f1ccf-105"><xref:System.Xml.XPath.XPathNavigator> XML Path dili (XPath) öneri 5 bölümünde açıklandığı gibi World Wide Web Konsorsiyumu (W3C) veri modeline dayanır.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="f1ccf-106"><xref:System.Xml.XPath.XPathNavigator> Bir imleç modeli herhangi bir depolama tanımlar ve hızlı, salt okunur XPath sorguları herhangi bir veri deposu sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="f1ccf-107"><xref:System.Xml.XPath.XPathNavigator> De sonuç ağaç parçaları yineleme için kullanılacak bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="f1ccf-108">API, depoda geçerli düğümden bilgi almak ve bağlı düğümlerine taşıma sağlar.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="f1ccf-109"><xref:System.Xml.XPath.XPathNavigator> Kümesi kullanılarak bir mağaza çapraz geçişi gerçekleştirir bir imleç stili modeldir **taşıma** yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="f1ccf-110"><xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğümde konumlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="f1ccf-111">Tüm **taşıma** bırakır başarısız yöntemi <xref:System.Xml.XPath.XPathNavigator> değişmez.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="f1ccf-112"><xref:System.Xml.XPath.XPathNavigator> Sonuç ağaç parçaları yineleme için kullanılacak bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="f1ccf-113">Aşağıdaki kod örneği bir stil sayfası içinden sonuç ağacı parçası parametresiyle işlevini çağırarak oluşturur `fragment`, XML içeriyor.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="f1ccf-114">Test.xsl</span><span class="sxs-lookup"><span data-stu-id="f1ccf-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="f1ccf-115">Test.XML</span><span class="sxs-lookup"><span data-stu-id="f1ccf-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="f1ccf-116">Aşağıdaki kod **test.xsl** stil sayfası ve **test.xml** giriş verileri.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="f1ccf-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f1ccf-117">Output</span></span>  
 <span data-ttu-id="f1ccf-118">Dönüşümün sonucunu dosyasında bulunan **out.xml**:</span><span class="sxs-lookup"><span data-stu-id="f1ccf-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="f1ccf-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f1ccf-119">See Also</span></span>  
 [<span data-ttu-id="f1ccf-120">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="f1ccf-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
