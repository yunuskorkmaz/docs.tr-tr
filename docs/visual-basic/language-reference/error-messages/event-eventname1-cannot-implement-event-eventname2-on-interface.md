---
description: "Hakkında daha fazla bilgi edinin: BC31423: ' ' <eventname1> <eventname2> <interface> <delegate1> ve ' ' temsilci türleri <delegate2> eşleşmediğinden ' ' olayı ' ' arabiriminde ' ' olayını uygulayamaz"
title: "'<eventname1>' ile '<eventname2>' temsilci türleri eşleşmediğinden '<interface>' olayı '<delegate1>' arabiriminde '<delegate2>' olayını uygulayamaz."
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: cfb967d2b43ce1f34f56f3d019a9a663b000296c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796463"
---
# <a name="bc31423-event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="a73b7-103">BC31423: ' ' \<eventname1> \<eventname2> \<interface> \<delegate1> ve ' ' temsilci türleri \<delegate2> eşleşmediğinden ' ' olayı ' ' arabiriminde ' ' olayını uygulayamaz</span><span class="sxs-lookup"><span data-stu-id="a73b7-103">BC31423: Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>

<span data-ttu-id="a73b7-104">Olayın temsilci türü arabirimdeki olayın temsilci türüyle eşleşmediğinden Visual Basic bir olay uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-104">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="a73b7-105">Bu hata, bir arabirimde birden çok olay tanımladığınızda ve ardından bunları aynı olayla birlikte uygulamaya çalıştığınızda ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-105">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="a73b7-106">Bir olay, yalnızca tüm uygulanan olaylar `As` söz dizimi kullanılarak bildirilirse ve aynı temsilci türünü belirtirseniz iki veya daha fazla olay uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="a73b7-106">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>

 <span data-ttu-id="a73b7-107">**Hata kimliği:** BC31423</span><span class="sxs-lookup"><span data-stu-id="a73b7-107">**Error ID:** BC31423</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a73b7-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a73b7-108">To correct this error</span></span>

- <span data-ttu-id="a73b7-109">Olayları ayrı olarak uygulayın.</span><span class="sxs-lookup"><span data-stu-id="a73b7-109">Implement the events separately.</span></span>

     <span data-ttu-id="a73b7-110">—veya—</span><span class="sxs-lookup"><span data-stu-id="a73b7-110">—or—</span></span>

- <span data-ttu-id="a73b7-111">Sözdizimini kullanarak arabirimdeki olayları tanımlayın `As` ve aynı temsilci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="a73b7-111">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>

## <a name="see-also"></a><span data-ttu-id="a73b7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a73b7-112">See also</span></span>

- [<span data-ttu-id="a73b7-113">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="a73b7-113">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="a73b7-114">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="a73b7-114">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="a73b7-115">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="a73b7-115">Events</span></span>](../../programming-guide/language-features/events/index.md)
