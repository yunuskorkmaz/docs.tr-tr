---
title: İç hata nedeniyle tam işlem sistem adı alınamadı
ms.date: 07/20/2015
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
ms.openlocfilehash: 192033348a779591a54860505d5d707a802c415a
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361728"
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="26811-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="26811-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="26811-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="26811-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="26811-104">Bu geçerli makinede mevcut değil WMI tarafından kaynaklanabilir.</span><span class="sxs-lookup"><span data-stu-id="26811-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="26811-105">Bir çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="26811-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="26811-106">Bu hatanın olası nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.</span><span class="sxs-lookup"><span data-stu-id="26811-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="26811-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="26811-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="26811-108">Ekleme bir `Try...Catch` bloğu içine çağrı `My.Computer.Info.OSFullName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="26811-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="26811-109">WMI ve nasıl yükleneceği hakkında daha fazla bilgi, Git ve "Windows Yönetim Araçları için çekirdek" arayın.</span><span class="sxs-lookup"><span data-stu-id="26811-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26811-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26811-110">See Also</span></span>  
 [<span data-ttu-id="26811-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="26811-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="26811-112">Özel durum ve Visual Basic'te işleme hatası</span><span class="sxs-lookup"><span data-stu-id="26811-112">Exception and Error Handling in Visual Basic</span></span>](https://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="26811-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="26811-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
