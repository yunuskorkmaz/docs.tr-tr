---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 67e8fb5e906800d28bf15714463b7ff6ae585693
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402284"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="1e57a-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="1e57a-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="1e57a-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="1e57a-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="1e57a-104">Bu durum, WMI 'nin geçerli makinede mevcut olmadığından kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e57a-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="1e57a-105">`My.Computer.Info.OSFullName`Özelliğe çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="1e57a-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="1e57a-106">Bu hatanın olası nedeni, geçerli bilgisayarda Windows Yönetim Araçları (WMI) yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="1e57a-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1e57a-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="1e57a-107">To correct this error</span></span>  
  
1. <span data-ttu-id="1e57a-108">Özelliğe yapılan `Try...Catch` çağrının etrafına bir blok ekleyin `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="1e57a-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="1e57a-109">WMI ve nasıl yükleneceğine ilişkin daha fazla bilgi için şuraya gidin ve "Windows Yönetim Araçları Core" ifadesini arayın.</span><span class="sxs-lookup"><span data-stu-id="1e57a-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e57a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e57a-110">See also</span></span>

- [<span data-ttu-id="1e57a-111">My. Computer. Info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="1e57a-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="1e57a-112">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="1e57a-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="1e57a-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="1e57a-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
