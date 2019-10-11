---
title: 'Nasıl yapılır: alt öğeler yöntemini kullanarak tek bir alt öğe bulma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: dbde5686d1b7670290d434c0a04515cbc10622fd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72249958"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a><span data-ttu-id="1571c-102">Nasıl yapılır: alt öğeler yöntemini kullanarak tek bir alt öğe bulma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1571c-102">How to: Find a Single Descendant Using the Descendants Method (Visual Basic)</span></span>
<span data-ttu-id="1571c-103">Tek bir benzersiz şekilde adlandırılmış öğe bulmak için kodu hızlı bir şekilde yazmak üzere <xref:System.Xml.Linq.XContainer.Descendants%2A> eksen yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1571c-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="1571c-104">Bu teknik özellikle belirli bir ada sahip belirli bir alt öğe bulmak istediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1571c-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="1571c-105">İstenen öğeye gitmek için kodu yazabilirsiniz, ancak <xref:System.Xml.Linq.XContainer.Descendants%2A> eksenini kullanarak kodun yazılması genellikle daha hızlı ve kolaydır.</span><span class="sxs-lookup"><span data-stu-id="1571c-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1571c-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="1571c-106">Example</span></span>  
 <span data-ttu-id="1571c-107">Bu örnek <xref:System.Linq.Enumerable.First%2A> standart sorgu işlecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="1571c-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 <span data-ttu-id="1571c-108">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1571c-108">This code produces the following output:</span></span>  
  
```console  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="1571c-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="1571c-109">Example</span></span>  
 <span data-ttu-id="1571c-110">Aşağıdaki örnek, bir ad alanında bulunan XML için aynı sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1571c-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="1571c-111">Daha fazla bilgi için bkz. [ad alanlarına genel bakış (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="1571c-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="1571c-112">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="1571c-112">This code produces the following output:</span></span>  
  
```console  
GC3 Value  
```  
  
## <a name="see-also"></a><span data-ttu-id="1571c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1571c-113">See also</span></span>

- [<span data-ttu-id="1571c-114">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1571c-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
