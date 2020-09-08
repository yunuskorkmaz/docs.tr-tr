---
title: XAttribute sınıfına genel bakış
description: XAttribute sınıfı, XML özniteliklerini temsil eder. LINQ to XML özniteliklerle çalışma, öğelerle çalışmaya benzer.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: deab6e8dd9695a442cd362401aec8b68cdbf218f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552944"
---
# <a name="xattribute-class-overview"></a><span data-ttu-id="62eec-104">XAttribute sınıfına genel bakış</span><span class="sxs-lookup"><span data-stu-id="62eec-104">XAttribute class overview</span></span>

<span data-ttu-id="62eec-105">Öznitelikler, bir öğesiyle ilişkili ad-değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="62eec-105">Attributes are name-value pairs that are associated with an element.</span></span> <span data-ttu-id="62eec-106"><xref:System.Xml.Linq.XAttribute>Sınıfı XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="62eec-106">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>

<span data-ttu-id="62eec-107">LINQ to XML özniteliklerle çalışma, öğelerle çalışmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="62eec-107">Working with attributes in LINQ to XML is similar to working with elements.</span></span> <span data-ttu-id="62eec-108">Oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="62eec-108">Their constructors are similar.</span></span> <span data-ttu-id="62eec-109">Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir.</span><span class="sxs-lookup"><span data-stu-id="62eec-109">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="62eec-110">Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine benzer.</span><span class="sxs-lookup"><span data-stu-id="62eec-110">A LINQ query expression for a collection of attributes looks similar to a LINQ query expression for a collection of elements.</span></span>

<span data-ttu-id="62eec-111">Öznitelikleri bir öğeye eklenme sırası korunur.</span><span class="sxs-lookup"><span data-stu-id="62eec-111">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="62eec-112">Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="62eec-112">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>

## <a name="the-xattribute-constructor"></a><span data-ttu-id="62eec-113">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="62eec-113">The XAttribute constructor</span></span>

<span data-ttu-id="62eec-114">Sınıfının aşağıdaki Oluşturucusu, <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanabileceğiniz bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="62eec-114">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you'll most commonly use:</span></span>

|<span data-ttu-id="62eec-115">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="62eec-115">Constructor</span></span>|<span data-ttu-id="62eec-116">Description</span><span class="sxs-lookup"><span data-stu-id="62eec-116">Description</span></span>|
|-----------------|-----------------|
|`XAttribute(XName name, object content)`|<span data-ttu-id="62eec-117">Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="62eec-117">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="62eec-118">`name`Bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62eec-118">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|

## <a name="example-create-an-element-with-an-attribute"></a><span data-ttu-id="62eec-119">Örnek: özniteliği olan bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="62eec-119">Example: Create an element with an attribute</span></span>

<span data-ttu-id="62eec-120">Aşağıdaki örnek, bir özniteliği içeren bir öğe oluşturma ortak görevini gösterir.</span><span class="sxs-lookup"><span data-stu-id="62eec-120">The following example shows the common task of creating an element that contains an attribute.</span></span>

```csharp
XElement phone = new XElement("Phone",
    new XAttribute("Type", "Home"),
    "555-555-5555");
Console.WriteLine(phone);
```

```vb
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>
Console.WriteLine(phone)
```

<span data-ttu-id="62eec-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="62eec-121">This example produces the following output:</span></span>

```xml
<Phone Type="Home">555-555-5555</Phone>
```

## <a name="example-functional-construction-of-attributes"></a><span data-ttu-id="62eec-122">Örnek: özniteliklerin Işlevsel olarak oluşturulması</span><span class="sxs-lookup"><span data-stu-id="62eec-122">Example: Functional construction of attributes</span></span>

<span data-ttu-id="62eec-123"><xref:System.Xml.Linq.XAttribute>Aşağıdaki örnekte gösterildiği gibi nesneleri oluşturma ile satır içi nesneler oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :</span><span class="sxs-lookup"><span data-stu-id="62eec-123">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as shown in the following example:</span></span>

```csharp
XElement c = new XElement("Customers",
    new XElement("Customer",
        new XElement("Name", "John Doe"),
        new XElement("PhoneNumbers",
            new XElement("Phone",
                new XAttribute("type", "home"),
                "555-555-5555"),
            new XElement("Phone",
                new XAttribute("type", "work"),
                "666-666-6666")
        )
    )
);
Console.WriteLine(c);
```

```vb
Dim c As XElement = _
    <Customers>
        <Customer>
            <Name>John Doe</Name>
            <PhoneNumbers>
                <Phone type="home">555-555-5555</Phone>
                <Phone type="work">666-666-6666</Phone>
            </PhoneNumbers>
        </Customer>
    </Customers>
Console.WriteLine(c)
```

<span data-ttu-id="62eec-124">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="62eec-124">This example produces the following output:</span></span>

```xml
<Customers>
  <Customer>
    <Name>John Doe</Name>
    <PhoneNumbers>
      <Phone type="home">555-555-5555</Phone>
      <Phone type="work">666-666-6666</Phone>
    </PhoneNumbers>
  </Customer>
</Customers>
```

## <a name="attributes-arent-nodes"></a><span data-ttu-id="62eec-125">Öznitelikler düğüm değildir</span><span class="sxs-lookup"><span data-stu-id="62eec-125">Attributes aren't nodes</span></span>

<span data-ttu-id="62eec-126">Öznitelikler ve öğeler arasında bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="62eec-126">There are some differences between attributes and elements.</span></span> <span data-ttu-id="62eec-127"><xref:System.Xml.Linq.XAttribute> nesneler XML ağacında düğüm değildir.</span><span class="sxs-lookup"><span data-stu-id="62eec-127"><xref:System.Xml.Linq.XAttribute> objects aren't nodes in the XML tree.</span></span> <span data-ttu-id="62eec-128">Bunlar bir XML öğesiyle ilişkili ad-değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="62eec-128">They're name-value pairs associated with an XML element.</span></span> <span data-ttu-id="62eec-129">Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır.</span><span class="sxs-lookup"><span data-stu-id="62eec-129">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="62eec-130"><xref:System.Xml.Linq.XAttribute>Nesneler gerçekte XML ağacında düğümler olmasa da nesnelerle çalışma, nesnelerle çalışmaya <xref:System.Xml.Linq.XAttribute> benzer <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="62eec-130">Although <xref:System.Xml.Linq.XAttribute> objects aren't actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="62eec-131">Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="62eec-131">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="62eec-132">Birçok geliştirici bu ayrım ile ilgilenmez.</span><span class="sxs-lookup"><span data-stu-id="62eec-132">Many developers won't be concerned with this distinction.</span></span>

## <a name="see-also"></a><span data-ttu-id="62eec-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62eec-133">See also</span></span>

- [<span data-ttu-id="62eec-134">LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="62eec-134">LINQ to XML overview</span></span>](linq-xml-overview.md)
