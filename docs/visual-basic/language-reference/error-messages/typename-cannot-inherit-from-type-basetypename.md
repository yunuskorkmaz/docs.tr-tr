---
title: '&#39;&lt;TypeName&gt; &#39; devralınmalıdır olamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598430"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="36296-102">&#39;&lt;TypeName&gt; &#39; devralınmalıdır olamaz &lt;türü&gt; &#39; &lt;basetypename&gt; &#39; taban erişimini genişlettiğinden &lt;türü&gt; derleme dışına</span><span class="sxs-lookup"><span data-stu-id="36296-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="36296-103">Sınıfta veya arabirimde bir taban sınıftan veya arabirim ancak daha az kısıtlayıcı bir erişim düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="36296-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="36296-104">Örneğin, bir `Public` arabirimi devralan bir `Friend` arabirimi, veya bir `Protected` sınıfı bir `Private` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="36296-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="36296-105">Bu, taban sınıf veya hedeflenen düzeyini aştığını erişmek için arabirim sunar.</span><span class="sxs-lookup"><span data-stu-id="36296-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="36296-106">**Hata Kimliği:** BC30910</span><span class="sxs-lookup"><span data-stu-id="36296-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36296-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="36296-107">To correct this error</span></span>  
  
-   <span data-ttu-id="36296-108">Türetilmiş sınıf veya en az olabildiğince kısıtlayıcı, temel sınıf veya arabirim arabirime erişim düzeyini değiştirin.</span><span class="sxs-lookup"><span data-stu-id="36296-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="36296-109">-veya-</span><span class="sxs-lookup"><span data-stu-id="36296-109">-or-</span></span>  
  
-   <span data-ttu-id="36296-110">Daha az kısıtlayıcı erişim düzeyi gerekiyorsa kaldırma `Inherits` deyimi.</span><span class="sxs-lookup"><span data-stu-id="36296-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="36296-111">Bir daha kısıtlı bir temel sınıf veya arabirim devralır olamaz.</span><span class="sxs-lookup"><span data-stu-id="36296-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36296-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36296-112">See Also</span></span>  
 [<span data-ttu-id="36296-113">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="36296-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="36296-114">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="36296-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="36296-115">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="36296-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="36296-116">Visual Basic'de erişim düzeyleri</span><span class="sxs-lookup"><span data-stu-id="36296-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
