---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="4b885-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b885-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="4b885-103">Bir veya daha fazla bildirilen üye değişkenleri olayları yükseltebilirsiniz bir sınıfın bir örneğine başvuru belirtir.</span><span class="sxs-lookup"><span data-stu-id="4b885-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b885-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4b885-104">Remarks</span></span>  
 <span data-ttu-id="4b885-105">Bir değişken kullanarak tanımlandığında `WithEvents`, bir yöntem kullanarak değişkenin olayları işleme bildirimli olarak belirtebilirsiniz `Handles` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="4b885-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="4b885-106">Kullanabileceğiniz `WithEvents` yalnızca düzeyinde sınıfı veya modülü.</span><span class="sxs-lookup"><span data-stu-id="4b885-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="4b885-107">Bu bildirimi bağlamının anlamına gelir bir `WithEvents` değişkeni bir sınıf veya modülü olmalıdır ve kaynak dosyasını, ad alanı, yapı veya yordam olamaz.</span><span class="sxs-lookup"><span data-stu-id="4b885-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="4b885-108">Kullanamazsınız `WithEvents` yapısı üyede.</span><span class="sxs-lookup"><span data-stu-id="4b885-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="4b885-109">Yalnızca bağımsız değişkenleri bildirebilir — değil diziler — ile `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="4b885-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4b885-110">Kurallar</span><span class="sxs-lookup"><span data-stu-id="4b885-110">Rules</span></span>  
  
-   <span data-ttu-id="4b885-111">**Öğe türleri.**</span><span class="sxs-lookup"><span data-stu-id="4b885-111">**Element Types.**</span></span> <span data-ttu-id="4b885-112">Bildirmelisiniz `WithEvents` bunlar kabul edebilmesi için nesne değişkenleri olmasını değişkenleri sınıf örnekleri.</span><span class="sxs-lookup"><span data-stu-id="4b885-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="4b885-113">Ancak, bunları olarak bildiremezsiniz `Object`.</span><span class="sxs-lookup"><span data-stu-id="4b885-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="4b885-114">Bunları olaylar oluşturabilir belirli sınıfı olarak bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4b885-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="4b885-115">`WithEvents` Bu bağlamda değiştirici kullanılabilir: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="4b885-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b885-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4b885-116">See Also</span></span>  
 [<span data-ttu-id="4b885-117">İşleme</span><span class="sxs-lookup"><span data-stu-id="4b885-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="4b885-118">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4b885-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="4b885-119">Olayları</span><span class="sxs-lookup"><span data-stu-id="4b885-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
