---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409575"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="97446-102">Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez</span><span class="sxs-lookup"><span data-stu-id="97446-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="97446-103">Değiştiriciyle belirtilen bir değişken `Shared` paylaşılan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="97446-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="97446-104">Paylaşılan değişken tam olarak bir depolama konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97446-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="97446-105">Değiştirici ile belirtilen bir değişken, `WithEvents` değişkenin ait olduğu türün, değişkenin oluşturulduğu olay kümesini işlediğini onaylar.</span><span class="sxs-lookup"><span data-stu-id="97446-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="97446-106">Değişkene bir değer atandığında, bildirim tarafından oluşturulan özellik `WithEvents` mevcut olay işleyicisinin kancalarını kaldırır ve yöntemi aracılığıyla yeni olay işleyicisini takar `Add` .</span><span class="sxs-lookup"><span data-stu-id="97446-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="97446-107">**Hata kimliği:** BC30594</span><span class="sxs-lookup"><span data-stu-id="97446-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97446-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="97446-108">To correct this error</span></span>  
  
- <span data-ttu-id="97446-109">Olay işleyicinizi bildirin `Shared` .</span><span class="sxs-lookup"><span data-stu-id="97446-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97446-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97446-110">See also</span></span>

- [<span data-ttu-id="97446-111">Shared</span><span class="sxs-lookup"><span data-stu-id="97446-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="97446-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="97446-112">WithEvents</span></span>](../modifiers/withevents.md)
