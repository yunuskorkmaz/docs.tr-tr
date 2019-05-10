---
title: Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamıyor
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 28a4b9286b13f8c7c72c4e98871846c2ca265aa9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619790"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Yazılması MaximumSize değerini aşmasına neden olacağından günlük dosyasına yazılamıyor
<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> Sınıfı için günlük dosyasına yazamadı:  
  
- Günlük dosyası boyutunu (bayt cinsinden) değerinden büyükse <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği  
  
     — ve —  
  
- Değerini <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliği <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException>.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Mevcut günlüklerini arşivleyin ve bunları izin vermek için bilgisayarınızdan <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> yeni günlükler oluşturulacak nesne.  
  
2. Değiştirin <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A> özelliği için daha büyük günlükleri izin vermek için.  
  
3. Ayarlama <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> özelliğini <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> günlük çok büyük ise, hiçbir uyarı iletileri atmak.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My.Application.Info.DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
