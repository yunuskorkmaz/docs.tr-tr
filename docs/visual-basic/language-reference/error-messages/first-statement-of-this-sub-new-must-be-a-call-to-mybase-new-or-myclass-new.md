---
title: Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır (Parametreler Olmadan Erişilebilir Yapıcı Yok)
ms.date: 07/20/2015
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
ms.openlocfilehash: 2b9d2568fb64e4af72733ad1f3dee58aaee650e5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402985"
---
# <a name="first-statement-of-this-sub-new-must-be-a-call-to-mybasenew-or-myclassnew-no-accessible-constructor-without-parameters"></a><span data-ttu-id="e63fc-102">Bu 'Sub New' öğesinin ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır (Parametreler Olmadan Erişilebilir Yapıcı Yok)</span><span class="sxs-lookup"><span data-stu-id="e63fc-102">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="e63fc-103">' ' Öğesinin ' ' temel sınıfında \<basename> \<derivedname> bağımsız değişken olmadan çağrılabilecek erişilebilir bir ' Sub New ' olmadığından, bu ' Sub New ' öğesinin ilk Ifadesinin ' MyBase. New ' veya ' MyClass. New ' çağrısı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e63fc-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="e63fc-104">Türetilmiş bir sınıfta, her oluşturucunun bir temel sınıf Oluşturucusu () çağırması gerekir `MyBase.New` .</span><span class="sxs-lookup"><span data-stu-id="e63fc-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="e63fc-105">Temel sınıfta, türetilmiş sınıfların erişebileceği parametre içermeyen bir Oluşturucu varsa, `MyBase.New` otomatik olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e63fc-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="e63fc-106">Aksi takdirde, bir temel sınıf oluşturucusunun parametrelerle çağrılması gerekir ve bu otomatik olarak gerçekleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e63fc-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="e63fc-107">Bu durumda, her türetilmiş sınıf oluşturucusunun ilk ifadesinin temel sınıfta parametreli bir Oluşturucu çağırması veya bir temel sınıf Oluşturucu çağrısını yapan türetilmiş sınıfta başka bir Oluşturucu çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e63fc-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="e63fc-108">**Hata kimliği:** BC30148</span><span class="sxs-lookup"><span data-stu-id="e63fc-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e63fc-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e63fc-109">To correct this error</span></span>  
  
- <span data-ttu-id="e63fc-110">Gerekli parametreleri çağırma ya da `MyBase.New` böyle bir çağrı yapan bir eşdüzey Oluşturucu çağırma.</span><span class="sxs-lookup"><span data-stu-id="e63fc-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="e63fc-111">Örneğin, temel sınıfın olarak belirtilen bir Oluşturucusu varsa `Public Sub New(ByVal index as Integer)` , türetilen sınıf oluşturucusunda ilk ifade olabilir `MyBase.New(100)` .</span><span class="sxs-lookup"><span data-stu-id="e63fc-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63fc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e63fc-112">See also</span></span>

- [<span data-ttu-id="e63fc-113">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="e63fc-113">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
