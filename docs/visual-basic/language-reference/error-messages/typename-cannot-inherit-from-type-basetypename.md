---
title: "'<typename>', <type> temelinin erişimini derleme dışına genişlettiğinden <basetypename> '<type>' öğesinden devralamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764367"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="521ab-102">'\<typename >' öğesinden devralamaz \<türü > '\<basetypename >' temelinin erişimini genişlettiğinden \<türü > derleme dışından</span><span class="sxs-lookup"><span data-stu-id="521ab-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="521ab-103">Bir sınıf veya arabirim bir temel sınıftan devraldığı veya arabirimi ancak daha az kısıtlayıcı bir erişim düzeyi yok.</span><span class="sxs-lookup"><span data-stu-id="521ab-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="521ab-104">Örneğin, bir `Public` arabirim sınıfından devralan bir `Friend` arabirimi veya `Protected` sınıfının devraldığı bir `Private` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="521ab-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="521ab-105">Bu, temel sınıf veya hedeflenen düzeyinin ötesinde erişmek için bir arabirimi kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="521ab-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="521ab-106">**Hata Kimliği:** BC30910</span><span class="sxs-lookup"><span data-stu-id="521ab-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="521ab-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="521ab-107">To correct this error</span></span>  
  
- <span data-ttu-id="521ab-108">Türetilmiş bir sınıf veya arabirim en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim erişim düzeyini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="521ab-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="521ab-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="521ab-109">-or-</span></span>  
  
- <span data-ttu-id="521ab-110">Daha az kısıtlayıcı erişim düzeyi gerekiyorsa, kaldırma `Inherits` deyimi.</span><span class="sxs-lookup"><span data-stu-id="521ab-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="521ab-111">Bir daha kısıtlı bir temel sınıfı veya arabirimi devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="521ab-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="521ab-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="521ab-112">See also</span></span>

- [<span data-ttu-id="521ab-113">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="521ab-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="521ab-114">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="521ab-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="521ab-115">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="521ab-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="521ab-116">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="521ab-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
