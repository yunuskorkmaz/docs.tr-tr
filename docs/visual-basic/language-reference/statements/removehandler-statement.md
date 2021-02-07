---
description: 'Daha fazla bilgi edinin: RemoveHandler ekstresi'
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
ms.openlocfilehash: 699db9edfc029b4149246e8b654645040ae6d89e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741308"
---
# <a name="removehandler-statement"></a><span data-ttu-id="60302-103">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="60302-103">RemoveHandler Statement</span></span>

<span data-ttu-id="60302-104">Bir olay ve olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="60302-104">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60302-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="60302-105">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="60302-106">Bölümler</span><span class="sxs-lookup"><span data-stu-id="60302-106">Parts</span></span>  
  
|<span data-ttu-id="60302-107">Süre</span><span class="sxs-lookup"><span data-stu-id="60302-107">Term</span></span>|<span data-ttu-id="60302-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="60302-108">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="60302-109">İşlenmekte olan olayın adı.</span><span class="sxs-lookup"><span data-stu-id="60302-109">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="60302-110">Şu anda olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="60302-110">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60302-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60302-111">Remarks</span></span>  

 <span data-ttu-id="60302-112">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="60302-112">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="60302-113">Özel olaylar için, `RemoveHandler` ifade olayın `RemoveHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="60302-113">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="60302-114">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="60302-114">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60302-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="60302-115">Example</span></span>  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="60302-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60302-116">See also</span></span>

- [<span data-ttu-id="60302-117">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="60302-117">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="60302-118">Handles</span><span class="sxs-lookup"><span data-stu-id="60302-118">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="60302-119">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="60302-119">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="60302-120">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="60302-120">Events</span></span>](../../programming-guide/language-features/events/index.md)
