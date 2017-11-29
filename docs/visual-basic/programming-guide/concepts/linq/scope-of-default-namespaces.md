---
title: "Visual Basic'de varsayılan ad alanları kapsamı"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aaf5395f1216b0cb56f2d1f003e42ed30790012
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="8a40e-102">Visual Basic'de varsayılan ad alanları kapsamı</span><span class="sxs-lookup"><span data-stu-id="8a40e-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="8a40e-103">XML ağacında belirtildiği şekilde varsayılan ad alanları sorgular için kapsamında değildir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="8a40e-104">Varsayılan ad alanı içinde XML varsa, yine bildirmelisiniz bir <xref:System.Xml.Linq.XNamespace> , değişken ve Sorguda kullanılacak bir tam ad yapmak için yerel ad ile birleştirerek.</span><span class="sxs-lookup"><span data-stu-id="8a40e-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="8a40e-105">XML ağaçları sorgulanırken en yaygın sorunları XML ağacında bir varsayılan ad alanı varsa, XML değil gibi davranarak bir ad alanındaki Geliştirici bazen sorgu yazdığını biridir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="8a40e-106">Bu konudaki örnekler ilk kümesi, bir varsayılan ad alanı XML yüklenir, ancak yanlış sorgulanan tipik bir yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="8a40e-107">XML ad alanında sorgulayabilmesi ikinci örneklerde gerekli düzeltmeleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a40e-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a40e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a40e-108">Example</span></span>  
 <span data-ttu-id="8a40e-109">Bu örnek, bir ad alanındaki XML oluşturulmasını gösterir ve boş bir sonuç döndüren bir sorgu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="8a40e-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a40e-110">Kod</span><span class="sxs-lookup"><span data-stu-id="8a40e-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8a40e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a40e-111">Comments</span></span>  
 <span data-ttu-id="8a40e-112">Bu örnekte aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="8a40e-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="8a40e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="8a40e-113">Example</span></span>  
 <span data-ttu-id="8a40e-114">Bu örnek, bir ad alanı ve düzgün şekilde kodlanmış bir sorgu XML oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="8a40e-115">Yukarıdaki yanlış kodlanmış örnek aksine, Visual Basic kullanırken doğru bildirin ve genel varsayılan ad alanı başlatma yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8a40e-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="8a40e-116">Bu, varsayılan ad alanını tüm XML özellikleri yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="8a40e-117">Başka bir değişiklikler örneği düzgün çalışması için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="8a40e-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8a40e-118">Kod</span><span class="sxs-lookup"><span data-stu-id="8a40e-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8a40e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8a40e-119">Comments</span></span>  
 <span data-ttu-id="8a40e-120">Bu örnekte aşağıdaki sonucu üretir:</span><span class="sxs-lookup"><span data-stu-id="8a40e-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="8a40e-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a40e-121">See Also</span></span>  
 [<span data-ttu-id="8a40e-122">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="8a40e-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
