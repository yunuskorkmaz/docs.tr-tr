---
title: 'Nasıl yapılsın: İsteğe Bağlı Öğeye Filtre Uygulayın'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: 6db377ae30582ef010d5af467e88c52b008483ed
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2020
ms.locfileid: "78267060"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="ba121-102">Nasıl yapılır: İsteğe Bağlı Öğeye Filtre Uygulayın (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba121-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="ba121-103">Bazen XML belgenizde var olduğundan emin değilseniz bile bir öğe için filtre yapmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ba121-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="ba121-104">Arama, belirli öğealt öğeye sahip değilse, bunun için filtre uygulayarak null bir başvuru özel durum tetiklemez, böylece yürütülmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba121-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="ba121-105">Aşağıdaki örnekte, `Child5` öğenin bir `Type` alt öğesi yoktur, ancak sorgu yine de doğru yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ba121-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba121-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba121-106">Example</span></span>  
 <span data-ttu-id="ba121-107">Bu örnek, <xref:System.Xml.Linq.Extensions.Elements%2A> uzantı yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ba121-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
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
  
 <span data-ttu-id="ba121-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ba121-108">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="ba121-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ba121-109">Example</span></span>  
 <span data-ttu-id="ba121-110">Aşağıdaki örnek, ad alanında olan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ba121-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ba121-111">Daha fazla bilgi için [Bkz. NameSpaces Genel Bakış (LINQ - XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ba121-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="ba121-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="ba121-112">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba121-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba121-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ba121-114">Temel Sorgular (LINQ- XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba121-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="ba121-115">XML Alt Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba121-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="ba121-116">XML Özniteliği Axis Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba121-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="ba121-117">XML Değeri Özelliği</span><span class="sxs-lookup"><span data-stu-id="ba121-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="ba121-118">Standart Sorgu Operatörlerine Genel Bakış (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba121-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="ba121-119">Projeksiyon İşlemleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba121-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
