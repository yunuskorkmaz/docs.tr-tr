---
title: Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme
ms.date: 03/30/2017
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: d99c09c4ac087152407fa8dc12894c216f9f43dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716180"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme

Zaman uyumsuz bir işlemin sonuçlarının, işlem tamamlanana kadar durdurulması gerekir. Zaman uyumsuz bir işlemin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
- Zaman uyumsuz işlemler **bitiş**_OperationName_ yöntemini çağırın. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> Zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın. Bu yaklaşımı gösteren bir örnek için bkz. [AsyncWaitHandle kullanarak uygulama yürütmeyi engelleme](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Zaman uyumsuz bir işlem tamamlanana kadar engellemek için **End**_OperationName_ yöntemini kullanan uygulamalar genellikle **BEGIN**_OperationName_ yöntemini çağırır, Işlem sonuçları olmadan yapılabilecek işleri gerçekleştirir ve sonra **End**_OperationName_' ı çağırır.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bir bilgisayar Için etki alanı adı sistem bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir. `null` `Nothing` <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` `stateObject` Bu yaklaşım kullanıldığında bağımsız değişkenler gerekli olmadığından, ve parametreleri için (Visual Basic olarak) geçtiğini unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
