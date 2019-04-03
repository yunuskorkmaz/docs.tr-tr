---
title: 'Nasıl yapılır: İsteğe bağlı bir öğe (Visual Basic) üzerinde filtreleme'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: f2a1c7d4091af80e79a6758bcede8f4ccc753f03
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820671"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="a175d-102">Nasıl yapılır: İsteğe bağlı bir öğe (Visual Basic) üzerinde filtreleme</span><span class="sxs-lookup"><span data-stu-id="a175d-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="a175d-103">Bazen, XML belgesinde varolduğundan emin olmadığınız halde bir öğe için filtrelemek istersiniz.</span><span class="sxs-lookup"><span data-stu-id="a175d-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="a175d-104">Arama, böylece belirli bir öğenin alt öğesi yoksa, bir null başvurusu özel durumu için filtreleyerek tetiklemez yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="a175d-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="a175d-105">Aşağıdaki örnekte, `Child5` öğesi yok bir `Type` alt öğesi, ancak sorgu hala yürütür doğru.</span><span class="sxs-lookup"><span data-stu-id="a175d-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a175d-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a175d-106">Example</span></span>  
 <span data-ttu-id="a175d-107">Bu örnekte <xref:System.Xml.Linq.Extensions.Elements%2A> genişletme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a175d-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1>  
            <Text>Child One Text</Text>  
            <Type Value="Yes"/>  
        </Child1>  
        <Child2>  
            <Text>Child Two Text</Text>  
            <Type Value="Yes"/>  
        </Child2>  
        <Child3>  
            <Text>Child Three Text</Text>  
            <Type Value="No"/>  
        </Child3>  
        <Child4>  
            <Text>Child Four Text</Text>  
            <Type Value="Yes"/>  
        </Child4>  
        <Child5>  
            <Text>Child Five Text</Text>  
        </Child5>  
    </Root>  
Dim cList As IEnumerable(Of String) = _  
    From typeElement In root.Elements().<Type> _  
    Where typeElement.@Value = "Yes" _  
    Select typeElement.Parent.<Text>.Value  
Dim str As String  
For Each str In cList  
    Console.WriteLine(str)  
Next  
```  
  
 <span data-ttu-id="a175d-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a175d-108">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="a175d-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="a175d-109">Example</span></span>  
 <span data-ttu-id="a175d-110">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="a175d-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="a175d-111">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a175d-111">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child1>  
                    <Text>Child One Text</Text>  
                    <Type Value="Yes"/>  
                </Child1>  
                <Child2>  
                    <Text>Child Two Text</Text>  
                    <Type Value="Yes"/>  
                </Child2>  
                <Child3>  
                    <Text>Child Three Text</Text>  
                    <Type Value="No"/>  
                </Child3>  
                <Child4>  
                    <Text>Child Four Text</Text>  
                    <Type Value="Yes"/>  
                </Child4>  
                <Child5>  
                    <Text>Child Five Text</Text>  
                </Child5>  
            </Root>  
        Dim cList As IEnumerable(Of String) = _  
            From typeElement In root.Elements().<Type> _  
            Where typeElement.@Value = "Yes" _  
            Select typeElement.Parent.<Text>.Value  
        Dim str As String  
        For Each str In cList  
            Console.WriteLine(str)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="a175d-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="a175d-112">This code produces the following output:</span></span>  
  
```  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="a175d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a175d-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="a175d-114">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a175d-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="a175d-115">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="a175d-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="a175d-116">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="a175d-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="a175d-117">XML Value Özelliği</span><span class="sxs-lookup"><span data-stu-id="a175d-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="a175d-118">Standart sorgu işleçlerine genel bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a175d-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="a175d-119">Projeksiyon işlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a175d-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
