---
title: Tanımlama sınıfının bir örneği olmayan nesnede Friend işlevi çağrılamaz
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c18c04470c4c49113e8195b92185326c5c4197c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400854"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="e97aa-102">Tanımlama sınıfının bir örneği olmayan nesnede Friend işlevi çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="e97aa-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="e97aa-103">`Friend`Bir sınıfın yordamını çağırmayı denediniz veya bir `Friend` özellik ya da yönteme çapraz işlem veya çapraz iş parçacığı ile erişmeye çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="e97aa-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="e97aa-104">Bir `Friend` yordam, sınıfının dışındaki bir modülden çağrılabilir, ancak sınıfın tanımlandığı projenin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="e97aa-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e97aa-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e97aa-105">To correct this error</span></span>  
  
- <span data-ttu-id="e97aa-106">Sınıfın tanımlandığı projenin parçası olan bir modülden çağırtığınızdan veya yordam ile eriştiğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="e97aa-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97aa-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e97aa-107">See also</span></span>

- [<span data-ttu-id="e97aa-108">Dost</span><span class="sxs-lookup"><span data-stu-id="e97aa-108">Friend</span></span>](../language-reference/modifiers/friend.md)
