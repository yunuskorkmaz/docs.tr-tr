---
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: b6b565c88acadca048ade22ab00ac68539725f78
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400376"
---
# <a name="resume-without-error"></a><span data-ttu-id="0a19f-102">Hatasız devam et</span><span class="sxs-lookup"><span data-stu-id="0a19f-102">Resume without error</span></span>
<span data-ttu-id="0a19f-103">Hata `Resume` işleme kodu dışında bir ifade görüntülendi veya hata olmamasına rağmen kod bir hata işleyicisine atlandı.</span><span class="sxs-lookup"><span data-stu-id="0a19f-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a19f-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0a19f-104">To correct this error</span></span>  
  
1. <span data-ttu-id="0a19f-105">`Resume`İfadeyi bir hata işleyicisine taşıyın veya silin.</span><span class="sxs-lookup"><span data-stu-id="0a19f-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="0a19f-106">Etiketlere atlamalar yordamlar arasında gerçekleşemez, bu nedenle hata işleyicisini tanımlayan etikete yönelik yordamda arama yapın.</span><span class="sxs-lookup"><span data-stu-id="0a19f-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="0a19f-107">Bir ifade olmayan bir deyimin hedefi olarak belirtilen yinelenen bir etiket bulursanız `GoTo` `On Error GoTo` , çizgi etiketini amaçlanan hedefle kabul etmek üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0a19f-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a19f-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a19f-108">See also</span></span>

- [<span data-ttu-id="0a19f-109">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="0a19f-109">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="0a19f-110">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="0a19f-110">On Error Statement</span></span>](../statements/on-error-statement.md)
