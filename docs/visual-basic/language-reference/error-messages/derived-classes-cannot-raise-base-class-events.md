---
description: 'Hakkında daha fazla bilgi edinin: BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz'
title: Türetilmiş sınıflar temel sınıf olayları oluşturamaz
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 68546f2654f7c34fcb309d5af68e237d5f1eac79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796606"
---
# <a name="bc30029-derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="26a73-103">BC30029: türetilmiş sınıflar temel sınıf olayları oluşturamaz</span><span class="sxs-lookup"><span data-stu-id="26a73-103">BC30029: Derived classes cannot raise base class events</span></span>

<span data-ttu-id="26a73-104">Bir olay yalnızca bildirildiği bildirim alanından oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="26a73-104">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="26a73-105">Bu nedenle, bir sınıf türetilmiş bir sınıftan bile diğer bir sınıftan olay oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="26a73-105">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>

 <span data-ttu-id="26a73-106">**Hata kimliği:** BC30029</span><span class="sxs-lookup"><span data-stu-id="26a73-106">**Error ID:** BC30029</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="26a73-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="26a73-107">To correct this error</span></span>

- <span data-ttu-id="26a73-108">`Event`İfadeyi veya `RaiseEvent` ifadeyi aynı sınıfta olacak şekilde taşıyın.</span><span class="sxs-lookup"><span data-stu-id="26a73-108">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>

## <a name="see-also"></a><span data-ttu-id="26a73-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26a73-109">See also</span></span>

- [<span data-ttu-id="26a73-110">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="26a73-110">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="26a73-111">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="26a73-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
