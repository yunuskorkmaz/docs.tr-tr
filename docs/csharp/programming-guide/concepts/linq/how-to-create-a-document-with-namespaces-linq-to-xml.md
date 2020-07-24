---
title: Ad alanları ile belge oluşturma (C#) (LINQ to XML)
description: Ad alanını yerel adla birleştirmek için bir XNamespace nesnesi kullanarak C# ' de LINQ to XML ad alanıyla bir belge oluşturmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 6472baefc73285af1c6dca0bfe7d874003940fc4
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103401"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="f03d2-103">Ad alanları ile belge oluşturma (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f03d2-103">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="f03d2-104">Bu konu başlığı altında, ad alanları ile belgelerin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-104">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f03d2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03d2-105">Example</span></span>  
 <span data-ttu-id="f03d2-106">Bir ad alanında olan bir öğe veya öznitelik oluşturmak için, önce bir nesne bildirir ve başlatın <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="f03d2-106">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="f03d2-107">Daha sonra, ad alanını bir dize olarak ifade edilen yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03d2-107">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="f03d2-108">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f03d2-108">The following example creates a document with one namespace.</span></span> <span data-ttu-id="f03d2-109">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Bu belgeyi varsayılan bir ad alanıyla seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-109">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f03d2-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03d2-110">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f03d2-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03d2-111">Example</span></span>  
 <span data-ttu-id="f03d2-112">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f03d2-112">The following example creates a document with one namespace.</span></span> <span data-ttu-id="f03d2-113">Ayrıca ad alanı öneki olan ad alanını bildiren bir öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f03d2-113">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="f03d2-114">Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliğin adının ad alanı öneki olduğu ve bu ad ad alanında olduğu bir öznitelik oluşturursunuz <xref:System.Xml.Linq.XNamespace.Xmlns%2A> .</span><span class="sxs-lookup"><span data-stu-id="f03d2-114">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="f03d2-115">Bu özniteliğin değeri, ad alanının URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-115">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f03d2-116">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03d2-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f03d2-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03d2-117">Example</span></span>  
 <span data-ttu-id="f03d2-118">Aşağıdaki örnek, iki ad alanı içeren bir belge oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-118">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="f03d2-119">Bunlardan biri varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="f03d2-119">One is the default namespace.</span></span> <span data-ttu-id="f03d2-120">Diğeri öneki olan bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="f03d2-120">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="f03d2-121">Ad alanı özniteliklerini kök öğesine ekleyerek, ad alanları varsayılan ad alanı olacak şekilde serileştirilir `http://www.adventure-works.com` ve `www.fourthcoffee.com` bir "FC" önekiyle serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-121">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="f03d2-122">Varsayılan ad alanını bildiren bir öznitelik oluşturmak için, ad alanı olmadan "xmlns" adlı bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="f03d2-122">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="f03d2-123">Özniteliğin değeri varsayılan ad alanı URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="f03d2-123">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="f03d2-124">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03d2-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f03d2-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03d2-125">Example</span></span>  
 <span data-ttu-id="f03d2-126">Aşağıdaki örnek, ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f03d2-126">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="f03d2-127">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03d2-127">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="f03d2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="f03d2-128">Example</span></span>  
 <span data-ttu-id="f03d2-129">Aynı sonucu gerçekleştirmenin başka bir yolu da bir nesne bildirmek ve oluşturmak yerine genişletilmiş adlar kullanmaktır <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="f03d2-129">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="f03d2-130">Bu yaklaşımın performans etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="f03d2-130">This approach has performance implications.</span></span> <span data-ttu-id="f03d2-131">Genişletilmiş bir adı içeren bir dizeyi her geçirdiğinizde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adı ayrıştırmalıdır, atomlanmış ad alanını bulun ve atomlanmış adı bulun.</span><span class="sxs-lookup"><span data-stu-id="f03d2-131">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="f03d2-132">Bu işlem CPU süresini alır.</span><span class="sxs-lookup"><span data-stu-id="f03d2-132">This process takes CPU time.</span></span> <span data-ttu-id="f03d2-133">Performans önemliyse, açıkça bir nesne bildirmek ve kullanmak isteyebilirsiniz <xref:System.Xml.Linq.XNamespace> .</span><span class="sxs-lookup"><span data-stu-id="f03d2-133">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="f03d2-134">Performans önemli bir sorun ise, daha fazla bilgi için bkz. [XName nesnelerinin ön Atomleştirmesi (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="f03d2-134">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="f03d2-135">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03d2-135">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f03d2-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f03d2-136">See also</span></span>

- [<span data-ttu-id="f03d2-137">Ad alanlarına genel bakış (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f03d2-137">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
