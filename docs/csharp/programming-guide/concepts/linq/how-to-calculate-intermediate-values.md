---
title: 'Nasıl yapılır: Ara değerleri hesaplama (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 12c8a87114859ce7b47b8206acb454cdc2838470
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702405"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Nasıl yapılır: Ara değerleri hesaplama (C#)
Bu örnek, sıralama, filtreleme ve seçme içinde kullanılan ara değerleri hesaplama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Let` yan tümcesi.  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Sayısal veriler (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Bu örnek aşağıdaki XML belgesi kullanır: [Örnek XML dosyası: Bir Namespace alanında sayısal veriler](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 Bu kod aşağıdaki çıktıyı üretir:  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel sorgular (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
