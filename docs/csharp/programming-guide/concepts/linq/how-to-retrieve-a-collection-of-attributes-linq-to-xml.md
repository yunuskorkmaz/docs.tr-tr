---
title: Özniteliklerin bir koleksiyonunu (LINQ- XML) (C#) nasıl alınır?
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 02871b38c3b1a1ed64fa6ca808e193811cd7f721
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347639"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="eaf8b-102">Özniteliklerin bir koleksiyonunu (LINQ- XML) (C#) nasıl alınır?</span><span class="sxs-lookup"><span data-stu-id="eaf8b-102">How to retrieve a collection of attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="eaf8b-103">Bu konu <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi tanır.</span><span class="sxs-lookup"><span data-stu-id="eaf8b-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="eaf8b-104">Bu yöntem, bir öğenin özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="eaf8b-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eaf8b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaf8b-105">Example</span></span>  
 <span data-ttu-id="eaf8b-106">Aşağıdaki örnek, bir öğenin özniteliklerinin toplanması yoluyla nasıl yinelenebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="eaf8b-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```csharp  
XElement val = new XElement("Value",  
    new XAttribute("ID", "1243"),  
    new XAttribute("Type", "int"),  
    new XAttribute("ConvertableTo", "double"),  
    "100");  
IEnumerable<XAttribute> listOfAttributes =  
    from att in val.Attributes()  
    select att;  
foreach (XAttribute a in listOfAttributes)  
    Console.WriteLine(a);  
```  
  
 <span data-ttu-id="eaf8b-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="eaf8b-107">This code produces the following output:</span></span>  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="eaf8b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf8b-108">See also</span></span>

- [<span data-ttu-id="eaf8b-109">LINQ - XML Eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="eaf8b-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
