---
title: "Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to iterate directories
ms.assetid: 555e9f48-f53d-4774-9bcf-3e965c732ec5
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3ac1af7922e1bbd81f4dfcee256f5c8892294003
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-iterate-file-directories-with-the-parallel-class"></a>Nasıl yapılır: Paralel Sınıfla Dosya Dizinlerini Yineleme
Çoğu durumda, dosya yineleme kolayca paralel birkaç ölçeklendirin bir işlemdir. Konu [nasıl yapılır: PLINQ ile dosya dizinlerini yineleme](../../../docs/standard/parallel-programming/how-to-iterate-file-directories-with-plinq.md) birçok senaryoları için bu görevi gerçekleştirmek için en kolay yolu gösterir. Ancak, kodunuzu türlerde dosya sistemi erişirken ortaya çıkabilecek özel durumlar dağıtılacak olduğunda zorluklar ortaya çıkabilir. Aşağıdaki örnek, soruna yönelik bir yaklaşım gösterir. Tüm dosya ve klasörlerin belirtilen dizin altında çapraz geçiş için yığın tabanlı yineleme kullanır ve yakalamak ve çeşitli özel durumları işleme kodunuzu sağlar. Elbette, özel durumları işleme biçimini size bağlıdır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, dizinleri sırayla tekrarlanan ancak paralel dosyaları işler. Büyük bir dosya dizin oranı varsa, bu büyük olasılıkla en iyi yaklaşımdır. Dizin Yineleme paralel hale ve her dosya sıralı olarak erişmek mümkündür. Bu, özellikle çok sayıda işlemciye sahip bir makine hedeflediğiniz sürece her iki döngüler paralel hale verimli büyük olasılıkla değil. Ancak, tüm durumlarda olduğu gibi en iyi yaklaşımı kapsamlı olarak belirlemek için uygulamanızı test etmeniz gerekir.  
  
 [!code-csharp[TPL_Parallel#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_file.cs#08)]
 [!code-vb[TPL_Parallel#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/fileiteration08.vb#08)]  
  
 Bu örnekte, dosya g/ç zaman uyumlu olarak gerçekleştirilir. Büyük dosyaları veya yavaş ağ bağlantıları ile ilgilenirken, dosyaları zaman uyumsuz olarak erişmek için tercih edilebilir. Zaman uyumsuz g/ç teknikleri paralel yineleme ile birleştirebilirsiniz. Daha fazla bilgi için bkz: [TPL ve geleneksel .NET Framework zaman uyumsuz Programming](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
 Yerel örnek kullanan `fileCount` işlenen dosya sayısı toplam sayısını korumak için değişkeni. Değişkeni eşzamanlı olarak birden çok görev tarafından erişilen çünkü erişimi çağırarak eşitlenir <xref:System.Threading.Interlocked.Add%2A?displayProperty=nameWithType> yöntemi.  
  
 Ana bir özel durum, iş parçacığı tarafından başlatılan iş parçacığı açtıysanız <xref:System.Threading.Tasks.Parallel.ForEach%2A> yöntemi çalışmaya devam edecek. Bu iş parçacıkları durdurmak için özel durum işleyicileri Boole değişkenini ve değerini her döngü paralel üzerinde denetleyin. Bir özel durum değeri gösterir kullanırsanız <xref:System.Threading.Tasks.ParallelLoopState> durdurmak veya döngüden ayırmak değişkeni. Daha fazla bilgi için bkz: [nasıl yapılır: durdurun ya da bir Parallel.For döngüden bölün](http://msdn.microsoft.com/library/de52e4f1-9346-4ad5-b582-1a4d54dc7f7e).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
