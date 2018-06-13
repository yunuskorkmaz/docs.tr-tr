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
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603658"
---
# <a name="addhandler-statement"></a><span data-ttu-id="24e79-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="24e79-102">AddHandler Statement</span></span>
<span data-ttu-id="24e79-103">Bir olayın olay işleyicisi ile çalışma zamanında ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="24e79-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24e79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24e79-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="24e79-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="24e79-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="24e79-106">İşlenecek Olay adı.</span><span class="sxs-lookup"><span data-stu-id="24e79-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="24e79-107">Olay işleme bir yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="24e79-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24e79-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24e79-108">Remarks</span></span>  
 <span data-ttu-id="24e79-109">`AddHandler` Ve `RemoveHandler` deyimleri program yürütme sırasında herhangi bir zamanda olay işleme durdurmak ve başlatmak izin.</span><span class="sxs-lookup"><span data-stu-id="24e79-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="24e79-110">İmzası `eventhandler` yordamı, olay imza eşleşmelidir `event`.</span><span class="sxs-lookup"><span data-stu-id="24e79-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="24e79-111">`Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="24e79-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="24e79-112">`AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="24e79-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="24e79-113">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="24e79-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="24e79-114">Daha fazla bilgi için bkz: [işleme](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="24e79-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e79-115">Özel olaylar için `AddHandler` deyimi çağırır olayın `AddHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="24e79-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="24e79-116">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="24e79-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24e79-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="24e79-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="24e79-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24e79-118">See Also</span></span>  
 [<span data-ttu-id="24e79-119">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="24e79-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="24e79-120">İşleme</span><span class="sxs-lookup"><span data-stu-id="24e79-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="24e79-121">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="24e79-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="24e79-122">Olaylar</span><span class="sxs-lookup"><span data-stu-id="24e79-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
