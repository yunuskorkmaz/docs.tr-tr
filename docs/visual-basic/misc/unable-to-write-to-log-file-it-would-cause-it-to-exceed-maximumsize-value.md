---
title: Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamadı
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: dabd9559864f9c04d7e4647f1e7da24adc679b24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamadı
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı için günlük dosyasına yazamadı:  
  
-   Günlük dosyası boyutunu (bayt cinsinden) değerinden daha büyük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği  
  
     — ve —  
  
-   Değeri <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliği olan <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Varolan günlükleri arşivlemek ve izin vermek için bilgisayardan kaldırmak <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.  
  
2.  Değerini değiştirme <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği için daha büyük günlükleri izin vermek için.  
  
3.  Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliğine <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> günlük çok büyük ise uyarmadan iletileri atmak için.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  
 [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
