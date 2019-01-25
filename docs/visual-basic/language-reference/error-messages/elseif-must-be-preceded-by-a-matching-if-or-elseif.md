---
title: '&#39;#ElseIf&#39; eşleşen bir gelmelidir &#39;#If&#39; veya &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 1e63595ee573e9356f6870a02b2131897c725baf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505789"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="9d31a-102">&#39;#ElseIf&#39; eşleşen bir gelmelidir &#39;#If&#39; veya &#39;#ElseIf&#39;</span><span class="sxs-lookup"><span data-stu-id="9d31a-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="9d31a-103">`#ElseIf` Koşullu derleme yönergesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="9d31a-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="9d31a-104">Bir `#ElseIf` yan tümcesi gerekir öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9d31a-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="9d31a-105">**Hata Kimliği:** BC30014</span><span class="sxs-lookup"><span data-stu-id="9d31a-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d31a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9d31a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9d31a-107">Bu maddeyi bir önceki `#If` veya `#ElseIf` bu ayrılmış değil `#ElseIf` bir müdahalede bulunan koşullu derleme blok veya yanlış yerleştirilmiş `#End If`.</span><span class="sxs-lookup"><span data-stu-id="9d31a-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="9d31a-108">Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırabilir ya da `#Else` veya değiştirmek için bir `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="9d31a-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="9d31a-109">Diğer her şey sırayla ekleyin bir `#If` koşullu derleme blok başına yönerge.</span><span class="sxs-lookup"><span data-stu-id="9d31a-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d31a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d31a-110">See also</span></span>
- [<span data-ttu-id="9d31a-111">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="9d31a-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
