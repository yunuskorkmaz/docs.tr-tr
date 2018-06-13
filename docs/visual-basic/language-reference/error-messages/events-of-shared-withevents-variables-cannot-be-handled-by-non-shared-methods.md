---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585177"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="7de05-102">Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez</span><span class="sxs-lookup"><span data-stu-id="7de05-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="7de05-103">İle bildirilen bir değişken `Shared` değiştiricisi paylaşılan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="7de05-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="7de05-104">Paylaşılan değişken tam olarak bir depolama konumu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7de05-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="7de05-105">İle bildirilen bir değişken `WithEvents` değiştiricisi onaylar değişkeni ait olduğu türü değişkeni başlatır olay kümesini işler.</span><span class="sxs-lookup"><span data-stu-id="7de05-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="7de05-106">Değişkene bir değer atandığında, özellik tarafından oluşturulan `WithEvents` bildirim varolan herhangi bir olay işleyicisini unhooks ve yeni olay işleyicisi kancalarını `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7de05-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="7de05-107">**Hata Kimliği:** BC30594</span><span class="sxs-lookup"><span data-stu-id="7de05-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7de05-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7de05-108">To correct this error</span></span>  
  
-   <span data-ttu-id="7de05-109">Olay işleyici bildirmek `Shared`.</span><span class="sxs-lookup"><span data-stu-id="7de05-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de05-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7de05-110">See Also</span></span>  
 [<span data-ttu-id="7de05-111">Shared</span><span class="sxs-lookup"><span data-stu-id="7de05-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="7de05-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="7de05-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
