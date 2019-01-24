---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 3cb61a40e4522695b876d85f67dac1a109d3c3e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595870"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="3a000-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="3a000-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="3a000-103">Bir olay, yalnızca içinde bildirildiği bildirim alanından yükseltilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a000-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="3a000-104">Bu nedenle, bir sınıf, olayları herhangi başka bir sınıftan, hatta bir türetilir oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="3a000-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="3a000-105">**Hata Kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="3a000-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3a000-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3a000-106">To correct this error</span></span>  
  
-   <span data-ttu-id="3a000-107">Taşıma `Event` deyimi veya `RaiseEvent` aynı sınıfta şekilde deyimi.</span><span class="sxs-lookup"><span data-stu-id="3a000-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a000-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a000-108">See also</span></span>
- [<span data-ttu-id="3a000-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="3a000-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="3a000-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="3a000-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
