---
title: AddHandler deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 6ed6f3d4fd77d714ab554d641c0c0fc4f403bbf8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715109"
---
# <a name="addhandler-statement"></a><span data-ttu-id="68846-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="68846-102">AddHandler Statement</span></span>
<span data-ttu-id="68846-103">Bir olay, çalışma zamanında bir olay işleyicisi ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="68846-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68846-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68846-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="68846-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="68846-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="68846-106">olay</span><span class="sxs-lookup"><span data-stu-id="68846-106">event</span></span>|<span data-ttu-id="68846-107">İşlenecek Olay adı.</span><span class="sxs-lookup"><span data-stu-id="68846-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="68846-108">Olayı işleyen bir yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="68846-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="68846-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68846-109">Remarks</span></span>  
 <span data-ttu-id="68846-110">`AddHandler` Ve `RemoveHandler` deyimleri, programın yürütülmesi sırasında herhangi bir zamanda olay işleme durdurmak ve başlatmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="68846-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="68846-111">İmzası `eventhandler` yordamı olay imzası eşleşmelidir `event`.</span><span class="sxs-lookup"><span data-stu-id="68846-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="68846-112">`Handles` Anahtar sözcüğü ve `AddHandler` iki deyimi belirli bir yordam belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="68846-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="68846-113">`AddHandler` Deyimi olayları yordamları çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="68846-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="68846-114">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="68846-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="68846-115">Daha fazla bilgi için [işler](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="68846-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68846-116">Özel olaylar için `AddHandler` deyimi çağırır olayın `AddHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="68846-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="68846-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68846-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68846-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="68846-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="68846-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68846-119">See also</span></span>
- [<span data-ttu-id="68846-120">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="68846-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="68846-121">İşleme</span><span class="sxs-lookup"><span data-stu-id="68846-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="68846-122">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="68846-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="68846-123">Olaylar</span><span class="sxs-lookup"><span data-stu-id="68846-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
