---
description: 'Hakkında daha fazla bilgi edinin: sınıf oluşturucusunda bir sınıfın varsayılan örneği kullanımı sonsuz özyinelemeli çağrıya neden olabilir'
title: Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: f65956c92f7d391aa77734d7afd5adf3bea1f906
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475688"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="77d96-103">Sınıf oluşturucusunda bir sınıfın varsayılan örneğinin kullanılması sonsuz özyinelemeli çağrıya yol açabilir</span><span class="sxs-lookup"><span data-stu-id="77d96-103">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="77d96-104">Sınıfının oluşturucusunda, sınıfının varsayılan bir örneği kullanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="77d96-104">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="77d96-105">Bu, sonsuz bir döngü olarak da bilinen sonsuz bir özyinelemeli çağrıya yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="77d96-105">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77d96-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="77d96-106">To correct this error</span></span>  
  
- <span data-ttu-id="77d96-107">Varsayılan örneği sınıf oluşturucusundan kaldırın.</span><span class="sxs-lookup"><span data-stu-id="77d96-107">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77d96-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77d96-108">See also</span></span>

- [<span data-ttu-id="77d96-109">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="77d96-109">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
