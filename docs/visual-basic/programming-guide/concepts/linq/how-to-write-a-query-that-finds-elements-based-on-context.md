---
title: 'Nasıl yapılır: (Visual Basic) bağlama göre öğeleri bulan bir sorgu yazma'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: 0981da1e35f2c0b6023c009d4f62c95a612d8971
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614889"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="fff49-102">Nasıl yapılır: (Visual Basic) bağlama göre öğeleri bulan bir sorgu yazma</span><span class="sxs-lookup"><span data-stu-id="fff49-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="fff49-103">Bazen, bağlama göre öğeleri seçen bir sorgu yazmak zorunda kalabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff49-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="fff49-104">Bağlı olarak önceki veya Eşdüzey öğeleri aşağıdaki filtreleme isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff49-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="fff49-105">Temel alınarak alt veya üst öğeleri filtrelemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fff49-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="fff49-106">Bir sorgu yazma ve sorgu sonuçlarının kullanarak bunu yapabilirsiniz `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fff49-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="fff49-107">İlk null karşı test etmeyi ve ardından değeri test varsa, sorgu yapılacağı daha kullanışlı bir `let` yan tümcesi ve ardından sonuçları `where` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="fff49-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fff49-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="fff49-108">Example</span></span>  
 <span data-ttu-id="fff49-109">Aşağıdaki örnekte tüm seçer `p` tarafından hemen ardından öğeleri bir `ul` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fff49-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 <span data-ttu-id="fff49-110">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fff49-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="fff49-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fff49-111">Example</span></span>  
 <span data-ttu-id="fff49-112">Aşağıdaki örnek, aynı sorgu için bir ad alanındaki XML gösterir.</span><span class="sxs-lookup"><span data-stu-id="fff49-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="fff49-113">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="fff49-113">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="fff49-114">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="fff49-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="fff49-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fff49-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="fff49-116">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fff49-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
