---
title: EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 22129ab0c4f7fe0a78300907a949d9368028c9fa
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58022311"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir
`EventLog` Farklı günlüğe kaydedilen kaynağına başvurmak çalışıyor. Girişler için olay günlüğünü yazıyorsanız, belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> özelliği. <xref:System.Diagnostics.EventLog.Source%2A> Özelliği ile olay günlüğü bileşeniniz girişler geçerli bir kaynak kaydeder. Tek bir kaynak ile ilişkili (ve bu nedenle girişlere yazma) aynı anda yalnızca bir olay günlüğü.  
  
 Kaynak ile olay günlüğüne kaydeder ilk bileşen, system gibi geçerli bir kaynak olarak otomatik olarak kayıtlı olmayan bir giriş yazmak çalışırsanız, varsayılan olarak, değerini kullanarak <xref:System.Diagnostics.EventLog.Source%2A> özelliği olarak kaynak dizesi.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kaynak doğru günlüğe kayıtlı olduğundan emin olun. Bunu yapmak için <xref:System.Diagnostics.EventLog.CreateEventSource%2A> yöntemi veya olay günlüğüne bileşeniniz benzersiz olarak tanımlayan bir dize belirtmek için bunun aşırı yüklerinden biri.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay günlüklerini yönetme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [Olay günlüğü başvuruları](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [Nasıl yapılır: Olay günlüğü girişleri kaynağı olarak uygulamanıza ekleme](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [Nasıl yapılır: Olay kaynağını Kaldır](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
