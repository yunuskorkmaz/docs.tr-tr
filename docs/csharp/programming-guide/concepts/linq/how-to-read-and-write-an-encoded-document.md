---
title: 'Nasıl yapılır: Okuma ve yazma kodlanmış belge (C#)'
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fdf3e05c705ca9caea32306616c79ade0aeb9be3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702314"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Nasıl yapılır: Okuma ve yazma kodlanmış belge (C#)
Kodlanmış bir XML belgesi oluşturmak için eklediğiniz bir <xref:System.Xml.Linq.XDeclaration> için istenen kod sayfası adı kodlama XML ağacına ayarlama.  
  
 Tarafından döndürülen herhangi bir değer <xref:System.Text.Encoding.WebName%2A> , geçerli bir değer.  
  
 Kodlanmış belge okuma <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.  
  
 Ayarlarsanız <xref:System.Xml.Linq.XDeclaration.Encoding%2A> geçerli kod sayfasına adına [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlama ile serileştirme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki belge, utf-8 kodlamalı, diğeri utf-16 kodlamalı oluşturur. Belgeleri yükler ve kodlama konsola yazdırır.  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
- [Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
