---
title: Yazılması ReservedSpace değerin altında boş disk alanı azaltır çünkü günlük dosyasına yazılamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: dc7e97bfc5aa3963e1edcd204f5b81d21edab579
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913242"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="9d8c1-102">Yazılması ReservedSpace değerin altında boş disk alanı azaltır çünkü günlük dosyasına yazılamıyor</span><span class="sxs-lookup"><span data-stu-id="9d8c1-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>
<span data-ttu-id="9d8c1-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı için günlük dosyasına yazamadı:</span><span class="sxs-lookup"><span data-stu-id="9d8c1-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="9d8c1-104">Boş disk alanı (bayt cinsinden) miktarı değerini'dan küçük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="9d8c1-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="9d8c1-105">— ve —</span><span class="sxs-lookup"><span data-stu-id="9d8c1-105">—and—</span></span>  
  
- <span data-ttu-id="9d8c1-106">Değerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliği <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9d8c1-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="9d8c1-107">To correct this error</span></span>  
  
1. <span data-ttu-id="9d8c1-108">Mevcut günlüklerini arşivleyin ve bunları izin vermek için bilgisayarınızdan <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="9d8c1-109">Değiştirin <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> özelliğini daha az disk alanı ayırmak için daha küçük bir sayı.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="9d8c1-110">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliğini <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> yeterli boş disk alanı değilse uyarı vermeden iletileri atmak.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d8c1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d8c1-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="9d8c1-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="9d8c1-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="9d8c1-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="9d8c1-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
