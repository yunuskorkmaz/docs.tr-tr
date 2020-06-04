---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409705"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="4d3a8-102">Türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="4d3a8-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="4d3a8-103">Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="4d3a8-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="4d3a8-104">Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="4d3a8-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="4d3a8-105">**Hata kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="4d3a8-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4d3a8-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4d3a8-106">To correct this error</span></span>  
  
- <span data-ttu-id="4d3a8-107">`Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="4d3a8-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d3a8-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d3a8-108">See also</span></span>

- [<span data-ttu-id="4d3a8-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="4d3a8-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="4d3a8-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="4d3a8-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
