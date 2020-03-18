---
title: Ad alanı önekleri (C#) (LINQ - XML) nasıl kontrol ediletilir?
ms.date: 07/20/2015
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 9f43c0804d8c830fa75f1e1390cb578c5f5d5106
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141387"
---
# <a name="how-to-control-namespace-prefixes-c-linq-to-xml"></a>Ad alanı önekleri (C#) (LINQ - XML) nasıl kontrol ediletilir?
Bu konu, bir XML ağacını seri hale alırken ad alanı öneklerini nasıl denetebileceğinizi açıklar.  
  
 Birçok durumda, ad alanı önekleri denetlemek gerekli değildir.  
  
 Ancak, bazı XML programlama araçları ad alanı önekleri belirli bir denetim gerektirir. Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgesini manipüle ediyor olabilirsiniz; bu durumda, belgenin bu özel öneklerle serihale edilmesi önemlidir.  
  
 Ad alanı öneklerini denetlemenin en yaygın nedeni budur.  
  
 Ad alanı öneklerini denetlemenin bir diğer yaygın nedeni de, kullanıcıların XML belgesini el ile yeniden oluşturmasını ve kullanıcının yazması için uygun ad alanı önekleri oluşturmasını istemenizdir. Örneğin, bir XSD belgesi oluşturuyor olabilirsiniz. Şemalar için sözleşmeler, şema `xs` `xsd` ad alanı için önek olarak veya kullanmanızı öneririz.  
  
 Ad alanı öneklerini denetlemek için, ad alanlarını bildiren öznitelikler eklersiniz. Ad alanlarını belirli öneklerle bildirirseniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] seri hale getirilirken ad alanı öneklerini onurlandırmaya çalışırsınız.  
  
 Önek ile bir ad alanı bildiren bir öznitelik oluşturmak için, öznitelik adının ad alanı ve <xref:System.Xml.Linq.XNamespace.Xmlns%2A>öznitelik adı ad alanı ad alanı öneki olduğu bir öznitelik oluşturun. Özniteliğin değeri ad alanının URI'sidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte iki ad alanı bildirir. Ad alanının `http://www.adventure-works.com` önekinin olduğunu ve `aw` `www.fourthcoffee.com` ad alanının '' önekinin `fc`olduğunu belirtir.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
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

- [İsim Alanlarına Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md)
