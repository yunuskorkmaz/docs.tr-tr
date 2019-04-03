---
title: 'Nasıl yapılır: Boş sorgu sonucu kümelerinin (Visual Basic) hata ayıklama'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 80e505be03a26f80bbba9d3673732505b27e9598
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822802"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="cc3f2-102">Nasıl yapılır: Boş sorgu sonucu kümelerinin (Visual Basic) hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="cc3f2-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="cc3f2-103">XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="cc3f2-104">Bu konudaki örnekler ilk kümesi, varsayılan ad alanı XML yüklenir ve hatalı sorgulanır normal bir şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="cc3f2-105">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="cc3f2-106">Daha fazla bilgi için [(Visual Basic) XML ad alanları ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="cc3f2-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc3f2-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc3f2-107">Example</span></span>  
 <span data-ttu-id="cc3f2-108">Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="cc3f2-109">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="cc3f2-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="cc3f2-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="cc3f2-110">Example</span></span>  
 <span data-ttu-id="cc3f2-111">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="cc3f2-112">Bildirmek ve bir genel varsayılan ad alanı başlatmak için kullanılan çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="cc3f2-113">Bu, varsayılan ad alanındaki tüm XML özellikleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="cc3f2-114">Herhangi bir değişiklik örneği düzgün çalışması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-114">No other modifications are required to the example to make it work properly.</span></span>  
  
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
  
 <span data-ttu-id="cc3f2-115">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="cc3f2-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc3f2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cc3f2-116">See also</span></span>

- [<span data-ttu-id="cc3f2-117">Temel sorgular (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc3f2-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
