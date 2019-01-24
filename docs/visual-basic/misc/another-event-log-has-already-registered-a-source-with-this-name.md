---
title: Zaten bir kaynak başka bir olay günlüğü bu ada sahip kayıtlı
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: fa4e8a022db1bbc19bff38fd529066b0619add68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646117"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Zaten bir kaynak başka bir olay günlüğü bu ada sahip kayıtlı
Bir giriş için bir olay günlüğüne yazmak için burada belirtilen kaynağı başka bir olay günlüğü ile kayıtlı çalışıldı.  
  
 Ayarlamalısınız <xref:System.Diagnostics.EventLog.Source%2A> özelliği, <xref:System.Diagnostics.EventLog> bileşeniniz girdiyi bir günlük dosyasına yazar. önce bileşen örneği. Bu durumda, sistem, belirtilen kaynak bileşen yazma olay günlüğü ve çağrıları ile kaydedildiğini denetler <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekirse.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  İlk günlük kullanarak kaynak ilişkilendirmesini Kaldır <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> veya <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> yöntemi.  
  
2.  Kaynak ile yeni bir günlük kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [My.Application.Log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)

