---
title: XAttribute Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: ceafe5478e41fb4c2038fd9300ef7b1ee6cb8411
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636659"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="17845-102">XAttribute sınıfına genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17845-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="17845-103">Öznitelikler, bir öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="17845-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="17845-104"><xref:System.Xml.Linq.XAttribute> sınıfı XML özniteliklerini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="17845-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="17845-105">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="17845-105">Overview</span></span>  
 <span data-ttu-id="17845-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] özniteliklerle çalışma, öğelerle çalışmaya benzer.</span><span class="sxs-lookup"><span data-stu-id="17845-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="17845-107">Oluşturucular benzerdir.</span><span class="sxs-lookup"><span data-stu-id="17845-107">Their constructors are similar.</span></span> <span data-ttu-id="17845-108">Bunların koleksiyonlarını almak için kullandığınız yöntemler benzerdir.</span><span class="sxs-lookup"><span data-stu-id="17845-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="17845-109">Öznitelik koleksiyonu için LINQ sorgu ifadesi bir öğe koleksiyonu için LINQ sorgu ifadesine çok benzer şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="17845-109">A LINQ query expression for a collection of attributes looks very similar to a LINQ query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="17845-110">Öznitelikleri bir öğeye eklenme sırası korunur.</span><span class="sxs-lookup"><span data-stu-id="17845-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="17845-111">Diğer bir deyişle, özniteliklerde yineleme yaparken, bunları eklendiği sırayla görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="17845-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="17845-112">XAttribute Oluşturucusu</span><span class="sxs-lookup"><span data-stu-id="17845-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="17845-113"><xref:System.Xml.Linq.XAttribute> sınıfının aşağıdaki Oluşturucusu, en sık kullandığınız bir sınıftır:</span><span class="sxs-lookup"><span data-stu-id="17845-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="17845-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="17845-114">Constructor</span></span>|<span data-ttu-id="17845-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17845-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="17845-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="17845-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="17845-117">`name` bağımsız değişkeni özniteliğin adını belirtir; `content` özniteliğin içeriğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="17845-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="17845-118">Özniteliği olan bir öğe oluşturma</span><span class="sxs-lookup"><span data-stu-id="17845-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="17845-119">Aşağıdaki kod, Visual Basic XML sabit değerlerini kullanan bir özniteliği içeren bir öğe gösterir:</span><span class="sxs-lookup"><span data-stu-id="17845-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="17845-120">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="17845-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="17845-121">Özniteliklerin işlevsel olarak oluşturulması</span><span class="sxs-lookup"><span data-stu-id="17845-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="17845-122"><xref:System.Xml.Linq.XElement> nesnelerinin yapımını aşağıdaki gibi <xref:System.Xml.Linq.XAttribute> nesneleri satır içinde oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17845-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="17845-123">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="17845-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="17845-124">Öznitelikler düğüm değil</span><span class="sxs-lookup"><span data-stu-id="17845-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="17845-125">Öznitelikler ve öğeler arasında bazı farklılıklar vardır.</span><span class="sxs-lookup"><span data-stu-id="17845-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="17845-126"><xref:System.Xml.Linq.XAttribute> nesneler XML ağacındaki düğümler değildir.</span><span class="sxs-lookup"><span data-stu-id="17845-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="17845-127">Bunlar bir XML öğesiyle ilişkili ad/değer çiftleridir.</span><span class="sxs-lookup"><span data-stu-id="17845-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="17845-128">Belge Nesne Modeli (DOM) aksine bu, XML yapısını daha yakından yansıtır.</span><span class="sxs-lookup"><span data-stu-id="17845-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="17845-129"><xref:System.Xml.Linq.XAttribute> nesneler gerçekten XML ağacında düğümler olmasa da, <xref:System.Xml.Linq.XAttribute> nesneleriyle çalışma <xref:System.Xml.Linq.XElement> nesneleriyle çalışmaya çok benzer.</span><span class="sxs-lookup"><span data-stu-id="17845-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="17845-130">Bu ayrım, birincil olarak yalnızca düğüm düzeyindeki XML ağaçları ile çalışan kod yazan geliştiriciler için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="17845-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="17845-131">Birçok geliştirici bu ayrım ile ilgilenmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="17845-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17845-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17845-132">See also</span></span>

- [<span data-ttu-id="17845-133">LINQ to XML programlamaya genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17845-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
