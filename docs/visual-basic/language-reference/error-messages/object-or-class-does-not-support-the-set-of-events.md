---
description: 'Hakkında daha fazla bilgi edinin: nesne veya sınıf olay kümesini desteklemiyor'
title: Nesne veya sınıf olay kümesini desteklemiyor
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: f13d47a6bb75a5e8394f5344b954afa523bedab3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795617"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="0890a-103">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="0890a-103">Object or class does not support the set of events</span></span>

<span data-ttu-id="0890a-104">`WithEvents`Belirtilen olay kümesi için olay kaynağı olarak çalışmayan bir bileşeni olan bir değişken kullanmaya çalıştınız.</span><span class="sxs-lookup"><span data-stu-id="0890a-104">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="0890a-105">Örneğin, bir nesnenin olaylarını havuza almak istiyordunuz ve ardından ilk nesne için başka bir nesne oluşturun `Implements` .</span><span class="sxs-lookup"><span data-stu-id="0890a-105">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="0890a-106">Olayları uygulanan nesnesinden havuzunuza uyacağını düşünebilseniz de, bu durum her zaman değildir.</span><span class="sxs-lookup"><span data-stu-id="0890a-106">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="0890a-107">`Implements` yalnızca Yöntemler ve özellikler için bir arabirim uygular.</span><span class="sxs-lookup"><span data-stu-id="0890a-107">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="0890a-108">`WithEvents``UserControls`, öğesini yükseltmek için gereken tür bilgisi çalışma zamanında kullanılabilir olmadığından Private için desteklenmez `ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="0890a-108">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0890a-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0890a-109">To correct this error</span></span>

- <span data-ttu-id="0890a-110">Olayları kaynak olmayan bir bileşen için havuza yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0890a-110">You cannot sink events for a component that does not source events.</span></span>

## <a name="see-also"></a><span data-ttu-id="0890a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0890a-111">See also</span></span>

- [<span data-ttu-id="0890a-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="0890a-112">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="0890a-113">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="0890a-113">Implements Statement</span></span>](../statements/implements-statement.md)
