---
title: RemoveHandler ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582017"
---
# <a name="removehandler-statement"></a><span data-ttu-id="0be5c-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0be5c-102">RemoveHandler Statement</span></span>
<span data-ttu-id="0be5c-103">Bir olay ve olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0be5c-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0be5c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0be5c-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="0be5c-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0be5c-105">Parts</span></span>  
  
|<span data-ttu-id="0be5c-106">Terim</span><span class="sxs-lookup"><span data-stu-id="0be5c-106">Term</span></span>|<span data-ttu-id="0be5c-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="0be5c-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="0be5c-108">İşlenmekte olan olayın adı.</span><span class="sxs-lookup"><span data-stu-id="0be5c-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="0be5c-109">Şu anda olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="0be5c-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0be5c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0be5c-110">Remarks</span></span>  
 <span data-ttu-id="0be5c-111">@No__t_0 ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0be5c-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0be5c-112">Özel olaylar için `RemoveHandler` ifade, olayın `RemoveHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0be5c-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="0be5c-113">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0be5c-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0be5c-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="0be5c-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="0be5c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0be5c-115">See also</span></span>

- [<span data-ttu-id="0be5c-116">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0be5c-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="0be5c-117">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="0be5c-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="0be5c-118">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="0be5c-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0be5c-119">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0be5c-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
