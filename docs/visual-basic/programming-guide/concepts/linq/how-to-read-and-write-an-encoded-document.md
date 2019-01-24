---
title: 'Nasıl yapılır: Okuma ve yazma kodlanmış belge (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: 52360b465e40a015e2cddee62ed4197d827bc560
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538706"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="5eab1-102">Nasıl yapılır: Okuma ve yazma kodlanmış belge (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eab1-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>
<span data-ttu-id="5eab1-103">Kodlanmış bir XML belgesi oluşturmak için eklediğiniz bir <xref:System.Xml.Linq.XDeclaration> için istenen kod sayfası adı kodlama XML ağacına ayarlama.</span><span class="sxs-lookup"><span data-stu-id="5eab1-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>  
  
 <span data-ttu-id="5eab1-104">Tarafından döndürülen herhangi bir değer <xref:System.Text.Encoding.WebName%2A> , geçerli bir değer.</span><span class="sxs-lookup"><span data-stu-id="5eab1-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>  
  
 <span data-ttu-id="5eab1-105">Kodlanmış belge okuma <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5eab1-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>  
  
 <span data-ttu-id="5eab1-106">Ayarlarsanız <xref:System.Xml.Linq.XDeclaration.Encoding%2A> geçerli kod sayfasına adına [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlama ile serileştirme.</span><span class="sxs-lookup"><span data-stu-id="5eab1-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5eab1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="5eab1-107">Example</span></span>  
 <span data-ttu-id="5eab1-108">Aşağıdaki örnek, iki belge, utf-8 kodlamalı, diğeri utf-16 kodlamalı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5eab1-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="5eab1-109">Belgeleri yükler ve kodlama konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5eab1-109">It then loads the documents and prints the encoding to the console.</span></span>  
  
```vb  
Console.WriteLine("Creating a document with utf-8 encoding")  
Dim encodedDoc8 As XDocument = _  
        <?xml version='1.0' encoding='utf-8' standalone='yes'?>  
        <Root>Content</Root>   
  
encodedDoc8.Save("EncodedUtf8.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Console.WriteLine("Creating a document with utf-16 encoding")  
Dim encodedDoc16 As XDocument = _  
        <?xml version='1.0' encoding='utf-16' standalone='yes'?>  
        <Root>Content</Root>  
  
encodedDoc16.Save("EncodedUtf16.xml")  
Console.WriteLine("Encoding is:{0}", encodedDoc16.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc8 As XDocument = XDocument.Load("EncodedUtf8.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf8.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc8.Declaration.Encoding)  
Console.WriteLine()  
  
Dim newDoc16 As XDocument = XDocument.Load("EncodedUtf16.xml")  
Console.WriteLine("Encoded document:")  
Console.WriteLine(File.ReadAllText("EncodedUtf16.xml"))  
Console.WriteLine()  
Console.WriteLine("Encoding of loaded document is:{0}", newDoc16.Declaration.Encoding)  
```  
  
 <span data-ttu-id="5eab1-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="5eab1-110">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5eab1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5eab1-111">See also</span></span>
- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5eab1-112">Gelişmiş LINQ to XML programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5eab1-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
