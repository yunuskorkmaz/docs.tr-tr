---
title: "'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803889"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="07465-102">'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="07465-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="07465-103">Bir özel dışı olay aksine bir `Custom Event` bildirimi gerektirir bir `As` olayı için temsilci türünü açıkça belirten bir olay adından yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="07465-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="07465-104">Özel olmayan olaylar olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü veya bir parametre listesinde hemen aşağıdaki olay adı.</span><span class="sxs-lookup"><span data-stu-id="07465-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="07465-105">**Hata Kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="07465-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="07465-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="07465-106">To correct this error</span></span>  
  
1. <span data-ttu-id="07465-107">Özel olay olarak aynı parametre listesiyle bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="07465-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="07465-108">Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="07465-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="07465-109">Özel olay ile parametre listesini değiştirin bir `As` temsilci türünü belirleme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="07465-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="07465-110">Örneğiyle devam etmesini `Custom Event` bildirimi yazılan gibi.</span><span class="sxs-lookup"><span data-stu-id="07465-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="07465-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="07465-111">Example</span></span>  
 <span data-ttu-id="07465-112">Bu örnek bildirir bir `Custom Event` ve gerekli belirtir `As` yan tümcesi bir temsilci türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="07465-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="07465-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07465-113">See also</span></span>

- [<span data-ttu-id="07465-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="07465-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="07465-115">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="07465-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="07465-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="07465-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
