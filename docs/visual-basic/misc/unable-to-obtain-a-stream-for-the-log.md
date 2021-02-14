---
description: 'Hakkında daha fazla bilgi edinin: günlük için akış alınamıyor'
title: Günlük için akış alınamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 6eda12eb4dc2b3cf303e543a66e1f2f7d739eb6b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100455281"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a><span data-ttu-id="f356f-103">Günlük için akış alınamıyor</span><span class="sxs-lookup"><span data-stu-id="f356f-103">Unable to obtain a stream for the log</span></span>

<span data-ttu-id="f356f-104">Günlük için akış alınamıyor.</span><span class="sxs-lookup"><span data-stu-id="f356f-104">Unable to obtain a stream for the log.</span></span> <span data-ttu-id="f356f-105">Öğesine göre olası dosya adları \<name> zaten kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="f356f-105">Potential file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f356f-106"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Temel alınarak tüm olası günlük dosyası adları zaten kullanımda olduğundan, sınıf yeni bir günlük dosyası oluşturamadı \<name> .</span><span class="sxs-lookup"><span data-stu-id="f356f-106">The <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class could not create a new log file because all potential log file names based on \<name> are already in use.</span></span>  
  
 <span data-ttu-id="f356f-107">Çok fazla günlük dosyası olması, uygulamayla ilgili bir mimari sorunu gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="f356f-107">Having too many log files may indicate an architectural problem with the application.</span></span> <span data-ttu-id="f356f-108"><xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Daha fazla bilgi için bkz. sınıf belgeleri.</span><span class="sxs-lookup"><span data-stu-id="f356f-108">See the documentation for the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class for more information.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f356f-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="f356f-109">To correct this error</span></span>  
  
1. <span data-ttu-id="f356f-110">Özelliğini, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosyası adına bir tarih damgası içerecek şekilde veya olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f356f-110">Set the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> property to <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> or <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> to include a date-stamp in the log file name.</span></span>  
  
2. <span data-ttu-id="f356f-111">Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f356f-111">Archive the existing logs and remove them from the computer to allow the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> object to create new logs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f356f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f356f-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [<span data-ttu-id="f356f-113">My. Application. log</span><span class="sxs-lookup"><span data-stu-id="f356f-113">My.Application.Log</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [<span data-ttu-id="f356f-114">My. Application. Info. DirectoryPath</span><span class="sxs-lookup"><span data-stu-id="f356f-114">My.Application.Info.DirectoryPath</span></span>](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
