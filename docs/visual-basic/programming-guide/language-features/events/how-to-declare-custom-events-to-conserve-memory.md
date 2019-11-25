---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345126"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="c7185-102">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7185-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="c7185-103">There are several circumstances when it is important that an application keep its memory usage low.</span><span class="sxs-lookup"><span data-stu-id="c7185-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="c7185-104">Custom events allow the application to use memory only for the events that it handles.</span><span class="sxs-lookup"><span data-stu-id="c7185-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="c7185-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span><span class="sxs-lookup"><span data-stu-id="c7185-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="c7185-106">If a class has many unused events, they needlessly take up memory.</span><span class="sxs-lookup"><span data-stu-id="c7185-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="c7185-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span><span class="sxs-lookup"><span data-stu-id="c7185-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7185-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c7185-108">Example</span></span>  
 <span data-ttu-id="c7185-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span><span class="sxs-lookup"><span data-stu-id="c7185-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="c7185-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span><span class="sxs-lookup"><span data-stu-id="c7185-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="c7185-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span><span class="sxs-lookup"><span data-stu-id="c7185-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="c7185-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7185-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="c7185-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="c7185-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="c7185-114">Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="c7185-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
