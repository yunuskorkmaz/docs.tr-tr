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
ms.openlocfilehash: 8beea344d233794ddc36d7fc53db1c01be84399f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Başka bir olay günlüğü bu ada sahip bir kaynak zaten kaydettirildi
Bir olay günlüğüne bir giriş yazmak için belirtilen kaynak ile başka bir olay günlüğü, kayıtlı çalışıldı.  
  
 Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz bir giriş bir günlük dosyasına yazar önce bileşen örneği. Bu durumda, sistem, belirtilen kaynak bileşeni yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekiyorsa.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  İlk günlük kullanarak kaynak ilişkilendirmesini kaldırmak <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.  
  
2.  Kaynak ile yeni bir günlük kaydedin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [My.Application.Log nesnesi](../../visual-basic/language-reference/objects/my-application-log-object.md)  
 [Nasıl yapılır: bir olay kaynağı Kaldır](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)  
 [Nasıl yapılır: olay günlüğü girişleri kaynağı olarak, uygulamanızın ekleyin](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
