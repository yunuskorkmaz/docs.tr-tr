---
title: Tek bir öznitelik (LINQ - XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168719"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="ffe64-102">Tek bir öznitelik (LINQ - XML) (C#) nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="ffe64-102">How to retrieve a single attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="ffe64-103">Bu konu, öznitelik adı verilen bir öğenin tek bir özniteliği almak için nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="ffe64-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="ffe64-104">Bu, belirli bir özniteliği olan bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ffe64-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="ffe64-105">Sınıfın yöntemi belirtilen adla döndürür. <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ffe64-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe64-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffe64-106">Example</span></span>  
 <span data-ttu-id="ffe64-107">Aşağıdaki örnekyöntemi <xref:System.Xml.Linq.XElement.Attribute%2A> kullanır.</span><span class="sxs-lookup"><span data-stu-id="ffe64-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="ffe64-108">Bu örnek, adlı `Phone`ağaçtaki tüm torunları bulur ve sonra `type`adlı özniteliği bulur.</span><span class="sxs-lookup"><span data-stu-id="ffe64-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="ffe64-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ffe64-109">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="ffe64-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffe64-110">Example</span></span>  
 <span data-ttu-id="ffe64-111">Özniteliğin değerini almak istiyorsanız, <xref:System.Xml.Linq.XElement> nesnelerde olduğu gibi onu atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ffe64-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="ffe64-112">Aşağıdaki örnek bunu göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="ffe64-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="ffe64-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ffe64-113">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="ffe64-114"><xref:System.Xml.Linq.XAttribute> sınıf için açık döküm `string`operatörleri `bool` `bool?`sağlar `int` `int?`, `uint` `uint?`, `long` `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `GUID` `GUID?`, , , , , , , , , , , , , , , , , , , , , , , `decimal` `decimal?` `DateTime` `DateTime?` `TimeSpan` `TimeSpan?`</span><span class="sxs-lookup"><span data-stu-id="ffe64-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffe64-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="ffe64-115">Example</span></span>  
 <span data-ttu-id="ffe64-116">Aşağıdaki örnek, ad alanında bulunan bir öznitelik için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ffe64-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="ffe64-117">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ffe64-117">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ffe64-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ffe64-118">This code produces the following output:</span></span>  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffe64-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ffe64-119">See also</span></span>

- [<span data-ttu-id="ffe64-120">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="ffe64-120">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
