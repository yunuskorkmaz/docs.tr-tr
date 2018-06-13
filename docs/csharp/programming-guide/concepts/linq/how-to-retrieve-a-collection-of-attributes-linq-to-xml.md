---
title: 'Nasıl yapılır: öznitelikleri (LINQ-XML) koleksiyonunu alma (C#)'
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 73e548b100893652b63dfcc69669eabce655efa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317849"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a><span data-ttu-id="8f147-102">Nasıl yapılır: öznitelikleri (LINQ-XML) koleksiyonunu alma (C#)</span><span class="sxs-lookup"><span data-stu-id="8f147-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8f147-103">Bu konu tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f147-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="8f147-104">Bu yöntem, bir öğenin özniteliklerini alır.</span><span class="sxs-lookup"><span data-stu-id="8f147-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f147-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="8f147-105">Example</span></span>  
 <span data-ttu-id="8f147-106">Aşağıdaki örnek, bir öğenin öznitelikleri toplulukta tekrarlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8f147-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
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
  
 <span data-ttu-id="8f147-107">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8f147-107">This code produces the following output:</span></span>  
  
```  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="8f147-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f147-108">See Also</span></span>  
 [<span data-ttu-id="8f147-109">LINQ-XML eksenleri (C#)</span><span class="sxs-lookup"><span data-stu-id="8f147-109">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
