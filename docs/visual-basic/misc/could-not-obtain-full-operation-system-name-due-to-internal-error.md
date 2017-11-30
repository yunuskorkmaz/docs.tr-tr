---
title: "İç hata nedeniyle tam işlem sistem adı alınamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65796c41d2a9fbd03517e7b15bc6b566ba4364fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="0afa2-102">İç hata nedeniyle tam işlem sistem adı alınamadı</span><span class="sxs-lookup"><span data-stu-id="0afa2-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="0afa2-103">İç hata nedeniyle tam işlem sistem adı alınamadı.</span><span class="sxs-lookup"><span data-stu-id="0afa2-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="0afa2-104">Bu WMI tarafından geçerli makineye mevcut değildir neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0afa2-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="0afa2-105">Çağrı `My.Computer.Info.OSFullName` özelliği başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0afa2-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="0afa2-106">Bu hatanın olası bir nedeni, Windows Yönetim Araçları (WMI) geçerli bilgisayarda yüklü değil, ' dir.</span><span class="sxs-lookup"><span data-stu-id="0afa2-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0afa2-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0afa2-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0afa2-108">Ekleme bir `Try...Catch` çağrısı geçici blok `My.Computer.Info.OSFullName` özelliği.</span><span class="sxs-lookup"><span data-stu-id="0afa2-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="0afa2-109">WMI ve nasıl yükleneceği hakkında daha fazla bilgi için gidin ve "Windows Yönetim Araçları'nı çekirdek için" araması yapın.</span><span class="sxs-lookup"><span data-stu-id="0afa2-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0afa2-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0afa2-110">See Also</span></span>  
 [<span data-ttu-id="0afa2-111">My.Computer.Info.OSFullName özelliği</span><span class="sxs-lookup"><span data-stu-id="0afa2-111">My.Computer.Info.OSFullName Property</span></span>](http://msdn.microsoft.com/en-us/b3b0fbd1-4dc5-428a-ad04-0d9fc9c2a9be)  
 [<span data-ttu-id="0afa2-112">Özel durum ve hata Visual Basic'te işleme</span><span class="sxs-lookup"><span data-stu-id="0afa2-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="0afa2-113">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="0afa2-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
