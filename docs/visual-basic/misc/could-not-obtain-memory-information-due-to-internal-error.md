---
description: 'Hakkında daha fazla bilgi edinin: iç hata nedeniyle bellek bilgileri alınamadı'
title: İç hata nedeniyle bellek bilgileri alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_Memory
ms.assetid: 1ba8f774-5858-438e-914e-99fddc9e5e7e
ms.openlocfilehash: 08e85371f19f1e6e365e201c1a43bd679d7847e6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463494"
---
# <a name="could-not-obtain-memory-information-due-to-internal-error"></a><span data-ttu-id="c7784-103">İç hata nedeniyle bellek bilgileri alınamadı</span><span class="sxs-lookup"><span data-stu-id="c7784-103">Could not obtain memory information due to internal error</span></span>

<span data-ttu-id="c7784-104">Nesnenin bellek bilgisi özelliklerinden birine çağrı `My.Computer.Info` başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="c7784-104">A call to one of the memory-information properties of the `My.Computer.Info` object failed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c7784-105">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c7784-105">To correct this error</span></span>  
  
- <span data-ttu-id="c7784-106">`Try...Catch`Nesnenin Memory-Information özelliğine yapılan çağrının etrafına bir blok ekleyin `My.Computer.Info` .</span><span class="sxs-lookup"><span data-stu-id="c7784-106">Add a `Try...Catch` block around the call to the memory-information property of the `My.Computer.Info` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7784-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7784-107">See also</span></span>

- [<span data-ttu-id="c7784-108">My.Computer.Info</span><span class="sxs-lookup"><span data-stu-id="c7784-108">My.Computer.Info</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo)
- [<span data-ttu-id="c7784-109">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="c7784-109">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
