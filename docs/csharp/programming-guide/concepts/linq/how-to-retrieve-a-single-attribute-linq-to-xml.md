---
title: "Nasıl yapılır: tek bir öznitelik (LINQ-XML) alma (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bcfdae1bd01d54baeac8946af9f2744da9a21bff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a><span data-ttu-id="661fb-102">Nasıl yapılır: tek bir öznitelik (LINQ-XML) alma (C#)</span><span class="sxs-lookup"><span data-stu-id="661fb-102">How to: Retrieve a Single Attribute (LINQ to XML) (C#)</span></span>
<span data-ttu-id="661fb-103">Bu konuda, bir öğenin tek bir özniteliği öznitelik adı verilen almak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="661fb-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="661fb-104">Belirli bir özniteliği olan bir öğeyi bulmak istediğiniz sorgu ifadeleri yazmak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="661fb-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="661fb-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Yöntemi <xref:System.Xml.Linq.XElement> sınıf döndürür <xref:System.Xml.Linq.XAttribute> belirtilen ada sahip.</span><span class="sxs-lookup"><span data-stu-id="661fb-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="661fb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="661fb-106">Example</span></span>  
 <span data-ttu-id="661fb-107">Aşağıdaki örnek kullanır <xref:System.Xml.Linq.XElement.Attribute%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="661fb-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
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
  
 <span data-ttu-id="661fb-108">Bu örnek adlı ağacında tüm alt öğeleri bulur `Phone`ve ardından adlı özniteliği bulur `type`.</span><span class="sxs-lookup"><span data-stu-id="661fb-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="661fb-109">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="661fb-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="661fb-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="661fb-110">Example</span></span>  
 <span data-ttu-id="661fb-111">Özniteliğin değerini almak istiyorsanız, sahip olduğu gibi çevirebilirsiniz <xref:System.Xml.Linq.XElement> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="661fb-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="661fb-112">Aşağıdaki örnekte bu gösterir.</span><span class="sxs-lookup"><span data-stu-id="661fb-112">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="661fb-113">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="661fb-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="661fb-114">Açık atama işleçleri sağlar <xref:System.Xml.Linq.XAttribute> sınıfının `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, ve  `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="661fb-114"> provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="661fb-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="661fb-115">Example</span></span>  
 <span data-ttu-id="661fb-116">Aşağıdaki örnek, bir ad alanı içinde bir öznitelik için aynı kodu gösterir.</span><span class="sxs-lookup"><span data-stu-id="661fb-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="661fb-117">Daha fazla bilgi için bkz: [XML ad alanları (C#) çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="661fb-117">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
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
  
 <span data-ttu-id="661fb-118">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="661fb-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="661fb-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="661fb-119">See Also</span></span>  
 [<span data-ttu-id="661fb-120">LINQ-XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="661fb-120">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
