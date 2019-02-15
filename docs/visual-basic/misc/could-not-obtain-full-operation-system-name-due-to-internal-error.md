---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 5514544a0f5933d557690cee7508d0545e4fdd63
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303626"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="3042c-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="3042c-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="3042c-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="3042c-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="3042c-104">Bu geçerli makinede mevcut değil WMI tarafından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="3042c-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="3042c-105">Bir çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="3042c-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="3042c-106">Bu hatanın olası nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.</span><span class="sxs-lookup"><span data-stu-id="3042c-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3042c-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="3042c-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="3042c-108">Ekleme bir `Try...Catch` bloğu içine çağrı `My.Computer.Info.OSFullName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="3042c-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="3042c-109">WMI ve nasıl yükleneceği hakkında daha fazla bilgi, Git ve "Windows Yönetim Araçları için çekirdek" arayın.</span><span class="sxs-lookup"><span data-stu-id="3042c-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3042c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3042c-110">See also</span></span>
- [<span data-ttu-id="3042c-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="3042c-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)
- [<span data-ttu-id="3042c-112">İşleme ve .NET özel durumları atma</span><span class="sxs-lookup"><span data-stu-id="3042c-112">Handling and throwing exceptions in .NET</span></span>](../../standard/exceptions/index.md)
- [<span data-ttu-id="3042c-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="3042c-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
