---
title: İş parçacıkları ve iş parçacığı oluşturmayı kullanma
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 14159ff9a6ca39108aec14b0ad46004e95fa3cf2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588426"
---
# <a name="using-threads-and-threading"></a>İş parçacıkları ve iş parçacığı oluşturmayı kullanma

.NET ile, aynı anda birden çok işlem gerçekleştiren uygulamalar yazabilirsiniz. Diğer işlemleri tutma potansiyeline sahip işlemler ayrı iş parçacıkları, *çok iş parçacığı* veya *serbest iş parçacığı*olarak bilinen bir işlem üzerinde yürütülebilir.  
  
İşlemci yoğun görevler ayrı iş parçacıkları üzerinde yürütülürken, kullanıcı arabirimi etkin kaldığından, çoklu iş parçacığı kullanan uygulamalar kullanıcı girişine daha duyarlıdır. İş yükü arttıkça iş parçacığı ekleyebilirsiniz, çünkü ölçeklenebilir uygulamalar oluştururken multithreading de yararlıdır.

> [!NOTE]
> Uygulamanın iş parçacıklarının davranışı üzerinde daha fazla denetime ihtiyacınız varsa, iş parçacıklarını kendiniz yönetebilirsiniz. Ancak, .NET Framework 4 ile başlayarak, çok iş parçacığı <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> programlama <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> büyük ölçüde ve sınıflar, [Paralel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanında yeni eşzamanlı toplama sınıfları ve iş parçacığı yerine görev kavramına dayalı yeni bir programlama modeli ile basitleştirilmiştir. Daha fazla bilgi için bkz: [Paralel Programlama](../parallel-programming/index.md) ve Görev [Paralel Kitaplığı (TPL).](../parallel-programming/task-parallel-library-tpl.md)

## <a name="how-to-create-and-start-a-new-thread"></a>Nasıl yapılsın: Yeni bir iş parçacığı oluşturma ve başlatma

<xref:System.Threading.Thread?displayProperty=nameWithType> Sınıfın yeni bir örneğini oluşturarak ve yeni bir iş parçacığı üzerinde çalıştırmak istediğiniz yöntemin adını oluşturarak yeni bir iş parçacığı oluşturursunuz. Oluşturulan bir iş parçacığı <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> başlatmak için yöntemi arayın. Daha fazla bilgi ve örnek için, başlangıç zamanı makalesinde <xref:System.Threading.Thread> ve API başvurusunda veri oluşturma ve [veri aktarın.](creating-threads-and-passing-data-at-start-time.md)

## <a name="how-to-stop-a-thread"></a>Nasıl yapilir: İş parçacığı durdurma

Bir iş parçacığının yürütülmesini <xref:System.Threading.CancellationToken?displayProperty=nameWithType>sonlandırmak için, . İş parçacığı ortak durdurmak için birleşik bir yol sağlar. Daha fazla bilgi için yönetilen [iş parçacıklarında İptal'e](cancellation-in-managed-threads.md)bakın.

Bazen bir iş parçacığının kooperatif iptali için tasarlanmadığından, iş parçacığının ortaklaşa durdurulması mümkün değildir. Bu durumda, yürütmezorla sonlandırmak isteyebilirsiniz. Bir iş parçacığının yürütülmesini zorla sonlandırmak için ,.NET Framework'de <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi kullanabilirsiniz. Bu yöntem, <xref:System.Threading.ThreadAbortException> çağrıldığı iş parçacığı üzerinde bir yükseltir. Daha fazla bilgi için [bkz.](destroying-threads.md) Yöntem <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> .NET Core'da desteklenmez. Üçüncü taraf kodunun yürütülmesini .NET Core'da zorla sonlandırmanız gerekiyorsa, bunu ayrı <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>bir işlemde çalıştırın ve kullanın.

.NET <xref:System.Threading.CancellationToken?displayProperty=nameWithType> Framework 4'ten önce kullanılamaz. Eski .NET Framework sürümlerinde bir iş parçacığı durdurmak için, iş parçacığı eşitleme tekniklerini kullanarak iş parçacığı iptalini el ile uygulamanız gerekir. Örneğin, uçucu boolean alanını `shouldStop` oluşturabilir ve iş parçacığı tarafından yürütülen kodu durdurmak için istemek için kullanabilirsiniz. Daha fazla bilgi [volatile](../../csharp/language-reference/keywords/volatile.md) için C# <xref:System.Threading.Volatile?displayProperty=nameWithType>Reference ve .

Arama <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> iş parçacığının durdurulduğu iş parçacığının sonlandırılmasını beklemesini sağlamak için yöntemi kullanın.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Nasıl yapilir: İş parçacığı duraklatma veya kesme

Geçerli iş <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> parçacığı belirli bir süre için duraklatmak için yöntemi kullanın. <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> Yöntemi arayarak engellenen bir iş parçacığı kesebilirsiniz. Daha fazla bilgi için [bkz.](pausing-and-resuming-threads.md)

## <a name="thread-properties"></a>İş parçacığı özellikleri

Aşağıdaki tablo bazı <xref:System.Threading.Thread> özellikleri sunar:  
  
|Özellik|Açıklama|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Bir `true` iş parçacığı başlatıldıysa ve henüz normal olarak sonlandırılmadıysa veya iptal edildiyse döndürür.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Bir iş parçacığının arka plan iş parçacığı olup olmadığını gösteren bir Boolean alır veya ayarlar. Arka plan iş parçacıkları ön plan iş parçacıkları gibidir, ancak arka plan iş parçacığı bir işlemin durmasını engellemez. Bir işleme ait tüm ön plan iş parçacıkları durdurulduktan sonra, ortak dil <xref:System.Threading.Thread.Abort%2A> çalışma süresi hala canlı olan arka plan iş parçacıkları üzerinde yöntem çağırarak işlemi sona erdirer. Daha fazla bilgi için [Foreground ve Background Threads'e](foreground-and-background-threads.md)bakın.|  
|<xref:System.Threading.Thread.Name%2A>|Bir iş parçacığının adını alır veya ayarlar. Hata ayıklama işlemini yaparken tek tek iş parçacıklarını bulmak için en sık kullanılır.|  
|<xref:System.Threading.Thread.Priority%2A>|İş parçacığı <xref:System.Threading.ThreadPriority> zamanlamasına öncelik vermek için işletim sistemi tarafından kullanılan bir değer alır veya ayarlar. Daha fazla bilgi için zamanlama iş <xref:System.Threading.ThreadPriority> [parçacıklarına](scheduling-threads.md) ve başvuruya bakın.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Bir <xref:System.Threading.ThreadState> iş parçacığının geçerli durumlarını içeren bir değer alır.|  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Paralel Programlama](../parallel-programming/index.md)
