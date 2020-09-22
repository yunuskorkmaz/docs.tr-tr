---
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: e55a5515d88bd2782e31fdea7c07e16c595d43b5
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873659"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="38388-102">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="38388-102">Object or class does not support the set of events</span></span>

<span data-ttu-id="38388-103">`WithEvents`Belirtilen olay kümesi için olay kaynağı olarak çalışmayan bir bileşeni olan bir değişken kullanmaya çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="38388-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="38388-104">Örneğin, bir nesnenin olaylarını havuza almak istiyordunuz ve ardından ilk nesne için başka bir nesne oluşturun `Implements` .</span><span class="sxs-lookup"><span data-stu-id="38388-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="38388-105">Olayları uygulanan nesnesinden havuzunuza uyacağını düşünebilseniz de, bu durum her zaman değildir.</span><span class="sxs-lookup"><span data-stu-id="38388-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="38388-106">`Implements` yalnızca Yöntemler ve özellikler için bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="38388-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="38388-107">`WithEvents``UserControls`, öğesini yükseltmek için gereken tür bilgisi çalışma zamanında kullanılabilir olmadığından Private için desteklenmez `ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="38388-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38388-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="38388-108">To correct this error</span></span>  
  
1. <span data-ttu-id="38388-109">Olayları kaynak olmayan bir bileşen için havuza yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="38388-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38388-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38388-110">See also</span></span>

- [<span data-ttu-id="38388-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="38388-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="38388-112">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="38388-112">Implements Statement</span></span>](../statements/implements-statement.md)
