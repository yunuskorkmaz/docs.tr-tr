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
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635873"
---
# <a name="how-to-cancel-a-plinq-query"></a>Nasıl yapılır: PLINQ Sorgusunu İptal Etme
Aşağıdaki örnekler, plinq sorgusunu iptal etmenin iki yolunu gösterir. İlk örnek, çoğunlukla veri geçişinden oluşan bir sorgunun nasıl iptal edilebildiğini gösterir. İkinci örnek, hesaplama olarak pahalı bir kullanıcı işlevi içeren bir sorguyu nasıl iptal ediletilir gösterir.

> [!NOTE]
> "Yalnızca Kodum" etkinleştirildiğinde, Visual Studio özel durumu atan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler. Bu hata iyi huylu. Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz. Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.
>
> Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.

## <a name="example"></a>Örnek

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

PLINQ çerçevesi tek <xref:System.OperationCanceledException> bir rulo <xref:System.AggregateException?displayProperty=nameWithType>yok; ayrı <xref:System.OperationCanceledException> bir yakalama bloğunda ele alınmalıdır. Bir veya daha fazla kullanıcı temsilcisi bir OperationCanceledException (harici CT) atar ama başka <xref:System.Threading.CancellationToken?displayProperty=nameWithType>bir özel `AsParallel().WithCancellation(externalCT)`durum, ve sorgu olarak <xref:System.OperationCanceledException> tanımlanmıştır , sonra <xref:System.AggregateException?displayProperty=nameWithType>PLINQ yerine tek bir (hariciCT) verecektir . Ancak, bir kullanıcı temsilcisi <xref:System.OperationCanceledException>bir , ve başka bir temsilci başka bir özel durum <xref:System.AggregateException>türü atar, sonra her iki özel durum bir .

İptal ile ilgili genel kılavuz aşağıdaki gibidir:

1. Kullanıcı temsilcisi iptali yaparsanız, PLINQ'yi <xref:System.Threading.CancellationToken> harici hakkında <xref:System.OperationCanceledException>bilgilendirmeli ve bir (harici CT) atmalısınız.

2. İptal oluşursa ve başka özel durumlar atılırsa, <xref:System.AggregateException>bir yerine . <xref:System.OperationCanceledException>

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanıcı kodunda hesaplama açısından pahalı bir işleviniz olduğunda iptalin nasıl işleyeceğinigösterir.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Kullanıcı kodundaki iptali işlediğinizde, sorgu <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> tanımında kullanmanız gerekmez. Ancak, sorgu performansı üzerinde <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>hiçbir <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> etkisi olmadığı ve iptalin sorgu operatörleri ve kullanıcı kodunuz tarafından gerçekleştirilmesini sağladığı için kullanmanızı tavsiye ettik.

Sistem duyarlılığını sağlamak için, iptali milisaniyede bir kez kontrol etmenizi öneririz; ancak, 10 milisaniyeye kadar olan herhangi bir dönem kabul edilebilir kabul edilir. Bu sıklığın kodunuzu performansında olumsuz bir etkisi olmamalıdır.

Bir enumerator atıldığında, örneğin sorgu sonuçları üzerinde yineleme yapan bir foreach (Visual Basic'teki her biri için) döngüsünden kod çıktığında, sorgu iptal edilir, ancak özel durum atılmaz.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
