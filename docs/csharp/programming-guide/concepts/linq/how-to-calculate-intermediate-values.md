---
title: 'Nasıl yapılır: Ara değerleri hesaplama (C#)'
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: cf0300294944d251b739a15edc6ace777eab5bd8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485932"
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
 Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir. Daha fazla bilgi için [(C#) XML ad alanları ile çalışma](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
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
