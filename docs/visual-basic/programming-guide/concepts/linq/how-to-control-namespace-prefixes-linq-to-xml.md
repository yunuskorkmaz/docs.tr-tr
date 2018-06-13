---
title: 'Nasıl yapılır: denetim Namespace önekleri (Visual Basic) (LINQ-XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: f60f90ef6742dfd725f51ff7e760436117346e85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641686"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="285d1-102">Nasıl yapılır: denetim Namespace önekleri (Visual Basic) (LINQ-XML)</span><span class="sxs-lookup"><span data-stu-id="285d1-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="285d1-103">Bu konu, ad alanı öneklerini nasıl kontrol edebilir açıklar.</span><span class="sxs-lookup"><span data-stu-id="285d1-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="285d1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="285d1-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="285d1-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="285d1-105">Description</span></span>  
 <span data-ttu-id="285d1-106">Bu örnek iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="285d1-106">This example declares two namespaces.</span></span> <span data-ttu-id="285d1-107">Gerektiğini belirtir `http://www.adventure-works.com` ad alanı öneki var. `aw`ve `www.fourthcoffee.com` ad alanı öneki var. `fc`.</span><span class="sxs-lookup"><span data-stu-id="285d1-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="285d1-108">Kod</span><span class="sxs-lookup"><span data-stu-id="285d1-108">Code</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="285d1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="285d1-109">Comments</span></span>  
 <span data-ttu-id="285d1-110">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="285d1-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="285d1-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="285d1-111">See Also</span></span>  
 [<span data-ttu-id="285d1-112">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="285d1-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
