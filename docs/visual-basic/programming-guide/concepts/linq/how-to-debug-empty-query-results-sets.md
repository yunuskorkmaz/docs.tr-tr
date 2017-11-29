---
title: "Nasıl yapılır: hata ayıklama boş sorgu sonuç kümeleri (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c483153f8ff41c08cfaa0141fed056de7f5f680
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="64452-102">Nasıl yapılır: hata ayıklama boş sorgu sonuç kümeleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64452-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="64452-103">XML ağaçları sorgulanırken en yaygın sorunları XML ağacında bir varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanındaki Geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="64452-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="64452-104">Bu konudaki örnekler ilk kümesi, bir varsayılan ad alanı XML yüklenir ve yanlış sorgulanan tipik bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="64452-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="64452-105">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64452-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="64452-106">Daha fazla bilgi için bkz: [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="64452-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64452-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="64452-107">Example</span></span>  
 <span data-ttu-id="64452-108">Bu örnek, bir ad alanındaki XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64452-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="64452-109">Bu örnekte aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="64452-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="64452-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="64452-110">Example</span></span>  
 <span data-ttu-id="64452-111">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64452-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="64452-112">Bildirme ve bir genel varsayılan ad alanı başlatmak için kullanılan çözümüdür.</span><span class="sxs-lookup"><span data-stu-id="64452-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="64452-113">Bu, varsayılan ad alanını tüm XML özellikleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="64452-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="64452-114">Başka bir değişiklikler örneği düzgün çalışması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="64452-114">No other modifications are required to the example to make it work properly.</span></span>  
  
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
  
 <span data-ttu-id="64452-115">Bu örnekte aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="64452-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="64452-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64452-116">See Also</span></span>  
 [<span data-ttu-id="64452-117">Temel sorgu (LINQ-XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64452-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
