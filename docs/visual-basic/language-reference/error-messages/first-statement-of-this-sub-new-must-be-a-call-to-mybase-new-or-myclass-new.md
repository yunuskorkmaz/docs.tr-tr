---
title: Bu ilk deyimi &#39;Sub New&#39; yapılan bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; (No Parametreler olmadan erişilebilir yapıcı)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 3b24385932700a4843ae295bc82ef9529cc86b9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589466"
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="10f1b-102">Bu ilk deyimi &#39;Sub New&#39; yapılan bir çağrı olmalıdır &#39;MyBase.New&#39; veya &#39;MyClass.New&#39; (No Parametreler olmadan erişilebilir yapıcı)</span><span class="sxs-lookup"><span data-stu-id="10f1b-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="10f1b-103">Bu 'Sub New' ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır, çünkü temel sınıfı\<basename >', '\<derivedname >' bir erişilebilir 'Sub bağımsız değişkenler olmadan çağrılabilen New' yok.</span><span class="sxs-lookup"><span data-stu-id="10f1b-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="10f1b-104">Türetilen bir sınıfta her Oluşturucusu bir temel sınıf oluşturucu çağırmanız gerekir (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="10f1b-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="10f1b-105">Taban sınıfı türetilen sınıflar için erişilebilir olan bir parametresiz oluşturucu varsa `MyBase.New` otomatik olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="10f1b-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="10f1b-106">Yoksa, bir taban sınıf oluşturucu parametrelerle çağrılması gerekir ve bu otomatik olarak yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="10f1b-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="10f1b-107">Bu durumda, her türetilmiş sınıf oluşturucu ilk deyimi gerekir parametreli Oluşturucusu çağrı üzerinde temel sınıfı veya başka bir oluşturucu çağrısı bir temel sınıf oluşturucu yapar türetilen sınıfta çağırın.</span><span class="sxs-lookup"><span data-stu-id="10f1b-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="10f1b-108">**Hata Kimliği:** BC30148</span><span class="sxs-lookup"><span data-stu-id="10f1b-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="10f1b-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="10f1b-109">To correct this error</span></span>  
  
-   <span data-ttu-id="10f1b-110">Her iki çağrı `MyBase.New` gerekli parametreleri belirtin veya böyle bir çağrı yapar eş Oluşturucusu çağırın.</span><span class="sxs-lookup"><span data-stu-id="10f1b-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="10f1b-111">Örneğin, temel sınıf olarak bildirilen bir oluşturucu varsa `Public Sub New(ByVal index as Integer)`, ilk ifade türetilen sınıf oluşturucu olabilir `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="10f1b-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10f1b-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="10f1b-112">See Also</span></span>  
 [<span data-ttu-id="10f1b-113">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="10f1b-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
