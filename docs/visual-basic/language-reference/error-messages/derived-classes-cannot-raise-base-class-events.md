---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835147"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="8ec4d-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="8ec4d-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="8ec4d-103">Bir olay, yalnızca içinde bildirildiği bildirim alanından yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="8ec4d-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="8ec4d-104">Bu nedenle, bir sınıf, olayları herhangi başka bir sınıftan, hatta bir türetilir oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="8ec4d-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="8ec4d-105">**Hata Kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="8ec4d-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ec4d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="8ec4d-106">To correct this error</span></span>  
  
-   <span data-ttu-id="8ec4d-107">Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="8ec4d-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec4d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec4d-108">See also</span></span>

- [<span data-ttu-id="8ec4d-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ec4d-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="8ec4d-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="8ec4d-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
