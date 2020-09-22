---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0233a1584c5e871506b5c4762e98874c343f19b8
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874483"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="6f856-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="6f856-102">Derived classes cannot raise base class events</span></span>

<span data-ttu-id="6f856-103">Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="6f856-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="6f856-104">Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="6f856-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="6f856-105">**Hata kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="6f856-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6f856-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6f856-106">To correct this error</span></span>  
  
- <span data-ttu-id="6f856-107">`Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="6f856-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f856-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f856-108">See also</span></span>

- [<span data-ttu-id="6f856-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f856-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="6f856-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="6f856-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
