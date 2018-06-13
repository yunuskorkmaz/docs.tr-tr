---
title: Olay &#39; &lt;eventname1&gt; &#39; olay uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; çünkü kendi temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 5c62b2f3e94de1c2a8919ec30b1ef106186bee11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589162"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="0e0c9-102">Olay &#39; &lt;eventname1&gt; &#39; olay uygulayamaz &#39; &lt;eventname2&gt; &#39; arabirimde &#39; &lt;arabirimi&gt; &#39; çünkü kendi temsilci türleri &#39; &lt;delegate1&gt; &#39; ve &#39; &lt;delegate2&gt; &#39; eşleşmiyor</span><span class="sxs-lookup"><span data-stu-id="0e0c9-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
<span data-ttu-id="0e0c9-103">Olay temsilci türü olay arabiriminde temsilci türü eşleşmediği için Visual Basic olaya uygulanamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="0e0c9-104">Bu hata, bir arabirim, birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="0e0c9-105">Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` sözdizimi ve aynı temsilci türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="0e0c9-106">**Hata Kimliği:** BC31423</span><span class="sxs-lookup"><span data-stu-id="0e0c9-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e0c9-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0e0c9-107">To correct this error</span></span>  
  
-   <span data-ttu-id="0e0c9-108">Olayları ayrı ayrı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="0e0c9-109">—veya—</span><span class="sxs-lookup"><span data-stu-id="0e0c9-109">—or—</span></span>  
  
-   <span data-ttu-id="0e0c9-110">Arabirimi kullanarak olayları tanımlayan `As` sözdizimi ve aynı temsilci türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e0c9-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e0c9-111">See Also</span></span>  
 [<span data-ttu-id="0e0c9-112">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e0c9-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="0e0c9-113">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e0c9-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="0e0c9-114">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0e0c9-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
