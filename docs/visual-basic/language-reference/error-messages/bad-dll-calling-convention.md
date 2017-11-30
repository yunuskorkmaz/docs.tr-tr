---
title: "Hatalı DLL çağırma kuralı"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="51ac7-102">Hatalı DLL çağırma kuralı</span><span class="sxs-lookup"><span data-stu-id="51ac7-102">Bad DLL calling convention</span></span>
<span data-ttu-id="51ac7-103">Dinamik bağlantı kitaplığı (DLL) için geçirilen bağımsız değişken tam olarak yordamı tarafından beklenen eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="51ac7-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="51ac7-104">Çağırma kuralları sayısı, türü ve bağımsız değişkenlerin sırası göz ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="51ac7-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="51ac7-105">Programınızı türü yanlış veya bağımsız değişken sayısı geçirilmiş bir DLL'de bir yordam çağırma.</span><span class="sxs-lookup"><span data-stu-id="51ac7-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="51ac7-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="51ac7-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="51ac7-107">Aradığınız yordamı bildiriminde belirtilen ile tüm bağımsız değişken türleri kabul emin olun.</span><span class="sxs-lookup"><span data-stu-id="51ac7-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="51ac7-108">Aradığınız yordamı bildiriminde belirtilen bağımsız değişkenler aynı sayıda geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="51ac7-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="51ac7-109">DLL yordam bağımsız değişkenleri değere göre bekler, emin olun `ByVal` yordamı için bildiriminde bu bağımsız değişkenler için belirtilir.</span><span class="sxs-lookup"><span data-stu-id="51ac7-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ac7-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51ac7-110">See Also</span></span>  
 [<span data-ttu-id="51ac7-111">Hata türleri</span><span class="sxs-lookup"><span data-stu-id="51ac7-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="51ac7-112">Call deyimi</span><span class="sxs-lookup"><span data-stu-id="51ac7-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="51ac7-113">Declare deyimi</span><span class="sxs-lookup"><span data-stu-id="51ac7-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
