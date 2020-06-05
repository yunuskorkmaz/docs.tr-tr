---
title: Yapıcı '<name>' kendisini çağıramaz
ms.date: 07/20/2015
f1_keywords:
- bc30298
- vbc30298
helpviewer_keywords:
- BC30298
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
ms.openlocfilehash: 6abb6dde624e129b52fefecf8c51e6cde2567ae1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409809"
---
# <a name="constructor-name-cannot-call-itself"></a><span data-ttu-id="798ad-102">Yapıcı '\<name>' kendisini çağıramaz</span><span class="sxs-lookup"><span data-stu-id="798ad-102">Constructor '\<name>' cannot call itself</span></span>
<span data-ttu-id="798ad-103">`Sub New`Bir sınıf veya yapıdaki yordam kendisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="798ad-103">A `Sub New` procedure in a class or structure calls itself.</span></span>  
  
 <span data-ttu-id="798ad-104">Bir oluşturucunun amacı, ilk oluşturulduğunda bir sınıfın veya yapının örneğini başlatmaktır.</span><span class="sxs-lookup"><span data-stu-id="798ad-104">The purpose of a constructor is to initialize an instance of a class or structure when it is first created.</span></span> <span data-ttu-id="798ad-105">Bir sınıf veya yapı, hepsi farklı parametre listelerine sahip olmaları şartıyla çeşitli oluşturuculara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="798ad-105">A class or structure can have several constructors, provided they all have different parameter lists.</span></span> <span data-ttu-id="798ad-106">Bir oluşturucunun kendisine ek olarak kendi işlevlerini yerine getirmek için başka bir Oluşturucu çağırması izin verilir.</span><span class="sxs-lookup"><span data-stu-id="798ad-106">A constructor is permitted to call another constructor to perform its functionality in addition to its own.</span></span> <span data-ttu-id="798ad-107">Ancak bir oluşturucunun kendisini çağırması anlamlı değildir ve aslında bu, izin verildiğinde sonsuz özyineleme oluşmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="798ad-107">But it is meaningless for a constructor to call itself, and in fact it would result in infinite recursion if permitted.</span></span>  
  
 <span data-ttu-id="798ad-108">**Hata kimliği:** BC30298</span><span class="sxs-lookup"><span data-stu-id="798ad-108">**Error ID:** BC30298</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="798ad-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="798ad-109">To correct this error</span></span>  
  
1. <span data-ttu-id="798ad-110">Çağrılan oluşturucunun parametre listesini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="798ad-110">Check the parameter list of the constructor being called.</span></span> <span data-ttu-id="798ad-111">Çağrıyı yapan oluşturucudan farklı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="798ad-111">It should be different from that of the constructor making the call.</span></span>  
  
2. <span data-ttu-id="798ad-112">Farklı bir Oluşturucu çağırmak istemiyorsanız, `Sub New` çağrıyı tamamen kaldırın.</span><span class="sxs-lookup"><span data-stu-id="798ad-112">If you do not intend to call a different constructor, remove the `Sub New` call entirely.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798ad-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="798ad-113">See also</span></span>

- [<span data-ttu-id="798ad-114">Nesne Ömrü: Nesneleri Oluşturma ve Yok Etme</span><span class="sxs-lookup"><span data-stu-id="798ad-114">Object Lifetime: How Objects Are Created and Destroyed</span></span>](../../programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
