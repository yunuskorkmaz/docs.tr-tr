---
title: RemoveHandler Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="c1c67-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="c1c67-102">RemoveHandler Statement</span></span>
<span data-ttu-id="c1c67-103">Bir olayın olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c1c67-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1c67-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="c1c67-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1c67-105">Parts</span></span>  
  
|<span data-ttu-id="c1c67-106">Terim</span><span class="sxs-lookup"><span data-stu-id="c1c67-106">Term</span></span>|<span data-ttu-id="c1c67-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="c1c67-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="c1c67-108">İşlenen olay adı.</span><span class="sxs-lookup"><span data-stu-id="c1c67-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="c1c67-109">Şu anda olay işleme yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="c1c67-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1c67-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1c67-110">Remarks</span></span>  
 <span data-ttu-id="c1c67-111">`AddHandler` Ve `RemoveHandler` deyimleri program yürütme sırasında her zaman belirli bir olay için olay işleme durdurmak ve başlatmak izin.</span><span class="sxs-lookup"><span data-stu-id="c1c67-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c67-112">Özel olaylar için `RemoveHandler` deyimi çağırır olayın `RemoveHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="c1c67-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="c1c67-113">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c1c67-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1c67-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="c1c67-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c1c67-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1c67-115">See Also</span></span>  
 [<span data-ttu-id="c1c67-116">AddHandler deyimi</span><span class="sxs-lookup"><span data-stu-id="c1c67-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="c1c67-117">İşleme</span><span class="sxs-lookup"><span data-stu-id="c1c67-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="c1c67-118">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="c1c67-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="c1c67-119">Olayları</span><span class="sxs-lookup"><span data-stu-id="c1c67-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
