---
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: d6fa76b2aba45e3455cef6ceafc0f737ef56225d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271557"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="6204c-102">'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır</span><span class="sxs-lookup"><span data-stu-id="6204c-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="6204c-103">`#ElseIf` Koşullu derleme yönergesi ' dir.</span><span class="sxs-lookup"><span data-stu-id="6204c-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="6204c-104">Bir `#ElseIf` yan tümcesi gerekir öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="6204c-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="6204c-105">**Hata Kimliği:** BC30014</span><span class="sxs-lookup"><span data-stu-id="6204c-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6204c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6204c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6204c-107">Bu maddeyi bir önceki `#If` veya `#ElseIf` bu ayrılmış değil `#ElseIf` bir müdahalede bulunan koşullu derleme blok veya yanlış yerleştirilmiş `#End If`.</span><span class="sxs-lookup"><span data-stu-id="6204c-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="6204c-108">Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırabilir ya da `#Else` veya değiştirmek için bir `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="6204c-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="6204c-109">Diğer her şey sırayla ekleyin bir `#If` koşullu derleme blok başına yönerge.</span><span class="sxs-lookup"><span data-stu-id="6204c-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6204c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6204c-110">See also</span></span>
- [<span data-ttu-id="6204c-111">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="6204c-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
