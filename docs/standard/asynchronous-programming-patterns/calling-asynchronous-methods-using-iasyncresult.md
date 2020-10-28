---
title: IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma
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
ms.openlocfilehash: 8e11f734410e266aa4c175551e8a3fbf5d9236c9
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888912"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma

.NET kitaplıkları ve üçüncü taraf sınıf kitaplıklarındaki türler, bir uygulamanın ana uygulama iş parçacığı dışındaki iş parçacıklarında zaman uyumsuz işlemler gerçekleştirirken yürütmeye devam etmesine izin veren yöntemler sağlayabilir. Aşağıdaki bölümlerde, tasarım modelini kullanan zaman uyumsuz yöntemleri çağırabileceğiniz farklı yolları gösteren kod örnekleri açıklanır ve sağlanmıştır <xref:System.IAsyncResult> .  
  
- [Zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](blocking-application-execution-by-ending-an-async-operation.md).  
  
- [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Zaman uyumsuz bir Işlemin durumu yoklanıyor](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Zaman uyumsuz bir Işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
