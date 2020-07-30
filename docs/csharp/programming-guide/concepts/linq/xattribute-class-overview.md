---
title: XAttribute sınıfına genel bakış (C#)
description: Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir. XAttribute XML özniteliklerini temsil eder. C# ' de LINQ to XML özniteliklerle çalışma hakkında bilgi edinin.
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 8a19de601041bbb20241c959e909483b97bcf797
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302236"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="8f73e-105">XAttribute sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="8f73e-105">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="8f73e-106">Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-106">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="8f73e-107"><xref:System.Xml.Linq.XAttribute>Sınıfı XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8f73e-107">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="8f73e-108">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8f73e-108">Overview</span></span>  
 <span data-ttu-id="8f73e-109">İçindeki özniteliklerle çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , öğelerle çalışmaya benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-109">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="8f73e-110">Oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-110">Their constructors are similar.</span></span> <span data-ttu-id="8f73e-111">Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-111">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="8f73e-112">Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine çok benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="8f73e-112">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="8f73e-113">Öznitelikleri bir öğeye eklenme sırası korunur.</span><span class="sxs-lookup"><span data-stu-id="8f73e-113">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="8f73e-114">Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="8f73e-114">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="8f73e-115">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="8f73e-115">The XAttribute Constructor</span></span>  
 <span data-ttu-id="8f73e-116">Sınıfının aşağıdaki Oluşturucusu, <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanabileceğiniz bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="8f73e-116">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="8f73e-117">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="8f73e-117">Constructor</span></span>|<span data-ttu-id="8f73e-118">Description</span><span class="sxs-lookup"><span data-stu-id="8f73e-118">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="8f73e-119">Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8f73e-119">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="8f73e-120">`name`Bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-120">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="8f73e-121">Özniteliği olan bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="8f73e-121">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="8f73e-122">Aşağıdaki kod, bir özniteliği içeren bir öğe oluşturma ortak görevini gösterir:</span><span class="sxs-lookup"><span data-stu-id="8f73e-122">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="8f73e-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8f73e-123">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="8f73e-124">Özniteliklerin işlevsel olarak oluşturulması</span><span class="sxs-lookup"><span data-stu-id="8f73e-124">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="8f73e-125">Nesneleri oluşturmak <xref:System.Xml.Linq.XAttribute> için aşağıdaki gibi nesneleri satır içinde oluşturabilirsiniz <xref:System.Xml.Linq.XElement> :</span><span class="sxs-lookup"><span data-stu-id="8f73e-125">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="8f73e-126">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8f73e-126">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="8f73e-127">Öznitelikler düğüm değil</span><span class="sxs-lookup"><span data-stu-id="8f73e-127">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="8f73e-128">Öznitelikler ve öğeler arasında bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="8f73e-128">There are some differences between attributes and elements.</span></span> <span data-ttu-id="8f73e-129"><xref:System.Xml.Linq.XAttribute>nesneler XML ağacındaki düğümler değildir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-129"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="8f73e-130">Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-130">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="8f73e-131">Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır.</span><span class="sxs-lookup"><span data-stu-id="8f73e-131">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="8f73e-132"><xref:System.Xml.Linq.XAttribute>Nesneler gerçekte XML ağacında düğümler olmasa da nesnelerle çalışma, <xref:System.Xml.Linq.XAttribute> nesnelerle çalışmaya çok benzer <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="8f73e-132">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="8f73e-133">Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-133">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="8f73e-134">Birçok geliştirici bu ayrım ile ilgilenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="8f73e-134">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f73e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f73e-135">See also</span></span>

- [<span data-ttu-id="8f73e-136">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="8f73e-136">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
