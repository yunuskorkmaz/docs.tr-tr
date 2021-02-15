---
description: 'Hakkında daha fazla bilgi edinin: nesne üzerinde, tanımlama sınıfının bir örneği olmayan arkadaş işlevi çağrılamaz'
title: Tanımlama sınıfının bir örneği olmayan nesnede Friend işlevi çağrılamaz
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: 612a169cf976881b82cb0bb0c44ac6c6e7f91755
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100478704"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="29481-103">Tanımlama sınıfının bir örneği olmayan nesnede Friend işlevi çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="29481-103">Cannot call friend function on object which is not an instance of defining class</span></span>

<span data-ttu-id="29481-104">`Friend`Bir sınıfın yordamını çağırmayı denediniz veya bir `Friend` özellik ya da yönteme çapraz işlem veya çapraz iş parçacığı ile erişmeye çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="29481-104">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="29481-105">Bir `Friend` yordam, sınıfının dışındaki bir modülden çağrılabilir, ancak sınıfın tanımlandığı projenin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="29481-105">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="29481-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="29481-106">To correct this error</span></span>  
  
- <span data-ttu-id="29481-107">Sınıfın tanımlandığı projenin parçası olan bir modülden çağırtığınızdan veya yordam ile eriştiğiniz emin olun.</span><span class="sxs-lookup"><span data-stu-id="29481-107">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29481-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29481-108">See also</span></span>

- [<span data-ttu-id="29481-109">Arkadaş</span><span class="sxs-lookup"><span data-stu-id="29481-109">Friend</span></span>](../language-reference/modifiers/friend.md)
