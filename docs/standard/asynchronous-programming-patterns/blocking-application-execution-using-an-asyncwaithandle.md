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
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121433"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
Zaman uyumsuz bir işlemin sonuçlarının, işlem tamamlanana kadar durdurulması gerekir. Zaman uyumsuz bir işlemin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
- Zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.AsyncWaitHandle%2A> özelliğini kullanın. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- Zaman uyumsuz işlemin **bitiş**_OperationName_ yöntemini çağırın. Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemi sonlandırarak uygulama yürütmeyi engelleme](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Zaman uyumsuz bir işlem tamamlanana kadar engellemek için bir veya daha fazla <xref:System.Threading.WaitHandle> nesnesi kullanan uygulamalar genellikle **BEGIN**_OperationName_ yöntemini çağırır, işlem sonuçları olmadan yapılabilecek işleri gerçekleştirir ve sonra engeller zaman uyumsuz işlemler tamamlanana kadar. Bir uygulama, <xref:System.IAsyncResult.AsyncWaitHandle%2A>kullanarak <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerinden birini çağırarak tek bir işlemde bloke edebilir. Zaman uyumsuz işlemlerin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesnelerini bir dizide depolayın ve <xref:System.Threading.WaitHandle.WaitAll%2A> yöntemlerinden birini çağırın. Zaman uyumsuz işlemler kümesinden herhangi birinin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesnelerini bir dizide depolayın ve <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerinden birini çağırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bir bilgisayar için etki alanı adı sistem bilgilerini almak üzere DNS sınıfındaki zaman uyumsuz yöntemleri kullanmayı gösterir. Örnek, zaman uyumsuz işlemle ilişkili <xref:System.Threading.WaitHandle> kullanarak engellemeyi gösterir. Bu yaklaşım kullanılırken gerekli olmadığından, <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` ve `stateObject` parametreleri için `null` (Visual Basic`Nothing`) geçtiğini unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
