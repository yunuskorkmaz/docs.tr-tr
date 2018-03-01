---
title: AddHandler Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="202c1-102">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="202c1-102">AddHandler Statement</span></span>
<span data-ttu-id="202c1-103">Bir olayın olay işleyicisi ile çalışma zamanında ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="202c1-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="202c1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="202c1-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="202c1-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="202c1-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="202c1-106">İşlenecek Olay adı.</span><span class="sxs-lookup"><span data-stu-id="202c1-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="202c1-107">Olay işleme bir yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="202c1-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="202c1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="202c1-108">Remarks</span></span>  
 <span data-ttu-id="202c1-109">`AddHandler` Ve `RemoveHandler` deyimleri program yürütme sırasında herhangi bir zamanda olay işleme durdurmak ve başlatmak izin.</span><span class="sxs-lookup"><span data-stu-id="202c1-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="202c1-110">İmzası `eventhandler` yordamı, olay imza eşleşmelidir `event`.</span><span class="sxs-lookup"><span data-stu-id="202c1-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="202c1-111">`Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="202c1-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="202c1-112">`AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="202c1-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="202c1-113">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="202c1-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="202c1-114">Daha fazla bilgi için bkz: [işleme](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="202c1-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="202c1-115">Özel olaylar için `AddHandler` deyimi çağırır olayın `AddHandler` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="202c1-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="202c1-116">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="202c1-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="202c1-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="202c1-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="202c1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="202c1-118">See Also</span></span>  
 [<span data-ttu-id="202c1-119">RemoveHandler deyimi</span><span class="sxs-lookup"><span data-stu-id="202c1-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="202c1-120">İşleme</span><span class="sxs-lookup"><span data-stu-id="202c1-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="202c1-121">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="202c1-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="202c1-122">Olayları</span><span class="sxs-lookup"><span data-stu-id="202c1-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
