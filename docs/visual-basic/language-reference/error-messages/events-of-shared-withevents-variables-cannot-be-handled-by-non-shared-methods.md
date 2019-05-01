---
title: Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803274"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="852c8-102">Paylaşılan WithEvents değişkenlerinin olayları paylaşılmayan yöntemler tarafından işlenemez</span><span class="sxs-lookup"><span data-stu-id="852c8-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="852c8-103">Bildirilen bir değişken `Shared` değiştiricisi paylaşılan bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="852c8-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="852c8-104">Paylaşılan değişken tam olarak bir depolama konumunu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="852c8-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="852c8-105">Bildirilen bir değişken `WithEvents` değiştiricisi onaylar değişkeni ait olduğu tür değişken başlatır olay kümesini işler.</span><span class="sxs-lookup"><span data-stu-id="852c8-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="852c8-106">Bir değeri bir değişkene atandığında, özellik tarafından oluşturulan `WithEvents` bildirimi var olan herhangi bir olay işleyici unhooks ve yeni olay işleyicisi'kurmak kancaları `Add` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="852c8-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="852c8-107">**Hata Kimliği:** BC30594</span><span class="sxs-lookup"><span data-stu-id="852c8-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="852c8-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="852c8-108">To correct this error</span></span>  
  
- <span data-ttu-id="852c8-109">Olay işleyici bildirmek `Shared`.</span><span class="sxs-lookup"><span data-stu-id="852c8-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="852c8-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="852c8-110">See also</span></span>

- [<span data-ttu-id="852c8-111">Shared</span><span class="sxs-lookup"><span data-stu-id="852c8-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="852c8-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="852c8-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
