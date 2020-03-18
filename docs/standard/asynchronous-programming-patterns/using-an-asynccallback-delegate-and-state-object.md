---
title: Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094600"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
Ayrı bir <xref:System.AsyncCallback> iş parçacığı içinde asynchronous işlemin sonuçlarını işlemek için bir temsilci kullandığınızda, geri aramaları arasında bilgi aktarmak ve nihai bir sonuç almak için bir durum nesnesi kullanabilirsiniz. Bu konu, bir [Eşzamanlı İşlemi Sona Erdirmek için Bir AsyncCallback Temsilci kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)örnek genişleterek bu uygulama gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, kullanıcı tarafından belirtilen bilgisayarlar <xref:System.Net.Dns> için Alan Adı Sistemi (DNS) bilgilerini almak için sınıfta eşzamanlı yöntemler ini gösterir. Bu örnek, durum `HostRequest` bilgilerini depolamak için sınıfı tanımlar ve kullanır. Kullanıcı `HostRequest` tarafından girilen her bilgisayar adı için bir nesne oluşturulur. Bu nesne <xref:System.Net.Dns.BeginGetHostByName%2A> yönteme geçirilir. Yöntem, `ProcessDnsInformation` bir istek her tamamlandığında çağrılır. Nesne `HostRequest` <xref:System.IAsyncResult.AsyncState%2A> özelliği kullanılarak alınır. Yöntem, `ProcessDnsInformation` `HostRequest` <xref:System.Net.IPHostEntry> iade edilen isteği veya istek tarafından <xref:System.Net.Sockets.SocketException> atılan bir depoyu depolamak için nesneyi kullanır. Tüm istekler tamamlandığında, uygulama `HostRequest` nesneler üzerinde yinelenir ve DNS <xref:System.Net.Sockets.SocketException> bilgisini veya hata iletisini görüntüler.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
