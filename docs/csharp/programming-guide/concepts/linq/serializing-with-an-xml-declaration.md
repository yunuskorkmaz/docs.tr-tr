---
title: XML bildirimiyle serileştirme (C#)
description: C# ' deki serileştirme 'in bir dosya, TextWriter ve XmlWriter 'da serileştirme de dahil olmak üzere bir XML bildirimi oluşturduğu konfigürasyonlar hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 7e91b61f037d28149f7c2355f4233dc319b54627
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302366"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="b81ae-103">XML bildirimiyle serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b81ae-103">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="b81ae-104">Bu konu, serileştirme 'in bir XML bildirimi oluşturup oluşturmayacağını nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b81ae-104">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="b81ae-105">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b81ae-105">XML Declaration Generation</span></span>  
 <span data-ttu-id="b81ae-106"><xref:System.IO.File>Yöntemini veya yöntemini kullanarak bir veya öğesine serileştirmek BIR <xref:System.IO.TextWriter> <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b81ae-106">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="b81ae-107">' A serileştirçalıştığınızda <xref:System.Xml.XmlWriter> , yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnede belirtilir) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b81ae-107">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="b81ae-108">Yöntemini kullanarak bir dizeye serileştirme yapıyorsanız `ToString` , elde EDILEN XML BIR XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="b81ae-108">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="b81ae-109">XML Bildirimi ile Serileştirme</span><span class="sxs-lookup"><span data-stu-id="b81ae-109">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="b81ae-110">Aşağıdaki örnek bir dosyası oluşturur <xref:System.Xml.Linq.XElement> , belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="b81ae-110">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="b81ae-111">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b81ae-111">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="b81ae-112">XML bildirimi olmadan serileştirme</span><span class="sxs-lookup"><span data-stu-id="b81ae-112">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="b81ae-113">Aşağıdaki örnekte, bir ' a nasıl kaydedileceği gösterilmektedir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="b81ae-113">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="b81ae-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b81ae-114">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b81ae-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b81ae-115">See also</span></span>

- [<span data-ttu-id="b81ae-116">XML ağaçlarını serileştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="b81ae-116">Serializing XML Trees (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
