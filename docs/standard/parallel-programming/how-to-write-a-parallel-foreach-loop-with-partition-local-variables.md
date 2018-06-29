---
title: 'Nasıl yapılır: bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma'
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
ms.openlocfilehash: edcc390014cfc70f4da4f72270c7dd53f9b9423b
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2018
ms.locfileid: "37076268"
---
# <a name="how-to-write-a-parallelforeach-loop-with-partition-local-variables"></a>Nasıl yapılır: bölüm yerel değişkenleriyle bir Parallel.ForEach döngüsü yazma
Aşağıdaki örnekte nasıl yazılacağını gösterir bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> bölüm yerel değişkenleri kullanan yöntemi. Zaman bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü yürütür, kendi kaynak koleksiyonu birden çok bölümlere ayırır. Her bölüm bölüm yerel değişken kopyasını sahiptir. Bir bölüm yerel değişken benzer bir [iş parçacığı yerel değişken](xref:System.Threading.ThreadLocal%601), birden çok bölüm tek bir iş parçacığı üzerinde çalıştırabilmeniz dışında.
  
 Bu örnekte parametreleri ve kod yakından ilgili benzer <xref:System.Threading.Tasks.Parallel.For%2A> yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: iş parçacığı yerel değişkenleriyle bir Parallel.For döngüsü yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md).  
  
 Bir bölüm yerel değişkende kullanmak için bir <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngüsü çağırmanız gerekir iki tür parametreleri alır yöntemi aşırı yüklemelerinden birini. İlk tür parametresi `TSource`, kaynak öğesi ve ikinci tür parametre türünü belirtir `TLocal`, bölüm yerel değişken türünü belirtir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çağrıları <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> bir dizi bir milyon öğelerin toplamını hesaplamak için aşırı yükleme. Bu aşırı dört parametre vardır:  
  
-   `source`, veri kaynağı değil. Uygulamanız gerekir <xref:System.Collections.Generic.IEnumerable%601>. Bizim örneğimizde veri kaynağında bir milyon üyesidir `IEnumerable<Int32>` tarafından döndürülen nesne <xref:System.Linq.Enumerable.Range%2A?displayProperty=nameWithType> yöntemi.  
  
-   `localInit`, ya da bölüm yerel değişkenini işlevi. Bu işlev, her bölüm için bir kez çağrılır <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> işlemini yürütür. Bizim örneğimizde sıfır bölüm yerel değişkene başlatır.  
  
-   `body`, bir <xref:System.Func%604> her döngü tekrarında üzerinde paralel döngü tarafından çağrılır. Kendi imzası `Func\<TSource, ParallelLoopState, TLocal, TLocal>`. Kod için temsilci sağlayın ve döngü olan giriş parametrelerinde geçirir:  
  
    -   Geçerli öğenin <xref:System.Collections.Generic.IEnumerable%601>.
  
    -   A <xref:System.Threading.Tasks.ParallelLoopState> değişken döngü durumunu incelemek için temsilcinin kodda kullanabilirsiniz.  
  
    -   Bölüm yerel değişken.  
  
     Temsilciniz sonraki döngü belirli bu bölümünde yürüten geçirilir bölüm yerel değişkeni döndürür. Her döngü bölüm bu değişken ayrı bir örneğini saklar.  
  
     Örnekte, her tamsayı değerini temsilci, çalışan bir tutar bölüm yerel değişkene ekler. Bu bölümde tamsayı öğelerinin değerlerini toplam.  
  
-   `localFinally`, bir `Action<TLocal>` , temsilci <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> her bölüm döngü işlemlerinde tamamlandığında çağırır. <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> Yöntemi geçişleri, `Action<TLocal>` Bu döngü bölümü için bölüm yerel değişkenin son değeri temsilci ve sonuçları ile bu bölümü sonucundan birleştirme için gerekli bir eylem gerçekleştirir kodu sağlayın diğer bölümler. Bu temsilci eşzamanlı olarak birden çok görev tarafından çağrılabilir. Bu nedenle, örnek kullanır <xref:System.Threading.Interlocked.Add%28System.Int32%40%2CSystem.Int32%29?displayProperty=nameWithType> erişimi eşitlemek için yöntemi `total` değişkeni. Temsilci türü olduğundan bir <xref:System.Action%601>, dönüş değeri yoktur.  
  
 [!code-csharp[TPL_Parallel#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/foreachthreadlocal.cs#04)]
 [!code-vb[TPL_Parallel#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/foreachthreadlocal.vb#04)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Nasıl yapılır: İş Parçacığı Yerel Değişkenleriyle bir Parallel.For Döngüsü Yazma](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
