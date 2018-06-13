---
title: XAttribute sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: e0020a8cd8841ef9a35781b534c82db5e15c257f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33324424"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="c79a2-102">XAttribute sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="c79a2-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="c79a2-103">Öznitelikleri bir öğesiyle ilişkilendirilmiş olan ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="c79a2-104"><xref:System.Xml.Linq.XAttribute> Sınıfı, XML öznitelikleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c79a2-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c79a2-105">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c79a2-105">Overview</span></span>  
 <span data-ttu-id="c79a2-106">Öznitelikleri ile çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleriyle çalışma için benzer.</span><span class="sxs-lookup"><span data-stu-id="c79a2-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="c79a2-107">Kendi oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-107">Their constructors are similar.</span></span> <span data-ttu-id="c79a2-108">Bunları koleksiyonlarını almak için kullandığınız yöntemleri benzerdir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="c79a2-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özniteliklerin bir koleksiyonu için sorgu ifadesi çok benzer şekilde görünen bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu öğe koleksiyonunu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="c79a2-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="c79a2-110">Öznitelikleri bir öğe olarak eklenen sipariş korunur.</span><span class="sxs-lookup"><span data-stu-id="c79a2-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="c79a2-111">Özniteliklerinden yinelemek, diğer bir deyişle, bunları bunlar eklenen sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="c79a2-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="c79a2-112">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="c79a2-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="c79a2-113">Aşağıdaki oluşturucusunun <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanacağınız bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="c79a2-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="c79a2-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="c79a2-114">Constructor</span></span>|<span data-ttu-id="c79a2-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c79a2-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="c79a2-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="c79a2-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="c79a2-117">`name` Bağımsız değişkeni; özniteliğin adını belirtir `content` öznitelik içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="c79a2-118">Bir öğesi olan bir öznitelik oluşturma</span><span class="sxs-lookup"><span data-stu-id="c79a2-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="c79a2-119">Aşağıdaki kod bir öznitelik içeren bir öğeyi oluşturma görevinin gösterir:</span><span class="sxs-lookup"><span data-stu-id="c79a2-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="c79a2-120">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c79a2-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="c79a2-121">İşlev öznitelikleri yapımı</span><span class="sxs-lookup"><span data-stu-id="c79a2-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="c79a2-122">Oluşturabileceğiniz <xref:System.Xml.Linq.XAttribute> nesneleri satır içi yapımı ile <xref:System.Xml.Linq.XElement> nesneleri, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="c79a2-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="c79a2-123">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="c79a2-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="c79a2-124">Öznitelikleri düğümleri olmayan</span><span class="sxs-lookup"><span data-stu-id="c79a2-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="c79a2-125">Öznitelikler ve öğeler arasındaki bazı farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="c79a2-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="c79a2-126"><xref:System.Xml.Linq.XAttribute> nesneler düğüm XML ağacında değildir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="c79a2-127">Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="c79a2-128">Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="c79a2-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="c79a2-129">Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten çalışmaya XML Ağaçtaki düğümler olmayan <xref:System.Xml.Linq.XAttribute> nesneleri ile çalışmaya çok benzer <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c79a2-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="c79a2-130">Bu ayrım, yalnızca XML ağaçlar olan düğüm düzeyinde çalışır kod yazma geliştiriciler öncelikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c79a2-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="c79a2-131">Geliştiricilerin çoğu Bu ayrım ile ilgilenen olmaz.</span><span class="sxs-lookup"><span data-stu-id="c79a2-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79a2-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c79a2-132">See Also</span></span>  
 [<span data-ttu-id="c79a2-133">LINQ-XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="c79a2-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
