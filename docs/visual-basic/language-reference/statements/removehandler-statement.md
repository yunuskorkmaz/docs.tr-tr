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
ms.openlocfilehash: a815241f20be12b3b7b4f2b87d50a8965021bbf0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871933"
---
# <a name="removehandler-statement"></a><span data-ttu-id="f32d9-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="f32d9-102">RemoveHandler Statement</span></span>

<span data-ttu-id="f32d9-103">Bir olay ve olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="f32d9-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f32d9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f32d9-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="f32d9-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="f32d9-105">Parts</span></span>  
  
|<span data-ttu-id="f32d9-106">Terim</span><span class="sxs-lookup"><span data-stu-id="f32d9-106">Term</span></span>|<span data-ttu-id="f32d9-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="f32d9-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="f32d9-108">İşlenmekte olan olayın adı.</span><span class="sxs-lookup"><span data-stu-id="f32d9-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="f32d9-109">Şu anda olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="f32d9-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f32d9-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f32d9-110">Remarks</span></span>  

 <span data-ttu-id="f32d9-111">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f32d9-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f32d9-112">Özel olaylar için, `RemoveHandler` ifade olayın `RemoveHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="f32d9-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="f32d9-113">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f32d9-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f32d9-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="f32d9-114">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="f32d9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f32d9-115">See also</span></span>

- [<span data-ttu-id="f32d9-116">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="f32d9-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="f32d9-117">Handles</span><span class="sxs-lookup"><span data-stu-id="f32d9-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="f32d9-118">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="f32d9-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="f32d9-119">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="f32d9-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
