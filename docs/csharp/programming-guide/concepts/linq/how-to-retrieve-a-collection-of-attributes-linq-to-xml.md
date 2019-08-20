---
title: 'Nasıl yapılır: Öznitelik koleksiyonu alma (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: b37600f02cd012e688d161a079c3c8647545cb2c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592670"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="bbf8b-102">Nasıl yapılır: Öznitelik koleksiyonu alma (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="bbf8b-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="bbf8b-103">Bu konuda <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbf8b-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="bbf8b-104">Bu yöntem bir öğenin özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="bbf8b-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbf8b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bbf8b-105">Example</span></span>  
 <span data-ttu-id="bbf8b-106">Aşağıdaki örnek, bir öğenin özniteliklerinin toplanması arasında nasıl yineleme yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bbf8b-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="bbf8b-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="bbf8b-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbf8b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbf8b-108">See also</span></span>

- [<span data-ttu-id="bbf8b-109">LINQ to XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="bbf8b-109">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
