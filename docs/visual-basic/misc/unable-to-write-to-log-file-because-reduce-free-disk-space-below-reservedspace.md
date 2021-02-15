---
description: 'Hakkında daha fazla bilgi edinin: dosyaya yazmak, ayrılan alan değerinin altındaki boş disk alanını azaltacağından günlük dosyasına yazılamıyor'
title: Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: e02fa9527539169da3ea99f89246dafe82646cff
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456958"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a><span data-ttu-id="d4761-103">Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı</span><span class="sxs-lookup"><span data-stu-id="d4761-103">Unable to write to log file because writing to it would reduce free disk space below ReservedSpace value</span></span>

<span data-ttu-id="d4761-104"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:</span><span class="sxs-lookup"><span data-stu-id="d4761-104">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="d4761-105">Boş disk alanı miktarı (bayt cinsinden), özelliğin değerinden daha küçüktür <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A></span><span class="sxs-lookup"><span data-stu-id="d4761-105">The amount of free disk space (in bytes) is less than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property</span></span>  
  
     <span data-ttu-id="d4761-106">'</span><span class="sxs-lookup"><span data-stu-id="d4761-106">—and—</span></span>  
  
- <span data-ttu-id="d4761-107"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .</span><span class="sxs-lookup"><span data-stu-id="d4761-107">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4761-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="d4761-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d4761-109">Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="d4761-109">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="d4761-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>Daha az disk alanı ayırmak için özelliğin değerini daha küçük bir sayı olarak değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d4761-110">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A> property to a smaller number to reserve less disk space.</span></span>  
  
3. <span data-ttu-id="d4761-111"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Yeterli boş disk alanı yoksa, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d4761-111">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if there is not enough free disk space.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4761-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4761-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="d4761-113">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="d4761-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="d4761-114">My. Application. Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="d4761-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
