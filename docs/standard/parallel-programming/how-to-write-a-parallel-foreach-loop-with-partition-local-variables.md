---
title: 'Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. ForEach Döngüsü Yazma'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
ms.openlocfilehash: cca48889670c3bd67366c879ccede94c89542c8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139690"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. ForEach Döngüsü Yazma

Aşağıdaki örnek, Bölüm yerel değişkenleri kullanan bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> yönteminin nasıl yazılacağını gösterir. <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsü yürütüldüğünde, kaynak koleksiyonunu birden çok bölüme böler. Her bölümün, Bölüm yerel değişkeninin kendi kopyası vardır. Bölüm yerel değişkeni, birden çok bölümün tek bir iş parçacığında çalıştırılabilmesi dışında, [iş parçacığı yerel değişkenine](xref:System.Threading.ThreadLocal%601)benzer.

Bu örnekteki kod ve parametreler karşılık gelen <xref:System.Threading.Tasks.Parallel.For%2A> yöntemine benzer. Daha fazla bilgi için bkz. [nasıl yapılır: Iş parçacığı yerel değişkenleriyle bir Parallel. for döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

<xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsünde bölüm yerel değişkenini kullanmak için, iki tür parametresi alan aşırı yüklerden birini çağırmanız gerekir. İlk tür parametresi `TSource`, kaynak öğenin türünü ve ikinci tür parametresini `TLocal`, Bölüm yerel değişkeninin türünü belirtir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, 1.000.000 öğelerinden oluşan bir dizi toplamını hesaplamak için <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> aşırı yüklemeyi çağırır. Bu aşırı yüklemede dört parametre bulunur:

- veri kaynağı olan `source`. <xref:System.Collections.Generic.IEnumerable%601>gerçekleştirmelidir. Örneğimizdeki veri kaynağı, <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> yöntemi tarafından döndürülen 1.000.000 üyesi `IEnumerable<Int32>` nesnesidir.

- `localInit`veya bölüm yerel değişkenini Başlatan işlev. Bu işlev, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> işleminin çalıştırıldığı her bölüm için bir kez çağrılır. Örneğimiz, Bölüm yerel değişkenini sıfır olarak başlatır.

- döngünün her yinelemesinde paralel döngü tarafından çağrılan bir <xref:System.Func%604> `body`. İmzası `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Temsilci için kod sağlarsınız ve döngü giriş parametrelerinde geçirilir ve şu şekilde olur:

  - <xref:System.Collections.Generic.IEnumerable%601>geçerli öğesi.

  - Döngünün durumunu incelemek için temsilcinin kodunda kullanabileceğiniz bir <xref:System.Threading.Tasks.ParallelLoopState> değişkeni.

  - Bölüm yerel değişkeni.

  Temsilciniz bölüm yerel değişkenini döndürür, daha sonra bu belirli bölümde yürütülen döngünün bir sonraki yinelemesine geçirilir. Her döngü bölümü, bu değişkenin ayrı bir örneğini tutar.

  Örnekte, temsilci her bir tamsayının değerini bölüm yerel değişkenine ekler ve bu, söz konusu bölümdeki tamsayı öğelerinin çalışan toplam değerlerini tutar.

- `localFinally`, her bölümdeki döngü işlemleri tamamlandığında <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> çağıran bir `Action<TLocal>` temsilcisi. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemi, bu döngü bölümünün bölüm yerel değişkeninin son değeri olan `Action<TLocal>` temsilcinizi geçirir ve sonucu bu bölümden birleştirmek için gerekli eylemi gerçekleştiren kodu diğer bölüme. Bu temsilci birden çok görev tarafından eşzamanlı olarak çağrılabilir. Bu nedenle örnek, `total` değişkenine erişimi eşzamanlı hale getirmek için <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> yöntemini kullanır. Temsilci türü bir <xref:System.Action%601>olduğundan, dönüş değeri yok.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
