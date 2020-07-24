---
title: Tek bir öznitelik alma (LINQ to XML) (C#)
description: Öznitelik adı verildiğinde C# içindeki bir öğenin tek bir özniteliğini alma LINQ to XML nasıl kullanacağınızı öğrenin.
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4efcae5324ad5a2e4664e68e35e15ec2053daece
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103439"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="0dba1-103">Tek bir öznitelik alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0dba1-103">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0dba1-104">Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliğinin nasıl alınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0dba1-104">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="0dba1-105">Bu, belirli bir özniteliğe sahip bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0dba1-105">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="0dba1-106"><xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> Sınıfının yöntemi, <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="0dba1-106">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dba1-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dba1-107">Example</span></span>  
 <span data-ttu-id="0dba1-108">Aşağıdaki örnek <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="0dba1-108">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="0dba1-109">Bu örnek adlı ağaçtaki tüm alt öğeleri bulur `Phone` ve sonra adlı özniteliği bulur `type` .</span><span class="sxs-lookup"><span data-stu-id="0dba1-109">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="0dba1-110">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0dba1-110">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="0dba1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dba1-111">Example</span></span>  
 <span data-ttu-id="0dba1-112">Özniteliğin değerini almak istiyorsanız, nesneleri ile yaptığınız gibi, bu özniteliği de çevirebilirsiniz <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="0dba1-112">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0dba1-113">Aşağıdaki örnek bunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dba1-113">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="0dba1-114">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0dba1-114">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0dba1-115">,,,,,,,,,,,,,, <xref:System.Xml.Linq.XAttribute> `string` `bool` `bool?` `int` `int?` ,, `uint` `uint?` `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` , `DateTime` , `DateTime?` `TimeSpan` `TimeSpan?` `GUID` `GUID?` ,,,,,,,,,,,,,,,,,, ve için</span><span class="sxs-lookup"><span data-stu-id="0dba1-115">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dba1-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="0dba1-116">Example</span></span>  
 <span data-ttu-id="0dba1-117">Aşağıdaki örnek, bir ad alanında olan bir özniteliği için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0dba1-117">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="0dba1-118">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0dba1-118">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="0dba1-119">Bu kod şu çıkışı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0dba1-119">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dba1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dba1-120">See also</span></span>

- [<span data-ttu-id="0dba1-121">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="0dba1-121">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
