---
description: "Hakkında daha fazla bilgi edinin: BC31122: ' Custom ' değiştiricisi açık temsilci türleri olmadan belirtilen olaylarda geçerli değildir"
title: "'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 6cbddd31dfa9c923038f8ea706bfc49233574cfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796684"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a><span data-ttu-id="3280c-103">BC31122: ' Custom ' değiştiricisi açık temsilci türleri olmadan belirtilen olaylarda geçerli değil</span><span class="sxs-lookup"><span data-stu-id="3280c-103">BC31122: 'Custom' modifier is not valid on events declared without explicit delegate types</span></span>

<span data-ttu-id="3280c-104">Özel olmayan bir olaydan farklı olarak, `Custom Event` bildirim, `As` olayın temsilci türünü açıkça belirten olay adından sonra bir yan tümce gerektirir.</span><span class="sxs-lookup"><span data-stu-id="3280c-104">Unlike a non-custom event, a `Custom Event` declaration requires an `As` clause following the event name that explicitly specifies the delegate type for the event.</span></span>

 <span data-ttu-id="3280c-105">Özel olmayan olaylar `As` , bir yan tümce ve açık bir temsilci türü ile ya da olay adından hemen sonra gelen bir parametre listesi ile tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3280c-105">Non-custom events can be defined either with an `As` clause and an explicit delegate type, or with a parameter list immediately following the event name.</span></span>

 <span data-ttu-id="3280c-106">**Hata kimliği:** BC31122</span><span class="sxs-lookup"><span data-stu-id="3280c-106">**Error ID:** BC31122</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="3280c-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3280c-107">To correct this error</span></span>

1. <span data-ttu-id="3280c-108">Özel olayla aynı parametre listesine sahip bir temsilci tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="3280c-108">Define a delegate with the same parameter list as the custom event.</span></span>

     <span data-ttu-id="3280c-109">Örneğin, `Custom Event` tarafından tanımlanmışsa, `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` ilgili temsilci aşağıdaki gibi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="3280c-109">For example, if the `Custom Event` was defined by `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, then the corresponding delegate would be the following.</span></span>

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. <span data-ttu-id="3280c-110">Özel olayın parametre listesini, `As` temsilci türünü belirten bir yan tümce ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3280c-110">Replace the parameter list of the custom event with an `As` clause specifying the delegate type.</span></span>

     <span data-ttu-id="3280c-111">Örnekle devam edildiğinde, `Custom Event` bildirim aşağıdaki şekilde yeniden yazılır.</span><span class="sxs-lookup"><span data-stu-id="3280c-111">Continuing with the example, `Custom Event` declaration would be rewritten as follows.</span></span>

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a><span data-ttu-id="3280c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="3280c-112">Example</span></span>

 <span data-ttu-id="3280c-113">Bu örnek bir bildirir `Custom Event` ve bir `As` temsilci türü ile gerekli yan tümceyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3280c-113">This example declares a `Custom Event` and specifies the required `As` clause with a delegate type.</span></span>

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a><span data-ttu-id="3280c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3280c-114">See also</span></span>

- [<span data-ttu-id="3280c-115">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="3280c-115">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="3280c-116">Delegate Deyimi</span><span class="sxs-lookup"><span data-stu-id="3280c-116">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="3280c-117">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="3280c-117">Events</span></span>](../../programming-guide/language-features/events/index.md)
