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
ms.openlocfilehash: fda8443666d1c90b31cf02c2f925d1c89243a8e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091325"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme
Çoğu durumda, dosya yineleme kolayca paralelleştirilebilen bir işlemdir. Konu [Nasıl Olur: PLINQ ile Dosya Dizinlerini Yineleyin,](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) birçok senaryo için bu görevi gerçekleştirmenin en kolay yolunu gösterir. Ancak, kodunuzu dosya sistemine erişirken ortaya çıkabilecek özel durumlar birçok türde uğraşmak zorunda olduğunda komplikasyonlar ortaya çıkabilir. Aşağıdaki örnek, soruna bir yaklaşım gösterir. Belirli bir dizin altında tüm dosya ve klasörleri geçiş yapmak için yığın tabanlı yineleme kullanır ve kodunuzu yakalamak ve çeşitli özel durumları işlemek için sağlar. Tabii ki, istisnaları ele yolu size kalmış.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizinleri sırayla yineler, ancak dosyaları paralel olarak işler. Büyük bir dosya-dizin oranına sahip olduğunuzda bu muhtemelen en iyi yaklaşımdır. Dizin yinelemesini paralelleştirmek ve her dosyaya sırayla erişmek de mümkündür. Özellikle çok sayıda işlemciye sahip bir makineyi hedeflemediğiniz sürece, her iki döngüyü de paralelleştirmek büyük olasılıkla etkili değildir. Ancak, her durumda olduğu gibi, en iyi yaklaşımı belirlemek için uygulamanızı iyice test etmeniz gerekir.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Bu örnekte, G/Ç dosyası eşzamanlı olarak gerçekleştirilir. Büyük dosyalarla veya yavaş ağ bağlantılarıyla uğraşırken, dosyalara eşit olarak erişmek tercih edilebilir. Asynchronous G/Ç tekniklerini paralel yineleme ile birleştirebilirsiniz. Daha fazla bilgi için [TPL ve Traditional .NET Framework Asynchronous Programming'e](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)bakın.  
  
 Örnek, işlenen `fileCount` toplam dosya sayısının sayısını korumak için yerel değişkeni kullanır. Değişkene aynı anda birden çok görev le erişilebildiği için, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> bu değişkene erişim yöntemi çağırArak eşitlenir.  
  
 Ana iş parçacığına bir özel durum atılırsa, <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntem tarafından başlatılan iş parçacıklarının çalışmaya devam edebileceğini unutmayın. Bu iş parçacığı durdurmak için, özel durum işleyicileri bir Boolean değişkeni ayarlayabilir ve paralel döngü her yineleme üzerindeki değerini kontrol edebilirsiniz. Değer bir özel durum atıldığını gösteriyorsa, döngüyü <xref:System.Threading.Tasks.ParallelLoopState> durdurmak veya kırmak için değişkeni kullanın. Daha fazla bilgi için [bkz: Nasıl: Bir Parallel.For Loop'u Durdurun veya Kırın.](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100))  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
