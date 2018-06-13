---
title: RemoveHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597994"
---
# <a name="removehandler-statement"></a><span data-ttu-id="535cd-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="535cd-102">RemoveHandler Statement</span></span>
<span data-ttu-id="535cd-103">Bir olayın olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="535cd-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="535cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="535cd-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="535cd-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="535cd-105">Parts</span></span>  
  
|<span data-ttu-id="535cd-106">Terim</span><span class="sxs-lookup"><span data-stu-id="535cd-106">Term</span></span>|<span data-ttu-id="535cd-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="535cd-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="535cd-108">İşlenen olay adı.</span><span class="sxs-lookup"><span data-stu-id="535cd-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="535cd-109">Şu anda olay işleme yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="535cd-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="535cd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="535cd-110">Remarks</span></span>  
 <span data-ttu-id="535cd-111">`AddHandler` Ve `RemoveHandler` deyimleri program yürütme sırasında her zaman belirli bir olay için olay işleme durdurmak ve başlatmak izin.</span><span class="sxs-lookup"><span data-stu-id="535cd-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="535cd-112">Özel olaylar için `RemoveHandler` deyimi çağırır olayın `RemoveHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="535cd-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="535cd-113">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="535cd-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="535cd-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="535cd-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="535cd-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="535cd-115">See Also</span></span>  
 [<span data-ttu-id="535cd-116">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="535cd-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="535cd-117">İşleme</span><span class="sxs-lookup"><span data-stu-id="535cd-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="535cd-118">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="535cd-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="535cd-119">Olaylar</span><span class="sxs-lookup"><span data-stu-id="535cd-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
