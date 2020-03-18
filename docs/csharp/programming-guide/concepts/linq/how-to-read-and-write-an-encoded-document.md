---
title: Kodlanmış bir belge (C#) okuma ve yazma
ms.date: 07/20/2015
ms.assetid: 84f64e71-39a6-42c6-ad68-f052bb158a03
ms.openlocfilehash: fa28c26845a0c6019943e0532ea0692a6dffd5a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347672"
---
# <a name="how-to-read-and-write-an-encoded-document-c"></a>Kodlanmış bir belge (C#) okuma ve yazma
Kodlanmış bir XML belgesi oluşturmak için, kodlamayı istenen kod sayfası adına ayarlayarak XML ağacına bir <xref:System.Xml.Linq.XDeclaration> belge eklersiniz.  
  
 Döndürülen <xref:System.Text.Encoding.WebName%2A> herhangi bir değer geçerli bir değerdir.  
  
 Kodlanmış bir belge okursanız, <xref:System.Xml.Linq.XDeclaration.Encoding%2A> özellik kod sayfası adına ayarlanır.  
  
 Geçerli bir <xref:System.Xml.Linq.XDeclaration.Encoding%2A> kod sayfası adı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olarak ayarlanırsanız, belirtilen kodlama ile seri hale gelir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, biri utf-8 kodlaması, diğeri utf-16 kodlaması olmak üzere iki belge oluşturulur. Daha sonra belgeleri yükler ve kodlamayı konsola yazdırır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XDeclaration.Encoding%2A?displayProperty=nameWithType>
