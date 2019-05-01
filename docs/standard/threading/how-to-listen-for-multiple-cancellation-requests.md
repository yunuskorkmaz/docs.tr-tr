---
title: 'Nasıl yapılır: Birden Çok İptal İsteğini Dinleme'
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
ms.openlocfilehash: 17874b8b9733ea18d4877e2c79810fcd6247db0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926207"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Nasıl yapılır: Birden Çok İptal İsteğini Dinleme
Bu örnek, bir işlem ya da belirteç istediği zaman iptal edebilirsiniz iki iptal belirteçleri için aynı anda dinlenecek gösterilmektedir.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci bir belirteç birleştirmek için kullanılır. Bu, yalnızca bir iptal belirteci bağımsız değişken olarak ele yöntemlere geçirilen belirteç sağlar. Örnek bir yöntem den sınıf ve sınıf içinde oluşturulan bir belirteç dışında geçirilen bir belirteç uymanız gerekir, yaygın bir senaryo gösterir.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Ne zaman bağlı belirteci oluşturur bir <xref:System.OperationCanceledException>, özel durum geçirilen belirteç bağlı, öncül belirteçlerin değil ya da belirtecidir. Hangi belirteçleri iptal edildi belirlemek için doğrudan öncül belirteçleri durumunu denetleyin.  
  
 Bu örnekte, <xref:System.AggregateException> hiçbir zaman durumun oluşturulması gerekir, ancak burada çünkü yakalandı gerçek dünya senaryolarında yanı sıra diğer tüm özel durumlar <xref:System.OperationCanceledException> görev temsilciden durum içinde sarmalanmış bir <xref:System.AggregateException>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
