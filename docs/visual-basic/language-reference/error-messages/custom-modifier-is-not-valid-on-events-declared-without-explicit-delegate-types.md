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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300950"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="f7cee-102">'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="f7cee-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="f7cee-103">Bir özel dışı olay aksine bir `Custom Event` bildirimi gerektirir bir `As` olayı için temsilci türünü açıkça belirten bir olay adından yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f7cee-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="f7cee-104">Özel olmayan olaylar olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü veya bir parametre listesinde hemen aşağıdaki olay adı.</span><span class="sxs-lookup"><span data-stu-id="f7cee-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="f7cee-105">**Hata Kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="f7cee-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7cee-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f7cee-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f7cee-107">Özel olay olarak aynı parametre listesiyle bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f7cee-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="f7cee-108">Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="f7cee-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="f7cee-109">Özel olay ile parametre listesini değiştirin bir `As` temsilci türünü belirleme yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="f7cee-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="f7cee-110">Örneğiyle devam etmesini `Custom Event` bildirimi yazılan gibi.</span><span class="sxs-lookup"><span data-stu-id="f7cee-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="f7cee-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7cee-111">Example</span></span>  
 <span data-ttu-id="f7cee-112">Bu örnek bildirir bir `Custom Event` ve gerekli belirtir `As` yan tümcesi bir temsilci türüne sahip.</span><span class="sxs-lookup"><span data-stu-id="f7cee-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7cee-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7cee-113">See also</span></span>

- [<span data-ttu-id="f7cee-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7cee-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="f7cee-115">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="f7cee-115">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="f7cee-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="f7cee-116">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
