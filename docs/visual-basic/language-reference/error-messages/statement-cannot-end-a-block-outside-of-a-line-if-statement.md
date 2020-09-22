---
title: Deyim, bir satır 'If' deyimi dışında blok sona erdiremez
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: 5e75c29e57a9c04c66e6bca79d99bb18c513f667
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870739"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-if-statement"></a><span data-ttu-id="33eba-102">Deyim, bir satır 'If' deyimi dışında blok sona erdiremez</span><span class="sxs-lookup"><span data-stu-id="33eba-102">Statement cannot end a block outside of a line 'If' statement</span></span>

<span data-ttu-id="33eba-103">Tek satırlı bir `If` deyim, iki nokta üst üste (:), `End` tek satır dışında bir denetim bloğu için bir deyim olan birden çok deyim içerir `If` .</span><span class="sxs-lookup"><span data-stu-id="33eba-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="33eba-104">Tek satırlı `If` deyimler `End If` deyimini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="33eba-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="33eba-105">**Hata kimliği:** BC32005</span><span class="sxs-lookup"><span data-stu-id="33eba-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33eba-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="33eba-106">To correct this error</span></span>  
  
- <span data-ttu-id="33eba-107">Tek satırlı `If` ifadeyi, ifadesini içeren denetim bloğunun dışında taşıyın `End If` .</span><span class="sxs-lookup"><span data-stu-id="33eba-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33eba-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33eba-108">See also</span></span>

- [<span data-ttu-id="33eba-109">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="33eba-109">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
