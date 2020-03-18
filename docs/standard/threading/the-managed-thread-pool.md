---
title: Yönetilen iş parçacığı havuzu
description: Arka plan alt iş parçacığı sağlayan .NET iş parçacığı havuzu hakkında bilgi edinin
ms.date: 08/02/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 2671ce7c9721b15de8a3805da27040e973a62804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400633"
---
# <a name="the-managed-thread-pool"></a>Yönetilen iş parçacığı havuzu

Sınıf, <xref:System.Threading.ThreadPool?displayProperty=nameWithType> uygulamanızı sistem tarafından yönetilen bir alt iş parçacığı havuzu sağlayarak iş parçacığı yönetimi yerine uygulama görevlerine odaklanmanızı sağlar. Arka plan işleme gerektiren kısa görevleriniz varsa, yönetilen iş parçacığı havuzu birden çok iş parçacığından yararlanmanın kolay bir yoludur. İş parçacığı havuzu iş parçacıkları üzerinde eşzamanlı görevler oluşturabileceğiniz <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> nesneler oluşturabileceğinizden, iş parçacığı havuzunun kullanımı Framework 4 ve sonraki durumlarda önemli ölçüde daha kolaydır.  
  
.NET, [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md) işlemleri, eşzamanlı G/Ç tamamlama, [zamanlayıcı](timers.md) geri aramaları, kayıtlı bekleme işlemleri, temsilci kullanan asenkron <xref:System.Net?displayProperty=nameWithType> yöntem çağrıları ve soket bağlantıları gibi birçok amaç için iş parçacığı havuzu iş parçacığı iş parçacığı kullanır.  

## <a name="thread-pool-characteristics"></a>İş parçacığı havuzu özellikleri

İş parçacığı havuzu iş parçacıkları [arka plan](foreground-and-background-threads.md) iş parçacıklarıdır. Her iş parçacığı varsayılan yığın boyutunu kullanır, varsayılan öncelikte çalışır ve çok iş parçacığı dairededir. İş parçacığı havuzundaki bir iş parçacığı görevini tamamladıktan sonra bekleyen iş parçacıkları kuyruğuna döndürülür. Şu andan itibaren yeniden kullanılabilir. Bu yeniden kullanım, uygulamaların her görev için yeni bir iş parçacığı oluşturma maliyetini önlemesini sağlar.
  
İşlem başına yalnızca bir iş parçacığı havuzu vardır.  
  
### <a name="exceptions-in-thread-pool-threads"></a>İş parçacığı havuzu iş parçacıklarındaki özel durumlar

İş parçacığı havuzu iş parçacıklarında işlenmemiş özel durumlar işlemi sonlandırır. Bu kuralın üç istisnası vardır:  
  
- A <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> çağrıldı çünkü <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> bir iş parçacığı havuzu iş parçacığı atılır.  
- Uygulama <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> etki alanı boşaltıldığından, iş parçacığı havuzu iş parçacığına A atılır.  
- Ortak dil çalışma süresi veya ana bilgisayar işlemi iş parçacığı sona erdirir.  
  
Daha fazla bilgi için [Yönetilen İş Parçacıkları'ndaki Özel Durumlar'a](exceptions-in-managed-threads.md)bakın.  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Maksimum iş parçacığı havuzu iş parçacığı sayısı

İş parçacığı havuzuna sıralan işlem sayısı yalnızca kullanılabilir bellekle sınırlıdır. Ancak, iş parçacığı havuzu aynı anda işlemde etkin olabilir iş parçacığı sayısını sınırlar. Tüm iş parçacığı havuzu iş parçacıkları meşgulse, bunları yürütmek için iş parçacıkları kullanılabilir hale geleni ek çalışma öğeleri sıraya alınır. .NET Framework 4'ten başlayarak, bir işlem için iş parçacığı havuzunun varsayılan boyutu, sanal adres alanının boyutu gibi çeşitli etkenlere bağlıdır. Bir işlem iş <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> parçacığı sayısını belirlemek için yöntemi çağırabilir.  
  
En fazla iş parçacığı sayısını <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> ve <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType> yöntemleri kullanarak kontrol edebilirsiniz.  

> [!NOTE]
> Ortak dil çalışma saatini barındıran [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) kod, yöntemi kullanarak boyutu ayarlayabilir.  
  
### <a name="thread-pool-minimums"></a>İş parçacığı havuzu minimumları

İş parçacığı havuzu, her kategori için belirli bir minimuma ulaşana kadar isteğe bağlı yeni alt iş parçacıkları veya G/Ç tamamlama iş parçacığı sağlar. Bu minimum <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> değerleri elde etmek için yöntemi kullanabilirsiniz.  
  
> [!NOTE]
> Talep düşük olduğunda, gerçek iş parçacığı havuzu iş parçacığı sayısı minimum değerlerin altına düşebilir.  
  
En aza ulaşıldığında, iş parçacığı havuzu ek iş parçacıkları oluşturabilir veya bazı görevler tamamlanana kadar bekleyebilir. .NET Framework 4'ten başlayarak, iş parçacığı havuzu, birim zaman başına tamamlanan görev sayısı olarak tanımlanan iş parçacığı oluşturma ve yok etme iş parçacığı iş parçacığı oluşturmaz ve yok eder. Çok az iş parçacığı kullanılabilir kaynakları en iyi şekilde kullanmayabilir, çok fazla iş parçacığı kaynak çekişmesini artırabilir ise.  
  
> [!CAUTION]
> En az <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> boşta kalan iş parçacığı sayısını artırmak için yöntemi kullanabilirsiniz. Ancak, gereksiz yere bu değerleri artırmak performans sorunlarına neden olabilir. Aynı anda çok fazla görev başlatılırsa, bunların tümü yavaş görünebilir. Çoğu durumda iş parçacığı havuzu iş parçacığı ayırmak için kendi algoritması ile daha iyi performans gösterecektir.  

## <a name="using-the-thread-pool"></a>İş parçacığı havuzunu kullanma

.NET Framework 4'ten başlayarak iş parçacığı havuzunu kullanmanın en kolay yolu [Görev Paralel Kitaplığı'nı (TPL)](../parallel-programming/task-parallel-library-tpl.md)kullanmaktır. Varsayılan olarak, Görevleri <xref:System.Threading.Tasks.Task> çalıştırmak <xref:System.Threading.Tasks.Task%601> için iş parçacığı havuzu iş parçacığı gibi tpl türleri ve kullanın.

İş parçacığı havuzunu, yönetilen <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> koddan (veya [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) yönetilmeyen koddan) <xref:System.Threading.WaitCallback?displayProperty=nameWithType> arayarak ve görevi gerçekleştiren yöntemi temsil eden bir temsilci yi yerek de kullanabilirsiniz.

İş parçacığı havuzunu kullanmanın başka bir yolu, <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> yöntemi kullanarak ve sinyal verildiğinde <xref:System.Threading.WaitHandle?displayProperty=nameWithType> veya zaman dolduğunda <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType> temsilci tarafından temsil edilen yöntemi çağıran bir geçiş işlemiyle ilgili iş öğelerini sıraya almaktır. İş parçacığı havuzu iş parçacıkları geri arama yöntemlerini çağırmak için kullanılır.  

Örnekler için, başvurulan API sayfalarını kontrol edin.
  
## <a name="skipping-security-checks"></a>Güvenlik denetimlerini atlama

İş parçacığı havuzu <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> da <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType> ve yöntemleri sağlar. Bu yöntemleri yalnızca, arayan yığınının sıralı görevin yürütülmesi sırasında gerçekleştirilen güvenlik denetimleri ile ilgisi olmadığından emin olduğunuzda kullanın. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType>ve <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> her ikisi de iş parçacığı bir görevi yürütmeye başladığında iş parçacığı havuzu iş parçacığı yığınıiçine birleştirilir arayan yığını, yakalayın. Güvenlik denetimi gerekiyorsa, yığının tamamının kontrol edilmesi gerekir. Kontrol güvenlik sağlasa da, aynı zamanda bir performans maliyeti de vardır.  

## <a name="when-not-to-use-thread-pool-threads"></a>İş parçacığı havuzu iş parçacığı kullanılmadığında

İş parçacığı havuzu iş parçacığı iş parçacığı kullanmak yerine kendi iş parçacığı oluşturmak ve yönetmek için uygun olan çeşitli senaryolar vardır:  
  
- Ön plan da bir iş parçacığına ihtiyacınız var.  
- Belirli bir önceliğe sahip olmak için bir iş parçacığı na ihtiyacınız var.  
- İş parçacığının uzun süre ler için engellenmesine neden olan görevleriniz vardır. İş parçacığı havuzu nun en fazla sayıda iş parçacığı vardır, bu nedenle çok sayıda engellenen iş parçacığı havuzu iş parçacığı görevleri başlatmayı engelleyebilir.  
- Tek dişli bir daire içine konuları yerleştirmek gerekir. Tüm <xref:System.Threading.ThreadPool> iş parçacıkları çok iş parçacığı dairebulunmaktadır.  
- İş parçacığıyla ilişkili kararlı bir kimliğe sahip olmanız veya bir iş parçacığının bir göreve ithaf etmesi gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Görev Paralel Kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md)
- [Nasıl yapılır: Bir Görevden Değer Döndürme](../parallel-programming/how-to-return-a-value-from-a-task.md)
- [İş Parçacığı Nesneleri ve Özellikleri](threading-objects-and-features.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Zaman Uyumsuz Dosya G/Ç](../io/asynchronous-file-i-o.md)
- [Zamanlayıcılar](timers.md)
