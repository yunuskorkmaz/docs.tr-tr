---
title: Visual Basic'de varsayılan ad alanlarının kapsamı
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8c48273f3788e20e24832be8bf2013af22419fac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527022"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="1656e-102">Visual Basic'de varsayılan ad alanlarının kapsamı</span><span class="sxs-lookup"><span data-stu-id="1656e-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="1656e-103">XML ağacı içinde gösterilen varsayılan ad alanı, sorgular için kapsamda değildir.</span><span class="sxs-lookup"><span data-stu-id="1656e-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="1656e-104">Yine de belirtmesi gerekir, varsayılan bir ad alanı XML varsa, bir <xref:System.Xml.Linq.XNamespace> değişkeni, sorguda kullanılan bir tam adı yerel adı ile birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1656e-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="1656e-105">XML ağaçlarını sorgulama sırasında sık karşılaşılan sorunlar XML ağacı varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanında geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="1656e-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="1656e-106">Bu konudaki örnekler ilk kümesi XML varsayılan ad alanı içinde yüklenir, ancak yanlış sorgulanır normal bir şekilde gösterir.</span><span class="sxs-lookup"><span data-stu-id="1656e-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="1656e-107">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1656e-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1656e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1656e-108">Example</span></span>  
 <span data-ttu-id="1656e-109">Bu örnek, bir ad alanında XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1656e-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1656e-110">Kod</span><span class="sxs-lookup"><span data-stu-id="1656e-110">Code</span></span>  
  
```vb  
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
  
### <a name="comments"></a><span data-ttu-id="1656e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1656e-111">Comments</span></span>  
 <span data-ttu-id="1656e-112">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="1656e-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="1656e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="1656e-113">Example</span></span>  
 <span data-ttu-id="1656e-114">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu içinde XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1656e-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="1656e-115">Yukarıdaki yanlış kodlanmış örnek aksine, Visual Basic kullanırken doğru bildirmek ve bir genel varsayılan ad alanı başlatmak için yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="1656e-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="1656e-116">Bu, varsayılan ad alanındaki tüm XML özellikleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="1656e-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="1656e-117">Herhangi bir değişiklik örneği düzgün çalışması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1656e-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1656e-118">Kod</span><span class="sxs-lookup"><span data-stu-id="1656e-118">Code</span></span>  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="1656e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1656e-119">Comments</span></span>  
 <span data-ttu-id="1656e-120">Bu örnek aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="1656e-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="1656e-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1656e-121">See also</span></span>
- [<span data-ttu-id="1656e-122">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="1656e-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
