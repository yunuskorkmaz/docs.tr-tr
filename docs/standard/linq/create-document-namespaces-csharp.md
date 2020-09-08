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
# <a name="how-to-create-a-document-with-namespaces-in-c-linq-to-xml"></a><span data-ttu-id="cb366-103">C# ' de ad alanlarıyla belge oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="cb366-103">How to create a document with namespaces in C# (LINQ to XML)</span></span>

<span data-ttu-id="cb366-104">Bu makalede, ad alanları Içeren C# dilinde belge oluşturma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb366-104">This article shows how to create documents in C# that have namespaces.</span></span>

## <a name="example-declare-and-initialize-a-default-namespace"></a><span data-ttu-id="cb366-105">Örnek: Declare ve varsayılan ad alanı başlatma</span><span class="sxs-lookup"><span data-stu-id="cb366-105">Example: Declare and initialize a default namespace</span></span>

<span data-ttu-id="cb366-106">Bir ad alanında olan bir öğe veya öznitelik oluşturmak için, önce bir nesne bildirir ve başlatın <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="cb366-106">To create an element or an attribute that's in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="cb366-107">Daha sonra, ad alanını bir dize olarak ifade edilen yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cb366-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>

<span data-ttu-id="cb366-108">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb366-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="cb366-109">Varsayılan olarak, LINQ to XML bu belgeyi varsayılan bir ad alanıyla seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="cb366-109">By default, LINQ to XML serializes this document with a default namespace.</span></span>

```csharp
// Create an XML tree in a namespace.
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="cb366-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb366-110">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child>child content</Child>
</Root>
```

## <a name="example-create-a-document-that-has-a-namespace-and-an-attribute"></a><span data-ttu-id="cb366-111">Örnek: bir ad alanı ve özniteliği bulunan bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="cb366-111">Example: Create a document that has a namespace and an attribute</span></span>

<span data-ttu-id="cb366-112">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb366-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="cb366-113">Ayrıca ad alanı öneki olan ad alanını bildiren bir öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb366-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="cb366-114">Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliğin adının ad alanı öneki olduğu ve bu ad ad alanında olduğu bir öznitelik oluşturursunuz <xref:System.Xml.Linq.XNamespace.Xmlns%2A> .</span><span class="sxs-lookup"><span data-stu-id="cb366-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="cb366-115">Bu özniteliğin değeri, ad alanının URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="cb366-115">The value of this attribute is the URI of the namespace.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XNamespace aw = "http://www.adventure-works.com";
XElement root = new XElement(aw + "Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement(aw + "Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="cb366-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb366-116">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="cb366-117">Örnek: biri öneki olan iki ad alanı olan bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="cb366-117">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="cb366-118">Aşağıdaki örnek, iki ad alanı içeren bir belge oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="cb366-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="cb366-119">Biri varsayılan ad alanıdır, diğeri öneki olan bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="cb366-119">One is the default namespace, the other is a namespace with a prefix.</span></span>

<span data-ttu-id="cb366-120">Ad alanı özniteliklerini kök öğesine ekleyerek, ad alanları varsayılan ad alanı olacak şekilde serileştirilir `http://www.adventure-works.com` ve `www.fourthcoffee.com` öneki ile serileştirilir `fc` .</span><span class="sxs-lookup"><span data-stu-id="cb366-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of `fc`.</span></span> <span data-ttu-id="cb366-121">Varsayılan bir ad alanı bildiren bir öznitelik oluşturmak için, ad alanı olmadan adlı bir öznitelik oluşturun `xmlns` .</span><span class="sxs-lookup"><span data-stu-id="cb366-121">To create an attribute that declares a default namespace, you create an attribute with the name `xmlns`, without a namespace.</span></span> <span data-ttu-id="cb366-122">Özniteliğin değeri varsayılan ad alanı URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="cb366-122">The value of the attribute is the default namespace URI.</span></span>

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

<span data-ttu-id="cb366-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb366-123">This example produces the following output:</span></span>

```xml
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <DifferentChild>other content</DifferentChild>
  </fc:Child>
  <Child2>c2 content</Child2>
  <fc:Child3>c3 content</fc:Child3>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="cb366-124">Örnek: iki ad alanı olan, her ikisi de önekle bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="cb366-124">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="cb366-125">Aşağıdaki örnek, ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cb366-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>

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

<span data-ttu-id="cb366-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb366-126">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="example-create-a-namespace-using-expanded-names"></a><span data-ttu-id="cb366-127">Örnek: genişletilmiş adlar kullanarak ad alanı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb366-127">Example: Create a namespace using expanded names</span></span>

<span data-ttu-id="cb366-128">Aynı sonucu gerçekleştirmenin başka bir yolu da bir nesne bildirmek ve oluşturmak yerine genişletilmiş adlar kullanmaktır <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="cb366-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>

<span data-ttu-id="cb366-129">Bu yaklaşımın performans etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="cb366-129">This approach has performance implications.</span></span> <span data-ttu-id="cb366-130">LINQ to XML bir genişletilmiş adı içeren bir dizeyi her geçirdiğinizde, LINQ to XML adı ayrıştırmalıdır, atomlanmış ad alanını bulur ve atomlanmış adını bulur.</span><span class="sxs-lookup"><span data-stu-id="cb366-130">Each time you pass a string that contains an expanded name to LINQ to XML, LINQ to XML must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="cb366-131">Bu işlem CPU süresini alır.</span><span class="sxs-lookup"><span data-stu-id="cb366-131">This process takes CPU time.</span></span> <span data-ttu-id="cb366-132">Performans önemliyse, açıkça bir nesne bildirmek ve kullanmak isteyebilirsiniz <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="cb366-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>

<span data-ttu-id="cb366-133">Performans önemli bir sorun ise daha fazla bilgi için bkz. [XName nesnelerinin ön Atommesi](pre-atomization-xname-objects.md) .</span><span class="sxs-lookup"><span data-stu-id="cb366-133">If performance is an important issue, see [Pre-Atomization of XName Objects](pre-atomization-xname-objects.md) for more information.</span></span>

```csharp
// Create an XML tree in a namespace, with a specified prefix
XElement root = new XElement("{http://www.adventure-works.com}Root",
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),
    new XElement("{http://www.adventure-works.com}Child", "child content")
);
Console.WriteLine(root);
```

<span data-ttu-id="cb366-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="cb366-134">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child>child content</aw:Child>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="cb366-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb366-135">See also</span></span>

- [<span data-ttu-id="cb366-136">Ad alanlarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="cb366-136">Namespaces overview</span></span>](namespaces-overview.md)
