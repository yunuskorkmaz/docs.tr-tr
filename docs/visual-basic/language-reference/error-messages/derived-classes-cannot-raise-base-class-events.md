---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586405"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="c3bd2-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="c3bd2-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="c3bd2-103">Bir olay, içinde bildirildiği yalnızca bildirim alanından yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="c3bd2-104">Bu nedenle, bir sınıfın başka bir sınıf, hatta bir onu türetildiği olaylarından yükseltemez.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="c3bd2-105">**Hata Kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="c3bd2-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c3bd2-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c3bd2-106">To correct this error</span></span>  
  
-   <span data-ttu-id="c3bd2-107">Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta; bu nedenle deyimi.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3bd2-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3bd2-108">See Also</span></span>  
 [<span data-ttu-id="c3bd2-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="c3bd2-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="c3bd2-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="c3bd2-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
