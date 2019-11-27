---
title: XML Bildirimi ile Serileştirme
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350627"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="53b47-102">XML bildirimiyle serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53b47-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="53b47-103">Bu konu, serileştirme 'in bir XML bildirimi oluşturup oluşturmayacağını nasıl denetleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="53b47-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="53b47-104">XML bildirimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="53b47-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="53b47-105"><xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> yöntemi veya <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> yöntemi kullanılarak bir <xref:System.IO.File> veya <xref:System.IO.TextWriter> serileştirilmesi bir XML bildirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53b47-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="53b47-106">Bir <xref:System.Xml.XmlWriter>seri hale getirmek istediğinizde, yazıcı ayarları (bir <xref:System.Xml.XmlWriterSettings> nesnesinde belirtilen) bir XML bildiriminin oluşturulup oluşturulmayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53b47-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="53b47-107">`ToString` yöntemini kullanarak bir dizeye serileştirilirsiniz, sonuçta elde edilen XML bir XML bildirimi içermez.</span><span class="sxs-lookup"><span data-stu-id="53b47-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="53b47-108">XML Bildirimi ile Serileştirme</span><span class="sxs-lookup"><span data-stu-id="53b47-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="53b47-109">Aşağıdaki örnek bir <xref:System.Xml.Linq.XElement>oluşturur, belgeyi bir dosyaya kaydeder ve sonra dosyayı konsola yazdırır:</span><span class="sxs-lookup"><span data-stu-id="53b47-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="53b47-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="53b47-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="53b47-111">XML bildirimi olmadan serileştirme</span><span class="sxs-lookup"><span data-stu-id="53b47-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="53b47-112">Aşağıdaki örnekte, bir <xref:System.Xml.Linq.XElement> <xref:System.Xml.XmlWriter>nasıl kaydedileceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="53b47-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="53b47-113">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="53b47-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="53b47-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53b47-114">See also</span></span>

- [<span data-ttu-id="53b47-115">XML ağaçlarını serileştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53b47-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
