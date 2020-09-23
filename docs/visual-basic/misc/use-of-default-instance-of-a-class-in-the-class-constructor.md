---
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: 5d239fdb7dcc5c488bf0341043b810ec7dadc083
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100327"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="3d993-102">Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir</span><span class="sxs-lookup"><span data-stu-id="3d993-102">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="3d993-103">Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3d993-103">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="3d993-104">Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="3d993-104">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3d993-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3d993-105">To correct this error</span></span>  
  
- <span data-ttu-id="3d993-106">Varsayılan örneği sınıf oluşturucusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3d993-106">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d993-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d993-107">See also</span></span>

- [<span data-ttu-id="3d993-108">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="3d993-108">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
