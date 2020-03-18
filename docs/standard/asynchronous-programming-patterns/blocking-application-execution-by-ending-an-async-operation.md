---
title: Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121323"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Zaman Uyumsuz bir İşlemi Sonlandırarak Uygulama Yürütmesini Engelleme
Eşzamanlı işlemin sonuçlarını beklerken başka işler yapmaya devam edemeyen uygulamaların işlem tamamlanana kadar engellenmesi gerekir. Asynchronous işleminin tamamlanmasını beklerken uygulamanızın ana iş parçacığını engellemek için aşağıdaki seçeneklerden birini kullanın:  
  
- Eşzamanlı işlemleri **Son**_İşlemName_ yöntemini arayın. Bu yaklaşım bu konuda gösterilmiştir.  
  
- Eşzamanlı işlemin **Begin**_OperationName_ yöntemiyle döndürülen <xref:System.IAsyncResult> özelliği kullanın. <xref:System.IAsyncResult.AsyncWaitHandle%2A> Bu yaklaşımı gösteren bir örnek için, [bkz.](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md)  
  
 Bir eşzamanlı işlem tamamlanana kadar engellemeyi engellemek için **Son**_İşlem Adı_ yöntemini kullanan uygulamalar genellikle_İşlemNameyi_ **Başlat**yöntemini çağırır, işlemin sonuçları olmadan yapılabilecek herhangi bir işi gerçekleştirir ve ardından **Son**_İşlem Name'yi_çağırır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir <xref:System.Net.Dns> bilgisayar için Alan Adı Sistemi bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir. `null` Bu yaklaşım`Nothing` kullanılırken bu bağımsız <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` değişkenler gerekli olmadığından ( Visual Basic'te) `stateObject` parametreler için geçirildiğini unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
