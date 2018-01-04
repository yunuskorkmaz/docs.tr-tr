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
ms.openlocfilehash: dba511ecd2a5c050fc2c037ac437e38715609e95
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Günlük için bir akış alınamıyor
Günlük için bir akış elde edilemiyor. Temel olası dosya adları \<adı > zaten kullanılıyor.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı tüm olası günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanılıyor.  
  
 Çok fazla günlük dosyalarını sahip uygulama mimari bir sorun olduğunu gösteriyor olabilir. Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.  
  
2.  Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
