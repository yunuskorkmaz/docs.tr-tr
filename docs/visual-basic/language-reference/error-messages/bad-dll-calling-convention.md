---
description: 'Daha fazla bilgi: Hatalı DLL çağırma kuralı'
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 7e98ce5131d440a12bff4a4630da087102bdc4da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797100"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="76be1-103">Hatalı DLL çağrı standardı</span><span class="sxs-lookup"><span data-stu-id="76be1-103">Bad DLL calling convention</span></span>

<span data-ttu-id="76be1-104">Dinamik bağlantı kitaplığına (DLL) geçirilen bağımsız değişkenler, yordam tarafından beklenen olanlarla tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="76be1-104">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="76be1-105">Çağırma kuralları, bağımsız değişkenlerin sayısı, türü ve sırası ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="76be1-105">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="76be1-106">Programınız yanlış tür veya bağımsız değişken sayısı geçirmekte olan bir DLL 'deki bir yordamı çağırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="76be1-106">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="76be1-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="76be1-107">To correct this error</span></span>  
  
1. <span data-ttu-id="76be1-108">Tüm bağımsız değişken türlerinin, aradığınız yordamın bildiriminde belirtilenlerle uyumlu olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="76be1-108">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="76be1-109">Aradığınız yordamın bildiriminde belirtilen sayıda bağımsız değişkeni geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="76be1-109">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="76be1-110">DLL yordamı değere göre bağımsız değişkenler bekliyorsa, `ByVal` Bu yordamın bildiriminde bu bağımsız değişkenler için belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="76be1-110">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76be1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76be1-111">See also</span></span>

- [<span data-ttu-id="76be1-112">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="76be1-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="76be1-113">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="76be1-113">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="76be1-114">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="76be1-114">Declare Statement</span></span>](../statements/declare-statement.md)
