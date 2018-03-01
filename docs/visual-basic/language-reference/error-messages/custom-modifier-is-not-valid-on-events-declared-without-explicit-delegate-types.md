---
title: "&#39; Özel &#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="dbad3-102">&#39; Özel &#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="dbad3-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="dbad3-103">Özel olmayan olay aksine bir `Custom Event` bildirimi gerektiren bir `As` açıkça olayı için temsilci türünü belirten bir olay adından yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="dbad3-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="dbad3-104">Olmayan özel olayları olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü ya da bir parametre listesi hemen olay adından.</span><span class="sxs-lookup"><span data-stu-id="dbad3-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="dbad3-105">**Hata Kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="dbad3-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dbad3-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="dbad3-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="dbad3-107">Bir temsilci ile aynı parametre listesine özel olayı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="dbad3-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="dbad3-108">Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="dbad3-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="dbad3-109">Özel olay ile parametre listesi yerine bir `As` temsilci türünü belirtme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="dbad3-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="dbad3-110">Bu örnekle devam edersek `Custom Event` bildirimi yeniden yazılmıştır gibi.</span><span class="sxs-lookup"><span data-stu-id="dbad3-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="dbad3-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbad3-111">Example</span></span>  
 <span data-ttu-id="dbad3-112">Bu örnek bildiren bir `Custom Event` ve gerekli belirtir `As` bir temsilci türüyle yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="dbad3-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dbad3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dbad3-113">See Also</span></span>  
 [<span data-ttu-id="dbad3-114">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="dbad3-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="dbad3-115">Delegate deyimi</span><span class="sxs-lookup"><span data-stu-id="dbad3-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="dbad3-116">Olayları</span><span class="sxs-lookup"><span data-stu-id="dbad3-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
