---
description: 'Hakkında daha fazla bilgi edinin: hata olmadan özgeçmişi'
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: a2284484be65ae975c6e09499ec19e3cfd8d4a04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792017"
---
# <a name="resume-without-error"></a><span data-ttu-id="246ec-103">Hatasız devam et</span><span class="sxs-lookup"><span data-stu-id="246ec-103">Resume without error</span></span>

<span data-ttu-id="246ec-104">Hata `Resume` işleme kodu dışında bir ifade görüntülendi veya hata olmamasına rağmen kod bir hata işleyicisine atlandı.</span><span class="sxs-lookup"><span data-stu-id="246ec-104">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="246ec-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="246ec-105">To correct this error</span></span>  
  
1. <span data-ttu-id="246ec-106">`Resume`İfadeyi bir hata işleyicisine taşıyın veya silin.</span><span class="sxs-lookup"><span data-stu-id="246ec-106">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="246ec-107">Etiketlere atlamalar yordamlar arasında gerçekleşemez, bu nedenle hata işleyicisini tanımlayan etikete yönelik yordamda arama yapın.</span><span class="sxs-lookup"><span data-stu-id="246ec-107">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="246ec-108">Bir ifade olmayan bir deyimin hedefi olarak belirtilen yinelenen bir etiket bulursanız `GoTo` `On Error GoTo` , çizgi etiketini amaçlanan hedefle kabul etmek üzere değiştirin.</span><span class="sxs-lookup"><span data-stu-id="246ec-108">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="246ec-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="246ec-109">See also</span></span>

- [<span data-ttu-id="246ec-110">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="246ec-110">Resume Statement</span></span>](../statements/resume-statement.md)
- [<span data-ttu-id="246ec-111">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="246ec-111">On Error Statement</span></span>](../statements/on-error-statement.md)
