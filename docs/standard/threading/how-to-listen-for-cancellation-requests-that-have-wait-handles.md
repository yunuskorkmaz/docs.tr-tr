---
title: "Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a0998703ef5b27b4de725a2c2adcfc3d9a2135b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme
Bir olay bildirilmesini bekleyen sırada bir yöntem engellenirse, bu iptal belirteci değerini denetleyin ve zamanında yanıt. İlk örnek gibi olaylar ile çalışırken bu sorunu çözmek gösterilmiştir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yerel olarak desteklemeyen birleşik iptal framework. İkinci örnek kullanır daha kolay bir yaklaşım gösterir <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, iptal birleşik hangi desteklemiyor.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Threading.ManualResetEvent> birleştirilmiş iptal desteklemeyen bekleme tanıtıcıları engelini kaldırma göstermek için.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanan bir <xref:System.Threading.ManualResetEventSlim> koordinasyon engelini kaldırma göstermek için destek temelleri iptal birleşik. Diğer basit koordinasyon temelleri ile aynı yaklaşımı gibi kullanılabilir <xref:System.Threading.Semaphore> `Slim` ve <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
