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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404258"
---
# <a name="removehandler-statement"></a><span data-ttu-id="8769a-102">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="8769a-102">RemoveHandler Statement</span></span>
<span data-ttu-id="8769a-103">Bir olay ve olay işleyicisi arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="8769a-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8769a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8769a-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="8769a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="8769a-105">Parts</span></span>  
  
|<span data-ttu-id="8769a-106">Terim</span><span class="sxs-lookup"><span data-stu-id="8769a-106">Term</span></span>|<span data-ttu-id="8769a-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="8769a-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="8769a-108">İşlenmekte olan olayın adı.</span><span class="sxs-lookup"><span data-stu-id="8769a-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="8769a-109">Şu anda olayı işleyen yordamın adı.</span><span class="sxs-lookup"><span data-stu-id="8769a-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8769a-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8769a-110">Remarks</span></span>  
 <span data-ttu-id="8769a-111">`AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="8769a-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8769a-112">Özel olaylar için, `RemoveHandler` ifade olayın `RemoveHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="8769a-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="8769a-113">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8769a-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8769a-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="8769a-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="8769a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8769a-115">See also</span></span>

- [<span data-ttu-id="8769a-116">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="8769a-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="8769a-117">Handles</span><span class="sxs-lookup"><span data-stu-id="8769a-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="8769a-118">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="8769a-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="8769a-119">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8769a-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
