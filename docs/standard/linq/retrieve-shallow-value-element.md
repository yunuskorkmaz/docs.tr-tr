---
title: Bir öğenin yüzeysel değerini alma-LINQ to XML
description: '`ShallowValue`Bir öğenin yüzeysel değerini almak için genişletme yöntemini kullanın. Yüzeysel değer yalnızca o öğenin değeridir; diğer bir deyişle, alt öğelerin değerlerini içermez.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 761ffc07b13ebdc652b75bf96ba5b121c7912fd7
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553879"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a>Bir öğenin yüzeysel değerini alma (LINQ to XML)

Bu makalede, alt öğelerin değerleri dahil değil, yalnızca o öğenin değeri olan bir öğenin yüzeysel değerinin nasıl alınacağı gösterilmektedir. Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.

<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>Bir öğe değerini almak için atama veya özellik kullandığınızda, bu değer alt öğeleri içerir. Yüzeysel değeri almak için `ShallowValue` , aşağıdaki örnekte gösterildiği gibi genişletme yöntemini kullanabilirsiniz. Örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir. Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a>Örnek: `ShallowValue` bir öğenin yüzeysel değerini almak için genişletme yöntemini kullanın

Örnekler, aşağıdakileri içeren Report.xml metin dosyasını kullanır:

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

Örnek için kod aşağıda verilmiştir:

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

```vb
Module Module1
    <System.Runtime.CompilerServices.Extension()> _
    Public Function ShallowValue(ByVal xe As XElement)
        Return xe _
               .Nodes() _
               .OfType(Of XText)() _
               .Aggregate(New StringBuilder(), _
                              Function(s, c) s.Append(c), _
                              Function(s) s.ToString())
    End Function

    Sub Main()
        Dim root As XElement = XElement.Load("Report.xml")

        Dim query As IEnumerable(Of XElement) = _
            From el In root.Descendants() _
            Where (el.ShallowValue().StartsWith("=")) _
            Select el

        For Each q As XElement In query
            Console.WriteLine("{0}{1}{2}", _
                q.Name.ToString().PadRight(8), _
                q.Attribute("Name").ToString().PadRight(20), _
                q.ShallowValue())
        Next
    End Sub
End Module
```

Bu örnek aşağıdaki çıktıyı üretir:

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenlerine genel bakış](linq-xml-axes-overview.md)
