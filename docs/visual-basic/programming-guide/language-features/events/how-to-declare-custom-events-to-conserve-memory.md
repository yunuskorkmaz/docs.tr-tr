---
title: 'Nasıl yapılır: (Visual Basic) bellekten kazanacak şekilde özel olayları bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3bd58a09d016d818c4cc88c1d2527e81a95411e6
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967132"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="14a71-102">Nasıl yapılır: (Visual Basic) bellekten kazanacak şekilde özel olayları bildirme</span><span class="sxs-lookup"><span data-stu-id="14a71-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="14a71-103">Uygulamanın bellek kullanımı düşük tutmak önemlidir, çeşitli koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="14a71-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="14a71-104">Özel olaylar yalnızca işleme olayları için bellek kullanmak için uygulamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="14a71-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="14a71-105">Bir sınıf bir olay bildirir, varsayılan olarak, derleyici olay bilgilerini depolamak bir alan için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="14a71-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="14a71-106">Bir sınıf birçok kullanılmayan olay varsa, bunlar gereksiz yere belleği yararlanın.</span><span class="sxs-lookup"><span data-stu-id="14a71-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="14a71-107">Visual Basic sağlayan olaylar varsayılan uygulamasını kullanmak yerine, bellek kullanımı daha dikkatli bir şekilde yönetmek için özel olaylar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="14a71-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14a71-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="14a71-108">Example</span></span>  
 <span data-ttu-id="14a71-109">Bu örnekte, sınıfın bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> depolanan sınıfı `Events` alan, kullanım olaylarına ilişkin bilgileri depolamak için.</span><span class="sxs-lookup"><span data-stu-id="14a71-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="14a71-110"><xref:System.ComponentModel.EventHandlerList> Temsilciler tutmak için tasarlanan bir en iyi duruma getirilmiş listesi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="14a71-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="14a71-111">Tüm olayları sınıfı kullanımda `Events` her bir olay işleme hangi yöntemi izlemek için alan.</span><span class="sxs-lookup"><span data-stu-id="14a71-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="14a71-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14a71-112">See also</span></span>
- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="14a71-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="14a71-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="14a71-114">Nasıl yapılır: Engellemekten Kaçınacak şekilde özel olayları bildirme</span><span class="sxs-lookup"><span data-stu-id="14a71-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
