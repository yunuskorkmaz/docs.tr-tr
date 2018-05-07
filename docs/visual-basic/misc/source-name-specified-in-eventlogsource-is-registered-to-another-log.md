---
title: EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: dc4c8f212de61a304f04c81d81d2e75c490450ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir
`EventLog` Farklı günlüğe kayıtlı bir kaynak başvurmak çalışıyor. Girişler için olay günlüğünü yazdığınız varsa, belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> özelliği. <xref:System.Diagnostics.EventLog.Source%2A> Özelliği olay günlüğüyle bileşeniniz giriş geçerli bir kaynak kaydeder. Tek bir kaynak ilişkilendirilmesi (ve bu nedenle girişlere yazma) aynı anda yalnızca bir olay günlüğü.  
  
 Kaynak ve olay günlüğüne kaydeder ilk bileşeniniz, sistem gibi geçerli bir kaynak otomatik olarak kayıtlı olmayan bir giriş yazmak çalışırsanız, varsayılan olarak, değeri kullanılarak <xref:System.Diagnostics.EventLog.Source%2A> özelliği kaynak dizesi olarak.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kaynak doğru günlüğe kayıtlı olduğundan emin olun. Bunu yapmak için kullanın <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metodunu ya kendi aşırı bileşeniniz olay günlüğüne benzersiz olarak tanımlayan bir dize belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay günlüklerini yönetme](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Olay günlüğü başvuruları](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Nasıl yapılır: olay günlüğü girişleri kaynağı olarak, uygulamanızın ekleyin](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Nasıl yapılır: bir olay kaynağı Kaldır](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
