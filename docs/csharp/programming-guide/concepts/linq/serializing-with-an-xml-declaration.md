---
title: (C#) bir XML bildirimi ile serileştirme
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 613280efc8c734c53c4af9252b4b83e2dd942f36
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537403"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="9ec72-102">(C#) bir XML bildirimi ile serileştirme</span><span class="sxs-lookup"><span data-stu-id="9ec72-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="9ec72-103">Bu konuda, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ec72-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="9ec72-104">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ec72-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="9ec72-105">Seri hale getirme için bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9ec72-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="9ec72-106">Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (belirtilen bir <xref:System.Xml.XmlWriterSettings> nesne) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="9ec72-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="9ec72-107">Kullanarak bir dize cricheditdoc::m_brtf `ToString` elde edilen XML yöntemi, bir XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="9ec72-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="9ec72-108">Bir XML bildirimi ile serileştirme</span><span class="sxs-lookup"><span data-stu-id="9ec72-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="9ec72-109">Aşağıdaki örnek, oluşturur bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve sonra dosyanın konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="9ec72-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="9ec72-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9ec72-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="9ec72-111">Bir XML bildirimi seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="9ec72-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="9ec72-112">Aşağıdaki örnek nasıl kaydedileceğini gösterir bir <xref:System.Xml.Linq.XElement> için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="9ec72-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="9ec72-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="9ec72-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ec72-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ec72-114">See Also</span></span>

- [<span data-ttu-id="9ec72-115">Serileştirmek XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="9ec72-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
