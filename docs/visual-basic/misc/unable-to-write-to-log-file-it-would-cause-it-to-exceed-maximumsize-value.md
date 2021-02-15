---
description: 'Hakkında daha fazla bilgi edinin: günlük dosyasına yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olacağından'
title: Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbrApplicationLog_FileExceedsMaximumSize
ms.assetid: 61747a9c-e460-424b-a365-73cdba9dd428
ms.openlocfilehash: 5c305c550f7a63183a0ac529adc788fa79b5794f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456945"
---
# <a name="unable-to-write-to-log-file-because-writing-to-it-would-cause-it-to-exceed-maximumsize-value"></a>Günlük dosyasına yazılamıyor çünkü buna yazmak, bu değerin en Büyükdeğer değerini aşmasına neden olabilir

<xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>Sınıf, şu nedenle günlük dosyasına yazılamadı:  
  
- Günlük dosyası boyutu (bayt), özelliğin değerinden daha büyük <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>  
  
     '  
  
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>Özelliğin değeri idi <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.ThrowException> .  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Nesnenin yeni Günlükler oluşturmasına izin vermek için mevcut günlükleri Arşivle ve bilgisayardan kaldır <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> .  
  
2. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>Özelliğin değerini daha büyük Günlükler için izin verecek şekilde değiştirin.  
  
3. <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A> <xref:Microsoft.VisualBasic.Logging.DiskSpaceExhaustedOption.DiscardMessages> Günlük çok büyükse, özelliği uyarı vermeden iletileri atmak için olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.MaxFileSize%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.DiskSpaceExhaustedBehavior%2A>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener>
- [My. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
- [My. Application. Info. DirectoryPath](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
