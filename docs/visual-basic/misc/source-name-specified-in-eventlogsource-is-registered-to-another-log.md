---
title: "EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c190caa7634760c2e4dc4a2bb7a9a09f532eb0ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource içinde belirtilen kaynak adı EventLogName içinde belirtilen dışında bir günlüğe kaydedilir
`EventLog` Farklı günlüğe kayıtlı bir kaynak başvurmak çalışıyor. Girişler için olay günlüğünü yazdığınız varsa, belirtmeniz gerekir <xref:System.Diagnostics.EventLog.Source%2A> özelliği. <xref:System.Diagnostics.EventLog.Source%2A> Özelliği olay günlüğüyle bileşeniniz giriş geçerli bir kaynak kaydeder. Tek bir kaynak ilişkilendirilmesi (ve bu nedenle girişlere yazma) aynı anda yalnızca bir olay günlüğü.  
  
 Kaynak ve olay günlüğüne kaydeder ilk bileşeniniz, sistem gibi geçerli bir kaynak otomatik olarak kayıtlı olmayan bir giriş yazmak çalışırsanız, varsayılan olarak, değeri kullanılarak <xref:System.Diagnostics.EventLog.Source%2A> özelliği kaynak dizesi olarak.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Kaynak doğru günlüğe kayıtlı olduğundan emin olun. Bunu yapmak için kullanın <xref:System.Diagnostics.EventLog.CreateEventSource%2A> metodunu ya kendi aşırı bileşeniniz olay günlüğüne benzersiz olarak tanımlayan bir dize belirtin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay günlüklerini yönetme](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Olay günlüğü başvuruları](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Nasıl yapılır: olay günlüğü girişleri kaynağı olarak, uygulamanızın ekleyin](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)  
 [Nasıl yapılır: bir olay kaynağı Kaldır](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)
