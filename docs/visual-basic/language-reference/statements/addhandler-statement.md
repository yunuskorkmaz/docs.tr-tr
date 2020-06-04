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
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408490"
---
# <a name="addhandler-statement"></a><span data-ttu-id="75308-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="75308-102">AddHandler Statement</span></span>
<span data-ttu-id="75308-103">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="75308-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75308-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="75308-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="75308-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="75308-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="75308-106">event</span><span class="sxs-lookup"><span data-stu-id="75308-106">event</span></span>|<span data-ttu-id="75308-107">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="75308-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="75308-108">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="75308-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="75308-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="75308-109">Remarks</span></span>  
 <span data-ttu-id="75308-110">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="75308-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="75308-111">Yordamın imzası, `eventhandler` olayın imzasıyla aynı olmalıdır `event` .</span><span class="sxs-lookup"><span data-stu-id="75308-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="75308-112">`Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="75308-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="75308-113">`AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="75308-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="75308-114">`Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="75308-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="75308-115">Daha fazla bilgi için bkz. [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="75308-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75308-116">Özel olaylar için, `AddHandler` ifade olayın `AddHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="75308-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="75308-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="75308-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75308-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="75308-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="75308-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75308-119">See also</span></span>

- [<span data-ttu-id="75308-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="75308-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="75308-121">Handles</span><span class="sxs-lookup"><span data-stu-id="75308-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="75308-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="75308-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="75308-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="75308-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
