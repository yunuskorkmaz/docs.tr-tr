---
title: 'Nasıl yapılır: Ad alanları ile belge oluşturma (C#) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: c64d23e18091ca06a5f345fc603231f442ad849c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485872"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="222f6-102">Nasıl yapılır: Ad alanları ile belge oluşturma (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="222f6-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="222f6-103">Bu konuda, ad alanları ile belge oluşturma işlemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="222f6-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="222f6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="222f6-104">Example</span></span>  
 <span data-ttu-id="222f6-105">Bir öğe veya bir ad alanında bir öznitelik oluşturmak için önce bildirmek ve başlatmak bir <xref:System.Xml.Linq.XNamespace> nesne.</span><span class="sxs-lookup"><span data-stu-id="222f6-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="222f6-106">Bir dize olarak ifade edilen yerel ada sahip ad alanı birleştirmek için Toplama işleci aşırı yüklemesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="222f6-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="222f6-107">Aşağıdaki örnek, bir ad alanı ile bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="222f6-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="222f6-108">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] varsayılan ad alanı bu belgeyle serileştirir.</span><span class="sxs-lookup"><span data-stu-id="222f6-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="222f6-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222f6-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="222f6-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="222f6-110">Example</span></span>  
 <span data-ttu-id="222f6-111">Aşağıdaki örnek, bir ad alanı ile bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="222f6-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="222f6-112">Ayrıca, ad alanı bir ad alanı öneki ile bildiren bir öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="222f6-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="222f6-113">Bir ad alanı öneki bildiren bir öznitelik oluşturmak için burada özniteliğinin adı ad alanı öneki ve bu ad bulunduğu bir öznitelik oluşturun. <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="222f6-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="222f6-114">Bu özniteliğin değeri ad alanı URI ' dir.</span><span class="sxs-lookup"><span data-stu-id="222f6-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="222f6-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222f6-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="222f6-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="222f6-116">Example</span></span>  
 <span data-ttu-id="222f6-117">Aşağıdaki örnek, iki ad alanları içeren bir belge oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="222f6-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="222f6-118">Varsayılan ad alanı biridir.</span><span class="sxs-lookup"><span data-stu-id="222f6-118">One is the default namespace.</span></span> <span data-ttu-id="222f6-119">Başka bir ad alanı öneki ' dir.</span><span class="sxs-lookup"><span data-stu-id="222f6-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="222f6-120">Kök öğesinde ad alanı öznitelikleri dahil ederek, ad alanlarını serileştirilme şeklini böylece `http://www.adventure-works.com` varsayılan ad alanı ve `www.fourthcoffee.com` "fc" öneki ile seri hale.</span><span class="sxs-lookup"><span data-stu-id="222f6-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="222f6-121">Varsayılan ad alanı bildiren bir öznitelik oluşturmak için adı "xmlns", ad alanı olmayan bir öznitelik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="222f6-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="222f6-122">Varsayılan ad alanı URI özniteliğinin değeridir.</span><span class="sxs-lookup"><span data-stu-id="222f6-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="222f6-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222f6-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="222f6-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="222f6-124">Example</span></span>  
 <span data-ttu-id="222f6-125">Aşağıdaki örnek iki ad ad alanı öneklerini her ikisini birden içeren bir belge oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="222f6-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="222f6-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222f6-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="222f6-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="222f6-127">Example</span></span>  
 <span data-ttu-id="222f6-128">Genişletilmiş adlarını bildirme ve oluşturma yerine kullanılacak aynı sonuca ulaşmak için başka bir yolu olan bir <xref:System.Xml.Linq.XNamespace> nesne.</span><span class="sxs-lookup"><span data-stu-id="222f6-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="222f6-129">Bu yaklaşım, performansı etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="222f6-129">This approach has performance implications.</span></span> <span data-ttu-id="222f6-130">Geçirdiğiniz bir dize, her zaman genişletilmiş bir adı içeren [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gerekir adı ayrıştırmak parçalara ayrılmış ad alanı bulmak ve parçalara ayrılmış adı bulun.</span><span class="sxs-lookup"><span data-stu-id="222f6-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="222f6-131">Bu işlemin CPU saat sürer.</span><span class="sxs-lookup"><span data-stu-id="222f6-131">This process takes CPU time.</span></span> <span data-ttu-id="222f6-132">Performans önemliyse bildirme ve kullanma isteyebileceğiniz bir <xref:System.Xml.Linq.XNamespace> açıkça nesne.</span><span class="sxs-lookup"><span data-stu-id="222f6-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="222f6-133">Performans önemli bir sorun olup olmadığını, [parçalara ayırma öncesi XName nesnelerin (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) daha fazla bilgi için</span><span class="sxs-lookup"><span data-stu-id="222f6-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="222f6-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="222f6-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="222f6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="222f6-135">See also</span></span>

- [<span data-ttu-id="222f6-136">XML ad alanları (C#) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="222f6-136">Working with XML Namespaces (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md)
