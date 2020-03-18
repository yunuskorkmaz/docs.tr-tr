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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121433"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Bir AsyncWaitHandle Kullanarak Uygulamanın Yürütülmesini Engelleme
Eşzamanlı işlemin sonuçlarını beklerken başka işler yapmaya devam edemeyen uygulamaların işlem tamamlanana kadar engellenmesi gerekir. Asynchronous işleminin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
- Eşzamanlı işlemin **Begin**_OperationName_ yöntemiyle döndürülen <xref:System.IAsyncResult> özelliği kullanın. <xref:System.IAsyncResult.AsyncWaitHandle%2A> Bu yaklaşım bu konuda gösterilmiştir.  
  
- Eşzamanlı işlemin **Son**_İşlemName_ yöntemini arayın. Bu yaklaşımı gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md)örnek için bkz.  
  
 Bir eşzamanlı işlem tamamlanana kadar engellemek için bir veya daha fazla <xref:System.Threading.WaitHandle> nesne kullanan uygulamalar genellikle **Begin**_OperationName_ yöntemini çağırır, işlem sonuçları olmadan yapılabilecek herhangi bir işi gerçekleştirir ve eşsenkronize işlem(ler) tamamlanana kadar engeller. Bir uygulama kullanarak <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemlerden birini arayarak tek <xref:System.IAsyncResult.AsyncWaitHandle%2A>bir işlem üzerinde engelleyebilir. Bir eşyokuz işlemleri kümesinin tamamlanmasını beklerken engellemek <xref:System.IAsyncResult.AsyncWaitHandle%2A> için, ilişkili nesneleri bir dizide depolayın ve yöntemlerden birini çağırın. <xref:System.Threading.WaitHandle.WaitAll%2A> Eşiş işlemleri kümesinin tamamlanmasını beklerken engellemek için, ilişkili <xref:System.IAsyncResult.AsyncWaitHandle%2A> nesneleri bir dizide depolayın ve <xref:System.Threading.WaitHandle.WaitAny%2A> yöntemlerden birini arayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir bilgisayar için Alan Adı Sistemi bilgilerini almak için DNS sınıfında eşzamanlı yöntemler ini gösterir. Örnek, eşzamanlı işlemle <xref:System.Threading.WaitHandle> ilişkili kullanımıengellemeyi göstermektedir. `null` Bu yaklaşımı`Nothing` kullanırken gerekli olmadığı <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` için `stateObject` (Visual Basic'te) parametreler için geçirildiğini unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
