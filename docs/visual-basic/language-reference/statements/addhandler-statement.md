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
ms.openlocfilehash: 79dbe174209e91f13f5b43e8cdeb0b42edc4d163
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866712"
---
# <a name="addhandler-statement"></a><span data-ttu-id="d557a-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="d557a-102">AddHandler Statement</span></span>

<span data-ttu-id="d557a-103">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="d557a-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d557a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d557a-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="d557a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="d557a-105">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="d557a-106">event</span><span class="sxs-lookup"><span data-stu-id="d557a-106">event</span></span>|<span data-ttu-id="d557a-107">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="d557a-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="d557a-108">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="d557a-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="d557a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d557a-109">Remarks</span></span>  

 <span data-ttu-id="d557a-110">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d557a-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="d557a-111">Yordamın imzası, `eventhandler` olayın imzasıyla aynı olmalıdır `event` .</span><span class="sxs-lookup"><span data-stu-id="d557a-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="d557a-112">`Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="d557a-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="d557a-113">`AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="d557a-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="d557a-114">`Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="d557a-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="d557a-115">Daha fazla bilgi için bkz. [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d557a-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d557a-116">Özel olaylar için, `AddHandler` ifade olayın `AddHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="d557a-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="d557a-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d557a-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d557a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="d557a-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="d557a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d557a-119">See also</span></span>

- [<span data-ttu-id="d557a-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="d557a-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="d557a-121">Handles</span><span class="sxs-lookup"><span data-stu-id="d557a-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="d557a-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="d557a-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="d557a-123">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="d557a-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
