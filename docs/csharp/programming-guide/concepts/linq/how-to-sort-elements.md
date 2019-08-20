---
title: 'Nasıl yapılır: Öğeleri Sırala (C#)'
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 074428413fa57d8f0e5ae94970c2aeeeb9e4cc7c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592461"
---
# <a name="how-to-sort-elements-c"></a>Nasıl yapılır: Öğeleri Sırala (C#)
Bu örnek, sonuçlarını sıralayan bir sorgunun nasıl yazılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Sayısal veri (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir. Daha fazla bilgi için bkz. [ad alanlarına genel bakış (C#LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 Bu örnek aşağıdaki XML belgesini kullanır: [Örnek XML dosyası: Bir ad alanındaki](./sample-xml-file-numerical-data-in-a-namespace.md)sayısal veri.  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Verileri sıralama (C#)](./sorting-data.md)
