---
title: 'Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16ba8000544d0b7d35a818d41a75f38e6fd0293d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178578"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme
Bu örnek, bir işlem ya da belirteç istediği zaman iptal edebilirsiniz iki iptal belirteçleri için aynı anda dinlenecek gösterilmektedir.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci bir belirteç birleştirmek için kullanılır. Bu, yalnızca bir iptal belirteci bağımsız değişken olarak ele yöntemlere geçirilen belirteç sağlar. Örnek bir yöntem den sınıf ve sınıf içinde oluşturulan bir belirteç dışında geçirilen bir belirteç uymanız gerekir, yaygın bir senaryo gösterir.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Ne zaman bağlı belirteci oluşturur bir <xref:System.OperationCanceledException>, özel durum geçirilen belirteç bağlı, öncül belirteçlerin değil ya da belirtecidir. Hangi belirteçleri iptal edildi belirlemek için doğrudan öncül belirteçleri durumunu denetleyin.  
  
 Bu örnekte, <xref:System.AggregateException> hiçbir zaman durumun oluşturulması gerekir, ancak burada çünkü yakalandı gerçek dünya senaryolarında yanı sıra diğer tüm özel durumlar <xref:System.OperationCanceledException> görev temsilciden durum içinde sarmalanmış bir <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
