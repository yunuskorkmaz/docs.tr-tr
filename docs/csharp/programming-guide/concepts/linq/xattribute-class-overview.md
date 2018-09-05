---
title: XAttribute sınıfına genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: 5a630f24-f9ad-400e-831e-c14ebfc9e142
ms.openlocfilehash: 5619a8442fde9f4e8f612f213bde16c86ba00115
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529080"
---
# <a name="xattribute-class-overview-c"></a><span data-ttu-id="b1ff5-102">XAttribute sınıfına genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b1ff5-102">XAttribute Class Overview (C#)</span></span>
<span data-ttu-id="b1ff5-103">Öznitelikleri bir öğe ile ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="b1ff5-104"><xref:System.Xml.Linq.XAttribute> Sınıfı için XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="b1ff5-105">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1ff5-105">Overview</span></span>  
 <span data-ttu-id="b1ff5-106">Öznitelikleri ile çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleri ile çalışmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="b1ff5-107">Oluşturucuları benzerdir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-107">Their constructors are similar.</span></span> <span data-ttu-id="b1ff5-108">Bunları koleksiyonlarını almak için kullandığınız yöntemleri benzerdir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="b1ff5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özniteliklerin bir koleksiyonu için sorgu ifadesi çok benzer görünür bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu ifadesi öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="b1ff5-110">Öznitelikleri bir öğe için eklenen sırasını korunur.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="b1ff5-111">Öznitelikleri yineleme yaptığınızda, diğer bir deyişle, bunları eklendikleri sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="b1ff5-112">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="b1ff5-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="b1ff5-113">Aşağıdaki oluşturucusuna <xref:System.Xml.Linq.XAttribute> sınıfı, en sık kullanacağınız bir:</span><span class="sxs-lookup"><span data-stu-id="b1ff5-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="b1ff5-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="b1ff5-114">Constructor</span></span>|<span data-ttu-id="b1ff5-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b1ff5-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="b1ff5-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="b1ff5-117">`name` Bağımsız değişkeni belirtir; öznitelik adı `content` öznitelik içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="b1ff5-118">Bir öznitelik bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1ff5-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="b1ff5-119">Aşağıdaki kod, bir öznitelik içeren bir öğeyi oluşturma görevinin gösterir:</span><span class="sxs-lookup"><span data-stu-id="b1ff5-119">The following code shows the common task of creating an element that contains an attribute:</span></span>  
  
```csharp  
XElement phone = new XElement("Phone",  
    new XAttribute("Type", "Home"),  
    "555-555-5555");  
Console.WriteLine(phone);  
```  
  
 <span data-ttu-id="b1ff5-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1ff5-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="b1ff5-121">İşlev öznitelikleri yapımı</span><span class="sxs-lookup"><span data-stu-id="b1ff5-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="b1ff5-122">Oluşturulabilir <xref:System.Xml.Linq.XAttribute> nesneler satır içi oluşumu ile <xref:System.Xml.Linq.XElement> gibi nesneler:</span><span class="sxs-lookup"><span data-stu-id="b1ff5-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="b1ff5-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="b1ff5-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="b1ff5-124">Öznitelik düğümleri olmayan</span><span class="sxs-lookup"><span data-stu-id="b1ff5-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="b1ff5-125">Öznitelikler ve öğeler arasında bazı farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="b1ff5-126"><xref:System.Xml.Linq.XAttribute> nesneler XML Ağaçtaki düğümler değildir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="b1ff5-127">Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="b1ff5-128">Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="b1ff5-129">Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten düğümleri ile çalışma XML ağacında olmayan <xref:System.Xml.Linq.XAttribute> nesneler ile çalışma için çok benzer <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="b1ff5-130">Bu ayrım, yalnızca XML ağaçları düğüm düzeyinde çalışan kod yazma geliştiriciler öncelikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="b1ff5-131">Bu ayrım ile ilgili birçok geliştiricinin olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ff5-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ff5-132">See Also</span></span>

- [<span data-ttu-id="b1ff5-133">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="b1ff5-133">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
