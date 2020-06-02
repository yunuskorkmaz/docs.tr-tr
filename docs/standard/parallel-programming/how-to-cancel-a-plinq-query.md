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
ms.openlocfilehash: 09405a8a9f5d96d80454bcc98cbf29db54df6725
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288218"
---
# <a name="how-to-cancel-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunu İptal Etme
Aşağıdaki örneklerde PLıNQ sorgusunu iptal etmenin iki yolu gösterilmektedir. İlk örnek, çoğunlukla veri geçişi içeren bir sorgunun nasıl iptal edildiğini gösterir. İkinci örnek, hesaplama açısından pahalı olan bir Kullanıcı işlevi içeren bir sorgunun nasıl iptal edildiğini gösterir.

> [!NOTE]
> "Yalnızca kendi kodum" etkinleştirildiğinde, Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler. Bu hata zararsız. F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz. Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.
>
> Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md).

## <a name="example"></a>Örnek

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

PLıNQ çerçevesi tek bir <xref:System.OperationCanceledException> içine değil <xref:System.AggregateException?displayProperty=nameWithType> ; <xref:System.OperationCanceledException> ayrı bir catch bloğunda işlenmelidir. Bir veya daha fazla kullanıcı temsilcisi bir Operationolaydexception (externalCT) oluşturursa (harici <xref:System.Threading.CancellationToken?displayProperty=nameWithType> ), ancak başka bir özel durum yoksa ve sorgu olarak tanımlanmışsa `AsParallel().WithCancellation(externalCT)` , PLINQ, <xref:System.OperationCanceledException> bir yerine tek bir (externalCT) verir <xref:System.AggregateException?displayProperty=nameWithType> . Ancak, bir kullanıcı temsilcisi bir oluşturursa <xref:System.OperationCanceledException> ve başka bir temsilci başka bir özel durum türü oluşturursa, her iki özel durum da bir öğesine alınacaktır <xref:System.AggregateException> .

İptal etme ile ilgili genel yönergeler aşağıdaki gibidir:

1. Kullanıcı temsilcisi iptali gerçekleştirmeniz durumunda, PLıNQ ile dış hakkında bilgilendirmeniz <xref:System.Threading.CancellationToken> ve bir <xref:System.OperationCanceledException> (externalCT) oluşturmanız gerekir.

2. İptal gerçekleşirse ve başka özel durumlar yoksa, yerine bir olarak işleyin <xref:System.OperationCanceledException> <xref:System.AggregateException> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, Kullanıcı kodunda hesaplama maliyetli bir işleviniz olduğunda iptalin nasıl işleneceğini gösterir.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Kullanıcı kodunda iptali işlerken, sorgu tanımında kullanmak zorunda değilsiniz <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> . Ancak, <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> sorgu performansı üzerinde hiçbir etkisi olmadığından ve İptalin sorgu işleçleri ve Kullanıcı kodunuz tarafından işlenmesini sağladığından, kullanmanız önerilir.

Sistem yanıt verme işlemini sağlamak için, her milisaniyenin etrafında iptali denetlemeniz önerilir; Ancak, 10 milisaniyeye kadar olan tüm süreleri kabul edilebilir kabul edilir. Bu sıklık kodunuzun performansı üzerinde olumsuz bir etkiye sahip olmamalıdır.

Bir Numaralandırıcı atıldığı zaman, örneğin, sorgu sonuçları üzerinde yineleme yapan bir foreach (Visual Basic for each) döngüsünde kod kesildiğinde sorgu iptal edilir, ancak özel durum oluşturulmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
- [Yönetilen İş Parçacıklarında İptal](../threading/cancellation-in-managed-threads.md)
