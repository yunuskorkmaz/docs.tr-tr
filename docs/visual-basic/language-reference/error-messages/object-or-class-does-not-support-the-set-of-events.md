---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 4a6f1f59f43cdb351d49fbcbfd18362db888586e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593210"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="6c12f-102">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="6c12f-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="6c12f-103">Kullanmaya çalıştığınız bir `WithEvents` olayları belirtilen kümesi için bir olay kaynağı olarak çalışamaz bir bileşeni ile değişken.</span><span class="sxs-lookup"><span data-stu-id="6c12f-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="6c12f-104">Örneğin, bir nesne olaylar indirilir, sonra başka bir nesne oluşturmak istediğiniz `Implements` ilk nesne.</span><span class="sxs-lookup"><span data-stu-id="6c12f-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="6c12f-105">Uygulanan nesneden olayları havuzu düşünebilirsiniz karşın, bu her zaman durumda değil.</span><span class="sxs-lookup"><span data-stu-id="6c12f-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="6c12f-106">`Implements` yalnızca yöntemleri ve özellikleri için bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="6c12f-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="6c12f-107">`WithEvents` Özel için desteklenmeyen `UserControls`, type Info yükseltmek gereken `ObjectEvent` çalışma zamanında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="6c12f-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6c12f-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="6c12f-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="6c12f-109">Olay kaynağı olmayan bir bileşen için olayları kapatamıyor.</span><span class="sxs-lookup"><span data-stu-id="6c12f-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c12f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c12f-110">See Also</span></span>  
 [<span data-ttu-id="6c12f-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="6c12f-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="6c12f-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="6c12f-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
