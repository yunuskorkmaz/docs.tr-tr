---
title: "Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="d794a-102">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d794a-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="d794a-103">Bir uygulama bellek kullanımı düşük tutmak önemlidir, çeşitli koşullar vardır.</span><span class="sxs-lookup"><span data-stu-id="d794a-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="d794a-104">Özel olaylar, işleme olayları yalnızca bellek kullanmak için uygulamayı izin verin.</span><span class="sxs-lookup"><span data-stu-id="d794a-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="d794a-105">Bir sınıf bir olay bildirir, varsayılan olarak, derleyicinin olay bilgilerini depolamak bir alan için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="d794a-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="d794a-106">Bir sınıf çok sayıda kullanılmayan olay varsa, bunlar gereksiz yere bellekte alın.</span><span class="sxs-lookup"><span data-stu-id="d794a-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="d794a-107">Visual Basic sağlar olayları varsayılan uygulaması kullanmak yerine, bellek kullanımı daha dikkatli bir şekilde yönetmek için özel olaylar kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d794a-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d794a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="d794a-108">Example</span></span>  
 <span data-ttu-id="d794a-109">Bu örnekte, sınıfı tek bir örneğini kullanır. <xref:System.ComponentModel.EventHandlerList> sınıfı, depolanan `Events` kullanımda olaylar hakkında bilgi depolamak için alan.</span><span class="sxs-lookup"><span data-stu-id="d794a-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="d794a-110"><xref:System.ComponentModel.EventHandlerList> Sınıftır temsilciler tutmak için tasarlanmış bir en iyi duruma getirilmiş listesi.</span><span class="sxs-lookup"><span data-stu-id="d794a-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="d794a-111">Tüm olayları sınıfı kullanımda `Events` hangi yöntemlerin her olay işleme izlemek için alan.</span><span class="sxs-lookup"><span data-stu-id="d794a-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d794a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d794a-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="d794a-113">Olayları</span><span class="sxs-lookup"><span data-stu-id="d794a-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="d794a-114">Nasıl yapılır: engellemekten Kaçınacak şekilde özel olayları bildirme</span><span class="sxs-lookup"><span data-stu-id="d794a-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
