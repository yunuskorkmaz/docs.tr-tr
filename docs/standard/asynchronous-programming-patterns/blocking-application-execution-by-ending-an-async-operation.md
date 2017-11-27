---
title: "Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.openlocfilehash: ccca6e1e4f6b5cdf098018b59426fb2262e2b346
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme
İşlemi tamamlanana kadar diğer iş zaman uyumsuz bir işlem sonuçları için beklenirken yapmak için devam edemiyor uygulamaları engellemelidir. Bir zaman uyumsuz bir işlemin tamamlanması beklenirken, uygulamanın ana iş parçacığı engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
-   Zaman uyumsuz işlemleri çağrısı **son** *OperationName* yöntemi. Bu yaklaşım, bu konuda gösterilmiştir.  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* yöntemi. Bu yaklaşım gösteren bir örnek için bkz: [engelleme uygulama yürütme kullanarak bir AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Kullanan uygulamalar **son** *OperationName* yöntemi zaman uyumsuz bir işlem tamamlanana kadar engellemek için genellikle çağıracaktır **başlamak**  *OperationName* yöntemi, işlemin sonuçlarını yapılabilir, ardından çağıran herhangi bir iş gerçekleştirmek **son** *OperationName*.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> sınıfı bir kullanıcı tarafından belirtilen bilgisayar için etki alanı adı sistemi bilgileri alınamadı. Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri bu bağımsız değişkenler bu yaklaşımı kullanarak, gerekli olmadığından.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
