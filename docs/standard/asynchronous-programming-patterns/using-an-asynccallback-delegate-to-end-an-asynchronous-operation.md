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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2ce3f194cbdaaa7b244504745c542da7ba8a73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969448"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
Zaman uyumsuz bir işlemin sonuçları için beklenirken diğer işlerinizi yapabilirsiniz uygulamalar işlem tamamlanana kadar bekleyen Engellemesi gereken değil. Bir zaman uyumsuz bir işlemin tamamlanması beklenirken yönergeleri yürütme devam etmek için aşağıdaki seçeneklerden birini kullanın:  
  
- Kullanım bir <xref:System.AsyncCallback> zaman uyumsuz işlemin ayrı bir iş parçacığında sonuçları işlemek için temsilci. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- Kullanım <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak**_OperationName_ işleminin tamamlanıp tamamlanmadığını belirlemek için yöntemi. Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemin durumu için yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf. Bu örnekte bir <xref:System.AsyncCallback> başvuran temsilci `ProcessDnsInformation` yöntemi. Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.  
  
 Kullanıcı tarafından belirtilen konak geçirilir Not <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametresi. Tanımlama ve daha karmaşık bir durum nesnesi kullanma gösteren bir örnek için bkz: [bir AsyncCallback temsilcisi ve durum nesnesi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
