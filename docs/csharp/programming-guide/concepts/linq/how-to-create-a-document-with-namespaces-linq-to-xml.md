---
title: Ad alanları (C#) (LINQ - XML) içeren bir belge oluşturma
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141327"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="ef261-102">Ad alanları (C#) (LINQ - XML) içeren bir belge oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef261-102">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="ef261-103">Bu konu, ad boşlukları içeren belgelerin nasıl oluşturulacak olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef261-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef261-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef261-104">Example</span></span>  
 <span data-ttu-id="ef261-105">Ad alanında bulunan bir öğe veya öznitelik oluşturmak için önce bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirir ve baş harfe bildirirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef261-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="ef261-106">Daha sonra ad alanını dize olarak ifade edilen yerel adla birleştirmek için ekleme işleci aşırı yüklenmesini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="ef261-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="ef261-107">Aşağıdaki örnek, tek bir ad alanına sahip bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef261-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="ef261-108">Varsayılan olarak, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] varsayılan ad alanı ile bu belgeyi serihale eder.</span><span class="sxs-lookup"><span data-stu-id="ef261-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="ef261-109">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef261-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef261-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef261-110">Example</span></span>  
 <span data-ttu-id="ef261-111">Aşağıdaki örnek, tek bir ad alanına sahip bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef261-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="ef261-112">Ayrıca, ad alanı önekiyle ad alanını bildiren bir öznitelik de oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef261-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="ef261-113">Önek ile bir ad alanı bildiren bir öznitelik oluşturmak için, öznitelik adı ad alanı önek ve bu ad <xref:System.Xml.Linq.XNamespace.Xmlns%2A> ad alanı içinde olduğu bir öznitelik oluşturun.</span><span class="sxs-lookup"><span data-stu-id="ef261-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="ef261-114">Bu özniteliğin değeri ad alanının URI'sidir.</span><span class="sxs-lookup"><span data-stu-id="ef261-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="ef261-115">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef261-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef261-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef261-116">Example</span></span>  
 <span data-ttu-id="ef261-117">Aşağıdaki örnekte, iki ad alanı içeren bir belge nin oluşturulması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef261-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="ef261-118">Bunlardan biri varsayılan ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="ef261-118">One is the default namespace.</span></span> <span data-ttu-id="ef261-119">Başka bir önek ile bir ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="ef261-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="ef261-120">Ad alanı öznitelikleri kök öğesine dahil edilerek, ad `http://www.adventure-works.com` alanları varsayılan ad `www.fourthcoffee.com` alanı olacak şekilde seri hale getirilir ve "fc" önekiyle seri hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="ef261-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="ef261-121">Varsayılan ad alanı bildiren bir öznitelik oluşturmak için, ad alanı olmadan "xmlns" adında bir öznitelik oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="ef261-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="ef261-122">Özniteliğin değeri varsayılan ad alanı URI'dir.</span><span class="sxs-lookup"><span data-stu-id="ef261-122">The value of the attribute is the default namespace URI.</span></span>  
  
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
  
 <span data-ttu-id="ef261-123">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef261-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef261-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef261-124">Example</span></span>  
 <span data-ttu-id="ef261-125">Aşağıdaki örnek, her ikisi de ad alanı önekleri ile iki ad alanı içeren bir belge oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ef261-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
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
  
 <span data-ttu-id="ef261-126">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef261-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="ef261-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef261-127">Example</span></span>  
 <span data-ttu-id="ef261-128">Aynı sonucu gerçekleştirmenin başka bir yolu da, bir <xref:System.Xml.Linq.XNamespace> nesneyi bildirmek ve oluşturmak yerine genişletilmiş adları kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ef261-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="ef261-129">Bu yaklaşımın performans etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="ef261-129">This approach has performance implications.</span></span> <span data-ttu-id="ef261-130">Genişletilmiş bir ad içeren bir dize [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] geçmek her zaman , adını ayrıştırmak gerekir, atomize ad alanı bulmak ve atomize adı bulmak.</span><span class="sxs-lookup"><span data-stu-id="ef261-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="ef261-131">Bu işlem CPU zaman alır.</span><span class="sxs-lookup"><span data-stu-id="ef261-131">This process takes CPU time.</span></span> <span data-ttu-id="ef261-132">Performans önemliyse, bir <xref:System.Xml.Linq.XNamespace> nesneyi açıkça beyan etmek ve kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef261-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="ef261-133">Performans önemli bir konuysa, daha fazla bilgi için [XName Nesnelerinin (LINQ-XML) (C#) Ön AtomizeLeştirilmesi'ne](./pre-atomization-of-xname-objects-linq-to-xml.md) bakın</span><span class="sxs-lookup"><span data-stu-id="ef261-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="ef261-134">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ef261-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef261-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef261-135">See also</span></span>

- [<span data-ttu-id="ef261-136">İsim Alanlarına Genel Bakış (LINQ - XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ef261-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
