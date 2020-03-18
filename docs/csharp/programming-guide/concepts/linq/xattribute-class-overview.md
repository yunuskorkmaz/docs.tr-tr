---
title: XAttribute Sınıf Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 7a806314664c6319fc45cff0dddedbe38027059d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635671"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="938a3-102">XAttribute Sınıf Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="938a3-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="938a3-103">Öznitelikler, bir öğeyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="938a3-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="938a3-104">Sınıf <xref:System.Xml.Linq.XAttribute> XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="938a3-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="938a3-105">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="938a3-105">Overview</span></span>  
 <span data-ttu-id="938a3-106">Öznitelikleri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ile çalışma öğeleri ile çalışmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="938a3-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="938a3-107">Yapıcıları benzer.</span><span class="sxs-lookup"><span data-stu-id="938a3-107">Their constructors are similar.</span></span> <span data-ttu-id="938a3-108">Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir.</span><span class="sxs-lookup"><span data-stu-id="938a3-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="938a3-109">Özniteliklerin bir koleksiyonu için linq sorgu ifadesi, öğeler topluluğu için linq sorgu ifadesine çok benzer görünür.</span><span class="sxs-lookup"><span data-stu-id="938a3-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="938a3-110">Özniteliklerin bir öğeye eklenme sırası korunur.</span><span class="sxs-lookup"><span data-stu-id="938a3-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="938a3-111">Diğer bir deyişle, öznitelikleri doğruladığınızda, onları eklendikleri sırada görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="938a3-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="938a3-112">XAttribute Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="938a3-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="938a3-113"><xref:System.Xml.Linq.XAttribute> Sınıfın aşağıdaki oluşturucusu en sık kullanacağınız şeydir:</span><span class="sxs-lookup"><span data-stu-id="938a3-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="938a3-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="938a3-114">Constructor</span></span>|<span data-ttu-id="938a3-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="938a3-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="938a3-116">Bir <xref:System.Xml.Linq.XAttribute> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="938a3-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="938a3-117">Bağımsız `name` değişken öznitelik adını belirtir; `content` özniteliğin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="938a3-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="938a3-118">Öznitelik ile Bir Öğe Oluşturma</span><span class="sxs-lookup"><span data-stu-id="938a3-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="938a3-119">Aşağıdaki kod, öznitelik içeren bir öğe oluşturma ortak görevi gösterir:</span><span class="sxs-lookup"><span data-stu-id="938a3-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="938a3-120">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="938a3-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="938a3-121">Niteliklerin Fonksiyonel Yapısı</span><span class="sxs-lookup"><span data-stu-id="938a3-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="938a3-122">Aşağıdaki gibi <xref:System.Xml.Linq.XAttribute> nesnelerin yapısı <xref:System.Xml.Linq.XElement> ile sıralı nesneleri oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="938a3-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="938a3-123">Bu örnek, aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="938a3-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="938a3-124">Öznitelikler Düğüm Değildir</span><span class="sxs-lookup"><span data-stu-id="938a3-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="938a3-125">Öznitelikler ve öğeler arasında bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="938a3-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="938a3-126"><xref:System.Xml.Linq.XAttribute>nesneler XML ağacında düğüm değildir.</span><span class="sxs-lookup"><span data-stu-id="938a3-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="938a3-127">Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="938a3-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="938a3-128">Belge Nesnesi Modeli'nin (DOM) aksine, bu xml yapısını daha yakından yansıtır.</span><span class="sxs-lookup"><span data-stu-id="938a3-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="938a3-129">Nesneler <xref:System.Xml.Linq.XAttribute> XML ağacında fiilen düğüm ler olmasa <xref:System.Xml.Linq.XAttribute> da, nesnelerle çalışmak <xref:System.Xml.Linq.XElement> nesnelerle çalışmaya çok benzer.</span><span class="sxs-lookup"><span data-stu-id="938a3-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="938a3-130">Bu ayrım, öncelikle düğüm düzeyinde XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="938a3-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="938a3-131">Birçok geliştirici bu ayrım ile ilgili olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="938a3-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938a3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="938a3-132">See also</span></span>

- [<span data-ttu-id="938a3-133">LINQ - XML Programlamaya Genel Bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="938a3-133">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
