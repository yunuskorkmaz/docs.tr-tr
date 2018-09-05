---
title: 'Nasıl yapılır: Okuma ve yazma kodlanmış belge (C#)'
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: a5e1d6f70d8ad2740e4d7daff8c78b49966bb7ee
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661641"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a><span data-ttu-id="267b8-102">Nasıl yapılır: Okuma ve yazma kodlanmış belge (C#)</span><span class="sxs-lookup"><span data-stu-id="267b8-102">How to: Read and Write an Encoded Document (C#)</span></span>
<span data-ttu-id="267b8-103">Kodlanmış bir XML belgesi oluşturmak için eklediğiniz bir <xref:System.Xml.Linq.XDeclaration> için istenen kod sayfası adı kodlama XML ağacına ayarlama.</span><span class="sxs-lookup"><span data-stu-id="267b8-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="267b8-104">Tarafından döndürülen herhangi bir değer <xref:System.Text.Encoding.WebName%2A> , geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="267b8-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="267b8-105">Kodlanmış belge okuma <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="267b8-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="267b8-106">Ayarlarsanız <xref:System.Xml.Linq.XDeclaration.Encoding%2A> geçerli kod sayfasına adına [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlama ile serileştirme.</span><span class="sxs-lookup"><span data-stu-id="267b8-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="267b8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="267b8-107">Example</span></span>  
 <span data-ttu-id="267b8-108">Aşağıdaki örnek, iki belge, utf-8 kodlamalı, diğeri utf-16 kodlamalı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="267b8-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="267b8-109">Belgeleri yükler ve kodlama konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="267b8-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
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
  
 <span data-ttu-id="267b8-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="267b8-110">This example produces the following output:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="267b8-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="267b8-111">See Also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="267b8-112">Gelişmiş LINQ to XML programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="267b8-112">Advanced LINQ to XML Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
