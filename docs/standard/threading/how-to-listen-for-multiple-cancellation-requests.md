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
ms.openlocfilehash: 2684f0fd43f84573933fc0a7107ce4f9035bc092
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913314"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Nasıl yapılır: Birden Çok İptal İsteğini Dinleme
Bu örnek, herhangi bir belirteç istediğinde bir işlemi iptal edebilmeniz için iki iptal belirtecinin aynı anda nasıl dinleneceğini gösterir.  
  
> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci tek bir belirteçte birleştirmek için kullanılır. Bu, belirtecin bağımsız değişken olarak yalnızca bir iptal belirteci alan yöntemlere geçirilmesini sağlar. Örnek, bir yöntemin, sınıfın dışından geçirilen bir belirteci ve sınıf içinde oluşturulan bir belirteci gözlemleyecek ortak bir senaryoyu gösterir.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Bağlantılı belirteç bir <xref:System.OperationCanceledException>oluşturduğunda, özel duruma geçirilen belirteç, öncül belirteçlerinden biri değil bağlı belirteçtir. Belirteçlerin hangilerinin iptal edildiğini öğrenmek için, öncül belirteçlerin durumunu doğrudan denetleyin.  
  
 Bu örnekte, <xref:System.AggregateException> hiçbir şekilde oluşturulmamalıdır, ancak gerçek dünyada senaryolar, görev temsilcisinden oluşturulan diğer tüm <xref:System.OperationCanceledException> özel durumlar ' a <xref:System.AggregateException>sarıldığından, burada yakalanmalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
