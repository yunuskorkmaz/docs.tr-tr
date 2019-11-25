---
title: XAttribute Sınıfına Genel Bakış
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 00aeeec3f251ecd1d21a313290326b3ba49d63d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349333"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="a1f94-102">XAttribute Class Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f94-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="a1f94-103">Attributes are name/value pairs that are associated with an element.</span><span class="sxs-lookup"><span data-stu-id="a1f94-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="a1f94-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span><span class="sxs-lookup"><span data-stu-id="a1f94-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="a1f94-105">Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a1f94-105">Overview</span></span>  
 <span data-ttu-id="a1f94-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span><span class="sxs-lookup"><span data-stu-id="a1f94-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="a1f94-107">Their constructors are similar.</span><span class="sxs-lookup"><span data-stu-id="a1f94-107">Their constructors are similar.</span></span> <span data-ttu-id="a1f94-108">The methods that you use to retrieve collections of them are similar.</span><span class="sxs-lookup"><span data-stu-id="a1f94-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="a1f94-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span><span class="sxs-lookup"><span data-stu-id="a1f94-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="a1f94-110">The order in which attributes were added to an element is preserved.</span><span class="sxs-lookup"><span data-stu-id="a1f94-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="a1f94-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span><span class="sxs-lookup"><span data-stu-id="a1f94-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="a1f94-112">The XAttribute Constructor</span><span class="sxs-lookup"><span data-stu-id="a1f94-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="a1f94-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span><span class="sxs-lookup"><span data-stu-id="a1f94-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="a1f94-114">Oluşturucu</span><span class="sxs-lookup"><span data-stu-id="a1f94-114">Constructor</span></span>|<span data-ttu-id="a1f94-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1f94-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="a1f94-116">Oluşturur bir <xref:System.Xml.Linq.XAttribute> nesne.</span><span class="sxs-lookup"><span data-stu-id="a1f94-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="a1f94-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span><span class="sxs-lookup"><span data-stu-id="a1f94-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="a1f94-118">Creating an Element with an Attribute</span><span class="sxs-lookup"><span data-stu-id="a1f94-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="a1f94-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a1f94-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="a1f94-120">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="a1f94-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="a1f94-121">Functional Construction of Attributes</span><span class="sxs-lookup"><span data-stu-id="a1f94-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="a1f94-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span><span class="sxs-lookup"><span data-stu-id="a1f94-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
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
  
 <span data-ttu-id="a1f94-123">This example produces the following output:</span><span class="sxs-lookup"><span data-stu-id="a1f94-123">This example produces the following output:</span></span>  
  
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
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="a1f94-124">Attributes Are Not Nodes</span><span class="sxs-lookup"><span data-stu-id="a1f94-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="a1f94-125">There are some differences between attributes and elements.</span><span class="sxs-lookup"><span data-stu-id="a1f94-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="a1f94-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span><span class="sxs-lookup"><span data-stu-id="a1f94-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="a1f94-127">They are name/value pairs associated with an XML element.</span><span class="sxs-lookup"><span data-stu-id="a1f94-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="a1f94-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span><span class="sxs-lookup"><span data-stu-id="a1f94-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="a1f94-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span><span class="sxs-lookup"><span data-stu-id="a1f94-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="a1f94-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span><span class="sxs-lookup"><span data-stu-id="a1f94-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="a1f94-131">Many developers will not be concerned with this distinction.</span><span class="sxs-lookup"><span data-stu-id="a1f94-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f94-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f94-132">See also</span></span>

- [<span data-ttu-id="a1f94-133">LINQ to XML Programming Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1f94-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
