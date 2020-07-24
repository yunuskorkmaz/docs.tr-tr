---
title: Öznitelik koleksiyonu alma (LINQ to XML) (C#)
description: C# içindeki Attributes yöntemi bir öğenin özniteliklerini alır. Bu LINQ to XML örnek, bir öğenin özniteliklerinin koleksiyonu boyunca yinelenir.
ms.date: 07/20/2015
ms.assetid: a49ee7a3-b2c2-4d49-9b5c-b7c6c41f4f13
ms.openlocfilehash: 5994086db6133530e63eb1328a7b524d30a0797d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103385"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-c"></a>Öznitelik koleksiyonu alma (LINQ to XML) (C#)
Bu konuda yöntemi tanıtılmaktadır <xref:System.Xml.Linq.XElement.Attributes%2A> . Bu yöntem bir öğenin özniteliklerini alır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir öğenin özniteliklerinin toplanması arasında nasıl yineleme yapılacağını gösterir.  
  
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
  
 Bu kod şu çıkışı oluşturur:  
  
```output  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
