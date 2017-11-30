---
title: "Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ-XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fc8d652c54be62fdf38e0aa05fcf6a81af3f719b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Nasıl yapılır: denetim Namespace önekleri (C#) (LINQ-XML)
Bu konuda, bir XML ağacı serileştirilirken ad alanı öneklerini nasıl denetleyebilirsiniz açıklanmaktadır.  
  
 Çoğu durumda, ad alanı öneklerini denetlemek gerekli değildir.  
  
 Ancak, belirli XML programlamaya ad alanı önekleri belirli denetim gerektirir. Örneğin, bir XSLT stil sayfası veya belirli bir ad alanı önekleri başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgeyi düzenleme; Bu durumda, belge bu belirli öneklerle serileştirilmesi önemlidir.  
  
 Ad alanı öneklerini denetlemek için kullanılan en yaygın nedeni budur.  
  
 Ad alanı öneklerini denetlemek için başka bir ortak XML belgesi el ile düzenlemek istediğiniz ve yazmak kullanıcı için kolay ad alanı öneklerini oluşturmak istediğiniz nedeni. Örneğin, bir XSD belge oluşturuyor. Şemaları için kuralları önermek ya da kullanmak `xs` veya `xsd` Şema ad alanı öneki olarak.  
  
 Ad alanı öneklerini denetlemek için ad alanlarını bildirme öznitelikleri ekleyin. Ad alanları belirli öneklerle bildirirseniz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serileştirilirken ad alanı önekleri kabul dener.  
  
 Özniteliğin öznitelik adını ad oluşturduğunuz ad alanı öneki bildiren bir öznitelik oluşturmak için <xref:System.Xml.Linq.XNamespace.Xmlns%2A>, ve ad alanı öneki öznitelik adıdır. Ad alanı URI'si öznitelik değeri.  
  
## <a name="example"></a>Örnek  
 Bu örnek iki ad alanı bildirir. Gerektiğini belirtir `http://www.adventure-works.com` ad alanı öneki var. `aw`ve `www.fourthcoffee.com` ad alanı öneki var. `fc`.  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
