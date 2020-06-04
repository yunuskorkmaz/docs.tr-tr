---
title: "'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 0c5a4188fedf9685afdd1cde4c1de93a0b43b919
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409795"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="d306c-102">'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="d306c-102">'Custom' modifier is not valid on events declared without explicit delegate types</span></span>
<span data-ttu-id="d306c-103">Özel olmayan bir olaydan farklı olarak, `Custom Event` bildirim, `As` olayın temsilci türünü açıkça belirten olay adından sonra bir yan tümce gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d306c-103">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>  
  
 <span data-ttu-id="d306c-104">Özel olmayan olaylar `As` , bir yan tümce ve açık bir temsilci türü ile ya da olay adından hemen sonra gelen bir parametre listesi ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d306c-104">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>  
  
 <span data-ttu-id="d306c-105">**Hata kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="d306c-105">**Error ID:** BC31122</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d306c-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d306c-106">To correct this error</span></span>  
  
1. <span data-ttu-id="d306c-107">Özel olayla aynı parametre listesine sahip bir temsilci tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d306c-107">Define a delegate with the same parameter list as the custom event.</span></span>  
  
     <span data-ttu-id="d306c-108">Örneğin, `Custom Event` tarafından tanımlanmışsa, `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` ilgili temsilci aşağıdaki gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d306c-108">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. <span data-ttu-id="d306c-109">Özel olayın parametre listesini, `As` temsilci türünü belirten bir yan tümce ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d306c-109">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>  
  
     <span data-ttu-id="d306c-110">Örnekle devam edildiğinde, `Custom Event` bildirim aşağıdaki şekilde yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="d306c-110">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="d306c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d306c-111">Example</span></span>  
 <span data-ttu-id="d306c-112">Bu örnek bir bildirir `Custom Event` ve bir `As` temsilci türü ile gerekli yan tümceyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="d306c-112">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d306c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d306c-113">See also</span></span>

- [<span data-ttu-id="d306c-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="d306c-114">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="d306c-115">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="d306c-115">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="d306c-116">Olaylar</span><span class="sxs-lookup"><span data-stu-id="d306c-116">Events</span></span>](../../programming-guide/language-features/events/index.md)
