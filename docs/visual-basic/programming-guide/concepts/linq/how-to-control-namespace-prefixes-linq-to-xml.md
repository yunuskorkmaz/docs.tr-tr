---
title: 'Nasıl yapılır: Denetim ad alanı önekleri (Visual Basic) (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
ms.openlocfilehash: 2b89b49aa76df526c08143cad49685386ffd5e7c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709816"
---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a><span data-ttu-id="42a92-102">Nasıl yapılır: Denetim ad alanı önekleri (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="42a92-102">How to: Control Namespace Prefixes (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="42a92-103">Bu konuda, ad alanı öneklerini nasıl denetleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="42a92-103">This topic describes how you can control namespace prefixes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42a92-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="42a92-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="42a92-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42a92-105">Description</span></span>  
 <span data-ttu-id="42a92-106">Bu örnek iki ad alanı bildirir.</span><span class="sxs-lookup"><span data-stu-id="42a92-106">This example declares two namespaces.</span></span> <span data-ttu-id="42a92-107">`http://www.adventure-works.com` Ad alanının öneki `aw`olduğunu ve `www.fourthcoffee.com` ad alanının öneki `fc`olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="42a92-107">It specifies that the `http://www.adventure-works.com` namespace has the prefix `aw`, and that the `www.fourthcoffee.com` namespace has the prefix of `fc`.</span></span>  
  
### <a name="code"></a><span data-ttu-id="42a92-108">Kod</span><span class="sxs-lookup"><span data-stu-id="42a92-108">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="42a92-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42a92-109">Comments</span></span>  
 <span data-ttu-id="42a92-110">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="42a92-110">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42a92-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42a92-111">See also</span></span>

- [<span data-ttu-id="42a92-112">Ad alanlarına genel bakış (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42a92-112">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
