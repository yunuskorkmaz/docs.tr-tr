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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091325"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme
Çoğu durumda, dosya yinelemesi kolayca paralelleştirilmiş bir işlemdir. [Nasıl yapılır: dosya dizinlerini PLINQ Ile yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) , bu görevi birçok senaryo için yapmanın en kolay yolunu gösterir. Ancak, kodunuzun dosya sistemine erişirken ortaya çıkabilecek çok sayıda özel durum türüyle uğraşmak gerektiğinde karmaşıklıklar ortaya çıkabilir. Aşağıdaki örnek, soruna yönelik bir yaklaşımı gösterir. Belirtilen bir dizin altındaki tüm dosya ve klasörleri çapraz bir şekilde geçirmek için yığın tabanlı yineleme kullanır ve kodunuzun çeşitli özel durumları yakalayıp işlemesini sağlar. Kuşkusuz, özel durumları işlemenin yolu size ait olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizinleri sırayla yineler, ancak dosyaları paralel olarak işler. Bu, büyük bir dosya-dizin oranına sahip olduğunuzda en iyi yaklaşımdan kaynaklanıyor olabilir. Ayrıca, Dizin yinelemesi paralel hale getirmek ve her dosyaya sıralı olarak erişebilirsiniz. Özellikle çok sayıda işlemciye sahip bir makineyi hedefliyorsanız, her iki döngüden paralel hale getirmek için de verimli değildir. Ancak, her durumda olduğu gibi, en iyi yaklaşımı belirleyebilmek için uygulamanızı iyice test etmelisiniz.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Bu örnekte, g/ç dosyası eşzamanlı olarak gerçekleştirilir. Büyük dosyalarla veya yavaş ağ bağlantılarıyla ilgilenirken, dosyalara zaman uyumsuz olarak erişmek tercih edilebilir. Zaman uyumsuz g/ç tekniklerini paralel yineleme ile birleştirebilirsiniz. Daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Örnek, işlenen toplam dosya sayısının sayısını korumak için yerel `fileCount` değişkenini kullanır. Birden çok görev tarafından aynı anda erişilebilir olabileceğinden, <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi çağırarak bu değişkene erişim eşitlenir.  
  
 Ana iş parçacığında bir özel durum oluşturulursa, <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi tarafından başlatılan iş parçacıklarının çalışmaya devam edebileceğini unutmayın. Bu iş parçacıklarını durdurmak için özel durum İşleyicileriniz içinde bir Boole değişkeni ayarlayabilir ve paralel döngünün her yinelemesinde değerini kontrol edebilirsiniz. Değer bir özel durumun yapıldığını gösteriyorsa, döngüyü durdurmak veya kesmek için <xref:System.Threading.Tasks.ParallelLoopState> değişkenini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: bir Parallel. for döngüsü durdurma veya kesme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
