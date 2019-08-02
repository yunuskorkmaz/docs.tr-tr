---
title: 'Nasıl yapılır: Ad alanları (C#) Ile bir belge oluşturma (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 9b9e81a131d4e17ce2d87dd3f511ed66e370d884
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710002"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="95da0-102">Nasıl yapılır: Ad alanları (C#) Ile bir belge oluşturma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="95da0-102">How to: Create a Document with Namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="95da0-103">Bu konu başlığı altında, ad alanları ile belgelerin nasıl oluşturulacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="95da0-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95da0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="95da0-104">Example</span></span>  
 <span data-ttu-id="95da0-105">Bir ad alanında olan bir öğe veya öznitelik oluşturmak için, önce bir <xref:System.Xml.Linq.XNamespace> nesne bildirir ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="95da0-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="95da0-106">Daha sonra, ad alanını bir dize olarak ifade edilen yerel adla birleştirmek için ek işleç aşırı yüklemesi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95da0-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="95da0-107">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95da0-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="95da0-108">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bu belgeyi varsayılan bir ad alanıyla seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="95da0-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="95da0-109">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95da0-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="95da0-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="95da0-110">Example</span></span>  
 <span data-ttu-id="95da0-111">Aşağıdaki örnek, bir ad alanı olan bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95da0-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="95da0-112">Ayrıca ad alanı öneki olan ad alanını bildiren bir öznitelik oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95da0-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="95da0-113">Önekiyle bir ad alanı bildiren bir öznitelik oluşturmak için, özniteliğin adının ad alanı öneki olduğu ve bu ad <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanında olduğu bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="95da0-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="95da0-114">Bu özniteliğin değeri, ad alanının URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="95da0-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="95da0-115">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95da0-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="95da0-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="95da0-116">Example</span></span>  
 <span data-ttu-id="95da0-117">Aşağıdaki örnek, iki ad alanı içeren bir belge oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="95da0-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="95da0-118">Bunlardan biri varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="95da0-118">One is the default namespace.</span></span> <span data-ttu-id="95da0-119">Diğeri öneki olan bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="95da0-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="95da0-120">Ad alanı özniteliklerini kök öğesine ekleyerek, ad alanları varsayılan ad alanı olacak şekilde `http://www.adventure-works.com` serileştirilir ve `www.fourthcoffee.com` bir "FC" önekiyle serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="95da0-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="95da0-121">Varsayılan ad alanını bildiren bir öznitelik oluşturmak için, ad alanı olmadan "xmlns" adlı bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="95da0-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="95da0-122">Özniteliğin değeri varsayılan ad alanı URI 'sidir.</span><span class="sxs-lookup"><span data-stu-id="95da0-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="95da0-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95da0-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="95da0-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="95da0-124">Example</span></span>  
 <span data-ttu-id="95da0-125">Aşağıdaki örnek, ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="95da0-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="95da0-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95da0-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="95da0-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="95da0-127">Example</span></span>  
 <span data-ttu-id="95da0-128">Aynı sonucu gerçekleştirmenin başka bir yolu da bir <xref:System.Xml.Linq.XNamespace> nesne bildirmek ve oluşturmak yerine genişletilmiş adlar kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="95da0-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="95da0-129">Bu yaklaşımın performans etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="95da0-129">This approach has performance implications.</span></span> <span data-ttu-id="95da0-130">Genişletilmiş bir adı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]içeren bir dizeyi her geçirdiğinizde, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adı ayrıştırmalıdır, atomlanmış ad alanını bulun ve atomlanmış adı bulun.</span><span class="sxs-lookup"><span data-stu-id="95da0-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="95da0-131">Bu işlem CPU süresini alır.</span><span class="sxs-lookup"><span data-stu-id="95da0-131">This process takes CPU time.</span></span> <span data-ttu-id="95da0-132">Performans önemliyse, açıkça bir <xref:System.Xml.Linq.XNamespace> nesne bildirmek ve kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95da0-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="95da0-133">Performans önemli bir sorun ise, daha fazla bilgi için bkz. [XName nesnelerinin ön atomitei (C#LINQ to XML) ()](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md)</span><span class="sxs-lookup"><span data-stu-id="95da0-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="95da0-134">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="95da0-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95da0-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95da0-135">See also</span></span>

- [<span data-ttu-id="95da0-136">Ad alanlarına genel bakış (LINQ to XMLC#) ()</span><span class="sxs-lookup"><span data-stu-id="95da0-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
