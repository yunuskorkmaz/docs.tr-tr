---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925768"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="c702a-102">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="c702a-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="c702a-103">Kullanmaya çalıştığınız bir `WithEvents` değişken bir bileşeniyle belirlenen olayları için olay kaynağı olarak çalışamaz.</span><span class="sxs-lookup"><span data-stu-id="c702a-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="c702a-104">Örneğin, bir nesnenin olaylar indirilir ve ardından başka bir nesne oluşturan istediğinizi `Implements` ilk nesne.</span><span class="sxs-lookup"><span data-stu-id="c702a-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="c702a-105">Uygulanan nesneden olayları havuz düşünebilirsiniz ancak bu her zaman böyle değildir.</span><span class="sxs-lookup"><span data-stu-id="c702a-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="c702a-106">`Implements` yalnızca yöntemler ve özellikler için bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="c702a-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="c702a-107">`WithEvents` Özel için desteklenmeyen `UserControls`tür bilgisini yükseltmek gerekli olduğundan `ObjectEvent` çalışma zamanında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="c702a-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c702a-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c702a-108">To correct this error</span></span>  
  
1. <span data-ttu-id="c702a-109">Olayları olay kaynağı olmayan bir bileşen için havuz olamaz.</span><span class="sxs-lookup"><span data-stu-id="c702a-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c702a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c702a-110">See also</span></span>

- [<span data-ttu-id="c702a-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="c702a-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="c702a-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="c702a-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
