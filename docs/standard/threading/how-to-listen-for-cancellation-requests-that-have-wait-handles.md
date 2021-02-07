---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bekleyen tutamaçları olan Iptal Isteklerini dinleme'
title: 'Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: d38e4892457873b3f918582bf154a6a596e9d361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666803"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme

Bir olayın sinyal vermesini beklediği sırada bir yöntem engellenirse, iptal belirtecinin değerini denetleyebilir ve zamanında yanıt verebilir. İlk örnek, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Birleşik iptal çerçevesini yerel olarak desteklemeyen gibi olaylarla çalışırken bu sorunun nasıl çözüleceğini gösterir. İkinci örnekte <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , Birleşik iptali destekleyen, kullanan daha kolay bir yaklaşım gösterilmektedir.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Threading.ManualResetEvent> Birleşik iptali desteklemeyen bekleme tanıtıcılarının engellemesini nasıl engellemenin nasıl yapılacağını göstermek için bir kullanır.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, <xref:System.Threading.ManualResetEventSlim> Birleşik iptalleri destekleyen düzenleme temel temellerini engellemeyi göstermek için bir kullanır. Aynı yaklaşım, ve gibi diğer basit düzenleme temelleri ile de kullanılabilir <xref:System.Threading.Semaphore> `Slim` <xref:System.Threading.CountdownEvent> .  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Iş parçacıklarında iptal](cancellation-in-managed-threads.md)
