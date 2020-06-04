---
title: "'<eventname1>' ile '<eventname2>' temsilci türleri eşleşmediğinden '<interface>' olayı '<delegate1>' arabiriminde '<delegate2>' olayını uygulayamaz."
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 32d6733580de8798a66c30d486b8439befd2af19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409614"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="1d5d5-102">'\<eventname1>' ile '\<eventname2>' temsilci türleri eşleşmediğinden '\<interface>' olayı '\<delegate1>' arabiriminde '\<delegate2>' olayını uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="1d5d5-103">Olayın temsilci türü arabirimdeki olayın temsilci türüyle eşleşmediğinden Visual Basic bir olay uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="1d5d5-104">Bu hata, bir arabirimde birden çok olay tanımladığınızda ve ardından bunları aynı olayla birlikte uygulamaya çalıştığınızda ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="1d5d5-105">Bir olay, yalnızca tüm uygulanan olaylar `As` söz dizimi kullanılarak bildirilirse ve aynı temsilci türünü belirtirseniz iki veya daha fazla olay uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="1d5d5-106">**Hata kimliği:** BC31423</span><span class="sxs-lookup"><span data-stu-id="1d5d5-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1d5d5-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1d5d5-107">To correct this error</span></span>  
  
- <span data-ttu-id="1d5d5-108">Olayları ayrı olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="1d5d5-109">—veya—</span><span class="sxs-lookup"><span data-stu-id="1d5d5-109">—or—</span></span>  
  
- <span data-ttu-id="1d5d5-110">Sözdizimini kullanarak arabirimdeki olayları tanımlayın `As` ve aynı temsilci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d5d5-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d5d5-111">See also</span></span>

- [<span data-ttu-id="1d5d5-112">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d5d5-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="1d5d5-113">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="1d5d5-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="1d5d5-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="1d5d5-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
