---
title: Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130931"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez. Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:  
  
- Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir <xref:System.AsyncCallback> temsilcisi kullanın. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen <xref:System.IAsyncResult> <xref:System.IAsyncResult.IsCompleted%2A> özelliğini kullanın. Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Kullanıcı tarafından belirtilen bilgisayarlar için etki alanı adı sistemi (DNS) bilgilerini almak üzere <xref:System.Net.Dns> sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir. Bu örnek, `ProcessDnsInformation` yöntemine başvuran bir <xref:System.AsyncCallback> temsilcisi oluşturur. Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.  
  
 Kullanıcı tarafından belirtilen konağın <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parametresine geçtiğini unutmayın. Daha karmaşık bir durum nesnesini tanımlamayı ve kullanmayı gösteren bir örnek için bkz. [AsyncCallback temsilcisi ve durum nesnesi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
