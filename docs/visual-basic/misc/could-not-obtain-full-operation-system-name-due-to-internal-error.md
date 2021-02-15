---
description: 'Hakkında daha fazla bilgi edinin: iç hata nedeniyle tam işlem sistem adı alınamadı'
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: d274a08728b084b21309862de69e2fded5c164da
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100463500"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="2e05a-103">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="2e05a-103">Could not obtain full operation system name due to internal error</span></span>

<span data-ttu-id="2e05a-104">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="2e05a-104">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="2e05a-105">Bu durum, WMI 'nin geçerli makinede mevcut olmadığından kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e05a-105">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="2e05a-106">`My.Computer.Info.OSFullName`Özelliğe çağrı başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="2e05a-106">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="2e05a-107">Bu hatanın olası nedeni, geçerli bilgisayarda Windows Yönetim Araçları (WMI) yüklü değildir.</span><span class="sxs-lookup"><span data-stu-id="2e05a-107">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2e05a-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="2e05a-108">To correct this error</span></span>  
  
1. <span data-ttu-id="2e05a-109">Özelliğe yapılan `Try...Catch` çağrının etrafına bir blok ekleyin `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="2e05a-109">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2. <span data-ttu-id="2e05a-110">WMI ve nasıl yükleneceğine ilişkin daha fazla bilgi için şuraya gidin ve "Windows Yönetim Araçları Core" ifadesini arayın.</span><span class="sxs-lookup"><span data-stu-id="2e05a-110">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e05a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e05a-111">See also</span></span>

- [<span data-ttu-id="2e05a-112">My. Computer. Info. OSFullName</span><span class="sxs-lookup"><span data-stu-id="2e05a-112">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="2e05a-113">.NET 'te özel durumları işleme ve atma</span><span class="sxs-lookup"><span data-stu-id="2e05a-113">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="2e05a-114">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="2e05a-114">Try...Catch...Finally Statement</span></span>](../language-reference/statements/try-catch-finally-statement.md)
