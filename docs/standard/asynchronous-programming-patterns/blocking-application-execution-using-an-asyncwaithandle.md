---
title: "Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2660b3cbf7e8ee43a22edbfb66a4262684983b87
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
İşlemi tamamlanana kadar diğer iş zaman uyumsuz bir işlem sonuçları için beklenirken yapmak için devam edemiyor uygulamaları engellemelidir. Bir zaman uyumsuz bir işlemin tamamlanması beklenirken, uygulamanın ana iş parçacığı engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
-   Kullanım <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* yöntemi. Bu yaklaşım, bu konuda gösterilmiştir.  
  
-   Zaman uyumsuz işlem çağrısı **son** *OperationName* yöntemi. Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırarak uygulamanın yürütülmesini engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Bir veya daha fazla kullanan uygulamaları <xref:System.Threading.WaitHandle> zaman uyumsuz bir işlem tamamlanana kadar engellemek için nesneleri genellikle çağıracaktır **başlamak** *OperationName* yöntemi yapılabilir herhangi bir iş gerçekleştirin işlem, ardından zaman uyumsuz işlemleri kadar blok sonuçlarını olmadan tamamlar. Bir uygulama üzerinde tek bir işlemi birini çağırarak engelleyebilirsiniz <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerini kullanarak <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Bir dizi tamamlamak için zaman uyumsuz işlemleri için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAll%2A> yöntemleri. Bir dizi tamamlamak için zaman uyumsuz işlemleri herhangi biri için beklenirken engellemek için ilişkili depolama <xref:System.IAsyncResult.AsyncWaitHandle%2A> bir dizi ve, çağrı nesneleri <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistemi bilgileri almak için DNS sınıfında zaman uyumsuz yöntemleri kullanarak gösterilmektedir. Örnek kullanarak engelleme gösterir <xref:System.Threading.WaitHandle> zaman uyumsuz işlemle ilişkili. Unutmayın `null` (`Nothing` Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` ve `stateObject` parametreleri bunlar bu yaklaşımı kullanarak, gerekli olmadığından.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
