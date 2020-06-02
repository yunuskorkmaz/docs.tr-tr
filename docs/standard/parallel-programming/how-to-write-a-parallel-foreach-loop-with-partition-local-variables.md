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
ms.openlocfilehash: eff176f7c3ae5cae4c450047214d8e9e20a6e66d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290752"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Nasıl yapılır: Bölüm Yerel Değişkenleriyle bir Parallel. ForEach Döngüsü Yazma

Aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.ForEach%2A> bölüm yerel değişkenleri kullanan bir yöntemin nasıl yazılacağını gösterir. Bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yürütüldüğünde, kaynak koleksiyonunu birden çok bölüme böler. Her bölümün, Bölüm yerel değişkeninin kendi kopyası vardır. Bölüm yerel değişkeni, birden çok bölümün tek bir iş parçacığında çalıştırılabilmesi dışında, [iş parçacığı yerel değişkenine](xref:System.Threading.ThreadLocal%601)benzer.

Bu örnekteki kod ve parametreler karşılık gelen <xref:System.Threading.Tasks.Parallel.For%2A> yönteme benzer. Daha fazla bilgi için bkz. [nasıl yapılır: Iş parçacığı yerel değişkenleriyle bir Parallel. for döngüsü yazma](how-to-write-a-parallel-for-loop-with-thread-local-variables.md).

Bir döngüde bölüm yerel değişkeni kullanmak için <xref:System.Threading.Tasks.Parallel.ForEach%2A> , iki tür parametresi alan aşırı yüklerden birini çağırmanız gerekir. İlk tür parametresi, `TSource` kaynak öğenin türünü ve ikinci tür parametresini belirtir, `TLocal` bölüm yerel değişkeninin türünü belirtir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 1.000.000 öğelerinden oluşan bir dizi toplamını hesaplamak için aşırı yüklemeyi çağırır. Bu aşırı yüklemede dört parametre bulunur:

- `source`, veri kaynağıdır. Uygulaması gerekir <xref:System.Collections.Generic.IEnumerable%601> . Örneğimizde veri kaynağı, `IEnumerable<Int32>` yöntemi tarafından döndürülen 1.000.000 üye nesnesidir <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> .

- `localInit`ya da bölüm yerel değişkenini Başlatan işlev. Bu işlev, işlemin yürütüldüğü her bölüm için bir kez çağrılır <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Örneğimiz, Bölüm yerel değişkenini sıfır olarak başlatır.

- `body`, <xref:System.Func%604> döngünün her yinelemesinde paralel döngü tarafından çağrılan bir. İmzası `Func\<TSource, ParallelLoopState, TLocal, TLocal>` . Temsilci için kod sağlarsınız ve döngü giriş parametrelerinde geçirilir ve şu şekilde olur:

  - Öğesinin geçerli öğesi <xref:System.Collections.Generic.IEnumerable%601> .

  - <xref:System.Threading.Tasks.ParallelLoopState>Döngünün durumunu incelemek için temsilcinin kodunda kullanabileceğiniz bir değişken.

  - Bölüm yerel değişkeni.

  Temsilciniz bölüm yerel değişkenini döndürür, daha sonra bu belirli bölümde yürütülen döngünün bir sonraki yinelemesine geçirilir. Her döngü bölümü, bu değişkenin ayrı bir örneğini tutar.

  Örnekte, temsilci her bir tamsayının değerini bölüm yerel değişkenine ekler ve bu, söz konusu bölümdeki tamsayı öğelerinin çalışan toplam değerlerini tutar.

- `localFinally`, `Action<TLocal>` <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> her bölümdeki döngü işlemleri tamamlandığında çağıran bir temsilci. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Yöntemi, `Action<TLocal>` temsilcinizi bu döngü bölümünün bölüm yerel değişkeninin son değerine geçirir ve bu bölümden elde edilen sonucu diğer bölümlerin sonuçlarıyla birleştirmek için gerekli eylemi gerçekleştiren kodu sağlarsınız. Bu temsilci birden çok görev tarafından eşzamanlı olarak çağrılabilir. Bu nedenle, örnek, <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> değişkenine erişimi senkronize etmek için yöntemini kullanır `total` . Temsilci türü bir olduğundan <xref:System.Action%601> , dönüş değeri yok.

[!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
[!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
