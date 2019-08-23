---
title: AddHandler ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: a9913cd682e52562422ba140e27187d37c592684
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928946"
---
# <a name="addhandler-statement"></a><span data-ttu-id="0e85b-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e85b-102">AddHandler Statement</span></span>
<span data-ttu-id="0e85b-103">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="0e85b-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e85b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e85b-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="0e85b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0e85b-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="0e85b-106">olay</span><span class="sxs-lookup"><span data-stu-id="0e85b-106">event</span></span>|<span data-ttu-id="0e85b-107">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="0e85b-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="0e85b-108">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="0e85b-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="0e85b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e85b-109">Remarks</span></span>  
 <span data-ttu-id="0e85b-110">`AddHandler` Ve`RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e85b-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="0e85b-111">`eventhandler` Yordamın imzası, olayın `event`imzasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e85b-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="0e85b-112">`Handles` Anahtar sözcüğü `AddHandler` ve deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="0e85b-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="0e85b-113">İfade `AddHandler` , çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="0e85b-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="0e85b-114">Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtarsözcüğünükullanın.`Handles`</span><span class="sxs-lookup"><span data-stu-id="0e85b-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="0e85b-115">Daha fazla bilgi için bkz. [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="0e85b-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0e85b-116">Özel olaylar için, `AddHandler` ifade `AddHandler` olayın erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0e85b-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="0e85b-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0e85b-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e85b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e85b-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="0e85b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e85b-119">See also</span></span>

- [<span data-ttu-id="0e85b-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e85b-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="0e85b-121">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="0e85b-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="0e85b-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e85b-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0e85b-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0e85b-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
