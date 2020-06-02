---
title: Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 6184e52c3f6e39e452331af27b83520e498062aa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289934"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
Zaman uyumsuz bir işlemin sonuçlarının, işlem tamamlanana kadar durdurulması gerekir. Zaman uyumsuz bir işlemin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
- <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> Zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- Zaman uyumsuz işlemin **bitiş**_OperationName_ yöntemini çağırın. Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](blocking-application-execution-by-ending-an-async-operation.md).  
  
 <xref:System.Threading.WaitHandle>Zaman uyumsuz bir işlem tamamlanana kadar engellemek için bir veya daha fazla nesne kullanan uygulamalar genellikle **BEGIN**_OperationName_ yöntemini çağırır, işlem sonuçları olmadan yapılabilecek işleri gerçekleştirir ve ardından zaman uyumsuz işlemler tamamlanana kadar blok yapmaz. Bir uygulama <xref:System.Threading.WaitHandle.WaitOne%2A> , yöntemini kullanarak yöntemlerinden birini çağırarak tek bir işlemde bloke edebilir <xref:System.IAsyncResult.AsyncWaitHandle%2A> . Zaman uyumsuz işlemlerin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve yöntemlerinden birini çağırın <xref:System.Threading.WaitHandle.WaitAll%2A> . Zaman uyumsuz işlemler kümesinden herhangi birinin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve yöntemlerden birini çağırın <xref:System.Threading.WaitHandle.WaitAny%2A> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistem bilgilerini almak üzere DNS sınıfındaki zaman uyumsuz yöntemleri kullanmayı gösterir. Örnek, <xref:System.Threading.WaitHandle> zaman uyumsuz işlemle ilişkili öğesini kullanarak engellemeyi gösterir. `null` `Nothing` <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` Bu yaklaşım kullanıldığında gerekli olmadığından, ve parametreleri için (Visual Basic olarak) geçtiğini unutmayın `stateObject` .  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
