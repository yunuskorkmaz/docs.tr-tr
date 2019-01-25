---
title: '&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: c909973ef1c00cb01179b0e5527dfecd6f41e577
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574787"
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="9dbbb-102">&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="9dbbb-102">&#39;Custom&#39; modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="9dbbb-103">Bir özel dışı olay aksine bir `Custom Event` bildirimi gerektirir bir `As` olayı için temsilci türünü açıkça belirten bir olay adından yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="9dbbb-104">Özel olmayan olaylar olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü veya bir parametre listesinde hemen aşağıdaki olay adı.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="9dbbb-105">**Hata Kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="9dbbb-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9dbbb-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9dbbb-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9dbbb-107">Özel olay olarak aynı parametre listesiyle bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="9dbbb-108">Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  <span data-ttu-id="9dbbb-109">Özel olay ile parametre listesini değiştirin bir `As` temsilci türünü belirleme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="9dbbb-110">Örneğiyle devam etmesini `Custom Event` bildirimi yazılan gibi.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="9dbbb-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9dbbb-111">Example</span></span>  
 <span data-ttu-id="9dbbb-112">Bu örnek bildirir bir `Custom Event` ve gerekli belirtir `As` yan tümcesi bir temsilci türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9dbbb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dbbb-113">See also</span></span>
- [<span data-ttu-id="9dbbb-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dbbb-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="9dbbb-115">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="9dbbb-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="9dbbb-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9dbbb-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
