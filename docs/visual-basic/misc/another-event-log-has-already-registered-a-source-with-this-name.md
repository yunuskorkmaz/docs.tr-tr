---
title: Başka bir olay günlüğü bu adı taşıyan bir kaynağı zaten kaydetti
ms.date: 07/20/2015
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
ms.openlocfilehash: 333c28036e2d1b7514c7370b98ff70a6d195a9dd
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058397"
---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Başka bir olay günlüğü bu adı taşıyan bir kaynağı zaten kaydetti

Belirtilen kaynağın başka bir olay günlüğü ile kaydedildiği bir olay günlüğüne giriş yazma girişiminde bulunuldu.  
  
 <xref:System.Diagnostics.EventLog.Source%2A> <xref:System.Diagnostics.EventLog> Bileşeninizin bir günlüğe giriş yazmadan önce bileşen örneğinizin özelliğini ayarlamanız gerekir. Bu durumda, sistem belirttiğiniz kaynağın, bileşenin yazıldığı olay günlüğüne kaydedilip kullanmadığını denetler ve <xref:System.Diagnostics.EventLog.CreateEventSource%2A> gerekirse çağırır.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Kaynak ilişkilendirmesini, veya yöntemini kullanarak ilk günlük ile kaldırın <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> .  
  
2. Kaynağı yeni günlüğe kaydedin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [My. Application. log](xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.Log)
