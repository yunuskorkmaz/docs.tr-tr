---
title: "İç hata nedeniyle tam işlem sistem adı alınamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="89a88-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="89a88-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="89a88-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="89a88-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="89a88-104">Bu WMI tarafından geçerli makineye mevcut değildir neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="89a88-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="89a88-105">Çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="89a88-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="89a88-106">Bu hatanın olası bir nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.</span><span class="sxs-lookup"><span data-stu-id="89a88-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89a88-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="89a88-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="89a88-108">Ekleme bir `Try...Catch` çağrısı geçici blok `My.Computer.Info.OSFullName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="89a88-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="89a88-109">WMI ve nasıl yükleneceği hakkında daha fazla bilgi için gidin ve "Windows Yönetim Araçları'nı çekirdek için" araması yapın.</span><span class="sxs-lookup"><span data-stu-id="89a88-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89a88-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89a88-110">See Also</span></span>  
 [<span data-ttu-id="89a88-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="89a88-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="89a88-112">Özel durum ve hata Visual Basic'te işleme</span><span class="sxs-lookup"><span data-stu-id="89a88-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="89a88-113">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="89a88-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
