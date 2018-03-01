---
title: "Günlük için bir akış alınamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="25a87-102">Günlük için bir akış alınamıyor</span><span class="sxs-lookup"><span data-stu-id="25a87-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="25a87-103">Günlük için bir akış elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="25a87-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="25a87-104">Temel olası dosya adları \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="25a87-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="25a87-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı tüm olası günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="25a87-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="25a87-106">Çok fazla günlük dosyalarını sahip uygulama mimari bir sorun olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="25a87-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="25a87-107">Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="25a87-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25a87-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="25a87-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="25a87-109">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.</span><span class="sxs-lookup"><span data-stu-id="25a87-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="25a87-110">Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="25a87-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a87-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="25a87-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="25a87-112">My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="25a87-112">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [<span data-ttu-id="25a87-113">My.Application.Info.DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="25a87-113">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
