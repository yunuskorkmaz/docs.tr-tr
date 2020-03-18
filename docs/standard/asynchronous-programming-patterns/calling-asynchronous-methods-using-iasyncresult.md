---
title: 'IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma '
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121310"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma 
.NET Framework ve üçüncü taraf sınıf kitaplıklarında kullanılan türler, ana uygulama iş parçacığı dışındaki iş parçacıklarında eşzamanlı işlemler gerçekleştirirken uygulamanın yürütmeye devam etmesine izin veren yöntemler sağlayabilir. Aşağıdaki bölümler, <xref:System.IAsyncResult> tasarım deseni kullanan eşzamanlı yöntemleri çağırabileceğiniz farklı yolları gösteren kod örneklerini açıklar ve sağlar.  
  
- [Bir Async İşlemini Sonlayarak Uygulama Yürütmeyi Engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- [AsyncWaitHandle kullanarak Uygulama Yürütme engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Bir Eşzamanlı İşlemin Durumu Için Yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Bir Eşzamanlı İşlemi Sona Erdirmek için Bir AsyncCallback Temsilcisi kullanma.](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
