---
title: 'Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: c9a049d3f15d5620152f064888a97bd0be5d46b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405137"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="8667d-102">Nasıl yapılır: Bellekten Kazanacak Şekilde Özel Olayları Bildirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8667d-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="8667d-103">Bir uygulamanın bellek kullanımını düşük tutması önemli olduğunda bazı durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="8667d-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="8667d-104">Özel olaylar, uygulamanın yalnızca işlediği olaylar için belleği kullanmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="8667d-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="8667d-105">Varsayılan olarak, bir sınıf bir olay bildirdiğini derleyici, olay bilgilerini depolamak için bir alan için bellek ayırır.</span><span class="sxs-lookup"><span data-stu-id="8667d-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="8667d-106">Bir sınıfta çok sayıda kullanılmamış olay varsa, bu, belleğin sorunsuz bir şekilde sürmasını isterler.</span><span class="sxs-lookup"><span data-stu-id="8667d-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="8667d-107">Visual Basic sağladığı olayların varsayılan uygulamasını kullanmak yerine, bellek kullanımını daha dikkatli bir şekilde yönetmek için özel olayları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8667d-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8667d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="8667d-108">Example</span></span>  
 <span data-ttu-id="8667d-109">Bu örnekte, sınıfı, <xref:System.ComponentModel.EventHandlerList> `Events` Kullanımdaki olaylar hakkında bilgi depolamak için, alanında depolanan sınıfının bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8667d-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="8667d-110"><xref:System.ComponentModel.EventHandlerList>Sınıfı, temsilcileri tutmak için tasarlanan iyileştirilmiş bir liste sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="8667d-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="8667d-111">Sınıftaki tüm olaylar, `Events` her bir olayın hangi yöntemlerin işleme olduğunu izlemek için alanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="8667d-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="8667d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8667d-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="8667d-113">Olaylar</span><span class="sxs-lookup"><span data-stu-id="8667d-113">Events</span></span>](index.md)
- [<span data-ttu-id="8667d-114">Nasıl yapılır: Engellemekten Kaçınacak Şekilde Özel Olayları Bildirme</span><span class="sxs-lookup"><span data-stu-id="8667d-114">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
