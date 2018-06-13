---
title: Hatalı DLL çağırma kuralı
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583844"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="2dd33-102">Hatalı DLL çağırma kuralı</span><span class="sxs-lookup"><span data-stu-id="2dd33-102">Bad DLL calling convention</span></span>
<span data-ttu-id="2dd33-103">Dinamik bağlantı kitaplığı (DLL) için geçirilen bağımsız değişken tam olarak yordamı tarafından beklenen eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="2dd33-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="2dd33-104">Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası göz ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="2dd33-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="2dd33-105">Programınızı türü yanlış veya bağımsız değişken sayısı geçirilmiş bir DLL'de bir yordam çağırma.</span><span class="sxs-lookup"><span data-stu-id="2dd33-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2dd33-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2dd33-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="2dd33-107">Aradığınız yordamı bildiriminde belirtilen ile tüm bağımsız değişken türleri kabul emin olun.</span><span class="sxs-lookup"><span data-stu-id="2dd33-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="2dd33-108">Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenler aynı sayıda geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2dd33-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="2dd33-109">DLL yordam bağımsız değişkenleri değere göre bekler, emin olun `ByVal` yordamı için bildiriminde bu bağımsız değişkenler için belirtilir.</span><span class="sxs-lookup"><span data-stu-id="2dd33-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dd33-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2dd33-110">See Also</span></span>  
 [<span data-ttu-id="2dd33-111">Hata Türleri</span><span class="sxs-lookup"><span data-stu-id="2dd33-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="2dd33-112">Call Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dd33-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="2dd33-113">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="2dd33-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
