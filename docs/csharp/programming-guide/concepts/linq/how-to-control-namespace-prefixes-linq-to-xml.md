---
title: 'Nasıl yapılır: Denetim ad alanı önekleriC#() (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 5b836be46001b660547532311b1b507ff234975f
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710159"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Nasıl yapılır: Denetim ad alanı önekleriC#() (LINQ to XML)
Bu konu, bir XML ağacını serileştirilirken ad alanı öneklerini nasıl denetleyebileceğinizi açıklar.  
  
 Birçok durumda, ad alanı öneklerini denetlemek gerekli değildir.  
  
 Ancak bazı XML programlama araçları, ad alanı önekleri için belirli bir denetim gerektirir. Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran gömülü XPath ifadeleri içeren bir XAML belgesini düzenleme Bu durumda, belgenin bu özel öneklerle serileştirilmesi önemlidir.  
  
 Bu, ad alanı öneklerini denetlemenin en yaygın nedenidir.  
  
 Ad alanı öneklerini denetlemenin bir diğer yaygın nedeni, kullanıcıların XML belgesini el ile düzenlemesini ve kullanıcının yazması için uygun olan ad alanı önekleri oluşturmasını istemesidir. Örneğin, bir XSD belgesi oluşturuluyor olabilirsiniz. Şemaların kuralları, şema ad alanı için önek `xs` olarak `xsd` ya da ' i kullanmanızı önerir.  
  
 Ad alanı öneklerini denetlemek için ad alanlarını bildiren öznitelikleri eklersiniz. Ad alanlarını belirli öneklerle bildirirseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serileştirilirken ad alanı öneklerini kabul etmeye çalışır.  
  
 Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliği adının ad alanının olduğu <xref:System.Xml.Linq.XNamespace.Xmlns%2A>ve özniteliğin adı ad alanı öneki olan bir öznitelik oluşturursunuz. Özniteliğin değeri, ad alanının URI 'sidir.  
  
## <a name="example"></a>Örnek  
 Bu örnek iki ad alanı bildirir. `http://www.adventure-works.com` Ad alanının `www.fourthcoffee.com` öneki olduğunu ve ad alanının öneki `fc`olduğunu belirtir. `aw`  
  
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
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış (LINQ to XMLC#) ()](namespaces-overview-linq-to-xml.md)
