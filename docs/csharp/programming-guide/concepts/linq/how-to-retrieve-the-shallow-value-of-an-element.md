---
title: Bir öğenin sığ değeri nasıl alınır (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347442"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Bir öğenin sığ değeri nasıl alınır (C#)
Bu konu, bir öğenin sığ değerini nasıl elde edilebildiğini gösterir. Sığ değer, tek bir dize içine sıkıştırılmış tüm soyundan gelen öğelerin değerlerini içeren derin değerin aksine, yalnızca belirli öğenin değeridir.  
  
 Döküm veya <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği kullanarak bir öğe değeri aldığınızda, derin değeri alırsınız. Sığ değeri almak için, aşağıdaki `ShallowValue` örnekte gösterildiği gibi uzantı yöntemini kullanabilirsiniz. Öğeleri içeriğine göre seçmek istediğinizde sığ değeri almak yararlıdır.  
  
 Aşağıdaki örnek, bir öğenin sığ değerini alan bir uzantı yöntemi ni bildirir. Daha sonra, hesaplanan değer içeren tüm öğeleri listelemek için sorgudaki uzantı yöntemini kullanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki metin dosyası, Report.xml, bu örneğin kaynağıdır.  
  
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
  
 Bu örnek, aşağıdaki çıktıyı üretir:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Eksenleri (C#)](./linq-to-xml-axes-overview.md)
