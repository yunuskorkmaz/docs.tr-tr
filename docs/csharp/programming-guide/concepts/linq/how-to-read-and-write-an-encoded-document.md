---
title: Kodlanmış bir belgeyi okuma ve yazma (C#)
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347672"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="15d8a-102">Kodlanmış bir belgeyi okuma ve yazma (C#)</span><span class="sxs-lookup"><span data-stu-id="15d8a-102">How to read and write an encoded document (C#)</span></span>
<span data-ttu-id="15d8a-103">Kodlanmış bir XML belgesi oluşturmak için, XML ağacına bir <xref:System.Xml.Linq.XDeclaration> ekler ve kodlamayı istenen kod sayfası adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="15d8a-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="15d8a-104"><xref:System.Text.Encoding.WebName%2A> tarafından döndürülen herhangi bir değer geçerli bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="15d8a-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="15d8a-105">Kodlanmış bir belgeyi okuduğunuzda, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="15d8a-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="15d8a-106"><xref:System.Xml.Linq.XDeclaration.Encoding%2A> geçerli bir kod sayfası adına ayarlarsanız, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlamayla serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="15d8a-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d8a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="15d8a-107">Example</span></span>  
 <span data-ttu-id="15d8a-108">Aşağıdaki örnek, biri UTF-8 kodlaması ve diğeri UTF-16 kodlaması ile iki belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="15d8a-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="15d8a-109">Daha sonra belgeleri yükler ve kodlamayı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="15d8a-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```csharp  
Console.WriteLine("Creating a document with utf-8 encoding");  
XDocument encodedDoc8 = new XDocument(  
    new XDeclaration("1.0", "utf-8", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc8.Save("EncodedUtf8.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
Console.WriteLine("Creating a document with utf-16 encoding");  
XDocument encodedDoc16 = new XDocument(  
    new XDeclaration("1.0", "utf-16", "yes"),  
    new XElement("Root", "Content")  
);  
encodedDoc16.Save("EncodedUtf16.xml");  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc8 = XDocument.Load("EncodedUtf8.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding);  
Console.WriteLine();  
  
XDocument newDoc16 = XDocument.Load("EncodedUtf16.xml");  
Console.WriteLine("Encoded document:");  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"));  
Console.WriteLine();  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding);  
```  
  
 <span data-ttu-id="15d8a-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="15d8a-110">This example produces the following output:</span></span>  
  
```output  
Creating a document with utf-8 encoding  
Encoding is:utf-8  
  
Creating a document with utf-16 encoding  
Encoding is:utf-16  
  
Encoded document:  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-8  
  
Encoded document:  
<?xml version="1.0" encoding="utf-16" standalone="yes"?>  
<Root>Content</Root>  
  
Encoding of loaded document is:utf-16  
```  
  
## <a name="see-also"></a><span data-ttu-id="15d8a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15d8a-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
