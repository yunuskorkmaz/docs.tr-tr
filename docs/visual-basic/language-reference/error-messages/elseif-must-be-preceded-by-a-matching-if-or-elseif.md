---
description: "Daha fazla bilgi edinin: BC30014: ' #ElseIf ' öncesinde eşleşen bir ' #If ' veya ' #ElseIf olmalıdır"
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 5eeb9c2fc0fd7267d95a8713a7071cd08788e48b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796567"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="02d9d-103">BC30014: ' #ElseIf ' öncesinde eşleşen bir ' #If ' veya ' #ElseIf ' olmalıdır</span><span class="sxs-lookup"><span data-stu-id="02d9d-103">BC30014: '#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>

<span data-ttu-id="02d9d-104">`#ElseIf` , koşullu bir derleme yönergedir.</span><span class="sxs-lookup"><span data-stu-id="02d9d-104">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="02d9d-105">Bir `#ElseIf` yan tümcesinin önünde bir eşleşen `#If` or `#ElseIf` yan tümcesi gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="02d9d-105">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>

 <span data-ttu-id="02d9d-106">**Hata kimliği:** BC30014</span><span class="sxs-lookup"><span data-stu-id="02d9d-106">**Error ID:** BC30014</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="02d9d-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="02d9d-107">To correct this error</span></span>

1. <span data-ttu-id="02d9d-108">Önceki `#If` veya `#ElseIf` bunun, bir `#ElseIf` araya giren koşullu derleme bloğu veya hatalı bir şekilde yerleştirilmiş olduğunu kontrol edin `#End If` .</span><span class="sxs-lookup"><span data-stu-id="02d9d-108">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>

2. <span data-ttu-id="02d9d-109">`#ElseIf`Önünde bir yönerge varsa, `#Else` veya öğesini kaldırın ya da `#Else` bir olarak değiştirin `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="02d9d-109">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>

3. <span data-ttu-id="02d9d-110">Başka her şey sıralamayla, `#If` koşullu derleme bloğunun başlangıcına bir yönerge ekleyin.</span><span class="sxs-lookup"><span data-stu-id="02d9d-110">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>

## <a name="see-also"></a><span data-ttu-id="02d9d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02d9d-111">See also</span></span>

- [<span data-ttu-id="02d9d-112">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="02d9d-112">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
