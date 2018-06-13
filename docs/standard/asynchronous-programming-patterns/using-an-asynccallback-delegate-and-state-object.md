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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 259f7de52dff04af043554382a5bad35355d9926
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567243"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
Kullandığınızda, bir <xref:System.AsyncCallback> zaman uyumsuz işlemi ayrı bir iş parçacığı sonuçlarını işlemek için temsilci seçme, bir durum nesnesi geri aramalar arasında bilgi aktarmak ve son sonucu almak için kullanabilirsiniz. Bu konuda, uygulama örnekte genişleterek gösterilir [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanarak](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde zaman uyumsuz yöntemleri kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf. Bu örnek tanımlar ve kullanır `HostRequest` durum bilgilerini depolamak için sınıf. A `HostRequest` nesne kullanıcı tarafından girilen her bir bilgisayar adı için oluşturulan. Bu nesne için geçirilen <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemi. `ProcessDnsInformation` Yöntemi, bir isteği tamamlayan her zaman çağrılır. `HostRequest` Nesnesi kullanarak alınır <xref:System.IAsyncResult.AsyncState%2A> özelliği. `ProcessDnsInformation` Yöntemi kullanan `HostRequest` depolamak için nesne <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya <xref:System.Net.Sockets.SocketException> istek tarafından oluşturulur. Tüm istekleri tamamlandığı zaman üzerinden uygulama tekrarlanan `HostRequest` nesneleri ve DNS bilgilerini görüntüler veya <xref:System.Net.Sockets.SocketException> hata iletisi.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
