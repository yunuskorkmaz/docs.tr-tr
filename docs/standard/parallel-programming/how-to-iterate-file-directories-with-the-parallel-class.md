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
ms.openlocfilehash: b14191d798baf458bd860c00913683f53d0a1fd8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555659"
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme
Çoğu durumda, dosya yinelemesi kolayca paralelleştirilmiş bir işlemdir. [Nasıl yapılır: dosya dizinlerini PLINQ Ile yineleme](how-to-iterate-file-directories-with-plinq.md) , bu görevi birçok senaryo için yapmanın en kolay yolunu gösterir. Ancak, kodunuzun dosya sistemine erişirken ortaya çıkabilecek çok sayıda özel durum türüyle uğraşmak gerektiğinde karmaşıklıklar ortaya çıkabilir. Aşağıdaki örnek, soruna yönelik bir yaklaşımı gösterir. Belirtilen bir dizin altındaki tüm dosya ve klasörleri çapraz bir şekilde geçirmek için yığın tabanlı yineleme kullanır ve kodunuzun çeşitli özel durumları yakalayıp işlemesini sağlar. Kuşkusuz, özel durumları işlemenin yolu size ait olur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizinleri sırayla yineler, ancak dosyaları paralel olarak işler. Bu, büyük bir dosya-dizin oranına sahip olduğunuzda en iyi yaklaşımdan kaynaklanıyor olabilir. Ayrıca, Dizin yinelemesi paralel hale getirmek ve her dosyaya sıralı olarak erişebilirsiniz. Özellikle çok sayıda işlemciye sahip bir makineyi hedefliyorsanız, her iki döngüden paralel hale getirmek için de verimli değildir. Ancak, her durumda olduğu gibi, en iyi yaklaşımı belirleyebilmek için uygulamanızı iyice test etmelisiniz.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Bu örnekte, g/ç dosyası eşzamanlı olarak gerçekleştirilir. Büyük dosyalarla veya yavaş ağ bağlantılarıyla ilgilenirken, dosyalara zaman uyumsuz olarak erişmek tercih edilebilir. Zaman uyumsuz g/ç tekniklerini paralel yineleme ile birleştirebilirsiniz. Daha fazla bilgi için bkz. [TPL ve geleneksel .NET Framework zaman uyumsuz programlama](tpl-and-traditional-async-programming.md).  
  
 Örnek, `fileCount` işlenen toplam dosya sayısının sayısını korumak için yerel değişkenini kullanır. Birden çok görev tarafından aynı anda erişilebilir olabileceğinden, yöntemi çağırarak bu değişkene erişim eşitlenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> .  
  
 Ana iş parçacığında bir özel durum oluşturulursa, yöntemi tarafından başlatılan iş parçacıklarının çalışmaya <xref:System.Threading.Tasks.Parallel.ForEach%2A> devam edebileceğini unutmayın. Bu iş parçacıklarını durdurmak için özel durum İşleyicileriniz içinde bir Boole değişkeni ayarlayabilir ve paralel döngünün her yinelemesinde değerini kontrol edebilirsiniz. Değer bir özel durumun yapıldığını gösteriyorsa, <xref:System.Threading.Tasks.ParallelLoopState> döngüyü durdurmak ya da kesmek için değişkeni kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: bir Parallel. for döngüsü durdurma veya kesme](/previous-versions/dotnet/netframework-4.0/dd460721(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
