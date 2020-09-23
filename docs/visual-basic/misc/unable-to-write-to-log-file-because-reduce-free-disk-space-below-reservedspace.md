---
title: Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_ReservedSpaceEncroached
ms.assetid: 95832e70-4ecc-47aa-90c1-f35c4d468151
ms.openlocfilehash: e5247876c683812edf0eb73ab5f1a5e607b48102
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075609"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-reduce-free-disk-space-below-reservedspace-value"></a>Günlük dosyası yazılamıyor çünkü dosyaya yazma, ayrılan alan değerinin altındaki boş disk alanını azalttı

<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:  
  
- Boş disk alanı miktarı (bayt cinsinden), özelliğin değerinden daha küçüktür <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>  
  
     '  
  
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .  
  
2. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>Daha az disk alanı ayırmak için özelliğin değerini daha küçük bir sayı olarak değiştirin.  
  
3. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Yeterli boş disk alanı yoksa, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.ReserveDiskSpace%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My. Application. Info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
