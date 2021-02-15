---
description: 'Hakkında daha fazla bilgi edinin: günlük dosyasına yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olacağından'
title: Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 5c305c550f7a63183a0ac529adc788fa79b5794f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456945"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="291c5-103">Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="291c5-103">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>

<span data-ttu-id="291c5-104"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:</span><span class="sxs-lookup"><span data-stu-id="291c5-104">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="291c5-105">Günlük dosyası boyutu (bayt), özelliğin değerinden daha büyük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="291c5-105">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="291c5-106">'</span><span class="sxs-lookup"><span data-stu-id="291c5-106">—and—</span></span>  
  
- <span data-ttu-id="291c5-107"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .</span><span class="sxs-lookup"><span data-stu-id="291c5-107">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="291c5-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="291c5-108">To correct this error</span></span>  
  
1. <span data-ttu-id="291c5-109">Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="291c5-109">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="291c5-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>Özelliğin değerini daha büyük Günlükler için izin verecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="291c5-110">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="291c5-111"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Günlük çok büyükse, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="291c5-111">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291c5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="291c5-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="291c5-113">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="291c5-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="291c5-114">My. Application. Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="291c5-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
