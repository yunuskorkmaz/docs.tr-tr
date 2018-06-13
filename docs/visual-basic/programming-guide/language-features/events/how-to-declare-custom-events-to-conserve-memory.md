---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: d19c91d66e458ca2317dc049d517b92fa7406ef6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647214"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="9e9da-102">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e9da-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="9e9da-103">Bir uygulama bellek kullanımı düşük tutmak önemlidir, çeşitli koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="9e9da-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="9e9da-104">Özel olaylar, işleme olayları yalnızca bellek kullanmak için uygulamayı izin verin.</span><span class="sxs-lookup"><span data-stu-id="9e9da-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="9e9da-105">Bir sınıf bir olay bildirir, varsayılan olarak, derleyicinin olay bilgilerini depolamak bir alan için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="9e9da-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="9e9da-106">Bir sınıf çok sayıda kullanılmayan olay varsa, bunlar gereksiz yere bellekte alın.</span><span class="sxs-lookup"><span data-stu-id="9e9da-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="9e9da-107">Visual Basic sağlar olayları varsayılan uygulaması kullanmak yerine, bellek kullanımı daha dikkatli bir şekilde yönetmek için özel olaylar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9e9da-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e9da-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e9da-108">Example</span></span>  
 <span data-ttu-id="9e9da-109">Bu örnekte, sınıfı tek bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> sınıfı, depolanan `Events` kullanımda olaylar hakkında bilgi depolamak için alan.</span><span class="sxs-lookup"><span data-stu-id="9e9da-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="9e9da-110"><xref:System.ComponentModel.EventHandlerList> Sınıftır temsilciler tutmak için tasarlanmış bir en iyi duruma getirilmiş listesi.</span><span class="sxs-lookup"><span data-stu-id="9e9da-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="9e9da-111">Tüm olayları sınıfı kullanımda `Events` hangi yöntemlerin her olay işleme izlemek için alan.</span><span class="sxs-lookup"><span data-stu-id="9e9da-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e9da-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e9da-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="9e9da-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="9e9da-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="9e9da-114">Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="9e9da-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
