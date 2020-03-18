---
title: Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123968"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemin Durumu için Yoklama
Eşzamanlı işlemin sonuçlarını beklerken başka bir iş yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellememelidir. Eşzamanlı işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için aşağıdaki seçeneklerden birini kullanın:  
  
- İşlemin <xref:System.IAsyncResult.IsCompleted%2A> tamamlanıp <xref:System.IAsyncResult> tamamlanmadığını belirlemek için eşzamanlı işlemin **Begin**_OperationName_ yöntemi yle döndürülen özelliği kullanın. Bu yaklaşım yoklama olarak bilinir ve bu konuda gösterilmiştir.  
  
- Ayrı <xref:System.AsyncCallback> bir iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullanın. Bu yaklaşımı gösteren bir örnek için [bkz.](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bir <xref:System.Net.Dns> bilgisayar için Alan Adı Sistemi bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir. Bu örnek, eşzamanlı işlemi başlatır ve işlem tamamlanana kadar konsolda dönemleri (".") yazdırır. Bu yaklaşım kullanılırken bu bağımsız değişkenler <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> <xref:System.Object> gerekli olmadığından, **null** (Visual Basic hiçbir**şey)** ve parametreler için geçirilir unutmayın.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
