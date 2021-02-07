---
description: 'Daha fazla bilgi edinin: AddHandler ekstresi'
title: AddHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c0c34abd7ff225765ab36278825a555e2b84b0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674109"
---
# <a name="addhandler-statement"></a><span data-ttu-id="dd19d-103">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="dd19d-103">AddHandler Statement</span></span>

<span data-ttu-id="dd19d-104">Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="dd19d-104">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd19d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd19d-105">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="dd19d-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="dd19d-106">Parts</span></span>  

|||
|---|---|
|<span data-ttu-id="dd19d-107">event</span><span class="sxs-lookup"><span data-stu-id="dd19d-107">event</span></span>|<span data-ttu-id="dd19d-108">İşlenecek etkinliğin adı.</span><span class="sxs-lookup"><span data-stu-id="dd19d-108">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="dd19d-109">Olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="dd19d-109">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="dd19d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dd19d-110">Remarks</span></span>  

 <span data-ttu-id="dd19d-111">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd19d-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="dd19d-112">Yordamın imzası, `eventhandler` olayın imzasıyla aynı olmalıdır `event` .</span><span class="sxs-lookup"><span data-stu-id="dd19d-112">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="dd19d-113">`Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="dd19d-113">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="dd19d-114">`AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="dd19d-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="dd19d-115">`Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="dd19d-115">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="dd19d-116">Daha fazla bilgi için bkz. [Handles](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="dd19d-116">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd19d-117">Özel olaylar için, `AddHandler` ifade olayın `AddHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="dd19d-117">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="dd19d-118">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="dd19d-118">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd19d-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="dd19d-119">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="dd19d-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd19d-120">See also</span></span>

- [<span data-ttu-id="dd19d-121">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="dd19d-121">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="dd19d-122">Handles</span><span class="sxs-lookup"><span data-stu-id="dd19d-122">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="dd19d-123">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="dd19d-123">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="dd19d-124">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="dd19d-124">Events</span></span>](../../programming-guide/language-features/events/index.md)
