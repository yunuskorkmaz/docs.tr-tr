---
title: IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830460"
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
