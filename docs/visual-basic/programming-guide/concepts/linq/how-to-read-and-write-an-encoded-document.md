---
title: 'Nasıl yapılır: Kodlanmış Belge Okuma ve Yazma'
ms.date: 07/20/2015
ms.assetid: 159d868f-5ac8-40f2-95ca-07dd925f35c6
ms.openlocfilehash: f66737429950e04f447dfbd58cf47b6434a22976
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397914"
---
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a><span data-ttu-id="64ae6-102">Nasıl yapılır: kodlanmış bir belgeyi okuma ve yazma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64ae6-102">How to: Read and Write an Encoded Document (Visual Basic)</span></span>

<span data-ttu-id="64ae6-103">Kodlanmış bir XML belgesi oluşturmak için, XML ağacına bir ekler ve <xref:System.Xml.Linq.XDeclaration> kodlamayı istenen kod sayfası adına ayarlar.</span><span class="sxs-lookup"><span data-stu-id="64ae6-103">To create an encoded XML document, you add an <xref:System.Xml.Linq.XDeclaration> to the XML tree, setting the encoding to the desired code page name.</span></span>

<span data-ttu-id="64ae6-104">Tarafından döndürülen herhangi <xref:System.Text.Encoding.WebName%2A> bir değer geçerli bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="64ae6-104">Any value returned by <xref:System.Text.Encoding.WebName%2A> is a valid value.</span></span>

<span data-ttu-id="64ae6-105">Kodlanmış bir belgeyi okuduğunuzda, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="64ae6-105">If you read an encoded document, the <xref:System.Xml.Linq.XDeclaration.Encoding%2A> property will be set to the code page name.</span></span>

<span data-ttu-id="64ae6-106"><xref:System.Xml.Linq.XDeclaration.Encoding%2A>Geçerli bir kod sayfası adı olarak ayarlarsanız, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlamayla serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="64ae6-106">If you set <xref:System.Xml.Linq.XDeclaration.Encoding%2A> to a valid code page name, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will serialize with the specified encoding.</span></span>

## <a name="example"></a><span data-ttu-id="64ae6-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="64ae6-107">Example</span></span>

<span data-ttu-id="64ae6-108">Aşağıdaki örnek, biri UTF-8 kodlaması ve diğeri UTF-16 kodlaması ile iki belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="64ae6-108">The following example creates two documents, one with utf-8 encoding, and one with utf-16 encoding.</span></span> <span data-ttu-id="64ae6-109">Daha sonra belgeleri yükler ve kodlamayı konsola yazdırır.</span><span class="sxs-lookup"><span data-stu-id="64ae6-109">It then loads the documents and prints the encoding to the console.</span></span>

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

<span data-ttu-id="64ae6-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="64ae6-110">This example produces the following output:</span></span>

```console
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

## <a name="see-also"></a><span data-ttu-id="64ae6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64ae6-111">See also</span></span>

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [<span data-ttu-id="64ae6-112">Gelişmiş LINQ to XML Programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64ae6-112">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
