---
title: 'Nasıl yapılır: bir öğenin yüzeysel değerini alma'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 7449d6d1230313aef6005284270370bb9d243a3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346905"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a>Nasıl yapılır: bir öğenin yüzeysel değerini alma (Visual Basic)

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

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML eksenleri (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
