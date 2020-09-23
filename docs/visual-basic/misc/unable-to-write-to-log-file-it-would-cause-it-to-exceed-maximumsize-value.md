---
title: Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 95a7b9036e7c1494cd44c250b0580bab5144417b
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059463"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a><span data-ttu-id="0f0c4-102">Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir</span><span class="sxs-lookup"><span data-stu-id="0f0c4-102">Unable to write to log file because writing to it would cause it to exceed MaximumSize value</span></span>

<span data-ttu-id="0f0c4-103"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:</span><span class="sxs-lookup"><span data-stu-id="0f0c4-103">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not write to the log file because:</span></span>  
  
- <span data-ttu-id="0f0c4-104">Günlük dosyası boyutu (bayt), özelliğin değerinden daha büyük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A></span><span class="sxs-lookup"><span data-stu-id="0f0c4-104">The log file size (in bytes) is greater than the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property</span></span>  
  
     <span data-ttu-id="0f0c4-105">'</span><span class="sxs-lookup"><span data-stu-id="0f0c4-105">—and—</span></span>  
  
- <span data-ttu-id="0f0c4-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .</span><span class="sxs-lookup"><span data-stu-id="0f0c4-106">The value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property was <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0f0c4-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0f0c4-107">To correct this error</span></span>  
  
1. <span data-ttu-id="0f0c4-108">Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="0f0c4-108">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
2. <span data-ttu-id="0f0c4-109"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>Özelliğin değerini daha büyük Günlükler için izin verecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="0f0c4-109">Change the value of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> property to allow for larger logs.</span></span>  
  
3. <span data-ttu-id="0f0c4-110"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Günlük çok büyükse, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0f0c4-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> property to <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> to discard messages without warning if the log is too large.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f0c4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f0c4-111">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [<span data-ttu-id="0f0c4-112">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="0f0c4-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="0f0c4-113">My. Application. Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="0f0c4-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
