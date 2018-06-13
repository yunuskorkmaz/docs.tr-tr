---
title: Varsayılan örneği sınıf kurucusunda bir sınıfın kullanımını sonsuz özyinelemeli çağrısına neden olabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: cf5d3e16c43920a90b69c815f91601c6d33c845d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33638384"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="5eea5-102">Varsayılan örneği sınıf kurucusunda bir sınıfın kullanımını sonsuz özyinelemeli çağrısına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="5eea5-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>
<span data-ttu-id="5eea5-103">Bir sınıfın varsayılan bir örnek sınıf oluşturucuda kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="5eea5-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="5eea5-104">Bu, bir sonsuz Özyinelemeli çağrı olarak da bilinen sonsuz bir döngüde neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5eea5-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5eea5-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5eea5-105">To correct this error</span></span>  
  
-   <span data-ttu-id="5eea5-106">Varsayılan örnek sınıf oluşturucudan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5eea5-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eea5-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eea5-107">See Also</span></span>  
 [<span data-ttu-id="5eea5-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="5eea5-108">Constructors</span></span>](~/docs/visual-basic/programming-guide/concepts/object-oriented-programming.md#constructors)
