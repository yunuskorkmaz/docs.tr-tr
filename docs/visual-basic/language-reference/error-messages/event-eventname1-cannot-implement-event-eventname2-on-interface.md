---
title: "Olay &#39; &lt;eventname1&gt;&#39; olay &#39; uygulayamaz&lt; eventname2&gt;&#39; arabirimi &#39;&lt; Arabirim&gt;&#39; çünkü bunların temsilci türleri &#39;&lt; delegate1&gt;&#39; ve &#39;&lt; delegate2&gt;&#39; eşleşmiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="e2b2e-102">Olay &#39; &lt;eventname1&gt;&#39; olay &#39; uygulayamaz&lt; eventname2&gt;&#39; arabirimi &#39;&lt; Arabirim&gt;&#39; çünkü bunların temsilci türleri &#39;&lt; delegate1&gt;&#39; ve &#39;&lt; delegate2&gt;&#39; eşleşmiyor</span><span class="sxs-lookup"><span data-stu-id="e2b2e-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e2b2e-103">Olay temsilci türü olay arabiriminde temsilci türü eşleşmediği için bir olay uygulayamaz.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="e2b2e-104">Bu hata, bir arabirim, birden çok olayı tanımlayın ve bunları aynı olay ile birlikte uygulama girişimi ortaya çıkabilir.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="e2b2e-105">Bir olay iki uygulayabilir veya yalnızca tüm olayları uygulanırsa, daha fazla olay kullanılarak bildirilen `As` sözdizimi ve aynı temsilci türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="e2b2e-106">**Hata Kimliği:** BC31423</span><span class="sxs-lookup"><span data-stu-id="e2b2e-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e2b2e-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e2b2e-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e2b2e-108">Olayları ayrı ayrı uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="e2b2e-109">—veya—</span><span class="sxs-lookup"><span data-stu-id="e2b2e-109">—or—</span></span>  
  
-   <span data-ttu-id="e2b2e-110">Arabirimi kullanarak olayları tanımlayan `As` sözdizimi ve aynı temsilci türü belirtin.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2b2e-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e2b2e-111">See Also</span></span>  
 [<span data-ttu-id="e2b2e-112">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="e2b2e-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="e2b2e-113">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="e2b2e-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="e2b2e-114">Olayları</span><span class="sxs-lookup"><span data-stu-id="e2b2e-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
