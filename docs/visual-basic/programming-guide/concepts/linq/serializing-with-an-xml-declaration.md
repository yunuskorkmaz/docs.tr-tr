---
title: Serileştirmek bir XML bildirimi (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: d0d6ccfdffa76de61c36e4cdb3f68f7cf85f1e68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558481"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="bcc49-102">Serileştirmek bir XML bildirimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bcc49-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="bcc49-103">Bu konuda, serileştirme bir XML bildirimi oluşturup oluşturmayacağını denetlemek nasıl açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bcc49-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="bcc49-104">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="bcc49-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="bcc49-105">Seri hale getirme için bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> kullanarak <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntem bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bcc49-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="bcc49-106">Ne zaman serileştirmek için bir <xref:System.Xml.XmlWriter>, yazıcı ayarları (belirtilen bir <xref:System.Xml.XmlWriterSettings> nesne) veya bir XML bildirimi oluşturulup oluşturulmayacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="bcc49-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="bcc49-107">Kullanarak bir dize cricheditdoc::m_brtf `ToString` elde edilen XML yöntemi, bir XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="bcc49-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="bcc49-108">Bir XML bildirimi ile serileştirme</span><span class="sxs-lookup"><span data-stu-id="bcc49-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="bcc49-109">Aşağıdaki örnek, oluşturur bir <xref:System.Xml.Linq.XElement>, belgeyi bir dosyaya kaydeder ve sonra dosyanın konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="bcc49-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="bcc49-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcc49-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="bcc49-111">Bir XML bildirimi seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="bcc49-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="bcc49-112">Aşağıdaki örnek nasıl kaydedileceğini gösterir bir <xref:System.Xml.Linq.XElement> için bir <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="bcc49-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="bcc49-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bcc49-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bcc49-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcc49-114">See also</span></span>
- [<span data-ttu-id="bcc49-115">(Visual Basic) XML ağaçlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="bcc49-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
