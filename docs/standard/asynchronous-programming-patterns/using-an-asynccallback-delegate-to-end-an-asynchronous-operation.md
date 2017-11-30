---
title: "Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbe170588776daa97fec4c736d4b1bdd871de518
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
Zaman uyumsuz bir işlem sonuçları için beklenirken diğer iş yapabilirsiniz uygulamaları işlemi tamamlanana kadar bekleyen bloğu değil. Bir zaman uyumsuz bir işlemin tamamlanması beklenirken yönergeleri yürütme devam etmek için aşağıdaki seçeneklerden birini kullanın:  
  
-   Kullanım bir <xref:System.AsyncCallback> zaman uyumsuz işlemi ayrı bir iş parçacığı sonuçlarını işlemek için temsilci. Bu yaklaşım, bu konuda gösterilmiştir.  
  
-   Kullanım <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* işleminin tamamlanıp tamamlanmadığını belirlemek için yöntem. Bu yaklaşım gösteren bir örnek için bkz: [için zaman uyumsuz bir işlem durumunu yoklama](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf. Bu örnekte bir <xref:System.AsyncCallback> başvuruyor temsilci `ProcessDnsInformation` yöntemi. Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.  
  
 Kullanıcı tarafından belirtilen konak geçirilir Not <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametresi. Tanımlama ve daha karmaşık bir durum nesnesi kullanma gösteren bir örnek için bkz: [bir AsyncCallback temsilcisi ve durum nesnesi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [IAsyncResult kullanarak zaman uyumsuz yöntemleri çağırma](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [Bir AsyncCallback temsilcisi ve durum nesnesi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
