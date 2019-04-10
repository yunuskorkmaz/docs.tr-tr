---
title: Hatalı DLL çağrı standardı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59306631"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="5779a-102">Hatalı DLL çağrı standardı</span><span class="sxs-lookup"><span data-stu-id="5779a-102">Bad DLL calling convention</span></span>
<span data-ttu-id="5779a-103">Bir dinamik bağlantı kitaplığı (DLL) geçirilen bağımsız değişkenler bu yordamı tarafından beklenen tam olarak eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="5779a-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="5779a-104">Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="5779a-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="5779a-105">Programınızı türü yanlış veya bağımsız değişken sayısı geçirilen bir DLL içinde bir yordam çağırma.</span><span class="sxs-lookup"><span data-stu-id="5779a-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5779a-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="5779a-106">To correct this error</span></span>  
  
1. <span data-ttu-id="5779a-107">Aradığınız yordamı bildiriminde belirtilen değerlerle tüm bağımsız değişken türlerini kabul emin olun.</span><span class="sxs-lookup"><span data-stu-id="5779a-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="5779a-108">Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenleri aynı sayıda geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="5779a-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="5779a-109">DLL yordamı değere göre bağımsız değişken bekler, emin `ByVal` yordam bildirimi bu bağımsız değişken belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="5779a-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5779a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5779a-110">See also</span></span>

- [<span data-ttu-id="5779a-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="5779a-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="5779a-112">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="5779a-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)
- [<span data-ttu-id="5779a-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="5779a-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
