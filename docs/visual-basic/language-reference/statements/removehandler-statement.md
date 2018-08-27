---
title: RemoveHandler deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: c1e6ffec64bc01936955a2e94aa9c110b317109f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925172"
---
# <a name="removehandler-statement"></a><span data-ttu-id="4e7f2-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e7f2-102">RemoveHandler Statement</span></span>
<span data-ttu-id="4e7f2-103">Bir olay bir olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e7f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e7f2-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4e7f2-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="4e7f2-105">Parts</span></span>  
  
|<span data-ttu-id="4e7f2-106">Terim</span><span class="sxs-lookup"><span data-stu-id="4e7f2-106">Term</span></span>|<span data-ttu-id="4e7f2-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="4e7f2-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="4e7f2-108">İşlenen olayın adı.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="4e7f2-109">Şu anda olay işleme yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e7f2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e7f2-110">Remarks</span></span>  
 <span data-ttu-id="4e7f2-111">`AddHandler` Ve `RemoveHandler` deyimleri, programın yürütülmesi sırasında herhangi bir zamanda belirli bir olay için olay işleme durdurmak ve başlatmak sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e7f2-112">Özel olaylar için `RemoveHandler` deyimi çağırır olayın `RemoveHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="4e7f2-113">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e7f2-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e7f2-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="4e7f2-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4e7f2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e7f2-115">See Also</span></span>  
 [<span data-ttu-id="4e7f2-116">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e7f2-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="4e7f2-117">İşleme</span><span class="sxs-lookup"><span data-stu-id="4e7f2-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="4e7f2-118">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="4e7f2-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="4e7f2-119">Olaylar</span><span class="sxs-lookup"><span data-stu-id="4e7f2-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
