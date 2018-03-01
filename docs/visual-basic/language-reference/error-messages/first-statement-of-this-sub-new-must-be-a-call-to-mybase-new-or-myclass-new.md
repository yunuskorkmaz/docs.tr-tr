---
title: "İlk ifade bu &#39; Yeni alt &#39; Çağrı &#39;olmalıdır; MyBase.New &#39; ya &#39; MyClass.New &#39; (Parametreler olmadan erişilebilir oluşturucu yok)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30148
- vbc30148
helpviewer_keywords:
- BC30148
ms.assetid: 4426e8fc-cb39-4eb8-ba95-503cd32fcc89
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1065643e1f6c868092fbad839af0dbbd33afaf01
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="first-statement-of-this-39sub-new39-must-be-a-call-to-39mybasenew39-or-39myclassnew39-no-accessible-constructor-without-parameters"></a><span data-ttu-id="91fe2-102">İlk ifade bu &#39; Yeni alt &#39; Çağrı &#39;olmalıdır; MyBase.New &#39; ya &#39; MyClass.New &#39; (Parametreler olmadan erişilebilir oluşturucu yok)</span><span class="sxs-lookup"><span data-stu-id="91fe2-102">First statement of this &#39;Sub New&#39; must be a call to &#39;MyBase.New&#39; or &#39;MyClass.New&#39; (No Accessible Constructor Without Parameters)</span></span>
<span data-ttu-id="91fe2-103">Bu 'Sub New' ilk deyimi 'MyBase.New' veya 'MyClass.New' için bir çağrı olmalıdır, çünkü temel sınıfı\<basename >', '\<derivedname >' bir erişilebilir 'Sub bağımsız değişkenler olmadan çağrılabilen New' yok.</span><span class="sxs-lookup"><span data-stu-id="91fe2-103">First statement of this 'Sub New' must be a call to 'MyBase.New' or 'MyClass.New' because base class '\<basename>' of '\<derivedname>' does not have an accessible 'Sub New' that can be called with no arguments.</span></span>  
  
 <span data-ttu-id="91fe2-104">Türetilen bir sınıfta her Oluşturucusu bir temel sınıf oluşturucu çağırmanız gerekir (`MyBase.New`).</span><span class="sxs-lookup"><span data-stu-id="91fe2-104">In a derived class, every constructor must call a base class constructor (`MyBase.New`).</span></span> <span data-ttu-id="91fe2-105">Taban sınıfı türetilen sınıflar için erişilebilir olan bir parametresiz oluşturucu varsa `MyBase.New` otomatik olarak çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="91fe2-105">If the base class has a constructor with no parameters that is accessible to derived classes, `MyBase.New` can be called automatically.</span></span> <span data-ttu-id="91fe2-106">Yoksa, bir taban sınıf oluşturucu parametrelerle çağrılması gerekir ve bu otomatik olarak yapılamaz.</span><span class="sxs-lookup"><span data-stu-id="91fe2-106">If not, a base class constructor must be called with parameters, and this cannot be done automatically.</span></span> <span data-ttu-id="91fe2-107">Bu durumda, her türetilmiş sınıf oluşturucu ilk deyimi gerekir parametreli Oluşturucusu çağrı üzerinde temel sınıfı veya başka bir oluşturucu çağrısı bir temel sınıf oluşturucu yapar türetilen sınıfta çağırın.</span><span class="sxs-lookup"><span data-stu-id="91fe2-107">In this case, the first statement of every derived class constructor must call a parameterized constructor on the base class, or call another constructor in the derived class that makes a base class constructor call.</span></span>  
  
 <span data-ttu-id="91fe2-108">**Hata Kimliği:** BC30148</span><span class="sxs-lookup"><span data-stu-id="91fe2-108">**Error ID:** BC30148</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="91fe2-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="91fe2-109">To correct this error</span></span>  
  
-   <span data-ttu-id="91fe2-110">Her iki çağrı `MyBase.New` gerekli parametreleri belirtin veya böyle bir çağrı yapar eş Oluşturucusu çağırın.</span><span class="sxs-lookup"><span data-stu-id="91fe2-110">Either call `MyBase.New` supplying the required parameters, or call a peer constructor that makes such a call.</span></span>  
  
     <span data-ttu-id="91fe2-111">Örneğin, temel sınıf olarak bildirilen bir oluşturucu varsa `Public Sub New(ByVal index as Integer)`, ilk ifade türetilen sınıf oluşturucu olabilir `MyBase.New(100)`.</span><span class="sxs-lookup"><span data-stu-id="91fe2-111">For example, if the base class has a constructor that’s declared as `Public Sub New(ByVal index as Integer)`, the first statement in the derived class constructor might be `MyBase.New(100)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91fe2-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91fe2-112">See Also</span></span>  
 [<span data-ttu-id="91fe2-113">Devralma temelleri</span><span class="sxs-lookup"><span data-stu-id="91fe2-113">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
