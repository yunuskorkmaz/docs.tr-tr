---
title: "Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f04afd5d061a44f572d95abfb0173ad6fa2ac27
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi
Bir olay günlüğüne bir giriş yazmak için belirtilen kaynak ile başka bir olay günlüğü, kayıtlı çalışıldı.  
  
 Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz bir giriş bir günlük dosyasına yazar önce bileşen örneği. Bu durumda, sistem, belirtilen kaynak bileşeni yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekiyorsa.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  İlk günlük kullanarak kaynak ilişkilendirmesini kaldırmak <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.  
  
2.  Kaynak ile yeni bir günlük kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)  

