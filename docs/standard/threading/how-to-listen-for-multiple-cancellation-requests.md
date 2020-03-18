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
ms.openlocfilehash: e35472040b6ee1263ebc4c4968fa1822045a2064
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138004"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme
Bu örnek, iki iptal jetonunun aynı anda nasıl dinleyeceğinigösterir, böylece belirteç isterse işlemi iptal edebilirsiniz.  
  
> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntem bir belirteç içine iki belirteçleri birleştirmek için kullanılır. Bu, belirteci bir argüman olarak sadece bir iptal belirteci almak yöntemleri geçirilebilir sağlar. Örnek, bir yöntemin hem sınıfın dışından geçirilen bir belirteci hem de sınıf içinde oluşturulan bir belirteci gözlemlemesi gereken ortak bir senaryoyu gösterir.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Bağlı belirteç bir <xref:System.OperationCanceledException>, özel durum geçirilir belirteci, önceki belirteçleri ya da bağlantılı belirteçleri atar. Belirteçlerden hangisinin iptal edildiğini belirlemek için, doğrudan öncül belirteçlerin durumunu denetleyin.  
  
 Bu örnekte, <xref:System.AggregateException> asla atılmamalıdır, ancak burada yakalanır çünkü gerçek dünya senaryolarında <xref:System.OperationCanceledException> görev temsilcisinden atılan diğer özel <xref:System.AggregateException>durumlar bir .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
