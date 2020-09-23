---
title: Günlük için akış alınamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ExhaustedPossibleStreamNames
ms.assetid: 33994f52-8efb-4790-a459-033e5c1db632
ms.openlocfilehash: 887356fac3abe5c9d28751f7c4d3b1908ed35acb
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078391"
---
# <a name="unable-to-obtain-a-stream-for-the-log"></a>Günlük için akış alınamıyor

Günlük için akış alınamıyor. Öğesine göre olası dosya adları \<name> zaten kullanılıyor.  
  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Temel alınarak tüm olası günlük dosyası adları zaten kullanımda olduğundan, sınıf yeni bir günlük dosyası oluşturamadı \<name> .  
  
 Çok fazla günlük dosyası olması, uygulamayla ilgili bir mimari sorunu gösteriyor olabilir. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Daha fazla bilgi için bkz. sınıf belgeleri.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özelliğini, <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A> <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Daily> <xref:Microsoft.VisualBasic.Logging.LogFileCreationScheduleOption.Weekly> günlük dosyası adına bir tarih damgası içerecek şekilde veya olarak ayarlayın.  
  
2. Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.LogFileCreationSchedule%2A>
- [My. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My. Application. Info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
