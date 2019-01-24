---
title: '&#39;&lt;TypeName&gt; &#39; devralamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; temelinin erişimini genişlettiğinden &lt;türü&gt; derleme dışından'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556489"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="96044-102">&#39;&lt;TypeName&gt; &#39; devralamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; temelinin erişimini genişlettiğinden &lt;türü&gt; derleme dışından</span><span class="sxs-lookup"><span data-stu-id="96044-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="96044-103">Bir sınıf veya arabirim bir temel sınıftan devraldığı veya arabirimi ancak daha az kısıtlayıcı bir erişim düzeyi yok.</span><span class="sxs-lookup"><span data-stu-id="96044-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="96044-104">Örneğin, bir `Public` arabirim sınıfından devralan bir `Friend` arabirimi veya `Protected` sınıfının devraldığı bir `Private` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="96044-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="96044-105">Bu, temel sınıf veya hedeflenen düzeyinin ötesinde erişmek için bir arabirimi kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="96044-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="96044-106">**Hata Kimliği:** BC30910</span><span class="sxs-lookup"><span data-stu-id="96044-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="96044-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="96044-107">To correct this error</span></span>  
  
-   <span data-ttu-id="96044-108">Türetilmiş bir sınıf veya arabirim en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim erişim düzeyini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="96044-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="96044-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="96044-109">-or-</span></span>  
  
-   <span data-ttu-id="96044-110">Daha az kısıtlayıcı erişim düzeyi gerekiyorsa, kaldırma `Inherits` deyimi.</span><span class="sxs-lookup"><span data-stu-id="96044-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="96044-111">Bir daha kısıtlı bir temel sınıfı veya arabirimi devralınamaz.</span><span class="sxs-lookup"><span data-stu-id="96044-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96044-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96044-112">See also</span></span>
- [<span data-ttu-id="96044-113">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="96044-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="96044-114">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="96044-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="96044-115">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="96044-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="96044-116">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="96044-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
