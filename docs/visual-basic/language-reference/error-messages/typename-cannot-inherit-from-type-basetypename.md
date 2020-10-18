---
title: "'<typename>', <type> temelinin erişimini derleme dışına genişlettiğinden <basetypename> '<type>' öğesinden devralamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 5c019f9d74b11e48aa05a1480b9449fa28488b43
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161848"
---
# <a name="bc30910-typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="4c706-102">BC30910: ' ', \<typename> \<type> \<basetypename> temel erişimini \<type> derleme dışına genişlettiğinden ' ' öğesinden devralma</span><span class="sxs-lookup"><span data-stu-id="4c706-102">BC30910: '\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>

<span data-ttu-id="4c706-103">Bir sınıf veya arabirim, temel bir sınıftan veya arabirimden devralınır, ancak daha az kısıtlayıcı erişim düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4c706-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>

 <span data-ttu-id="4c706-104">Örneğin, bir `Public` arabirim bir arabirimden devralınır veya bir sınıf bir `Friend` `Protected` sınıftan devralınır `Private` .</span><span class="sxs-lookup"><span data-stu-id="4c706-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="4c706-105">Bu, hedeflenen düzeyin ötesine erişmek için temel sınıfı veya arabirimi kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="4c706-105">This exposes the base class or interface to access beyond the intended level.</span></span>

 <span data-ttu-id="4c706-106">**Hata kimliği:** BC30910</span><span class="sxs-lookup"><span data-stu-id="4c706-106">**Error ID:** BC30910</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="4c706-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="4c706-107">To correct this error</span></span>

- <span data-ttu-id="4c706-108">Türetilmiş sınıfın veya arabirimin erişim düzeyini, en az temel sınıf veya arabirim ile kısıtlayıcı olacak şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="4c706-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>

     <span data-ttu-id="4c706-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="4c706-109">-or-</span></span>

- <span data-ttu-id="4c706-110">Daha az kısıtlayıcı erişim düzeyine ihtiyacınız varsa, `Inherits` ifadesini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="4c706-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="4c706-111">Daha kısıtlı bir temel sınıftan veya arabirimden devralma yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="4c706-111">You cannot inherit from a more restricted base class or interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c706-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c706-112">See also</span></span>

- [<span data-ttu-id="4c706-113">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c706-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="4c706-114">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c706-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="4c706-115">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="4c706-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="4c706-116">Visual Basic erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="4c706-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
