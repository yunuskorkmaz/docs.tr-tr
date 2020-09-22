---
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 0481bd5e4dfe7a24dff454d0754b519509fa967f
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875740"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="a4feb-102">Hatalı DLL çağrı standardı</span><span class="sxs-lookup"><span data-stu-id="a4feb-102">Bad DLL calling convention</span></span>

<span data-ttu-id="a4feb-103">Dinamik bağlantı kitaplığına (DLL) geçirilen bağımsız değişkenler, yordam tarafından beklenen olanlarla tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="a4feb-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="a4feb-104">Çağırma kuralları, bağımsız değişkenlerin sayısı, türü ve sırası ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="a4feb-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="a4feb-105">Programınız yanlış tür veya bağımsız değişken sayısı geçirmekte olan bir DLL 'deki bir yordamı çağırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4feb-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a4feb-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a4feb-106">To correct this error</span></span>  
  
1. <span data-ttu-id="a4feb-107">Tüm bağımsız değişken türlerinin, aradığınız yordamın bildiriminde belirtilenlerle uyumlu olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4feb-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="a4feb-108">Aradığınız yordamın bildiriminde belirtilen sayıda bağımsız değişkeni geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4feb-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="a4feb-109">DLL yordamı değere göre bağımsız değişkenler bekliyorsa, `ByVal` Bu yordamın bildiriminde bu bağımsız değişkenler için belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a4feb-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4feb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4feb-110">See also</span></span>

- [<span data-ttu-id="a4feb-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="a4feb-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="a4feb-112">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="a4feb-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="a4feb-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="a4feb-113">Declare Statement</span></span>](../statements/declare-statement.md)
