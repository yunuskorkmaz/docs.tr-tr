---
title: Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır (Parametreler Olmadan Erişilebilir Yapıcı Yok)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: debab4e495d05a05801dd11850d0665c8bd6b299
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834328"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="5dfdd-102">Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır (Parametreler Olmadan Erişilebilir Yapıcı Yok)</span><span class="sxs-lookup"><span data-stu-id="5dfdd-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="5dfdd-103">Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' çağrısı olmalıdır, çünkü temel sınıfı\<basename >', '\<derivedname >' bir erişilebilir 'Sub bağımsız değişken olmadan çağrılabilecek New' yok.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="5dfdd-104">Türetilen bir sınıfta bir temel sınıf oluşturucusu her Oluşturucu çağırmanız gerekir (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="5dfdd-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="5dfdd-105">Temel sınıfın türetilmiş sınıflar için erişilebilir olan parametresiz bir oluşturucu varsa `MyBase.New` otomatik olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="5dfdd-106">Aksi halde bir temel sınıf oluşturucusunu parametrelerle çağrılması gerekir ve bu otomatik olarak yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="5dfdd-107">Bu durumda, her türetilmiş sınıf oluşturucusunun ilk deyimi gerekir parametreli bir kurucu taban sınıfını çağırın veya bir temel sınıf oluşturucusunu çağırma kılan türetilmiş bir sınıf içindeki başka bir oluşturucusunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="5dfdd-108">**Hata Kimliği:** BC30148</span><span class="sxs-lookup"><span data-stu-id="5dfdd-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5dfdd-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5dfdd-109">To correct this error</span></span>  
  
-   <span data-ttu-id="5dfdd-110">Her iki çağrı `MyBase.New` gerekli parametreleri belirtin veya bu tür bir çağrıda bir eş oluşturucusunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="5dfdd-111">Örneğin, temel sınıf olarak bildirilen bir oluşturucusu varsa `Public Sub New(ByVal index as Integer)`, ilk ifade türetilen sınıf oluşturucusu olabilir `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dfdd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dfdd-112">See also</span></span>

- [<span data-ttu-id="5dfdd-113">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="5dfdd-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
