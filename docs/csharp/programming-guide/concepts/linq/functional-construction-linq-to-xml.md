---
title: İşlev yapımı (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: 57a82bcf-de03-4f1c-a0c8-9a76e989d542
ms.openlocfilehash: c837660adf9c62c8f4304b92d37f732795c981c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="functional-construction-linq-to-xml-c"></a>İşlev yapımı (LINQ-XML) (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] adlı XML öğeleri oluşturmak için güçlü bir yol sağlar *işlevsel yapım*. Bir XML ağacı tek bir deyimde oluşturabilme işlevsel yapıdır.  
  
 Birkaç temel özellikleri vardır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] işlevsel yapım etkinleştirmek programlama arabirimi:  
  
-   <xref:System.Xml.Linq.XElement> Oluşturucusu çeşitli içerik için bağımsız değişkenleri alır. Örneğin, başka bir geçirebilirsiniz <xref:System.Xml.Linq.XElement> bir alt öğesi olur nesnesi. Geçirebilirsiniz bir <xref:System.Xml.Linq.XAttribute> öğesinin özniteliği hale nesnesi. Veya herhangi bir dizeye dönüştürülür ve öğenin metin içeriğini olur, nesne türü geçirebilirsiniz.  
  
-   <xref:System.Xml.Linq.XElement> Oluşturucusu geçen bir `params` türünde dizi <xref:System.Object>, böylece oluşturucuya herhangi bir sayıda nesnelerini geçirebilirsiniz. Bu, karmaşık içeriğe sahip bir öğe oluşturmanıza olanak sağlar.  
  
-   Bir nesne uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>nesne koleksiyonunda numaralandırılan ve koleksiyondaki tüm öğeleri eklenir. Koleksiyon içeriyorsa <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute> nesneleri, koleksiyondaki her öğe ayrı olarak eklenir. Sonuçlarını geçirmenize olanak tanır bu önemlidir, çünkü bir [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgu oluşturucuya.  
  
 Bu özellikler bir XML ağacı oluşturmak üzere kod yazmak etkinleştirin. Bir örnek verilmiştir:  
  
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
  
 Bu özellikleri de sonuçlarını kullanan kodu yazmanızı etkinleştirmek [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] sorgular ne zaman bir XML ağacı gibi oluşturun:  
  
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
  
 Bu örnek şu çıkışı üretir:  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oluşturma XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)
