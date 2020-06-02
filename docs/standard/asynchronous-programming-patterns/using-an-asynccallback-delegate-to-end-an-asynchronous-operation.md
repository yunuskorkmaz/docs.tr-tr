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
ms.openlocfilehash: 8766e64c52688e820d0eb6a259e39926555d97bd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276355"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Zaman Uyumsuz Bir İşlemi Sonlandırmak için Bir AsyncCallback Temsilcisi Kullanma
Zaman uyumsuz bir işlemin sonuçlarını beklerken diğer işleri yapabilen uygulamalar, işlem tamamlanana kadar beklemeyi engellemez. Zaman uyumsuz bir işlemin tamamlanmasını beklerken yönergeleri yürütmeye devam etmek için şu seçeneklerden birini kullanın:  
  
- <xref:System.AsyncCallback>Zaman uyumsuz işlemin sonuçlarını ayrı bir iş parçacığında işlemek için bir temsilci kullanın. Bu yaklaşım, bu konuda gösterilmiştir.  
  
- <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> İşlemin tamamlanıp tamamlanmadığını anlamak için, zaman uyumsuz işlemin **BEGIN**_OperationName_ yöntemi tarafından döndürülen özelliğini kullanın. Bu yaklaşımı gösteren bir örnek için bkz. [zaman uyumsuz bir Işlemin durumu Için yoklama](polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Net.Dns> Kullanıcı tarafından belirtilen bilgisayarlar Için etki alanı adı sistemi (DNS) bilgilerini almak üzere sınıfında zaman uyumsuz yöntemleri kullanmayı gösterir. Bu örnek <xref:System.AsyncCallback> , yöntemine başvuran bir temsilci oluşturur `ProcessDnsInformation` . Bu yöntem, DNS bilgileri için her zaman uyumsuz istek için bir kez çağrılır.  
  
 Kullanıcı tarafından belirtilen konağın parametreye geçtiğini unutmayın <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> . Daha karmaşık bir durum nesnesini tanımlamayı ve kullanmayı gösteren bir örnek için bkz. [AsyncCallback temsilcisi ve durum nesnesi kullanma](using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Olay Tabanlı Zaman Uyumsuz Desen (EAP)](event-based-asynchronous-pattern-eap.md)
- [Olay Tabanlı Zaman Uyumsuz Desene Genel Bakış](event-based-asynchronous-pattern-overview.md)
- [IAsyncResult Kullanarak Zaman Uyumsuz Yöntemleri Çağırma ](calling-asynchronous-methods-using-iasyncresult.md)
- [Bir AsyncCallback Temsilcisi ve Durum Nesnesi Kullanma](using-an-asynccallback-delegate-and-state-object.md)
