---
title: Bir öğenin (C#) Yüzeysel değerini alma
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347442"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Bir öğenin (C#) Yüzeysel değerini alma
Bu konu, bir öğenin yüzeysel değerinin nasıl alınacağını gösterir. Yüzeysel değer, tek bir dizeye birleştirilmiş tüm alt öğelerin değerlerini içeren derin değeri aksine, yalnızca belirli bir öğenin değeridir.  
  
 Bir öğe değerini, ya da <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliğini kullanarak aldığınızda, derin değeri elde edersiniz. Yüzeysel değeri almak için, aşağıdaki örnekte gösterildiği gibi `ShallowValue` uzantısı yöntemini kullanabilirsiniz. Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.  
  
 Aşağıdaki örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir. Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki metin dosyası, Report. xml, bu örneğin kaynağıdır.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 Bu örnek aşağıdaki çıktıyı üretir:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (C#)](./linq-to-xml-axes-overview.md)
