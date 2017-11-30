---
title: "Nesne veya sınıf olay kümesini desteklemiyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="2c316-102">Nesne veya sınıf olay kümesini desteklemiyor</span><span class="sxs-lookup"><span data-stu-id="2c316-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="2c316-103">Kullanmaya çalıştığınız bir `WithEvents` olayları belirtilen kümesi için bir olay kaynağı olarak çalışamaz bir bileşeni ile değişken.</span><span class="sxs-lookup"><span data-stu-id="2c316-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="2c316-104">Örneğin, bir nesne olaylar indirilir, sonra başka bir nesne oluşturmak istediğiniz `Implements` ilk nesne.</span><span class="sxs-lookup"><span data-stu-id="2c316-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="2c316-105">Uygulanan nesneden olayları havuzu düşünebilirsiniz karşın, bu her zaman durumda değil.</span><span class="sxs-lookup"><span data-stu-id="2c316-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="2c316-106">`Implements`yalnızca yöntemleri ve özellikleri için bir arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="2c316-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="2c316-107">`WithEvents`Özel için desteklenmeyen `UserControls`, type Info yükseltmek gereken `ObjectEvent` çalışma zamanında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="2c316-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2c316-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2c316-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="2c316-109">Olay kaynağı olmayan bir bileşen için olayları kapatamıyor.</span><span class="sxs-lookup"><span data-stu-id="2c316-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c316-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2c316-110">See Also</span></span>  
 [<span data-ttu-id="2c316-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="2c316-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="2c316-112">Implements deyimi</span><span class="sxs-lookup"><span data-stu-id="2c316-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
