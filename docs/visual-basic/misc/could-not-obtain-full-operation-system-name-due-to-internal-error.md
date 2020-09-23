---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 744d549b9313727af2feb82e45c24b729cae7262
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91079093"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="38e06-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="38e06-102">Could not obtain full operation system name due to internal error</span></span>

<span data-ttu-id="38e06-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="38e06-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="38e06-104">Bu durum, WMI 'nin geçerli makinede mevcut olmadığından kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="38e06-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="38e06-105">`My.Computer.Info.OSFullName`Özelliğe çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="38e06-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="38e06-106">Bu hatanın olası nedeni, geçerli bilgisayarda Windows Yönetim Araçları (WMI) yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="38e06-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38e06-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="38e06-107">To correct this error</span></span>  
  
1. <span data-ttu-id="38e06-108">Özelliğe yapılan `Try...Catch` çağrının etrafına bir blok ekleyin `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="38e06-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="38e06-109">WMI ve nasıl yükleneceğine ilişkin daha fazla bilgi için şuraya gidin ve "Windows Yönetim Araçları Core" ifadesini arayın.</span><span class="sxs-lookup"><span data-stu-id="38e06-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e06-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38e06-110">See also</span></span>

- [<span data-ttu-id="38e06-111">My. Computer. Info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="38e06-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="38e06-112">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="38e06-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="38e06-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="38e06-113">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
