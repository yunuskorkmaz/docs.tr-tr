---
title: "Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme"
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
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme
Bu örnek, ya da belirteci isterse bir işlem iptal edebilirsiniz iki iptal belirteçlerini aynı anda dinlenecek gösterilmiştir.  
  
> [!NOTE]
>  "Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir Bu hata zararsız kaynaklanır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın. Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci bir belirteç katılmak için kullanılır. Bu yalnızca bir iptal belirteci bağımsız değişken olarak ele yöntemleri geçirilmesi için belirteci sağlar. Örnek bir yöntem gelen dışında sınıfı ve sınıf içinde oluşturulan bir belirteç geçirilen hem bir belirteç uymanız gerekir yaygın bir senaryo gösterir.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Ne zaman bağlantılı belirteci oluşturur bir <xref:System.OperationCanceledException>, özel durumu geçirilen belirteç bağlantılı, öncül belirteçlerin ya belirtecidir. Hangi belirteçlerin iptal edildi belirlemek için doğrudan öncül belirteçleri durumunu kontrol edin.  
  
 Bu örnekte, <xref:System.AggregateException> hiçbir zaman oluşturulması, ancak çünkü burada yakaladığı gerçek dünya senaryolarında yanı sıra diğer tüm özel durumlar <xref:System.OperationCanceledException> görev temsilciden oluşturulan içinde kaydırılan bir <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
