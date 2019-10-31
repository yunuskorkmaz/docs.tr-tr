---
title: İş parçacıkları ve iş parçacığı oluşturmayı kullanma
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 863fa565f7c107214273912a6d110b7664bffe6b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131492"
---
# <a name="using-threads-and-threading"></a>İş parçacıkları ve iş parçacığı oluşturmayı kullanma

.NET ile aynı anda birden çok işlem gerçekleştiren uygulamalar yazabilirsiniz. Diğer işlemleri tutan potansiyel işlemler, çok iş *parçacıklı* veya *ücretsiz iş parçacığı*olarak bilinen bir işlem olan ayrı iş parçacıklarında çalıştırılabilir.  
  
İş parçacığı kullanan uygulamalar, kullanıcı girdisine daha fazla yanıt verir, çünkü kullanıcı arabirimi ayrı iş parçacıklarında yürütülen işlemci yoğun görevler olarak etkin kalır. Çoklu iş parçacığı, ölçeklenebilir uygulamalar oluşturduğunuzda da yararlıdır, çünkü iş yükü arttıkça iş parçacığı ekleyebilirsiniz.

> [!NOTE]
> Uygulamanın iş parçacıklarının davranışı üzerinde daha fazla denetime ihtiyacınız varsa, iş parçacıklarını kendiniz yönetebilirsiniz. Ancak, .NET Framework 4 ' den itibaren, çok iş parçacıklı programlama, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları, [paralel LINQ (PLıNQ)](../parallel-programming/parallel-linq-plinq.md), <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanındaki yeni eşzamanlı koleksiyon sınıfları ve yeni bir programlama modeli ile büyük ölçüde basitleştirilmiştir Bu, iş parçacıkları yerine görev kavramını temel alır. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md) ve [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Nasıl yapılır: yeni bir iş parçacığı oluşturma ve başlatma

<xref:System.Threading.Thread?displayProperty=nameWithType> sınıfının yeni bir örneğini oluşturarak ve oluşturucuya yeni bir iş parçacığında yürütmek istediğiniz yöntemin adını sağlayarak yeni bir iş parçacığı oluşturursunuz. Oluşturulan bir iş parçacığını başlatmak için <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemini çağırın. Daha fazla bilgi ve örnek için, [Başlangıç zamanında iş parçacığı oluşturma ve veri geçirme](creating-threads-and-passing-data-at-start-time.md) makalesine ve <xref:System.Threading.Thread> API Başvurusu ' na bakın.

## <a name="how-to-stop-a-thread"></a>Nasıl yapılır: iş parçacığını durdurma

Bir iş parçacığının yürütülmesini sonlandırmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemini kullanın. Bu yöntem, üzerinde çağrıldığı iş parçacığında bir <xref:System.Threading.ThreadAbortException> oluşturur. Daha fazla bilgi için bkz. [iş parçacıklarını yok](destroying-threads.md)etme.

.NET Framework 4 ' ten başlayarak, bir iş parçacığını birlikte iptal etmek için <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanabilirsiniz. Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](cancellation-in-managed-threads.md).

Çağıran iş parçacığının, yöntemin çağrıldığı iş parçacığının sonlandırmasını beklemesini sağlamak için <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemini kullanın.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Nasıl yapılır: iş parçacığını duraklatma veya kesme

Geçerli iş parçacığını belirli bir süre için duraklatmak üzere <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> yöntemini kullanırsınız. Engellenen bir iş parçacığını <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemini çağırarak kesintiye getirebilirsiniz. Daha fazla bilgi için bkz. [iş parçacıklarını duraklatma ve kesme](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>İş parçacığı özellikleri

Aşağıdaki tabloda bazı <xref:System.Threading.Thread> özellikleri sunulmaktadır:  
  
|Özellik|Açıklama|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Bir iş parçacığı başlatılmışsa ve normal olarak sonlandırılırsa veya durdurulmadıysa `true` döndürür.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Bir iş parçacığının arka plan iş parçacığı olup olmadığını gösteren bir Boole değeri alır veya ayarlar. Arka plan iş parçacıkları, ön plan iş parçacıkları gibidir, ancak arka plan iş parçacığı bir işlemin durdurulmasına engel olmaz. Bir işleme ait olan tüm ön plan iş parçacıkları durdurulduğunda, ortak dil çalışma zamanı, hala etkin olan arka plan iş parçacıklarında <xref:System.Threading.Thread.Abort%2A> yöntemini çağırarak işlemi sonlandırır. Daha fazla bilgi için bkz. [ön plan ve arka plan Iş parçacıkları](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Bir iş parçacığının adını alır veya ayarlar. Hata ayıkladığınızda bireysel iş parçacıklarını saptamak için en sık kullanılan.|  
|<xref:System.Threading.Thread.Priority%2A>|İş parçacığı zamanlamasını önceliklendirmek için işletim sistemi tarafından kullanılan bir <xref:System.Threading.ThreadPriority> değeri alır veya ayarlar. Daha fazla bilgi için bkz. [iş parçacıklarını zamanlama](scheduling-threads.md) ve <xref:System.Threading.ThreadPriority> başvurusu.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Bir iş parçacığının geçerli durumlarını içeren <xref:System.Threading.ThreadState> bir değer alır.|  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Paralel Programlama](../parallel-programming/index.md)
