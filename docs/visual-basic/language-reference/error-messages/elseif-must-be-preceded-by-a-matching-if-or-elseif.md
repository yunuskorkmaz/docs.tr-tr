---
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 808cf35fb05da092cdef560721b2f667778aa78f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409666"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="e47b0-102">'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır</span><span class="sxs-lookup"><span data-stu-id="e47b0-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="e47b0-103">`#ElseIf`, koşullu bir derleme yönergedir.</span><span class="sxs-lookup"><span data-stu-id="e47b0-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="e47b0-104">Bir `#ElseIf` yan tümcesinin önünde bir eşleşen `#If` or `#ElseIf` yan tümcesi gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="e47b0-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="e47b0-105">**Hata kimliği:** BC30014</span><span class="sxs-lookup"><span data-stu-id="e47b0-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e47b0-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e47b0-106">To correct this error</span></span>  
  
1. <span data-ttu-id="e47b0-107">Önceki `#If` veya `#ElseIf` bunun, bir `#ElseIf` araya giren koşullu derleme bloğu veya hatalı bir şekilde yerleştirilmiş olduğunu kontrol edin `#End If` .</span><span class="sxs-lookup"><span data-stu-id="e47b0-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2. <span data-ttu-id="e47b0-108">`#ElseIf`Önünde bir yönerge varsa, `#Else` veya öğesini kaldırın ya da `#Else` bir olarak değiştirin `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="e47b0-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3. <span data-ttu-id="e47b0-109">Başka her şey sıralamayla, `#If` koşullu derleme bloğunun başlangıcına bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e47b0-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e47b0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e47b0-110">See also</span></span>

- [<span data-ttu-id="e47b0-111">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="e47b0-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
