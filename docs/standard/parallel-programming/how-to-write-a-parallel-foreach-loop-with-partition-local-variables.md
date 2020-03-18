---
title: 'Nasıl yapılır: Partition-local değişkenli Parallel.ForEach döngüsü yazma'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: cca48889670c3bd67366c879ccede94c89542c8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139690"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Nasıl yapılır: Partition-local değişkenli Parallel.ForEach döngüsü yazma

Aşağıdaki örnekte, bölüm-yerel değişkenleri kullanan bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemnasıl yazılalış gösterilmektedir. Bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yürütüldüğünde, kaynak koleksiyonunu birden çok bölüme böler. Her bölüm bölüm-yerel değişkenin kendi kopyasıvardır. Bir bölüm-yerel değişken, birden çok bölüm tek bir iş parçacığı üzerinde çalıştırabilirsiniz dışında bir [iş parçacığı yerel değişkenbenzerdir.](xref:System.Threading.ThreadLocal%601)

Bu örnekteki kod ve parametreler karşılık <xref:System.Threading.Tasks.Parallel.For%2A> gelen yönteme yakından benzer. Daha fazla bilgi için [bkz: Thread-Local Variables ile Parallel.For Loop yazın.](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)

Bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüde bir bölüm yerel değişkenkullanmak için, iki tür parametresini alan yöntem aşırı yüklerinden birini aramanız gerekir. İlk tür parametresi, `TSource`kaynak öğenin türünü belirtir ve ikinci tür `TLocal`parametre, bölüm-yerel değişkenin türünü belirtir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> bir milyon öğenin toplamını hesaplamak için aşırı yüklemeyi çağırır. Bu aşırı yüklemenin dört parametresi vardır:

- `source`, veri kaynağıdır. Bunu uygulamalı. <xref:System.Collections.Generic.IEnumerable%601> Örneğimizdeki veri kaynağı, yöntemle `IEnumerable<Int32>` döndürülen <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> bir milyon üye nesnedir.

- `localInit`veya bölüm-yerel değişkeni başlatlayan işlev. Bu işlev, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> işlemin yürütüldettiği her bölüm için bir kez çağrılır. Örneğimiz, bölüm-yerel değişkeni sıfıra indirir.

- `body`, <xref:System.Func%604> döngünün her yinelemesinde paralel döngü tarafından çağrılan bir döngüdür. `Func\<TSource, ParallelLoopState, TLocal, TLocal>`İmzası. Temsilci için kodu siz sağlarsınız ve döngü giriş parametrelerinde geçer:

  - Geçerli <xref:System.Collections.Generic.IEnumerable%601>öğe.

  - Döngünün durumunu incelemek için temsilcinizin kodunda kullanabileceğiniz bir <xref:System.Threading.Tasks.ParallelLoopState> değişken.

  - Bölüm-yerel değişken.

  Temsilciniz, daha sonra bu bölümü yürüten döngünün bir sonraki yinelemesine geçirilen bölüm-yerel değişkeni döndürür. Her döngü bölümü bu değişkenin ayrı bir örneğini tutar.

  Örnekte, temsilci, her bir tamsede değerini, bu bölümdeki tamsayı öğelerinin çalışan toplamını koruyan bölüm-yerel değişkene ekler.

- `localFinally`, `Action<TLocal>` her bölümdeki döngü işlemleri tamamlandığında <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> çağıran bir temsilci. Yöntem, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> bu `Action<TLocal>` döngü bölümü için bölüm-yerel değişkenin son değerini temsilcinize geçirir ve bu bölümün sonucunu diğer bölümlerin sonuçlarıyla birleştirmek için gerekli eylemi gerçekleştiren kodu sağlarsınız. Bu temsilci aynı anda birden çok görev tarafından çağrılabilir. Bu nedenle, örnek <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> `total` değişkene erişimi eşitlemek için yöntemi kullanır. Temsilci türü bir <xref:System.Action%601>olduğundan, geri dönüş değeri yoktur.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
