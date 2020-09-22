---
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 6dd6805151de52a5e0cf51c520485c0e8558e0a7
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90870835"
---
# <a name="resume-without-error"></a><span data-ttu-id="d6acc-102">Hatasız devam et</span><span class="sxs-lookup"><span data-stu-id="d6acc-102">Resume without error</span></span>

<span data-ttu-id="d6acc-103">Hata `Resume` işleme kodu dışında bir ifade görüntülendi veya hata olmamasına rağmen kod bir hata işleyicisine atlandı.</span><span class="sxs-lookup"><span data-stu-id="d6acc-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6acc-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d6acc-104">To correct this error</span></span>  
  
1. <span data-ttu-id="d6acc-105">`Resume`İfadeyi bir hata işleyicisine taşıyın veya silin.</span><span class="sxs-lookup"><span data-stu-id="d6acc-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="d6acc-106">Etiketlere atlamalar yordamlar arasında gerçekleşemez, bu nedenle hata işleyicisini tanımlayan etikete yönelik yordamda arama yapın.</span><span class="sxs-lookup"><span data-stu-id="d6acc-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="d6acc-107">Bir ifade olmayan bir deyimin hedefi olarak belirtilen yinelenen bir etiket bulursanız `GoTo` `On Error GoTo` , çizgi etiketini amaçlanan hedefle kabul etmek üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d6acc-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6acc-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6acc-108">See also</span></span>

- [<span data-ttu-id="d6acc-109">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="d6acc-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="d6acc-110">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="d6acc-110">On Error Statement</span></span>](../statements/on-error-statement.md)
