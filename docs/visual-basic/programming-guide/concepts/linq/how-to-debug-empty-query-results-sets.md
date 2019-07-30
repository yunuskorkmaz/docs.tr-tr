---
title: 'Nasıl yapılır: Boş sorgu sonuçları kümelerinde hata ayıkla (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 076e7109dc89294ba0c1706bf9a66120e6a0b85d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630982"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="6c27e-102">Nasıl yapılır: Boş sorgu sonuçları kümelerinde hata ayıkla (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c27e-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="6c27e-103">XML ağaçlarını sorgularken en yaygın sorunlardan biri, XML ağacının varsayılan bir ad alanına sahip olması ve geliştiricinin bazen sorguyu bir ad alanında olmamasına rağmen yazar.</span><span class="sxs-lookup"><span data-stu-id="6c27e-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="6c27e-104">Bu konudaki ilk örnek kümesi, varsayılan bir ad alanındaki XML 'nin yüklendiği ve yanlış sorgulandığı tipik bir yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c27e-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="6c27e-105">İkinci örnek kümesinde, bir ad alanında XML 'yi sorgulayabilmeniz için gerekli düzeltmeler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c27e-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="6c27e-106">Daha fazla bilgi için bkz. [XML ad alanları Ile çalışma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="6c27e-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>

## <a name="example"></a><span data-ttu-id="6c27e-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c27e-107">Example</span></span>

<span data-ttu-id="6c27e-108">Bu örnek, bir ad alanında XML oluşturmayı ve boş bir sonuç kümesi döndüren bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c27e-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```vb
Dim root As XElement = _
    <Root xmlns='http://www.adventure-works.com'>
        <Child>1</Child>
        <Child>2</Child>
        <Child>3</Child>
        <AnotherChild>4</AnotherChild>
        <AnotherChild>5</AnotherChild>
        <AnotherChild>6</AnotherChild>
    </Root>
Dim c1 As IEnumerable(Of XElement) = _
        From el In root.<Child> _
        Select el
Console.WriteLine("Result set follows:")
For Each el As XElement In c1
    Console.WriteLine(el.Value)
Next
Console.WriteLine("End of result set")
```

<span data-ttu-id="6c27e-109">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="6c27e-109">This example produces the following result:</span></span>

```
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="6c27e-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="6c27e-110">Example</span></span>

<span data-ttu-id="6c27e-111">Bu örnek, bir ad alanında XML oluşturmayı ve düzgün kodlanmış bir sorguyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c27e-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="6c27e-112">Çözüm, genel bir varsayılan ad alanını bildirmek ve başlatmak.</span><span class="sxs-lookup"><span data-stu-id="6c27e-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="6c27e-113">Bu, tüm XML özelliklerini varsayılan ad alanına koyar.</span><span class="sxs-lookup"><span data-stu-id="6c27e-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="6c27e-114">Doğru çalışması için örnek için başka bir değişiklik yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6c27e-114">No other modifications are required to the example to make it work properly.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="6c27e-115">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="6c27e-115">This example produces the following result:</span></span>

```
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="6c27e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c27e-116">See also</span></span>

- [<span data-ttu-id="6c27e-117">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c27e-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
