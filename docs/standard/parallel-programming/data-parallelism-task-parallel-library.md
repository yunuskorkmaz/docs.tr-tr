---
title: Veri Paralelliği (Görev Paralel Kitaplığı)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallelism, data
ms.assetid: 3f05f33f-f1da-4b16-81c2-9ceff1bef449
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3450908cadff453df79ab8fcf10285c25dfa50a7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976232"
---
# <a name="data-parallelism-task-parallel-library"></a>Veri Paralelliği (Görev Paralel Kitaplığı)
*Veri paralelliği* senaryoları için aynı işlem gerçekleştirilir eşzamanlı olarak başvurur (diğer bir deyişle, içinde paralel) öğelerinde bir kaynak koleksiyonu veya dizi. Birden çok iş parçacığı üzerinde farklı segmentlere eşzamanlı olarak çalışabilir, böylece veri paralel işlemleri, kaynak koleksiyonu bölümlenir.  
  
 Görev paralel kitaplığı (TPL) aracılığıyla veri paralelliği destekler <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> sınıfı. Metot tabanlı paralel uygulamaları bu sınıfın sağladığı [için](~/docs/csharp/language-reference/keywords/for.md) ve [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) döngüler (`For` ve `For Each` Visual Basic'te). Döngü mantığı için yazdığınız bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sıralı döngü yazmak istediğiniz kadar döngü. İş parçacığı oluşturma veya iş öğelerini kuyruğa gerekmez. Temel Döngülerde kilitleri olması gerekmez. TPL, alt düzey işin tümünü sizin için işler. Kullanımı hakkında ayrıntılı bilgi için <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, belgeyi indirme [desenleri paralel programlama için: Anlama ve uygulama ile paralel düzenleri .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222). Aşağıdaki kod örneği basit gösterir `foreach` döngü ve paralel eşdeğeri.  
  
> [!NOTE]
>  TPL'de temsilciler tanımlamak için bu belgede lambda ifadeleri kullanılır. C# veya Visual Basic'te lambda ifadelerine aşina değilseniz bkz [PLINQ ve TPL'deki Lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
 [!code-csharp[TPL#20](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#20)]
 [!code-vb[TPL#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/tpl_vb.vb#20)]  
  
 Ne zaman paralel döngü çalıştığında, TPL bölümler veri kaynağı böylece döngü birden çok parça için de aynı anda çalışabilir. Arka planda, Görev Zamanlayıcı'yı sistem kaynakları ve iş yüküne göre görev bölümler. Mümkün olduğunda, iş yükü dengesiz hale gelirse Zamanlayıcı İş birden çok iş parçacığı ve işlemciler arasında yeniden dağıtır.  
  
> [!NOTE]
>  Ayrıca, kendi özel bölümleyici veya Zamanlayıcı sağlayabilirsiniz. Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md) ve [görev planlayıcılar](xref:System.Threading.Tasks.TaskScheduler).  
  
 Hem <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemi, durdurmak veya döngü yürütmeyi kesme, diğer iş parçacıkları üzerinde döngü durumunu izlemek, iş parçacığı-yerel durumunu korumak, iş parçacığı-yerel nesneleri sonlandırma, eşzamanlılık derecesini kontrol olanak veren çeşitli aşırı yükler vardır ve benzeri. Bu işlevselliği etkinleştirmek yardımcı türler <xref:System.Threading.Tasks.ParallelLoopState>, <xref:System.Threading.Tasks.ParallelOptions>, <xref:System.Threading.Tasks.ParallelLoopResult>, <xref:System.Threading.CancellationToken>, ve <xref:System.Threading.CancellationTokenSource>.  
  
 Daha fazla bilgi için [desenleri paralel programlama için: Anlama ve uygulama ile paralel düzenleri .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=19222).  
  
 Bildirim temelli veya sorgu benzeri sözdizimi ile veri paralelliğinin PLINQ tarafından desteklenir. Daha fazla bilgi için [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Basit bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü herhangi bir dizi üzerindeki veya dizinlenebilir <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu.|  
|[Nasıl yapılır: Basit bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-foreach-loop.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> herhangi üzerine döngü <xref:System.Collections.Generic.IEnumerable%601> kaynak koleksiyonu.|  
|[Nasıl yapılır: Durdurma veya döngüden bir Parallel.For döngüsü](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))|Durdurma veya tüm iş parçacığı eylemin bilgilendirilmesi paralel bir döngüden kurtulmak kesme açıklar.|  
|[Nasıl yapılır: İş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.For%2A> döngü her iş parçacığı diğer iş parçacıkları ve döngü tamamlandığında, tüm iş parçacıklarının sonuçlardan eşitleme için görünür değil özel bir değişken tutar.|  
|[Nasıl yapılır: Bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-partition-local-variables.md)|Nasıl yazılacağını açıklar bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü her iş parçacığı diğer iş parçacıkları ve döngü tamamlandığında, tüm iş parçacıklarının sonuçlardan eşitleme için görünür değil özel bir değişken tutar.|  
|[Nasıl yapılır: Bir Parallel.For veya ForEach döngüsünü iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-parallel-for-or-foreach-loop.md)|Paralel bir döngüden kullanarak iptal etmeyi açıklar bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType>|  
|[Nasıl yapılır: Küçük döngü gövdelerini hızlandırma](../../../docs/standard/parallel-programming/how-to-speed-up-small-loop-bodies.md)|Döngü gövdesi çok küçük olduğunda yürütme hızlandırmanın bir yolu açıklar.|  
|[Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|Görev paralel kitaplığı genel bir bakış sağlar.|  
|[Paralel Programlama](../../../docs/standard/parallel-programming/index.md)|.NET Framework'te paralel programlama tanıtır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
