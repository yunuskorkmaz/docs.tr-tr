---
title: 'Nasıl yapılır: (Visual Basic) öğenin yüzeysel değerini alma'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 69e85c3b87ef1052bbb3eab832f93774fa35066f
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678676"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>Nasıl yapılır: (Visual Basic) öğenin yüzeysel değerini alma

Bu konuda, bir öğenin yüzeysel değerini alma gösterilmektedir. Basit yalnızca belirli öğenin değeri tek bir dize olarak birleştirilmiş tüm alt öğe değerlerini içeren ayrıntılı değer aksine değerdir.

Ya da bir çevrim kullanarak bir öğe değeri aldığınızda veya <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> özelliği, derin değeri alın. Yüzeysel değerini almak için kullanabileceğiniz `ShallowValue` genişletme yöntemi, aşağıdaki örnekte gösterildiği gibi. Yüzeysel değerini alma içeriklerine göre öğeleri seçmek istediğinizde yararlıdır.

Aşağıdaki örnek, bir öğenin yüzeysel değerini alır. bir genişletme yöntemi bildirir. Ardından, hesaplanan değeri içeren tüm öğeleri listelemek için genişletme yöntemi bir sorguda kullanır.

## <a name="example"></a>Örnek

Aşağıdaki metin dosyası Report.xml, bu örnekte kaynağıdır.

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

```
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
