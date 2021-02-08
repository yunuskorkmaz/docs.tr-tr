---
description: "Hakkında daha fazla bilgi edinin: BC30298: ' <name> ' Oluşturucusu kendisini çağıramaz"
title: Yapıcı '<name>' kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 486495eb822e3e3008382232091fe3923851f97c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796723"
---
# <a name="bc30298-constructor-name-cannot-call-itself"></a><span data-ttu-id="1c694-103">BC30298: ' \<name> ' Oluşturucusu kendisini çağıramaz</span><span class="sxs-lookup"><span data-stu-id="1c694-103">BC30298: Constructor '\<name>' cannot call itself</span></span>

<span data-ttu-id="1c694-104">`Sub New`Bir sınıf veya yapıdaki yordam kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="1c694-104">A `Sub New` procedure in a class or structure calls itself.</span></span>

 <span data-ttu-id="1c694-105">Bir oluşturucunun amacı, ilk oluşturulduğunda bir sınıfın veya yapının örneğini başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="1c694-105">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="1c694-106">Bir sınıf veya yapı, hepsi farklı parametre listelerine sahip olmaları şartıyla çeşitli oluşturuculara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c694-106">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="1c694-107">Bir oluşturucunun kendisine ek olarak kendi işlevlerini yerine getirmek için başka bir Oluşturucu çağırması izin verilir.</span><span class="sxs-lookup"><span data-stu-id="1c694-107">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="1c694-108">Ancak bir oluşturucunun kendisini çağırması anlamlı değildir ve aslında bu, izin verildiğinde sonsuz özyineleme oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1c694-108">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>

 <span data-ttu-id="1c694-109">**Hata kimliği:** BC30298</span><span class="sxs-lookup"><span data-stu-id="1c694-109">**Error ID:** BC30298</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1c694-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1c694-110">To correct this error</span></span>

1. <span data-ttu-id="1c694-111">Çağrılan oluşturucunun parametre listesini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="1c694-111">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="1c694-112">Çağrıyı yapan oluşturucudan farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1c694-112">It should be different from that of the constructor making the call.</span></span>

2. <span data-ttu-id="1c694-113">Farklı bir Oluşturucu çağırmak istemiyorsanız, `Sub New` çağrıyı tamamen kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c694-113">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c694-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c694-114">See also</span></span>

- [<span data-ttu-id="1c694-115">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="1c694-115">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
