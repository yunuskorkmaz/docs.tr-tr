---
title: Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 28a4b9286b13f8c7c72c4e98871846c2ca265aa9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619790"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="0601b-102">Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamıyor</span><span class="sxs-lookup"><span data-stu-id="0601b-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>
<span data-ttu-id="0601b-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı için günlük dosyasına yazamadı:</span><span class="sxs-lookup"><span data-stu-id="0601b-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="0601b-104">Günlük dosyası boyutunu (bayt cinsinden) değerinden büyükse <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği</span><span class="sxs-lookup"><span data-stu-id="0601b-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="0601b-105">— ve —</span><span class="sxs-lookup"><span data-stu-id="0601b-105">—and—</span></span>  
  
- <span data-ttu-id="0601b-106">Değerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliği <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span><span class="sxs-lookup"><span data-stu-id="0601b-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0601b-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0601b-107">To correct this error</span></span>  
  
1. <span data-ttu-id="0601b-108">Mevcut günlüklerini arşivleyin ve bunları izin vermek için bilgisayarınızdan <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="0601b-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="0601b-109">Değiştirin <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği için daha büyük günlükleri izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="0601b-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="0601b-110">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliğini <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> günlük çok büyük ise, hiçbir uyarı iletileri atmak.</span><span class="sxs-lookup"><span data-stu-id="0601b-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0601b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0601b-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="0601b-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="0601b-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="0601b-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="0601b-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
