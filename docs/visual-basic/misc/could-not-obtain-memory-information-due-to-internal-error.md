---
title: İç hata nedeniyle bellek bilgileri alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: dff6ee2f0f46052efae557e1216f73b9f249b464
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402258"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="36b48-102">İç hata nedeniyle bellek bilgileri alınamadı</span><span class="sxs-lookup"><span data-stu-id="36b48-102">Could not obtain memory information due to internal error</span></span>
<span data-ttu-id="36b48-103">Nesnenin bellek bilgisi özelliklerinden birine çağrı `My.Computer.Info` başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="36b48-103">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="36b48-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="36b48-104">To correct this error</span></span>  
  
- <span data-ttu-id="36b48-105">`Try...Catch`Nesnenin Memory-Information özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Info` .</span><span class="sxs-lookup"><span data-stu-id="36b48-105">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36b48-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36b48-106">See also</span></span>

- [<span data-ttu-id="36b48-107">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="36b48-107">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [<span data-ttu-id="36b48-108">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="36b48-108">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
