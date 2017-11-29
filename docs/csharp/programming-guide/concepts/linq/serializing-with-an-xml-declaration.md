---
title: Seri hale getirilirken bir XML bildirimi ile (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44d7f199508abd6d60bb554806409cebb1b7f845
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="6578e-102">Seri hale getirilirken bir XML bildirimi ile (C#)</span><span class="sxs-lookup"><span data-stu-id="6578e-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="6578e-103">Bu konu, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="6578e-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="6578e-104">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6578e-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="6578e-105">İçin seri hale getirilirken bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntemi bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6578e-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="6578e-106">Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (içinde belirtilen bir <xref:System.Xml.XmlWriterSettings> nesnesi) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="6578e-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="6578e-107">Kullanarak bir dize serileştirme, `ToString` yöntemi, sonuç XML olmayan bir XML bildirimi içerir.</span><span class="sxs-lookup"><span data-stu-id="6578e-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="6578e-108">Bir XML bildirimi ile seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="6578e-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="6578e-109">Aşağıdaki örnekte bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve dosyanın konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="6578e-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="6578e-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="6578e-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="6578e-111">Bir XML bildirimi seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="6578e-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="6578e-112">Aşağıdaki örnekte nasıl kaydedileceğini gösteren bir <xref:System.Xml.Linq.XElement> için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="6578e-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="6578e-113">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="6578e-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6578e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6578e-114">See Also</span></span>  
 [<span data-ttu-id="6578e-115">Biçimlendiricisi XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="6578e-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
