---
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 7b86420466d77a6aa45b1201a9375b4433e4b5ec
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163447"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="18e9d-102">BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="18e9d-102">BC30029: Derived classes cannot raise base class events</span></span>

<span data-ttu-id="18e9d-103">Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="18e9d-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="18e9d-104">Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="18e9d-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>

 <span data-ttu-id="18e9d-105">**Hata kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="18e9d-105">**Error ID:** BC30029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="18e9d-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="18e9d-106">To correct this error</span></span>

- <span data-ttu-id="18e9d-107">`Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="18e9d-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>

## <a name="see-also"></a><span data-ttu-id="18e9d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18e9d-108">See also</span></span>

- [<span data-ttu-id="18e9d-109">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="18e9d-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="18e9d-110">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="18e9d-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
