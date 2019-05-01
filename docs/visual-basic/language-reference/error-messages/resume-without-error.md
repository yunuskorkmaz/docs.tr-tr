---
title: Hatasız devam et
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 61332486b20af66af24eac06b222a38353578c16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055166"
---
# <a name="resume-without-error"></a><span data-ttu-id="0019d-102">Hatasız devam et</span><span class="sxs-lookup"><span data-stu-id="0019d-102">Resume without error</span></span>
<span data-ttu-id="0019d-103">A `Resume` deyimi görünen hata işleme kodu dışında ya da kodu herhangi bir hata oluştu rağmen bir hata işleyicisine Atlanan.</span><span class="sxs-lookup"><span data-stu-id="0019d-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0019d-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0019d-104">To correct this error</span></span>  
  
1. <span data-ttu-id="0019d-105">Taşıma `Resume` bir hata işleyicisi INTO deyimi veya silin.</span><span class="sxs-lookup"><span data-stu-id="0019d-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2. <span data-ttu-id="0019d-106">Etiketlere atlama yordamları arasında oluşamaz yordamı hata işleyicisi tanımlayan etiket için arama.</span><span class="sxs-lookup"><span data-stu-id="0019d-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="0019d-107">Hedefi olarak belirtilen bir yinelenen etiket bulursanız bir `GoTo` olmayan deyimi bir `On Error GoTo` deyimi, hedeflenen hedefine ile uyuşacak şekilde satır etiketi değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0019d-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0019d-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0019d-108">See also</span></span>

- [<span data-ttu-id="0019d-109">Resume Deyimi</span><span class="sxs-lookup"><span data-stu-id="0019d-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)
- [<span data-ttu-id="0019d-110">On Error Deyimi</span><span class="sxs-lookup"><span data-stu-id="0019d-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
