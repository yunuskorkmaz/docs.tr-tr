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
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137986"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme
Bir yöntem, bir olayın sinyal verilen olmasını beklerken engellenirse, iptal jetonunun değerini denetleyemez ve zamanında yanıt veremez. İlk örnek, birleşik iptal çerçevesini yerel olarak desteklemeyen olaylarla <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> çalışırken bu sorunu nasıl çözeceğinizi gösterir. İkinci örnek, birleşik iptali destekleyen <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>daha akıcı bir yaklaşım gösterir.  
  
> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Threading.ManualResetEvent> birleşik iptali desteklemeyen bekleme tanıtıcılarının engelini nasıl kaldırılacağını göstermek için a kullanır.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:System.Threading.ManualResetEventSlim> birleşik iptali destekleyen koordinasyon ilkellerinin engelini nasıl kaldırılabildiğini göstermek için a kullanır. Aynı yaklaşım gibi <xref:System.Threading.Semaphore> `Slim` diğer hafif koordinasyon ilkel, ve <xref:System.Threading.CountdownEvent>kullanılabilir.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
