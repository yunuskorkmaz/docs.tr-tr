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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137993"
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Nasıl Yapılır: İptal İstekleri için Geri Çağırmaları Kaydetme
Aşağıdaki örnek, belirteci oluşturan nesneye <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> <xref:System.Threading.CancellationTokenSource.Cancel%2A> yapılan çağrı nedeniyle bir özellik gerçek olduğunda çağrılacak bir temsilcinin nasıl kaydedilemeyeceğini gösterir. Birleşik iptal çerçevesini yerel olarak desteklemeyen eşzamanlı işlemleri iptal etmek ve eşzamanlı işlemin tamamlanmasını bekleyen yöntemleri kaldırmak için bu tekniği kullanın.  
  
> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Net.WebClient.CancelAsync%2A> iptal belirteci aracılığıyla iptal istendiğinde çağrılacak yöntem olarak yöntem kaydedilir.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Geri arama kaydedildiğinde iptal isteminde bulunulmuşsa, geri aramanın çağrılması garanti edilir. Bu özel durumda, <xref:System.Net.WebClient.CancelAsync%2A> hiçbir eşzamanlı işlem devam ediyorsa yöntem hiçbir şey yapmaz, bu nedenle yöntemi aramak her zaman güvenlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
