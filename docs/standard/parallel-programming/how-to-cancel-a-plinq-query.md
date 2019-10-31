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
ms.openlocfilehash: 272f25d62cb63c60209be3bc54dc5e76fb30df54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134224"
---
# <a name="how-to-cancel-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunu İptal Etme
Aşağıdaki örneklerde PLıNQ sorgusunu iptal etmenin iki yolu gösterilmektedir. İlk örnek, çoğunlukla veri geçişi içeren bir sorgunun nasıl iptal edildiğini gösterir. İkinci örnek, hesaplama açısından pahalı olan bir Kullanıcı işlevi içeren bir sorgunun nasıl iptal edildiğini gösterir.

> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.
>
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Örnek

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

PLıNQ Framework <xref:System.AggregateException?displayProperty=nameWithType>tek bir <xref:System.OperationCanceledException> almaz; <xref:System.OperationCanceledException> ayrı bir catch bloğunda işlenmelidir. Bir veya daha fazla kullanıcı temsilcisi bir Operationolaydexception (externalCT) oluşturursa (dış <xref:System.Threading.CancellationToken?displayProperty=nameWithType>kullanarak), ancak başka bir özel durum yoksa ve sorgu `AsParallel().WithCancellation(externalCT)`olarak tanımlanmışsa, PLıNQ bir <xref:System.AggregateException?displayProperty=nameWithType>değil tek bir <xref:System.OperationCanceledException> (externalCT) verir. Ancak, bir kullanıcı temsilcisi bir <xref:System.OperationCanceledException>oluşturursa ve başka bir temsilci başka bir özel durum türü oluşturursa, her iki özel durum da bir <xref:System.AggregateException>alınacaktır.

İptal etme ile ilgili genel yönergeler aşağıdaki gibidir:

1. Kullanıcı temsilcisi iptali gerçekleştirmeniz durumunda, PLıNQ ' i dış <xref:System.Threading.CancellationToken> bildirmeniz ve bir <xref:System.OperationCanceledException>(externalCT) oluşturmanız gerekir.

2. İptal gerçekleşirse ve başka özel durumlar yoksa, bir <xref:System.AggregateException>yerine <xref:System.OperationCanceledException> işlemeniz gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Kullanıcı kodunda hesaplama maliyetli bir işleviniz olduğunda iptalin nasıl işleneceğini gösterir.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Kullanıcı kodunda iptali işlerken, sorgu tanımında <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> kullanmanız gerekmez. Ancak <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>, sorgu performansı üzerinde hiçbir etkisi olmadığından ve İptalin sorgu işleçleri ve Kullanıcı kodunuz tarafından işlenmesini sağladığından bunu yapmanızı öneririz.

Sistem yanıt verme işlemini sağlamak için, her milisaniyenin etrafında iptali denetlemeniz önerilir; Ancak, 10 milisaniyeye kadar olan tüm süreleri kabul edilebilir kabul edilir. Bu sıklık kodunuzun performansı üzerinde olumsuz bir etkiye sahip olmamalıdır.

Bir Numaralandırıcı atıldığı zaman, örneğin, sorgu sonuçları üzerinde yineleme yapan bir foreach (Visual Basic for each) döngüsünde kod kesildiğinde sorgu iptal edilir, ancak hiçbir özel durum oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
