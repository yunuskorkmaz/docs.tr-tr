---
title: Dönüşümlerde XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 118f97d1-7110-4d1b-b0bd-4143252c0bb0
ms.openlocfilehash: 59fb399d80e1d4d33d1a3c659d2ff74a37fd367d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282824"
---
# <a name="xpathnavigator-in-transformations"></a><span data-ttu-id="b5b4a-102">Dönüşümlerde XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="b5b4a-102">XPathNavigator in Transformations</span></span>
<span data-ttu-id="b5b4a-103"><xref:System.Xml.XPath.XPathNavigator>Sınıfı, verilere salt okunurdur ve dönüşümler (XSLT) Için Genişletilebilir Stil sayfası dili girişi olarak kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-103">The <xref:System.Xml.XPath.XPathNavigator> class provides read-only random access to data and is designed for use as an input to Extensible Stylesheet Language for Transformations (XSLT).</span></span> <span data-ttu-id="b5b4a-104">, Ve üzerinde uygulanır <xref:System.Xml.XPath.XPathDocument> <xref:System.Xml.XmlDataDocument> <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="b5b4a-104">It is implemented on the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDataDocument>, and <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="b5b4a-105">, <xref:System.Xml.XPath.XPathNavigator> XML yol dili (XPath) önerisinin 5. bölümünde açıklandığı gibi World Wide Web Konsorsiyumu (W3C) veri modelini temel alır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-105">The <xref:System.Xml.XPath.XPathNavigator> is based upon the World Wide Web Consortium (W3C) Data Model as described in section 5 of the XML Path Language (XPath) recommendation.</span></span>  
  
 <span data-ttu-id="b5b4a-106">, <xref:System.Xml.XPath.XPathNavigator> Herhangi bir mağaza üzerinde bir imleç modeli tanımlar ve tüm veri depolarındaki hızlı, salt okuma XPath sorguları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-106">The <xref:System.Xml.XPath.XPathNavigator> defines a cursor model over any store and provides fast, read-only XPath queries over any data store.</span></span> <span data-ttu-id="b5b4a-107"><xref:System.Xml.XPath.XPathNavigator>Ayrıca, sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-107">The <xref:System.Xml.XPath.XPathNavigator> is also the class to use for iterating over result tree fragments.</span></span>  
  
 <span data-ttu-id="b5b4a-108">API, depodaki geçerli düğümden bilgi almanızı ve bağlantılı düğümlere taşımanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-108">The API enables you to get information from the current node in the store and move to connected nodes.</span></span> <span data-ttu-id="b5b4a-109">, Bir <xref:System.Xml.XPath.XPathNavigator> **taşıma** yöntemleri kümesi kullanarak bir mağaza üzerinde geçiş yapan bir imleç stil modelidir.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-109">The <xref:System.Xml.XPath.XPathNavigator> is a cursor style model that performs traversal over a store using a set of **Move** methods.</span></span> <span data-ttu-id="b5b4a-110">, <xref:System.Xml.XPath.XPathNavigator> Her zaman bir düğüm üzerinde konumlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-110">The <xref:System.Xml.XPath.XPathNavigator> is always positioned on a node.</span></span> <span data-ttu-id="b5b4a-111">Başarısız olan herhangi bir **Move** yöntemi değişmeden bırakılamaz <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="b5b4a-111">Any **Move** method that fails leaves the <xref:System.Xml.XPath.XPathNavigator> unchanged.</span></span>  
  
 <span data-ttu-id="b5b4a-112">, <xref:System.Xml.XPath.XPathNavigator> Sonuç ağacı parçaları üzerinde yineleme için kullanılacak sınıftır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-112">The <xref:System.Xml.XPath.XPathNavigator> is the class to use for iterating over result tree fragments.</span></span> <span data-ttu-id="b5b4a-113">Aşağıdaki kod örneği, bir stil sayfası içinde, XML içeren parametresiyle işlevi çağırarak bir sonuç ağacı parçası oluşturur `fragment` .</span><span class="sxs-lookup"><span data-stu-id="b5b4a-113">The following code sample creates a result tree fragment within a style sheet by calling the function with the parameter, `fragment`, which contains XML.</span></span>  
  
## <a name="testxsl"></a><span data-ttu-id="b5b4a-114">test. Xsl</span><span class="sxs-lookup"><span data-stu-id="b5b4a-114">test.xsl</span></span>  
  
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
  
## <a name="testxml"></a><span data-ttu-id="b5b4a-115">test. xml</span><span class="sxs-lookup"><span data-stu-id="b5b4a-115">test.xml</span></span>  
  
```xml  
<root>Some text</root>  
```  
  
 <span data-ttu-id="b5b4a-116">Aşağıdaki kod, **test. xsl** stil sayfası ve **test. xml** giriş verilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-116">The following code uses the **test.xsl** style sheet and **test.xml** input data.</span></span>  
  
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
  
## <a name="output"></a><span data-ttu-id="b5b4a-117">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b5b4a-117">Output</span></span>  
 <span data-ttu-id="b5b4a-118">Dönüşümün sonucu, **out. xml**dosyasında bulunur:</span><span class="sxs-lookup"><span data-stu-id="b5b4a-118">The result of the transformation is found in the file **out.xml**:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>Joe  
```  
  
## <a name="see-also"></a><span data-ttu-id="b5b4a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5b4a-119">See also</span></span>

- [<span data-ttu-id="b5b4a-120">XslTransform Sınıfı XSLT İşlemcisini Uygular</span><span class="sxs-lookup"><span data-stu-id="b5b4a-120">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
