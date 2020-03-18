---
title: Ara değerler nasıl hesaplanır (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141441"
---
# <a name="how-to-calculate-intermediate-values-c"></a>Ara değerler nasıl hesaplanır (C#)
Bu örnek, sıralama, filtreleme ve seçmede kullanılabilecek ara değerlerin nasıl hesaplanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Let` yan tümce kullanılır.  
  
 Bu örnekte aşağıdaki XML belgesi kullanılır: [Örnek XML Dosyası: Sayısal Veriler (LINQ-XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
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
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir. Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Bu örnekte aşağıdaki XML belgesi kullanılır: [Örnek XML Dosyası: Ad alanında Sayısal Veriler.](./sample-xml-file-numerical-data-in-a-namespace.md)  
  
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
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
