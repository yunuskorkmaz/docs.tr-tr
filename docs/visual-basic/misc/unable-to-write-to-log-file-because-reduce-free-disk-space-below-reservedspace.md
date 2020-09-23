---
title: Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: e5247876c683812edf0eb73ab5f1a5e607b48102
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075609"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="37e4e-102">Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı</span><span class="sxs-lookup"><span data-stu-id="37e4e-102">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>

<span data-ttu-id="37e4e-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:</span><span class="sxs-lookup"><span data-stu-id="37e4e-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="37e4e-104">Boş disk alanı miktarı (bayt cinsinden), özelliğin değerinden daha küçüktür <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span><span class="sxs-lookup"><span data-stu-id="37e4e-104">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="37e4e-105">'</span><span class="sxs-lookup"><span data-stu-id="37e4e-105">—and—</span></span>  
  
- <span data-ttu-id="37e4e-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .</span><span class="sxs-lookup"><span data-stu-id="37e4e-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="37e4e-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="37e4e-107">To correct this error</span></span>  
  
1. <span data-ttu-id="37e4e-108">Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="37e4e-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="37e4e-109"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>Daha az disk alanı ayırmak için özelliğin değerini daha küçük bir sayı olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="37e4e-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="37e4e-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Yeterli boş disk alanı yoksa, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="37e4e-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37e4e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="37e4e-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="37e4e-112">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="37e4e-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="37e4e-113">My. Application. Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="37e4e-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
