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
# <a name="how-to-retrieve-the-shallow-value-of-an-element-linq-to-xml"></a><span data-ttu-id="567ef-104">Bir öğenin yüzeysel değerini alma (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="567ef-104">How to retrieve the shallow value of an element (LINQ to XML)</span></span>

<span data-ttu-id="567ef-105">Bu makalede, alt öğelerin değerleri dahil değil, yalnızca o öğenin değeri olan bir öğenin yüzeysel değerinin nasıl alınacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="567ef-105">This article shows how to retrieve the shallow value of an element, which is the value of that element only, not including values of descendent elements.</span></span> <span data-ttu-id="567ef-106">Yüzeysel değer alma, içeriğine göre öğeleri seçmek istediğinizde faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="567ef-106">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="567ef-107"><xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>Bir öğe değerini almak için atama veya özellik kullandığınızda, bu değer alt öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="567ef-107">When you use casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property to retrieve an element value, the value includes the descendants.</span></span> <span data-ttu-id="567ef-108">Yüzeysel değeri almak için `ShallowValue` , aşağıdaki örnekte gösterildiği gibi genişletme yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="567ef-108">To retrieve the shallow value you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="567ef-109">Örnek, bir öğenin yüzeysel değerini alan bir genişletme yöntemi bildirir.</span><span class="sxs-lookup"><span data-stu-id="567ef-109">The example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="567ef-110">Daha sonra, hesaplanmış bir değer içeren tüm öğeleri listelemek için bir sorgudaki genişletme yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="567ef-110">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example-use-the-shallowvalue-extension-method-to-retrieve-the-shallow-value-of-an-element"></a><span data-ttu-id="567ef-111">Örnek: `ShallowValue` bir öğenin yüzeysel değerini almak için genişletme yöntemini kullanın</span><span class="sxs-lookup"><span data-stu-id="567ef-111">Example: Use the `ShallowValue` extension method to retrieve the shallow value of an element</span></span>

<span data-ttu-id="567ef-112">Örnekler, aşağıdakileri içeren Report.xml metin dosyasını kullanır:</span><span class="sxs-lookup"><span data-stu-id="567ef-112">The examples uses the text file Report.xml that contains the following:</span></span>

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

<span data-ttu-id="567ef-113">Örnek için kod aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="567ef-113">Here is the code for the example:</span></span>

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

<span data-ttu-id="567ef-114">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="567ef-114">This example produces the following output:</span></span>

```output
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="567ef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="567ef-115">See also</span></span>

- [<span data-ttu-id="567ef-116">LINQ to XML eksenlerine genel bakış</span><span class="sxs-lookup"><span data-stu-id="567ef-116">LINQ to XML axes overview</span></span>](linq-xml-axes-overview.md)
