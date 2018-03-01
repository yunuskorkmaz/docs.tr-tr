---
title: "Yazılması ReservedSpace değerin altında boş disk alanını azaltma çünkü günlük dosyasına yazılamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 486f27efe5da0a5d663e7bdae9d5789df4add4e7
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="915bb-102">Yazılması ReservedSpace değerin altında boş disk alanını azaltma çünkü günlük dosyasına yazılamadı</span><span class="sxs-lookup"><span data-stu-id="915bb-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="915bb-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı için günlük dosyasına yazamadı:</span><span class="sxs-lookup"><span data-stu-id="915bb-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
-   <span data-ttu-id="915bb-104">Boş disk alanı (bayt cinsinden) değeri'dan küçük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="915bb-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="915bb-105">— ve —</span><span class="sxs-lookup"><span data-stu-id="915bb-105">—and—</span></span>  
  
-   <span data-ttu-id="915bb-106">Değeri <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliği olan <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="915bb-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="915bb-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="915bb-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="915bb-108">Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="915bb-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2.  <span data-ttu-id="915bb-109">Değerini değiştirme <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> özelliği için daha az disk alanı ayırmak için daha küçük bir sayı.</span><span class="sxs-lookup"><span data-stu-id="915bb-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3.  <span data-ttu-id="915bb-110">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> yeterli boş disk alanı olduğunda uyarı olmadan iletileri atmak için.</span><span class="sxs-lookup"><span data-stu-id="915bb-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915bb-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="915bb-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [<span data-ttu-id="915bb-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="915bb-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="915bb-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="915bb-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
