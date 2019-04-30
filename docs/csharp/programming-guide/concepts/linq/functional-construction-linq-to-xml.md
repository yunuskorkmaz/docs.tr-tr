---
title: İşlevsel oluşturma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: 5c749868606e70837a8eb423a6e4fada21407d4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702613"
---
# <a name="functional-construction-linq-to-xml-c"></a>İşlevsel oluşturma (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel oluşturma*. Tek bir deyimde bir XML ağacı oluşturma olanağı işlevsel yapısıdır.  
  
 Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel oluşturma sağlayan bir programlama arabirimi:  
  
- <xref:System.Xml.Linq.XElement> Oluşturucusu, çeşitli içerik için bağımsız değişkenleri alır. Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olan nesne. Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin bir özniteliği olan nesne. Veya başka türde bir nesne bir dizeye dönüştürülür ve öğenin metin içeriğini olur geçirebilirsiniz.  
  
- <xref:System.Xml.Linq.XElement> Oluşturucusu alır bir `params` türünde dizi <xref:System.Object>, böylece herhangi bir sayıda nesneleri için oluşturucu geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, koleksiyon nesnesi içinde listelenmiş ve koleksiyondaki tüm öğelerin eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler, koleksiyondaki her öğe ayrı olarak eklenir. Sonuçlarını geçirmenize izin verdiğinden, bu önemli bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] Sorgu Oluşturucusu.  
  
 Bu özellikleri bir XML ağacı oluşturmak için kod yazmanıza olanak sağlar. Bir örnek verilmiştir:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Bu özellikler ayrıca sonuçlarını kullanan kod yazmanıza etkinleştirme [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular ne zaman bir XML ağacı şu şekilde oluşturun:  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
