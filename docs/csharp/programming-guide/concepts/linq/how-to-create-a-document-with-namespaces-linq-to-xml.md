---
title: "Nasıl yapılır: ad alanları (C#) (LINQ-XML) ile bir belge oluşturun"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d913cdf8b9018aa2bf91fd5a05b823e90ba63df2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="dbc5b-102">Nasıl yapılır: ad alanları (C#) (LINQ-XML) ile bir belge oluşturun</span><span class="sxs-lookup"><span data-stu-id="dbc5b-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="dbc5b-103">Bu konuda, ad alanları ile belgeleri oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc5b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbc5b-104">Example</span></span>  
 <span data-ttu-id="dbc5b-105">Bir öğenin veya bir ad alanındaki bir öznitelik oluşturmak için önce bildirme ve başlatma bir <xref:System.Xml.Linq.XNamespace> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="dbc5b-106">Toplama işleci aşırı sonra yerel adıyla bir dize olarak ifade edilen ad birleştirmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="dbc5b-107">Aşağıdaki örnek bir belge içeren bir ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="dbc5b-108">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir varsayılan ad alanı bu belgeyle serileştirir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbc5b-109">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbc5b-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="dbc5b-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbc5b-110">Example</span></span>  
 <span data-ttu-id="dbc5b-111">Aşağıdaki örnek bir belge içeren bir ad oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="dbc5b-112">Ayrıca, bir ad alanı öneki ad bildiren bir öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="dbc5b-113">Bir ad alanı öneki bildiren bir öznitelik oluşturmak için burada özniteliğin adını ad alanı öneki ve bu adı kullanılıyor bir öznitelik oluşturun <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="dbc5b-114">Bu öznitelik ad alanı URI değeri.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbc5b-115">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbc5b-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="dbc5b-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbc5b-116">Example</span></span>  
 <span data-ttu-id="dbc5b-117">Aşağıdaki örnekte, iki ad alanı içeren bir belge oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="dbc5b-118">Varsayılan ad alanını biridir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-118">One is the default namespace.</span></span> <span data-ttu-id="dbc5b-119">Başka bir ad alanı öneki ' dir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="dbc5b-120">Ad alanları kök öğesinin ad alanı öznitelikleri dahil ederek, böylece http://www.adventure-works.com varsayılan ad alanıdır ve www.fourthcoffee.com "fc" önekiyle seri serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-120">By including namespace attributes in the root element, the namespaces are serialized so that http://www.adventure-works.com is the default namespace, and www.fourthcoffee.com is serialized with a prefix of "fc".</span></span> <span data-ttu-id="dbc5b-121">Bir varsayılan ad alanını tanımlayan bir öznitelik oluşturmak için bir öznitelik adı "xmlns", bir ad olmadan ile oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="dbc5b-122">Varsayılan ad alanı URI'si öznitelik değeri.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="dbc5b-123">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbc5b-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="dbc5b-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbc5b-124">Example</span></span>  
 <span data-ttu-id="dbc5b-125">Aşağıdaki örnek, iki ad alanı, ad alanı öneklerini her ikisi de içeren bir belgeyi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="dbc5b-126">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbc5b-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="dbc5b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbc5b-127">Example</span></span>  
 <span data-ttu-id="dbc5b-128">Genişletilmiş adları bildirme ve oluşturma yerine kullanmak için aynı sonucu gerçekleştirmenin başka bir yolu olan bir <xref:System.Xml.Linq.XNamespace> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="dbc5b-129">Bu yaklaşım performans etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-129">This approach has performance implications.</span></span> <span data-ttu-id="dbc5b-130">Geçirdiğiniz bir dize, her zaman genişletilmiş bir adı olan içeren [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gerekir adı ayrıştırılamıyor atomized ad alanını bulun ve atomized adı bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="dbc5b-131">Bu işlem CPU saat sürer.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-131">This process takes CPU time.</span></span> <span data-ttu-id="dbc5b-132">Performans önemliyse, bildirme ve kullanma isteyebilirsiniz bir <xref:System.Xml.Linq.XNamespace> açıkça nesne.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="dbc5b-133">Performans önemli bir sorun olup olmadığını [öncesi Atomization XName nesnelerin (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) daha fazla bilgi için</span><span class="sxs-lookup"><span data-stu-id="dbc5b-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="dbc5b-134">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="dbc5b-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dbc5b-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbc5b-135">See Also</span></span>  
 [<span data-ttu-id="dbc5b-136">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="dbc5b-136">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)
