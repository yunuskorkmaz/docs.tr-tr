---
title: 'Nasıl yapılır: PLINQ Sorgusunu İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80dc5f72bac436d4935c1697347d588b1a302f86
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305344"
---
# <a name="how-to-cancel-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunu İptal Etme
Aşağıdaki örnekler, PLINQ sorgusunu iptal etme için iki yol gösterir. İlk örnek, çoğunlukla veri geçişini oluşan bir sorguyu iptal gösterilmektedir. İkinci örnek, hesaplama açısından pahalıdır bir kullanıcı işlevi içeren bir sorguyu iptal gösterilmektedir.  
  
> [!NOTE]
>  "Yalnızca kendi kodum" etkin olduğunda, Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler Bu hata zararsızdır. Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın. Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.  
>   
>  Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 Tek bir PLINQ framework dönmez <xref:System.OperationCanceledException> içine bir <xref:System.AggregateException?displayProperty=nameWithType>; <xref:System.OperationCanceledException> ayrı bir catch bloğu içinde işlenmesi gerekir. Bir veya daha fazla kullanıcı temsilcileri bir OperationCanceledException(externalCT) oluşturursa (Dış kullanarak <xref:System.Threading.CancellationToken?displayProperty=nameWithType>) başka bir özel durum ve sorgu olarak tanımlandı, ancak `AsParallel().WithCancellation(externalCT)`, tek bir PLINQ verecek sonra <xref:System.OperationCanceledException> (externalCT) yerine <xref:System.AggregateException?displayProperty=nameWithType>. Bir kullanıcı temsilcisi ancak oluşturur bir <xref:System.OperationCanceledException>ve başka bir özel durum türü başka bir temsilci oluşturur ve ardından her iki özel durum halinde alınacak bir <xref:System.AggregateException>.  
  
 İptal seçeneğiyle ilgili genel kılavuz aşağıdaki gibidir:  
  
1. Kullanıcı Temsilcisi iptal gerçekleştirirseniz PLINQ dış hakkında bilgilendirmek <xref:System.Threading.CancellationToken> ve throw bir <xref:System.OperationCanceledException>(externalCT).  
  
2. İptal gerçekleşirse ve başka bir özel durum oluşturulur, ardından, işleyeceğini bir <xref:System.OperationCanceledException> yerine <xref:System.AggregateException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanıcı kodunda hesaplama açısından pahalı bir işlev olduğunda iptal nasıl ele alınacağını gösterir.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Kullanıcı kodunda iptal işlediğinizde kullanın gerekmez <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu tanımı içinde. Ancak, çünkü bunu yapmanızı öneririz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi yoktur ve sorgu işleçleri ve kullanıcı kod tarafından işlenecek iptal sağlar.  
  
 Sistem yanıt hızını emin olmak için İptal milisaniyelik başına bir kez etrafında kontrol etmenizi öneririz; Ancak, herhangi bir süre 10 milisaniyeden kadar kabul edilebilir kabul edilir. Bu sıklığı kodunuzun performansı üzerinde olumsuz bir etkiye sahip olmamalıdır.  
  
 Bir numaralandırıcı, örneğin, kod, sorgu sonuçları üzerinde yineleme (For Each Visual Basic'te) foreach döngüsünün dışında keser sonra sorgu iptal edildi, ancak hiçbir özel durum.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
