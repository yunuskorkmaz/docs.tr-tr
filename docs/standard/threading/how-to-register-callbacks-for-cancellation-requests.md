---
title: 'Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: 87ba1ab9ac095c733a53f766d00ebb7530a8d9c4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137993"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme
Aşağıdaki örnek, belirteci oluşturan nesnedeki bir <xref:System.Threading.CancellationTokenSource.Cancel%2A> çağrısı nedeniyle <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği true olduğunda çağrılacak bir temsilcinin nasıl kaydedileceği gösterilmektedir. Birleşik iptal çerçevesini yerel olarak desteklemeyen zaman uyumsuz işlemleri iptal etmek ve zaman uyumsuz bir işlemin tamamlanmasını bekleyen yöntemlerin engellenmesini kaldırma için bu tekniği kullanın.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> yöntemi iptal belirteci aracılığıyla iptal istendiğinde çağrılacak yöntem olarak kaydedilir.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Geri çağırma kaydedildiğinde iptal işlemi zaten isteniyorsa, geri aramanın çağrılması garanti edilir. Bu durumda, zaman uyumsuz bir işlem devam ederken <xref:System.Net.WebClient.CancelAsync%2A> yöntemi hiçbir şey yapmaz, bu nedenle yöntemi çağırmak her zaman güvenlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
