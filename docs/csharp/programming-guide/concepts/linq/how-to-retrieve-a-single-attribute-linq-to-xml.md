---
title: 'Nasıl yapılır: Tek bir öznitelik al (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: d8c8d0e3a99f94c4404f0ab23a5edf082be77952
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253404"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="7fe7d-102">Nasıl yapılır: Tek bir öznitelik al (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="7fe7d-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="7fe7d-103">Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="7fe7d-104">Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="7fe7d-105">Sınıfının yöntemi ,<xref:System.Xml.Linq.XAttribute>belirtilen ada <xref:System.Xml.Linq.XElement.Attribute%2A>sahipöğesinidöndürür. <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="7fe7d-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fe7d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fe7d-106">Example</span></span>  
 <span data-ttu-id="7fe7d-107">Aşağıdaki örnek <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="7fe7d-108">Bu örnek adlı `Phone`ağaçtaki tüm alt öğeleri bulur ve sonra adlı `type`özniteliği bulur.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="7fe7d-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7fe7d-109">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="7fe7d-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fe7d-110">Example</span></span>  
 <span data-ttu-id="7fe7d-111">Özniteliğin değerini almak istiyorsanız, nesneleri ile <xref:System.Xml.Linq.XElement> yaptığınız gibi, bu özniteliği de çevirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="7fe7d-112">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="7fe7d-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7fe7d-113">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7fe7d-114"><xref:System.Xml.Linq.XAttribute> sınıfına`bool?`, ,,`uint?`,,,,, ,,,,,,,,,,,,`long?` `bool` `string` `int` `int?` `uint` `long` `ulong` ,,,`double?` ,`TimeSpan`,, ,`decimal` ,`GUID`,,, ,`TimeSpan?`, ve `DateTime` `decimal?` `float?` `double` `ulong?` `float` `DateTime?`  `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fe7d-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="7fe7d-115">Example</span></span>  
 <span data-ttu-id="7fe7d-116">Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="7fe7d-117">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7fe7d-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="7fe7d-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="7fe7d-118">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="7fe7d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fe7d-119">See also</span></span>

- [<span data-ttu-id="7fe7d-120">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="7fe7d-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
