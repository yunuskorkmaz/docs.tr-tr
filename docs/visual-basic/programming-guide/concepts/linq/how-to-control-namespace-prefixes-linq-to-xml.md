---
title: 'Nasıl yapılır: Denetim Namespace önekleri (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 7e5a05d2fa93e61338f450d0a4d890fa94c04fd2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839047"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="08aff-102">Nasıl yapılır: Denetim Namespace önekleri (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="08aff-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="08aff-103">Bu konuda, ad alanı öneklerini nasıl denetleyebileceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="08aff-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08aff-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="08aff-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="08aff-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08aff-105">Description</span></span>  
 <span data-ttu-id="08aff-106">Bu örnek iki ad alanları bildirir.</span><span class="sxs-lookup"><span data-stu-id="08aff-106">This example declares two namespaces.</span></span> <span data-ttu-id="08aff-107">Belirtir `http://www.adventure-works.com` ad alanı öneki olan `aw`ve `www.fourthcoffee.com` ad alanı öneki olan `fc`.</span><span class="sxs-lookup"><span data-stu-id="08aff-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="08aff-108">Kod</span><span class="sxs-lookup"><span data-stu-id="08aff-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="08aff-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08aff-109">Comments</span></span>  
 <span data-ttu-id="08aff-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="08aff-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="08aff-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08aff-111">See also</span></span>

- [<span data-ttu-id="08aff-112">XML ad alanları (Visual Basic) ile çalışma</span><span class="sxs-lookup"><span data-stu-id="08aff-112">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
