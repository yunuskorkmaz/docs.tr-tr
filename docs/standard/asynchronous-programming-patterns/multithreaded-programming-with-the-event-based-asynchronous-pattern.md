---
title: Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6d93e449877456e415ebd4d3490a7df99280e7e5
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a>Olay Tabanlı Zaman Uyumsuz Desenle Çok İş Parçacıklı Programlama
Bir istemci kodu için zaman uyumsuz özellikler kullanıma sunmak için çeşitli yöntemler vardır. Olay tabanlı zaman uyumsuz desen zaman uyumsuz davranışı sunmak sınıflar için önerilen yol önerir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 Nasıl olay tabanlı zaman uyumsuz desen birden çok iş parçacıklı uygulamalar avantajları birçok karmaşık sorunları birden çok iş parçacıklı tasarımında yapısında gizleme çalışırken kullanılabilir hale getirir açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Deseni Uygulama](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 Zaman uyumsuz özellikler olan bir sınıfı paketlemek için standartlaştırılmış biçimini tanımlar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desen Uygulamak için En İyi Yöntemler](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen göre zaman uyumsuz özellikler gösterme gereksinimlerini açıklar.  
  
 [Olay Tabanlı Zaman Uyumsuz Desenin Ne Zaman Uygulanacağını Belirleme](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 Yerine olay tabanlı zaman uyumsuz desen uygulamak seçtiğinizde belirlemek açıklar <xref:System.IAsyncResult> düzeni.  
  
 [İzlenecek yol: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bir Bileşeni Uygulama](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz desen uygulayan bir bileşen oluşturulacağını gösterir. Yardımcı sınıfları kullanılarak uygulanır <xref:System.ComponentModel?displayProperty=nameWithType> ad alanı altında herhangi bir uygulama modeli bileşeni düzgün çalıştığını sağlar.  
  
 [Nasıl yapılır: Olay Tabanlı Zaman Uyumsuz Deseni Destekleyen Bileşenleri Kullanma](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 Olay tabanlı zaman uyumsuz deseni destekleyen bir bileşeni kullanmayı açıklar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.ComponentModel.AsyncOperation>  
 Açıklar <xref:System.ComponentModel.AsyncOperation> sınıfı ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 Açıklar <xref:System.ComponentModel.AsyncOperationManager> sınıfı ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 Açıklar <xref:System.ComponentModel.BackgroundWorker> bileşeni ve tüm üyeleri bağlantılar içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [Olaylar](../../../docs/standard/events/index.md)  
 [Bileşenleri çoklu iş parçacığı kullanımı](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
