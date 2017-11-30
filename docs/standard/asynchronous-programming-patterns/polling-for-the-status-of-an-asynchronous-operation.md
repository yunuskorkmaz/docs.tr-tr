---
title: "Zaman Uyumsuz Bir İşlemin Durumu için Yoklama"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1f7f74a8b38c06f6a042d55c0def76ddfc5da77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
Zaman uyumsuz bir işlem sonuçları için beklenirken diğer iş yapabilirsiniz uygulamaları işlemi tamamlanana kadar bekleyen bloğu değil. Bir zaman uyumsuz bir işlemin tamamlanması beklenirken yönergeleri yürütme devam etmek için aşağıdaki seçeneklerden birini kullanın:  
  
-   Kullanım <xref:System.IAsyncResult.IsCompleted%2A> özelliği <xref:System.IAsyncResult> zaman uyumsuz işlem tarafından döndürülen **başlamak** *OperationName* işleminin tamamlanıp tamamlanmadığını belirlemek için yöntem. Bu yaklaşım, yoklama olarak bilinir ve bu konuda gösterilmiştir.  
  
-   Kullanım bir <xref:System.AsyncCallback> zaman uyumsuz işlemi ayrı bir iş parçacığı sonuçlarını işlemek için temsilci. Bu yaklaşım gösteren bir örnek için bkz: [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> sınıfı bir kullanıcı tarafından belirtilen bilgisayar için etki alanı adı sistemi bilgileri alınamadı. Bu örnekte, zaman uyumsuz işlemi başlatır ve dönemleri yazdırır (".") işlemi tamamlanana kadar konsolda. Unutmayın **null** (**hiçbir şey** Visual Basic'te) geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> ve <xref:System.Object> parametreleri bu bağımsız değişkenler bu yaklaşımı kullanarak, gerekli olmadığından.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay tabanlı zaman uyumsuz desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Olay tabanlı zaman uyumsuz desene genel bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
