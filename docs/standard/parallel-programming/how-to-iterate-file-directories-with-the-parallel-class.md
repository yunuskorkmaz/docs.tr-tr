---
title: 'Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1ec270159430434adc074f1fa6ca92ec3c4a455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781218"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme
Çoğu durumda, dosya yineleme kolayca paralel bir işlemdir. Konu [nasıl yapılır: PLINQ ile dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) birçok senaryo için bu görevi gerçekleştirmek için en kolay yolu gösterir. Ancak, kodunuzu türlerde dosya sistemine erişirken oluşabilecek özel durumları ile uğraşmak zorunda kaldığında zorluklar ortaya çıkabilir. Aşağıdaki örnek, sorunun bir yaklaşımı gösterir. Tüm dosya ve klasörlerin belirtilen dizinin altındaki geçirmek için bir yığın tabanlı yineleme kullanır ve catch ve çeşitli özel durumları işlemek için kodunuzu sağlar. Elbette, özel durumları işlemeye size kalmıştır yoludur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizinleri sırayla yinelenir, ancak paralel dosyaları işler. Büyük bir dosya dizini oranına sahip olduğunuzda bu büyük olasılıkla en iyi yaklaşımdır. Dizin Yineleme paralel hale getirmek ve her bir dosyanın sıralı olarak erişmek mümkündür. Bu, özellikle çok sayıda işlemciye sahip bir makine hedeflediğiniz sürece her iki döngü paralel hale getirmek için verimlidir olmayabilir. Ancak tüm durumlarda olduğu gibi kapsamlı en iyi yaklaşım belirlemek için uygulamanızı test etmeniz gerekir.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Bu örnekte, dosya g/ç zaman uyumlu olarak gerçekleştirilir. Büyük dosyaları veya yavaş ağ bağlantıları ile ilgilenirken, dosyaları zaman uyumsuz olarak erişmek için tercih edilebilir. Zaman uyumsuz g/ç teknikleri ile paralel yineleme birleştirebilirsiniz. Daha fazla bilgi için [TPL ve geleneksel .NET Framework Asynchronous Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Yerel örnek kullanan `fileCount` işlenen dosyalarının toplam sayısını sayısını korumak için değişkeni. Değişken aynı anda birden çok görev tarafından erişilebilir olduğundan erişimi çağırarak eşitlenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi.  
  
 Ana üzerinde bir özel durum oluşturulursa, iş parçacığı başlatılır iş parçacıkları unutmayın <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi çalışmaya devam. Bu iş parçacıkları durdurmak için özel durum işleyicileri Boolean değişkenini ve değerini paralel döngü her yinelemede denetleyin. Bir özel durum değeri gösterir kullanırsanız <xref:System.Threading.Tasks.ParallelLoopState> durdurma veya döngüden kesme değişkeni. Daha fazla bilgi için [nasıl yapılır: Durdurma veya döngüden bir Parallel.For döngüsü](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
