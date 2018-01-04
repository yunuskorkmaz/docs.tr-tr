---
title: "Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamadı"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4004dca2a3b9f13583cfdfe43f89bc4bff5dd6d6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
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
