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
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="645dd-102">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="645dd-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="645dd-103"><xref:System.Xml.XPath.XPathNavigator> sınıfı verilere salt okunurdur ve dönüşümler (XSLT) için Genişletilebilir Stil sayfası dili girişi olarak kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="645dd-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="645dd-104"><xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>ve <xref:System.Xml.XmlDocument>uygulanır.</span><span class="sxs-lookup"><span data-stu-id="645dd-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="645dd-105"><xref:System.Xml.XPath.XPathNavigator>, XML yol dili (XPath) önerisinin 5. bölümünde açıklandığı gibi World Wide Web Konsorsiyumu (W3C) veri modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="645dd-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="645dd-106"><xref:System.Xml.XPath.XPathNavigator> herhangi bir mağaza üzerinde bir imleç modeli tanımlar ve tüm veri depolarındaki hızlı, salt okuma XPath sorguları sağlar.</span><span class="sxs-lookup"><span data-stu-id="645dd-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="645dd-107"><xref:System.Xml.XPath.XPathNavigator> Ayrıca, sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır.</span><span class="sxs-lookup"><span data-stu-id="645dd-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="645dd-108">API, depodaki geçerli düğümden bilgi almanızı ve bağlantılı düğümlere taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="645dd-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="645dd-109"><xref:System.Xml.XPath.XPathNavigator>, bir **taşıma** yöntemleri kümesi kullanarak bir mağaza üzerinde geçiş yapan bir imleç stil modelidir.</span><span class="sxs-lookup"><span data-stu-id="645dd-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="645dd-110"><xref:System.Xml.XPath.XPathNavigator> her zaman bir düğüm üzerinde konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="645dd-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="645dd-111">Başarısız olan herhangi bir **Move** yöntemi, <xref:System.Xml.XPath.XPathNavigator> değişmeden bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="645dd-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="645dd-112"><xref:System.Xml.XPath.XPathNavigator>, sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır.</span><span class="sxs-lookup"><span data-stu-id="645dd-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="645dd-113">Aşağıdaki kod örneği, bir stil sayfası içinde, XML içeren `fragment`parametresiyle işlevi çağırarak bir sonuç ağacı parçası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="645dd-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="645dd-114">test. Xsl</span><span class="sxs-lookup"><span data-stu-id="645dd-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="645dd-115">test. xml</span><span class="sxs-lookup"><span data-stu-id="645dd-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="645dd-116">Aşağıdaki kod, **test. xsl** stil sayfası ve **test. xml** giriş verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="645dd-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="645dd-117">Çıkış</span><span class="sxs-lookup"><span data-stu-id="645dd-117">Output</span></span>  
 <span data-ttu-id="645dd-118">Dönüşümün sonucu, **out. xml**dosyasında bulunur:</span><span class="sxs-lookup"><span data-stu-id="645dd-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="645dd-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="645dd-119">See also</span></span>

- [<span data-ttu-id="645dd-120">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="645dd-120">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
