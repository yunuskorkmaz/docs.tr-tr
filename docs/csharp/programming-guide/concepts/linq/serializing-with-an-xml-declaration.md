---
title: XML Bildirimi (C#) ile serileştirme
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4533d69f2b0bee68b4adee6e18fe28dde18078ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "66483476"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="e11a0-102">XML Bildirimi (C#) ile serileştirme</span><span class="sxs-lookup"><span data-stu-id="e11a0-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="e11a0-103">Bu konu, serileştirmenin bir XML bildirimi oluşturup oluşturmadığını nasıl denetleyiş olarak açıklar.</span><span class="sxs-lookup"><span data-stu-id="e11a0-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="e11a0-104">XML Beyanname Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e11a0-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="e11a0-105">Bir veya <xref:System.IO.File> yöntem <xref:System.IO.TextWriter> veya <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem kullanarak serileştirme bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e11a0-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="e11a0-106">Bir <xref:System.Xml.XmlWriter>, yazar ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilen) bir XML bildirimi oluşturulur olup olmadığını belirlemek için serileştirdiğinizde.</span><span class="sxs-lookup"><span data-stu-id="e11a0-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="e11a0-107">`ToString` Yöntemi kullanarak bir dize serihale ediyorsanız, ortaya çıkan XML bir XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="e11a0-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="e11a0-108">XML Bildirimi ile Serileştirme</span><span class="sxs-lookup"><span data-stu-id="e11a0-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="e11a0-109">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement>belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="e11a0-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="e11a0-110">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e11a0-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="e11a0-111">XML Bildirimi olmadan serileştirme</span><span class="sxs-lookup"><span data-stu-id="e11a0-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="e11a0-112">Aşağıdaki örnekte, bir <xref:System.Xml.Linq.XElement> 'den <xref:System.Xml.XmlWriter>bir'e nasıl kaydılsüreceğini gösterir</span><span class="sxs-lookup"><span data-stu-id="e11a0-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="e11a0-113">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="e11a0-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e11a0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e11a0-114">See also</span></span>

- [<span data-ttu-id="e11a0-115">XML Ağaçlarını Serihale Getirme (C#)</span><span class="sxs-lookup"><span data-stu-id="e11a0-115">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
