---
title: Bir akış günlüğü alınamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 0553da64ca8fcac148cd8da5c22227b5824387de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628753"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="27386-102">Bir akış günlüğü alınamıyor</span><span class="sxs-lookup"><span data-stu-id="27386-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="27386-103">Bir akış günlüğü için alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="27386-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="27386-104">Olası dosya adlarına göre \<adı > zaten kullanımda.</span><span class="sxs-lookup"><span data-stu-id="27386-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="27386-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı olası tüm günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanımda.</span><span class="sxs-lookup"><span data-stu-id="27386-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="27386-106">Günlük dosyaları çok fazla olması, uygulamanın mimari bir sorun olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="27386-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="27386-107">Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="27386-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27386-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="27386-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="27386-109">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğini <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.</span><span class="sxs-lookup"><span data-stu-id="27386-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="27386-110">Mevcut günlüklerini arşivleyin ve bunları izin vermek için bilgisayarınızdan <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="27386-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27386-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27386-111">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="27386-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="27386-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="27386-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="27386-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
