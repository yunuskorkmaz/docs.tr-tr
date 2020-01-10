---
title: İşlevsel oluşturma (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: e55b0010a5f75eee8137d1e9bcefc573b5e07e72
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635762"
---
# <a name="functional-construction-linq-to-xml-c"></a>İşlevsel oluşturma (LINQ to XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] *işlevsel oluşturma*adlı XML öğeleri oluşturmak için güçlü bir yol sağlar. İşlevsel oluşturma, tek bir bildirimde bir XML ağacı oluşturma olanağıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programlama arabiriminin işlevsel oluşturmayı etkinleştiren birkaç temel özelliği vardır:  
  
- <xref:System.Xml.Linq.XElement> Oluşturucu içerik için çeşitli bağımsız değişken türlerini alır. Örneğin, bir alt öğe haline gelen başka bir <xref:System.Xml.Linq.XElement> nesnesini geçirebilirsiniz. Öğesinin bir özniteliği haline gelen bir <xref:System.Xml.Linq.XAttribute> nesnesini geçirebilirsiniz. Ya da bir dizeye dönüştürülen ve öğenin metin içeriği haline gelen başka herhangi bir nesne türünü geçirebilirsiniz.  
  
- <xref:System.Xml.Linq.XElement> Oluşturucu <xref:System.Object>türünde bir `params` dizisi alır, böylece oluşturucuya herhangi bir sayıda nesne geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
- Bir nesne <xref:System.Collections.Generic.IEnumerable%601>uygularsa, nesnedeki koleksiyon numaralandırılır ve koleksiyondaki tüm öğeler eklenir. Koleksiyon <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneler içeriyorsa, koleksiyondaki her öğe ayrı olarak eklenir. Bir LINQ sorgusunun sonuçlarını oluşturucuya geçirmenize izin sağladığından bu önemlidir.  
  
 Bu özellikler bir XML ağacı oluşturmak için kod yazmanıza olanak sağlar. Aşağıda bir örnek verilmiştir:  
  
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
  
 Bu özellikler ayrıca, bir XML ağacı oluştururken aşağıdaki gibi LINQ sorgularının sonuçlarını kullanan kodu yazmanızı de sağlar:  
  
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
  