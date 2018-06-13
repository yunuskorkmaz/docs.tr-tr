---
title: Arkadaş işlevi sınıfı tanımlayan bir örneği değil bir nesne üzerinde çağrılamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrID97
ms.assetid: b9d821f0-8565-4f15-bb35-184789c69662
ms.openlocfilehash: a655207110d512805490b693e413b1d22b0367ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33634942"
---
# <a name="cannot-call-friend-function-on-object-which-is-not-an-instance-of-defining-class"></a><span data-ttu-id="c51a6-102">Arkadaş işlevi sınıfı tanımlayan bir örneği değil bir nesne üzerinde çağrılamıyor</span><span class="sxs-lookup"><span data-stu-id="c51a6-102">Cannot call friend function on object which is not an instance of defining class</span></span>
<span data-ttu-id="c51a6-103">Ulaşmaya çalıştık ya da `Friend` erişmeyi denedi yordamı bir sınıf veya bir `Friend` özellik veya yöntem çapraz işlem veya iş parçacıkları arası.</span><span class="sxs-lookup"><span data-stu-id="c51a6-103">Either you tried to call the `Friend` procedure of a class, or you tried to access a `Friend` property or method either cross-process or cross-thread.</span></span> <span data-ttu-id="c51a6-104">A `Friend` yordam sınıf dışında bir modülden aranabilir, ancak sınıf tanımlanır projesinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="c51a6-104">A `Friend` procedure is callable from a module outside the class, but is part of the project in which the class is defined.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c51a6-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c51a6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="c51a6-106">Çağırma veya yordam sınıfı tanımlandığı projesinin bir parçası olan bir modülden erişme emin olun.</span><span class="sxs-lookup"><span data-stu-id="c51a6-106">Ensure that you are calling or accessing the procedure from a module that is part of the project in which the class is defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51a6-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c51a6-107">See Also</span></span>  
 [<span data-ttu-id="c51a6-108">Friend</span><span class="sxs-lookup"><span data-stu-id="c51a6-108">Friend</span></span>](../../visual-basic/language-reference/modifiers/friend.md)
