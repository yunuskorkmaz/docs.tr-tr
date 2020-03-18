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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130931"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
Eşzamanlı işlemin sonuçlarını beklerken başka bir iş yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellememelidir. Eşzamanlı işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için aşağıdaki seçeneklerden birini kullanın:  
  
- Ayrı <xref:System.AsyncCallback> bir iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullanın. Bu yaklaşım bu konuda gösterilmiştir.  
  
- İşlemin <xref:System.IAsyncResult.IsCompleted%2A> tamamlanıp <xref:System.IAsyncResult> tamamlanmadığını belirlemek için eşzamanlı işlemin **Begin**_OperationName_ yöntemi yle döndürülen özelliği kullanın. Bu yaklaşımı gösteren bir örnek için, bir [Eşzamanlı İşlemin Durumu Için Yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md)bölümüne bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bilgisayarlar <xref:System.Net.Dns> için Alan Adı Sistemi (DNS) bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir. Bu örnek, <xref:System.AsyncCallback> `ProcessDnsInformation` yönteme başvuran bir temsilci oluşturur. Bu yöntem, DNS bilgileri için her bir eşzamanlı istek için bir kez çağrılır.  
  
 Kullanıcı tarafından belirtilen ana bilgisayar parametreye <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> geçirildiğini unutmayın. Daha karmaşık bir durum nesnesi tanımlamayı ve kullanmayı gösteren [bir](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)örnek için bkz.  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma ](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
