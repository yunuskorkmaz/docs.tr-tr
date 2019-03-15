---
title: Sonsuz Özyinelenen çağrı sınıfı oluşturucusunda bir sınıf örneği varsayılan kullanımına neden olabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 14c498bf3067415f8de2afaeaaa57cf3f28ae857
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58045269"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="bf1d8-102">Sonsuz Özyinelenen çağrı sınıfı oluşturucusunda bir sınıf örneği varsayılan kullanımına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="bf1d8-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="bf1d8-103">Sınıfın oluşturucusunda bir sınıfın varsayılan bir örnek kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="bf1d8-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="bf1d8-104">Bu, bir sonsuz Özyinelemeli çağrı olarak da bilinen bir sonsuz döngüye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="bf1d8-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf1d8-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bf1d8-105">To correct this error</span></span>  
  
-   <span data-ttu-id="bf1d8-106">Varsayılan örnek sınıf oluşturucusunda kaldırın.</span><span class="sxs-lookup"><span data-stu-id="bf1d8-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf1d8-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf1d8-107">See also</span></span>

- [<span data-ttu-id="bf1d8-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="bf1d8-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
