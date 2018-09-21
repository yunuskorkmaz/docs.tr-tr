---
title: 'Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519480"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme
Bir olay için sinyal bekliyor ancak bir yöntem engellenirse bu iptal belirteci değerini kontrol edin ve zamanında yanıt. İlk örnek gibi olaylar ile çalışırken, bu sorunu çözmek gösterilmektedir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yerel olarak desteklemeyen birleşik iptalini çerçevesi. İkinci örnek kullanan daha kolay bir yaklaşımı gösterir <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, iptal birleşik hangi desteklemiyor.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Threading.ManualResetEvent> birleşik iptal desteklemeyen bekleme tanıtıcıları engelini kaldırma işlemini göstermek için.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir <xref:System.Threading.ManualResetEventSlim> koordinasyon engelini kaldırma işlemini göstermek için destek temelleri iptal birleşik. Diğer hafif koordinasyon temelleri ile aynı yaklaşımı gibi kullanılabilir <xref:System.Threading.Semaphore> `Slim` ve <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
