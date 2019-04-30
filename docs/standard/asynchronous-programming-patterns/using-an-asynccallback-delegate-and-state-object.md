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
ms.openlocfilehash: bb62b191dc3b3246745f9f0ea3737ed74a2bf57b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699012"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma
Kullandığınızda, bir <xref:System.AsyncCallback> zaman uyumsuz işlemin ayrı bir iş parçacığında sonuçları işlemek için temsilci, bir durum nesnesi geri çağırmalar arasında bilgi geçirmek ve Nihai sonuç almak için kullanabilirsiniz. Bu konuda, örnekte genişleterek o uygulama gösterilir [zaman uyumsuz bir işlemi sonlandırmak için bir AsyncCallback temsilcisi kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, zaman uyumsuz metotlar kullanma gösterilmektedir <xref:System.Net.Dns> kullanıcı tarafından belirtilen bilgisayarların etki alanı adı sistemi (DNS) bilgilerini almak için sınıf. Bu örnek, tanımlar ve kullandığı `HostRequest` durum bilgilerini depolamak için sınıf. A `HostRequest` nesne kullanıcı tarafından girilen her bir bilgisayar adı için oluşturulur. Bu nesne geçirilir <xref:System.Net.Dns.BeginGetHostByName%2A> yöntemi. `ProcessDnsInformation` Yöntemi, bir istek tamamlandıktan her zaman çağrılır. `HostRequest` Nesnesi kullanılarak alınır <xref:System.IAsyncResult.AsyncState%2A> özelliği. `ProcessDnsInformation` Yöntemi kullanan `HostRequest` depolamak için nesne <xref:System.Net.IPHostEntry> istek tarafından döndürülen veya <xref:System.Net.Sockets.SocketException> istek tarafından oluşturulur. Tüm istekleri tamamlandığı zaman, uygulama üzerinden yinelenir `HostRequest` nesneleri ve DNS bilgilerini görüntüler veya <xref:System.Net.Sockets.SocketException> hata iletisi.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
