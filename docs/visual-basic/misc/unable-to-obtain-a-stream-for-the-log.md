---
title: Günlük için bir akış alınamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 3f5ac83e6957d6d5883bf5ab191e2a922c874df3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33639548"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="f6f08-102">Günlük için bir akış alınamıyor</span><span class="sxs-lookup"><span data-stu-id="f6f08-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="f6f08-103">Günlük için bir akış elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="f6f08-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="f6f08-104">Temel olası dosya adları \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="f6f08-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f6f08-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı tüm olası günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="f6f08-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f6f08-106">Çok fazla günlük dosyalarını sahip uygulama mimari bir sorun olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6f08-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="f6f08-107">Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="f6f08-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f6f08-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f6f08-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="f6f08-109">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.</span><span class="sxs-lookup"><span data-stu-id="f6f08-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="f6f08-110">Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="f6f08-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f08-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f08-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="f6f08-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="f6f08-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="f6f08-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="f6f08-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
