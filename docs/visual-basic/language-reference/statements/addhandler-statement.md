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
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004537"
---
# <a name="addhandler-statement"></a><span data-ttu-id="4e25f-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e25f-102">AddHandler Statement</span></span>
<span data-ttu-id="4e25f-103">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="4e25f-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e25f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e25f-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4e25f-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4e25f-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="4e25f-106">olay</span><span class="sxs-lookup"><span data-stu-id="4e25f-106">event</span></span>|<span data-ttu-id="4e25f-107">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="4e25f-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="4e25f-108">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="4e25f-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="4e25f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e25f-109">Remarks</span></span>  
 <span data-ttu-id="4e25f-110">@No__t-0 ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e25f-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="4e25f-111">@No__t-0 yordamının imzası, olay `event` ' in imzasıyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4e25f-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="4e25f-112">@No__t-0 anahtar sözcüğü ve `AddHandler` deyimlerinin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="4e25f-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="4e25f-113">@No__t-0 ekstresi çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="4e25f-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="4e25f-114">Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="4e25f-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="4e25f-115">Daha fazla bilgi için bkz. [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4e25f-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e25f-116">Özel olaylar için `AddHandler` ifadesinde olayın `AddHandler` erişimcisi çağırılır.</span><span class="sxs-lookup"><span data-stu-id="4e25f-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="4e25f-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e25f-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e25f-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e25f-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="4e25f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e25f-119">See also</span></span>

- [<span data-ttu-id="4e25f-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e25f-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="4e25f-121">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="4e25f-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="4e25f-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e25f-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="4e25f-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4e25f-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
