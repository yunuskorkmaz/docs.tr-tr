---
title: 'Nasıl yapılır: Bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma'
ms.date: 06/26/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to use local state
ms.assetid: 24b10041-b30b-45cb-aa65-66cf568ca76d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9e88050cdc7e6136a928e74bf643a489bd32c00
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645322"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Nasıl yapılır: Bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma
Aşağıdaki örnek nasıl yazılacağını gösterir. bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> bölüm yerel değişkenler kullanan yöntemi. Olduğunda bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yürütür, kendi kaynak koleksiyonu birden çok bölümlere böler. Her bölüm, kendi bölümü yerel değişken kopyasına sahip olur. Bir bölüm yerel değişkene benzer bir [iş parçacığı yerel değişkeni](xref:System.Threading.ThreadLocal%601)dışında birden çok bölüm tek bir iş parçacığı üzerinde çalıştırabilirsiniz.
  
 Bu örnekte parametreleri ve kodu yakından ilgili benzer <xref:System.Threading.Tasks.Parallel.For%2A> yöntemi. Daha fazla bilgi için [nasıl yapılır: İş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Bir bölüm yerel değişkende kullanmak için bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü çağırmanız iki tür parametreleri alan yöntemi aşırı yüklemelerinden. İlk tür parametresi `TSource`, kaynak öğesi ve ikinci tür parametresi türünü belirten `TLocal`, bölüm yerel değişken türünü belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> dizi bir milyon öğelerin toplamını hesaplamak için aşırı yükleme. Bu aşırı yükleme dört parametrelere sahiptir:  
  
- `source`, veri kaynağı olan. Bunu uygulamalıdır <xref:System.Collections.Generic.IEnumerable%601>. Bir milyon üye veri kaynağı Bizim örneğimizde, `IEnumerable<Int32>` tarafından döndürülen nesne <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> yöntemi.  
  
- `localInit`, veya bölüm yerel değişkenini işlevi. Bu işlev, her bölüm için bir kez çağrılır <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> işlemini yürütür. Bizim örneğimizde, sıfır bölüm yerel değişkene başlatır.  
  
- `body`, bir <xref:System.Func%604> döngünün her yinelemesinden üzerinde paralel döngü tarafından çağrılır. Kendi imzası `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Temsilci için kod sağlayın ve döngü olan giriş parametrelerinde geçirir:  
  
    - Geçerli öğenin <xref:System.Collections.Generic.IEnumerable%601>.
  
    - A <xref:System.Threading.Tasks.ParallelLoopState> değişken Temsilcinizin kodda döngü durumunu incelemek için kullanabilirsiniz.  
  
    - Bölüm yerel değişken.  
  
     Ardından, belirli bir bölümünde yürüten döngünün sonraki yinelemesine geçirilir bölüm yerel değişken, temsilci döndürür. Her döngü bölüm bu değişkenin ayrı bir örneğini saklar.  
  
     Örnekte, her bir tamsayı değeri temsilci, çalışan bir tutar bölüm yerel değişkene ekler. Bu bölümde tamsayı öğelerin değerlerinin toplamını.  
  
- `localFinally`, bir `Action<TLocal>` , temsilci <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> döngü her bölüm işlemleri tamamladıktan sonra çağırır. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Yöntemi geçişleri, `Action<TLocal>` son değeri bu döngü bölümü için bölüm yerel değişkenin temsilci olarak seçmeyi ve bu bölüm sonuçtan sonuçlardan ile birleştirmek için gerekli bir eylem gerçekleştiren kodu sağlayın diğer bölümler. Bu temsilci, aynı anda birden çok görev tarafından çağrılabilir. Bu nedenle, örnekte <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> erişimi eşitlemek için yöntemi `total` değişkeni. Temsilci türü olduğundan bir <xref:System.Action%601>, dönüş değeri yoktur.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [Nasıl yapılır: İş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
