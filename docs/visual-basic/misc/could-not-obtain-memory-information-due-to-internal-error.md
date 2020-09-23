---
title: İç hata nedeniyle bellek bilgileri alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: 550ac0345d54c8a78e805b224ffaba47a3970ea9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91076285"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="495bf-102">İç hata nedeniyle bellek bilgileri alınamadı</span><span class="sxs-lookup"><span data-stu-id="495bf-102">Could not obtain memory information due to internal error</span></span>

<span data-ttu-id="495bf-103">Nesnenin bellek bilgisi özelliklerinden birine çağrı `My.Computer.Info` başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="495bf-103">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="495bf-104">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="495bf-104">To correct this error</span></span>  
  
- <span data-ttu-id="495bf-105">`Try...Catch`Nesnenin Memory-Information özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Info` .</span><span class="sxs-lookup"><span data-stu-id="495bf-105">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495bf-106">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="495bf-106">See also</span></span>

- [<span data-ttu-id="495bf-107">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="495bf-107">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [<span data-ttu-id="495bf-108">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="495bf-108">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
