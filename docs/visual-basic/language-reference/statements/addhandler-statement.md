---
title: AddHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350185"
---
# <a name="addhandler-statement"></a><span data-ttu-id="18536-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="18536-102">AddHandler Statement</span></span>
<span data-ttu-id="18536-103">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="18536-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18536-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18536-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="18536-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="18536-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="18536-106">olay</span><span class="sxs-lookup"><span data-stu-id="18536-106">event</span></span>|<span data-ttu-id="18536-107">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="18536-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="18536-108">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="18536-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="18536-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18536-109">Remarks</span></span>  
 <span data-ttu-id="18536-110">`AddHandler` ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="18536-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="18536-111">`eventhandler` yordamının imzası, olay `event`imzasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="18536-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="18536-112">`Handles` anahtar sözcüğü ve `AddHandler` deyimin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="18536-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="18536-113">`AddHandler` ifade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="18536-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="18536-114">Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="18536-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="18536-115">Daha fazla bilgi için bkz. [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="18536-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18536-116">Özel olaylar için `AddHandler` ifade, olayın `AddHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="18536-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="18536-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="18536-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18536-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="18536-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="18536-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18536-119">See also</span></span>

- [<span data-ttu-id="18536-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="18536-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="18536-121">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="18536-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="18536-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="18536-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="18536-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="18536-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
