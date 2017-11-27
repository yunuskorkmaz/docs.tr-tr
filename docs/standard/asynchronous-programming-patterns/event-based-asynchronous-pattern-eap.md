---
title: "Olay Tabanlı Zaman Uyumsuz Desen (EAP)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b5f242b9586c4ea3b045daf8f10b84127b81085
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-based-asynchronous-pattern-eap"></a>Olay Tabanlı Zaman Uyumsuz Desen (EAP)
Bir istemci kodu için zaman uyumsuz özellikler kullanıma sunmak için çeşitli yöntemler vardır. Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranışı sunmak sınıflar için bir yol önerir.  
  
> [!NOTE]
>  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], görev paralel kitaplığı zaman uyumsuz ve paralel programlama için yeni bir modeli sağlar. Daha fazla bilgi için bkz: [paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Nasıl olay tabanlı zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir açıklar.  
  
 [Olay tabanlı zaman uyumsuz deseni uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Zaman uyumsuz özellikler olan bir sınıfı paketlemek için standartlaştırılmış biçimini tanımlar.  
  
 [Olay tabanlı zaman uyumsuz desen uygulamak için en iyi uygulamalar](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimlerini açıklar.  
  
 [Olay tabanlı zaman uyumsuz desen uygulamak karar verme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Yerine olay tabanlı zaman uyumsuz desen uygulamak seçtiğinizde belirlemek açıklar <xref:System.IAsyncResult> düzeni.  
  
 [İzlenecek yol: Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturulacağını gösterir. Yardımcı sınıfları kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı altında herhangi bir uygulama modeli bileşeni düzgün çalıştığını sağlar.  
  
 [Nasıl yapılır: olay tabanlı zaman uyumsuz deseni destekleyen bileşenleri kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.AsyncOperation>  
 Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşeni ve tüm üyeleri bağlantılar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Görev paralel kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 Zaman uyumsuz ve paralel işlemleri için bir programlama modeli açıklar.  
  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 .NET Framework'teki çoklu iş parçacığı özellikleri açıklar.  
  
 [İş parçacığı oluşturma](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 C# ve Visual Basic dillerde çoklu iş parçacığı özellikleri açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen iş parçacığı oluşturma en iyi uygulamalar](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Olayları](../../../docs/standard/events/index.md)  
 [Bileşenleri çoklu iş parçacığı kullanımı](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [Zaman uyumsuz programlama tasarım desenleri](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
