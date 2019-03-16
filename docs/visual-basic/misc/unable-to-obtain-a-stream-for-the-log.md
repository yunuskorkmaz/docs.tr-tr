---
title: Bir akış günlüğü alınamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 45b7a16608bea4879e84fa7004097a8c38312284
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031701"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Bir akış günlüğü alınamıyor
Bir akış günlüğü için alınamıyor. Olası dosya adlarına göre \<adı > zaten kullanımda.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı olası tüm günlük dosyası adları dayalı olduğundan yeni bir günlük dosyası oluşturamadı \<adı > zaten kullanımda.  
  
 Günlük dosyaları çok fazla olması, uygulamanın mimari bir sorun olduğunu gösteriyor olabilir. Belgelerine bakın <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> daha fazla bilgi için sınıf.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> özelliğini <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> veya <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosya adında tarih damgası eklenecek.  
  
2.  Mevcut günlüklerini arşivleyin ve bunları izin vermek için bilgisayarınızdan <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
