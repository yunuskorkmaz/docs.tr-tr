---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 3fe3faaa3637446bb6ab443ba1d6e1d1004b4d48
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400324"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="7244d-102">Deyim, bir satır 'If' deyimi dışında blok sona erdiremez</span><span class="sxs-lookup"><span data-stu-id="7244d-102">Statement cannot end a block outside of a line 'If' statement</span></span>
<span data-ttu-id="7244d-103">Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` .</span><span class="sxs-lookup"><span data-stu-id="7244d-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="7244d-104">Tek satırlı `If` deyimler `End If` deyimini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="7244d-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="7244d-105">**Hata kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="7244d-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7244d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7244d-106">To correct this error</span></span>  
  
- <span data-ttu-id="7244d-107">Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .</span><span class="sxs-lookup"><span data-stu-id="7244d-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7244d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7244d-108">See also</span></span>

- [<span data-ttu-id="7244d-109">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="7244d-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
