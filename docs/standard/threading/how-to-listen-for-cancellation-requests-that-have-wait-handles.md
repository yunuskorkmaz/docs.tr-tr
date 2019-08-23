---
title: 'Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
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
ms.openlocfilehash: 67cf434737257a942e094fcb38ed18d597645d46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913339"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme
Bir olayın sinyal vermesini beklediği sırada bir yöntem engellenirse, iptal belirtecinin değerini denetleyebilir ve zamanında yanıt verebilir. İlk örnek, Birleşik iptal çerçevesini yerel olarak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> desteklemeyen gibi olaylarla çalışırken bu sorunun nasıl çözüleceğini gösterir. İkinci örnekte, Birleşik iptali destekleyen, kullanan <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>daha kolay bir yaklaşım gösterilmektedir.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Birleşik iptali <xref:System.Threading.ManualResetEvent> desteklemeyen bekleme tanıtıcılarının engellemesini nasıl engellemenin nasıl yapılacağını göstermek için bir kullanır.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Birleşik iptalleri destekleyen düzenleme temel temellerini engellemeyi göstermek için bir <xref:System.Threading.ManualResetEventSlim> kullanır. Aynı yaklaşım, <xref:System.Threading.Semaphore> `Slim` ve <xref:System.Threading.CountdownEvent>gibi diğer basit düzenleme temelleri ile de kullanılabilir.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
