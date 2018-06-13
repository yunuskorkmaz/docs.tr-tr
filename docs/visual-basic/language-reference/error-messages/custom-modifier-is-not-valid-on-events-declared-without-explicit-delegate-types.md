---
title: '&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587530"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="b38ba-102">&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="b38ba-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="b38ba-103">Özel olmayan olay aksine bir `Custom Event` bildirimi gerektiren bir `As` açıkça olayı için temsilci türünü belirten bir olay adından yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b38ba-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="b38ba-104">Olmayan özel olayları olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü ya da bir parametre listesi hemen olay adından.</span><span class="sxs-lookup"><span data-stu-id="b38ba-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="b38ba-105">**Hata Kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="b38ba-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b38ba-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="b38ba-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b38ba-107">Bir temsilci ile aynı parametre listesine özel olayı olarak tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="b38ba-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="b38ba-108">Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b38ba-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="b38ba-109">Özel olay ile parametre listesi yerine bir `As` temsilci türünü belirtme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b38ba-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="b38ba-110">Bu örnekle devam edersek `Custom Event` bildirimi yeniden yazılmıştır gibi.</span><span class="sxs-lookup"><span data-stu-id="b38ba-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="b38ba-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b38ba-111">Example</span></span>  
 <span data-ttu-id="b38ba-112">Bu örnek bildiren bir `Custom Event` ve gerekli belirtir `As` bir temsilci türüyle yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="b38ba-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b38ba-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b38ba-113">See Also</span></span>  
 [<span data-ttu-id="b38ba-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="b38ba-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="b38ba-115">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="b38ba-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="b38ba-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="b38ba-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
