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
# <a name="how-to-read-and-write-an-encoded-document-visual-basic"></a>Nasıl yapılır: Okuma ve yazma kodlanmış belge (Visual Basic)
Kodlanmış bir XML belgesi oluşturmak için eklediğiniz bir <xref:System.Xml.Linq.XDeclaration> için istenen kod sayfası adı kodlama XML ağacına ayarlama.  
  
 Tarafından döndürülen herhangi bir değer <xref:System.Text.Encoding.WebName%2A> , geçerli bir değer.  
  
 Kodlanmış belge okuma <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özelliği kod sayfası adına ayarlanır.  
  
 Ayarlarsanız <xref:System.Xml.Linq.XDeclaration.Encoding%2A> geçerli kod sayfasına adına [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belirtilen kodlama ile serileştirme.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki belge, utf-8 kodlamalı, diğeri utf-16 kodlamalı oluşturur. Belgeleri yükler ve kodlama konsola yazdırır.  
  
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
- [Gelişmiş LINQ to XML programlama (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
