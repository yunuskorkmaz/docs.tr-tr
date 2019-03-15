---
title: Arkadaş işlevi sınıf tanımlamanın bir örneği değil bir nesne üzerinde çağrılamaz
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: c65bbb5028cf042b702bb2b8336d40512c980790
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58018257"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="5e2db-102">Arkadaş işlevi sınıf tanımlamanın bir örneği değil bir nesne üzerinde çağrılamaz</span><span class="sxs-lookup"><span data-stu-id="5e2db-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="5e2db-103">Çağırmaya çalıştığınız ya da `Friend` erişmeyi denedi yordamı bir sınıf veya bir `Friend` özellik veya yöntem çapraz işlem veya iş parçacıkları arası.</span><span class="sxs-lookup"><span data-stu-id="5e2db-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="5e2db-104">A `Friend` yordamı sınıf dışında bir modülden çağrılabilir, ancak sınıf tanımlanır projenin bir parçası.</span><span class="sxs-lookup"><span data-stu-id="5e2db-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e2db-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5e2db-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5e2db-106">Arama veya sınıf tanımlandığı projeye bir parçası olan bir modülden yordamı erişme emin emin olun.</span><span class="sxs-lookup"><span data-stu-id="5e2db-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e2db-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e2db-107">See also</span></span>

- [<span data-ttu-id="5e2db-108">Friend</span><span class="sxs-lookup"><span data-stu-id="5e2db-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
