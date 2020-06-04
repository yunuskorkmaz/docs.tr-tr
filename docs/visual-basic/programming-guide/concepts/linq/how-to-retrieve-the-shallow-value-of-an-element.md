---
title: 'Nasıl yapılır: Öğenin Yüzeysel Değerini Alma'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 24e6b128481f56941f0a61da9766f02813a46e97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397823"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="42df2-102">Nasıl yapılır: bir öğenin yüzeysel değerini alma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42df2-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>

<span data-ttu-id="42df2-103">Bu konu, bir öğenin yüzeysel değerinin nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42df2-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="42df2-104">Yüzeysel değer, tek bir dizeye birleştirilmiş tüm alt öğelerin değerlerini içeren derin değeri aksine, yalnızca belirli bir öğenin değeridir.</span><span class="sxs-lookup"><span data-stu-id="42df2-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>

<span data-ttu-id="42df2-105">Ya da özelliğini kullanarak bir öğe değeri aldığınızda <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> , derin değeri alırsınız.</span><span class="sxs-lookup"><span data-stu-id="42df2-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="42df2-106">Yüzeysel değeri almak için, `ShallowValue` Aşağıdaki örnekte gösterildiği gibi genişletme yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42df2-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="42df2-107">Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="42df2-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="42df2-108">Aşağıdaki örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="42df2-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="42df2-109">Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="42df2-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example"></a><span data-ttu-id="42df2-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="42df2-110">Example</span></span>

<span data-ttu-id="42df2-111">Aşağıdaki metin dosyası, Report. xml, bu örneğin kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="42df2-111">The following text file, Report.xml, is the source for this example.</span></span>

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

<span data-ttu-id="42df2-112">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="42df2-112">This example produces the following output:</span></span>

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="42df2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42df2-113">See also</span></span>

- [<span data-ttu-id="42df2-114">LINQ to XML eksenleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42df2-114">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
