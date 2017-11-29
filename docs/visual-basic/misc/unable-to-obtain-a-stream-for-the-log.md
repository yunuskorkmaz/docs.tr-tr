---
title: "Günlük için bir akış alınamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dd3051b2331502c9f4f3430bbf88731b307d1b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="03876-102">Günlük için bir akış alınamıyor</span><span class="sxs-lookup"><span data-stu-id="03876-102">Unable to obtain a stream for the log</span></span>
<span data-ttu-id="03876-103">Günlük için bir akış elde edilemiyor.</span><span class="sxs-lookup"><span data-stu-id="03876-103">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="03876-104">Temel olası dosya adları \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="03876-104">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="03876-105"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı tüm olası günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="03876-105">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="03876-106">Çok fazla günlük dosyalarını sahip uygulama mimari bir sorun olduğunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="03876-106">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="03876-107">Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.</span><span class="sxs-lookup"><span data-stu-id="03876-107">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="03876-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="03876-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="03876-109">Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.</span><span class="sxs-lookup"><span data-stu-id="03876-109">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2.  <span data-ttu-id="03876-110">Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.</span><span class="sxs-lookup"><span data-stu-id="03876-110">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03876-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="03876-111">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [<span data-ttu-id="03876-112">My.Application.Log nesnesi</span><span class="sxs-lookup"><span data-stu-id="03876-112">My.Application.Log Object</span></span>](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [<span data-ttu-id="03876-113">My.Log nesnesi</span><span class="sxs-lookup"><span data-stu-id="03876-113">My.Log Object</span></span>](../../visual-basic/language-reference/objects/my-log-object.md)
