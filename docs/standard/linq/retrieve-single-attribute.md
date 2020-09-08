---
title: Tek bir özniteliği alma-LINQ to XML
description: Öznitelik adı verilen bir öğenin tek bir özniteliğini alın.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: a8a56ec62275f2376d19d7fc9090414b74fc77ad
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553878"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml"></a><span data-ttu-id="7cb81-103">Tek bir özniteliği alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="7cb81-103">How to retrieve a single attribute (LINQ to XML)</span></span>

<span data-ttu-id="7cb81-104">Bu makalede, öznitelik adı verildiğinde bir öğenin tek bir özniteliği nasıl alınır açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7cb81-104">This article explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="7cb81-105">Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7cb81-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>

<span data-ttu-id="7cb81-106"><xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> Sınıfının yöntemi, <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="7cb81-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>

## <a name="example-retrieve-attribute-values-given-the-element-and-attribute-names"></a><span data-ttu-id="7cb81-107">Örnek: öğe ve öznitelik adları verilen öznitelik değerlerini alın</span><span class="sxs-lookup"><span data-stu-id="7cb81-107">Example: Retrieve attribute values, given the element and attribute names</span></span>

<span data-ttu-id="7cb81-108">Aşağıdaki örnek, <xref:System.Xml.Linq.XElement> adlı bir öğe oluşturmak için yöntemini kullanır `PhoneNumbers` .</span><span class="sxs-lookup"><span data-stu-id="7cb81-108">The following example uses the <xref:System.Xml.Linq.XElement> method to create an element named `PhoneNumbers`.</span></span> <span data-ttu-id="7cb81-109">Ardından adlı tüm alt öğeleri bulur `Phone` ve her biri için, <xref:System.Xml.Linq.XElement.Attribute%2A> adlı özniteliğin değerini almak ve çıkarmak için yöntemini kullanır `type` :</span><span class="sxs-lookup"><span data-stu-id="7cb81-109">It then finds all the descendant elements named `Phone` and, for each, uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method to obtain and output the value of the attribute named `type`:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList = From el In cust...<Phone>
For Each e As XElement In elList
    Console.WriteLine(e.@type)
Next
```

<span data-ttu-id="7cb81-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7cb81-110">This example produces the following output:</span></span>

```output
home
work
```

## <a name="example-retrieve-an-attribute-value-with-a-cast"></a><span data-ttu-id="7cb81-111">Örnek: bir atama ile öznitelik değeri alma</span><span class="sxs-lookup"><span data-stu-id="7cb81-111">Example: Retrieve an attribute value with a cast</span></span>

<span data-ttu-id="7cb81-112">Bir özniteliğin değerini, nesneleri ile yaptığınız gibi, kaldırarak alabilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="7cb81-112">You can retrieve the value of an attribute by casting it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="7cb81-113">Aşağıdaki örnek şunu gösterir:</span><span class="sxs-lookup"><span data-stu-id="7cb81-113">The following example demonstrates this:</span></span>

```csharp
XElement cust = new XElement("PhoneNumbers",
    new XElement("Phone",
        new XAttribute("type", "home"),
        "555-555-5555"),
    new XElement("Phone",
        new XAttribute("type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants("Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute("type"));
```

```vb
Dim cust As XElement = <PhoneNumbers>
                           <Phone type="home">555-555-5555</Phone>
                           <Phone type="work">555-555-6666</Phone>
                       </PhoneNumbers>
Dim elList As IEnumerable(Of XElement) = _
    From el In cust...<Phone> _
    Select el
For Each el As XElement In elList
    Console.WriteLine(el.@type)
Next
```

<span data-ttu-id="7cb81-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7cb81-114">This example produces the following output:</span></span>

```output
home
work
```

<span data-ttu-id="7cb81-115">LINQ to XML,,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` , `double?` , `decimal` , `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,,,,,,, ve</span><span class="sxs-lookup"><span data-stu-id="7cb81-115">LINQ to XML provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>

## <a name="example-cast-for-an-attribute-in-a-namespace"></a><span data-ttu-id="7cb81-116">Örnek: ad alanındaki bir öznitelik için atama</span><span class="sxs-lookup"><span data-stu-id="7cb81-116">Example: Cast for an attribute in a namespace</span></span>

<span data-ttu-id="7cb81-117">Aşağıdaki örnek, bir ad alanında olan bir öznitelik için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7cb81-117">The following example shows the same code for an attribute that's in a namespace.</span></span> <span data-ttu-id="7cb81-118">Daha fazla bilgi için bkz. [ad alanlarına genel bakış](namespaces-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7cb81-118">For more information, see [Namespaces overview](namespaces-overview.md).</span></span>

```csharp
XNamespace aw = "http://www.adventure-works.com";
XElement cust = new XElement(aw + "PhoneNumbers",
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "home"),
        "555-555-5555"),
    new XElement(aw + "Phone",
        new XAttribute(aw + "type", "work"),
        "555-555-6666")
);
IEnumerable<XElement> elList =
    from el in cust.Descendants(aw + "Phone")
    select el;
foreach (XElement el in elList)
    Console.WriteLine((string)el.Attribute(aw + "type"));
```

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim cust As XElement = _
            <aw:PhoneNumbers>
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>
            </aw:PhoneNumbers>
        Dim elList As IEnumerable(Of XElement) = _
            From el In cust...<aw:Phone> _
            Select el
        For Each el As XElement In elList
            Console.WriteLine(el.@aw:type)
        Next
    End Sub
End Module
```

<span data-ttu-id="7cb81-119">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7cb81-119">This example produces the following output:</span></span>

```output
home
work
```

## <a name="see-also"></a><span data-ttu-id="7cb81-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cb81-120">See also</span></span>

- [<span data-ttu-id="7cb81-121">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="7cb81-121">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
