---
title: XAttribute sınıfına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 08b8ebf31a39325c98023d4bb333f8e06bbdeb3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646971"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="d8342-102">XAttribute sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8342-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="d8342-103">Öznitelikleri bir öğesiyle ilişkilendirilmiş olan ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="d8342-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="d8342-104"><xref:System.Xml.Linq.XAttribute> Sınıfı, XML öznitelikleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d8342-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d8342-105">Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d8342-105">Overview</span></span>  
 <span data-ttu-id="d8342-106">Öznitelikleri ile çalışma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] öğeleriyle çalışma için benzer.</span><span class="sxs-lookup"><span data-stu-id="d8342-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="d8342-107">Kendi oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d8342-107">Their constructors are similar.</span></span> <span data-ttu-id="d8342-108">Bunları koleksiyonlarını almak için kullandığınız yöntemleri benzerdir.</span><span class="sxs-lookup"><span data-stu-id="d8342-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="d8342-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] özniteliklerin bir koleksiyonu için sorgu ifadesi çok benzer şekilde görünen bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu öğe koleksiyonunu ifadesi.</span><span class="sxs-lookup"><span data-stu-id="d8342-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="d8342-110">Öznitelikleri bir öğe olarak eklenen sipariş korunur.</span><span class="sxs-lookup"><span data-stu-id="d8342-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="d8342-111">Özniteliklerinden yinelemek, diğer bir deyişle, bunları bunlar eklenen sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="d8342-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="d8342-112">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="d8342-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="d8342-113">Aşağıdaki oluşturucusunun <xref:System.Xml.Linq.XAttribute> en yaygın olarak kullanacağınız bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="d8342-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="d8342-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="d8342-114">Constructor</span></span>|<span data-ttu-id="d8342-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8342-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="d8342-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="d8342-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="d8342-117">`name` Bağımsız değişkeni; özniteliğin adını belirtir `content` öznitelik içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8342-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="d8342-118">Bir öğesi olan bir öznitelik oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8342-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="d8342-119">Aşağıdaki kod, Visual Basic'te XML değişmez değerleri kullanarak bir öznitelik içeren bir öğeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="d8342-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="d8342-120">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="d8342-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="d8342-121">İşlev öznitelikleri yapımı</span><span class="sxs-lookup"><span data-stu-id="d8342-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="d8342-122">Oluşturabileceğiniz <xref:System.Xml.Linq.XAttribute> nesneleri satır içi yapımı ile <xref:System.Xml.Linq.XElement> nesneleri, aşağıdaki gibi:</span><span class="sxs-lookup"><span data-stu-id="d8342-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="d8342-123">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="d8342-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="d8342-124">Öznitelikleri düğümleri olmayan</span><span class="sxs-lookup"><span data-stu-id="d8342-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="d8342-125">Öznitelikler ve öğeler arasındaki bazı farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="d8342-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="d8342-126"><xref:System.Xml.Linq.XAttribute> nesneler düğüm XML ağacında değildir.</span><span class="sxs-lookup"><span data-stu-id="d8342-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="d8342-127">Bunlar bir XML öğesi ile ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="d8342-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="d8342-128">Belge nesne modeli (DOM) aksine bu daha yakından XML yapısını yansıtır.</span><span class="sxs-lookup"><span data-stu-id="d8342-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="d8342-129">Ancak <xref:System.Xml.Linq.XAttribute> nesneleri gerçekten çalışmaya XML Ağaçtaki düğümler olmayan <xref:System.Xml.Linq.XAttribute> nesneleri ile çalışmaya çok benzer <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d8342-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="d8342-130">Bu ayrım, yalnızca XML ağaçlar olan düğüm düzeyinde çalışır kod yazma geliştiriciler öncelikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d8342-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="d8342-131">Geliştiricilerin çoğu Bu ayrım ile ilgilenen olmaz.</span><span class="sxs-lookup"><span data-stu-id="d8342-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8342-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8342-132">See Also</span></span>  
 [<span data-ttu-id="d8342-133">LINQ-XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8342-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
