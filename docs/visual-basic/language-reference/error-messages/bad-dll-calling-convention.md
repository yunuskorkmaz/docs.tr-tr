---
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409887"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="f19f2-102">Hatalı DLL çağrı standardı</span><span class="sxs-lookup"><span data-stu-id="f19f2-102">Bad DLL calling convention</span></span>
<span data-ttu-id="f19f2-103">Dinamik bağlantı kitaplığına (DLL) geçirilen bağımsız değişkenler, yordam tarafından beklenen olanlarla tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="f19f2-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="f19f2-104">Çağırma kuralları, bağımsız değişkenlerin sayısı, türü ve sırası ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="f19f2-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="f19f2-105">Programınız yanlış tür veya bağımsız değişken sayısı geçirmekte olan bir DLL 'deki bir yordamı çağırıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f19f2-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f19f2-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f19f2-106">To correct this error</span></span>  
  
1. <span data-ttu-id="f19f2-107">Tüm bağımsız değişken türlerinin, aradığınız yordamın bildiriminde belirtilenlerle uyumlu olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="f19f2-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="f19f2-108">Aradığınız yordamın bildiriminde belirtilen sayıda bağımsız değişkeni geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f19f2-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="f19f2-109">DLL yordamı değere göre bağımsız değişkenler bekliyorsa, `ByVal` Bu yordamın bildiriminde bu bağımsız değişkenler için belirtildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f19f2-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19f2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f19f2-110">See also</span></span>

- [<span data-ttu-id="f19f2-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="f19f2-111">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="f19f2-112">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="f19f2-112">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="f19f2-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="f19f2-113">Declare Statement</span></span>](../statements/declare-statement.md)
