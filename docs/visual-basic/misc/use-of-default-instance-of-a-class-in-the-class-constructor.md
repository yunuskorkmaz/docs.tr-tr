---
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cec3d3d462822ca571cab59a2e4d7e730d2aec46
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664376"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="2989e-102">Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir</span><span class="sxs-lookup"><span data-stu-id="2989e-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="2989e-103">Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="2989e-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="2989e-104">Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2989e-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2989e-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2989e-105">To correct this error</span></span>  
  
- <span data-ttu-id="2989e-106">Varsayılan örneği sınıf oluşturucusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2989e-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2989e-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2989e-107">See also</span></span>

- [<span data-ttu-id="2989e-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2989e-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
