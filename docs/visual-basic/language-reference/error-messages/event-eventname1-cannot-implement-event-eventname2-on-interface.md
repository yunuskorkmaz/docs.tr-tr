---
title: "'<eventname1>' ile '<eventname2>' temsilci türleri eşleşmediğinden '<interface>' olayı '<delegate1>' arabiriminde '<delegate2>' olayını uygulayamaz."
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 3ec3e7bb2f28bf8c4dd38bc71e11193456860021
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272857"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="0cbe3-102">Olay '\<eventname1 >' olayını uygulayamaz '\<eventname2 >' arabiriminde '\<arabirimi >' için temsilci türleri\<delegate1 >' ve '\<delegate2 >' eşleşmiyor</span><span class="sxs-lookup"><span data-stu-id="0cbe3-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="0cbe3-103">Visual Basic olaya uygulanamıyor arabirimdeki olayın temsilci türü olay temsilci türü eşleşmiyor.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="0cbe3-104">Bu hata, bir arabirimde birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="0cbe3-105">Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` söz dizimi ve aynı temsilci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="0cbe3-106">**Hata Kimliği:** BC31423</span><span class="sxs-lookup"><span data-stu-id="0cbe3-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0cbe3-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0cbe3-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0cbe3-108">Olayları ayrı ayrı uygular.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="0cbe3-109">—veya—</span><span class="sxs-lookup"><span data-stu-id="0cbe3-109">—or—</span></span>  
  
-   <span data-ttu-id="0cbe3-110">Arabirimi kullanarak olayları tanımlamanız `As` söz dizimi ve aynı temsilci türünü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbe3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0cbe3-111">See also</span></span>
- [<span data-ttu-id="0cbe3-112">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="0cbe3-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0cbe3-113">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="0cbe3-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="0cbe3-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0cbe3-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
