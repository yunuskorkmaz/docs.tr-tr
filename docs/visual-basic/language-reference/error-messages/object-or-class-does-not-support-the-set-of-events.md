---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409367"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="369da-102">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="369da-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="369da-103">`WithEvents`Belirtilen olay kümesi için olay kaynağı olarak çalışmayan bir bileşeni olan bir değişken kullanmaya çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="369da-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="369da-104">Örneğin, bir nesnenin olaylarını havuza almak istiyordunuz ve ardından ilk nesne için başka bir nesne oluşturun `Implements` .</span><span class="sxs-lookup"><span data-stu-id="369da-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="369da-105">Olayları uygulanan nesnesinden havuzunuza uyacağını düşünebilseniz de, bu durum her zaman değildir.</span><span class="sxs-lookup"><span data-stu-id="369da-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="369da-106">`Implements`yalnızca Yöntemler ve özellikler için bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="369da-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="369da-107">`WithEvents``UserControls`, öğesini yükseltmek için gereken tür bilgisi çalışma zamanında kullanılabilir olmadığından Private için desteklenmez `ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="369da-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="369da-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="369da-108">To correct this error</span></span>  
  
1. <span data-ttu-id="369da-109">Olayları kaynak olmayan bir bileşen için havuza yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="369da-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369da-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="369da-110">See also</span></span>

- [<span data-ttu-id="369da-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="369da-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="369da-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="369da-112">Implements Statement</span></span>](../statements/implements-statement.md)
