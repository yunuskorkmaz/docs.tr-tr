---
title: Ad alanı öneklerini denetleme-LINQ to XML
description: C# ve Visual Basic bir XML ağacını serileştirmek için ad alanı öneklerini denetleyebilirsiniz. Bunu yapmak için ad alanlarını bildiren öznitelikleri ekleyin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 64de5186-b81a-4ddd-8327-8693df59a01b
ms.openlocfilehash: 07efc23c11cd0dc0d281968911cf24d6ecbc76a2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553021"
---
# <a name="how-to-control-namespace-prefixes-linq-to-xml"></a>Ad alanı ön eklerini denetleme (LINQ to XML)

Bu makalede, C# ve Visual Basic bir XML ağacını serileştirilirken ad alanı öneklerini nasıl denetleyebileceğinizi açıklamaktadır.

Birçok durumda, ad alanı öneklerini denetlemek gerekli değildir. Ancak, belirli XML programlama araçları bunu gerektirir. Örneğin, bir XSLT stil sayfasını veya belirli ad alanı öneklerine başvuran katıştırılmış XPath ifadeleri içeren bir XAML belgesini düzenleme gibi olabilirsiniz. Böyle bir durumda, belgenin bu öneklerle serileştirilmesi önemlidir. Bu, ad alanı öneklerini denetlemenin yaygın bir nedenidir.

Diğer bir nedenden dolayı, kullanıcıların XML belgesini el ile düzenlemesini ve Kullanıcı için uygun olan ad alanı önekleri oluşturmasını istemeniz gerekir. Örneğin, bir XSD belgesi oluşturuluyor olabilirsiniz. Şemaların kuralları `xs` `xsd` , şema ad alanı için önek olarak ya da ' i kullanmanızı önerir.

Ad alanı öneklerini denetlemek için ad alanlarını bildiren öznitelikleri eklersiniz. Ad alanlarını belirli öneklerle bildirirseniz LINQ to XML serileştirilirken ad alanı öneklerini kabul etmeye çalışır.

Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliği adının ad alanının olduğu <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ve özniteliğin adı ad alanı öneki olan bir öznitelik oluşturursunuz. Özniteliğin değeri, ad alanının URI 'sidir.

## <a name="example-create-two-namespaces-that-have-prefixes"></a>Örnek: ön ekleri olan iki ad alanı oluşturma

Bu örnek iki ad alanı bildirir. `aw`Ad alanı için ön ek `http://www.adventure-works.com` ve `fc` `www.fourthcoffee.com` ad alanı öneki belirler.

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

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

This example produces the following output:

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

- [Ad alanlarına genel bakış](namespaces-overview.md)
