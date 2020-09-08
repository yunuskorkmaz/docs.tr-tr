---
title: C# LINQ to XML ad alanları içeren bir belge oluşturma
description: Ön ek içeren varsayılan ad alanları veya ad alanları içeren belgeler oluşturmak Için C# içinde XNamespace nesnesini kullanın.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 3ec9624bcc599a73a6872e5c4c79504a1a4b4380
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553518"
---
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a>C# ' de ad alanlarıyla belge oluşturma (LINQ to XML)

Bu makalede, ad alanları Içeren C# dilinde belge oluşturma gösterilmektedir.

## <a name="example-declare-and-initialize-a-default-namespace"></a>Örnek: Declare ve varsayılan ad alanı başlatma

Bir ad alanında olan bir öğe veya öznitelik oluşturmak için, önce bir nesne bildirir ve başlatın <xref:System.Xml.Linq.XNamespace> . Daha sonra, ad alanını bir dize olarak ifade edilen yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanabilirsiniz.

Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur. Varsayılan olarak, LINQ to XML bu belgeyi varsayılan bir ad alanıyla seri hale getirir.

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a>Örnek: bir ad alanı ve özniteliği bulunan bir belge oluşturun

Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur. Ayrıca ad alanı öneki olan ad alanını bildiren bir öznitelik oluşturur. Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliğin adının ad alanı öneki olduğu ve bu ad ad alanında olduğu bir öznitelik oluşturursunuz <xref:System.Xml.Linq.XNamespace.Xmlns%2A> . Bu özniteliğin değeri, ad alanının URI 'sidir.

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>Örnek: biri öneki olan iki ad alanı olan bir belge oluşturun

Aşağıdaki örnek, iki ad alanı içeren bir belge oluşturmayı gösterir. Biri varsayılan ad alanıdır, diğeri öneki olan bir ad alanıdır.

Ad alanı özniteliklerini kök öğesine ekleyerek, ad alanları varsayılan ad alanı olacak şekilde serileştirilir `http://www.adventure-works.com` ve `www.fourthcoffee.com` öneki ile serileştirilir `fc` . Varsayılan bir ad alanı bildiren bir öznitelik oluşturmak için, ad alanı olmadan adlı bir öznitelik oluşturun `xmlns` . Özniteliğin değeri varsayılan ad alanı URI 'sidir.

```csharp
// The http://www.adventure-works.com namespace is forced to be the default namespace.
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute("xmlns", "http://www.adventure-works.com"),
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
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>Örnek: iki ad alanı olan, her ikisi de önekle bir belge oluşturun

Aşağıdaki örnek, ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.

```csharp
XNamespace aw = "http://www.adventure-works.com";
XNamespace fc = "www.fourthcoffee.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),
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

## <a name="example-create-a-namespace-using-expanded-names"></a>Örnek: genişletilmiş adlar kullanarak ad alanı oluşturma

Aynı sonucu gerçekleştirmenin başka bir yolu da bir nesne bildirmek ve oluşturmak yerine genişletilmiş adlar kullanmaktır <xref:System.Xml.Linq.XNamespace> .

Bu yaklaşımın performans etkileri vardır. LINQ to XML bir genişletilmiş adı içeren bir dizeyi her geçirdiğinizde, LINQ to XML adı ayrıştırmalıdır, atomlanmış ad alanını bulur ve atomlanmış adını bulur. Bu işlem CPU süresini alır. Performans önemliyse, açıkça bir nesne bildirmek ve kullanmak isteyebilirsiniz <xref:System.Xml.Linq.XNamespace> .

Performans önemli bir sorun ise daha fazla bilgi için bkz. [XName nesnelerinin ön Atommesi](pre-atomization-xname-objects.md) .

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

Bu örnek aşağıdaki çıktıyı üretir:

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ad alanlarına genel bakış](namespaces-overview.md)
