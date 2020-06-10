---
title: İş parçacıkları ve iş parçacığı oluşturmayı kullanma
description: .NET ' te iş parçacıklarını ve iş parçacığını kullanma hakkında bilgi edinin. bu sayede, aynı anda (çoklu iş parçacıklı) birçok işlem gerçekleştirmek için uygulama yazabilirsiniz.
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: c092994818c9105a555acaf63ceba4b8e99bcada
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663037"
---
# <a name="using-threads-and-threading"></a>İş parçacıkları ve iş parçacığı oluşturmayı kullanma

.NET ile aynı anda birden çok işlem gerçekleştiren uygulamalar yazabilirsiniz. Diğer işlemleri tutan potansiyel işlemler, çok iş *parçacıklı* veya *ücretsiz iş parçacığı*olarak bilinen bir işlem olan ayrı iş parçacıklarında çalıştırılabilir.  
  
İş parçacığı kullanan uygulamalar, kullanıcı girdisine daha fazla yanıt verir, çünkü kullanıcı arabirimi ayrı iş parçacıklarında yürütülen işlemci yoğun görevler olarak etkin kalır. Çoklu iş parçacığı, ölçeklenebilir uygulamalar oluşturduğunuzda da yararlıdır, çünkü iş yükü arttıkça iş parçacığı ekleyebilirsiniz.

> [!NOTE]
> Uygulamanın iş parçacıklarının davranışı üzerinde daha fazla denetime ihtiyacınız varsa, iş parçacıklarını kendiniz yönetebilirsiniz. Ancak, .NET Framework 4 ' ten itibaren, çok iş parçacıklı programlama, <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları, [paralel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), ad alanındaki yeni eşzamanlı koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ve iş parçacıkları yerine görev kavramını temel alan yeni bir programlama modeli ile büyük ölçüde basitleştirilmiştir. Daha fazla bilgi için bkz. [paralel programlama](../parallel-programming/index.md) ve [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Nasıl yapılır: yeni bir iş parçacığı oluşturma ve başlatma

Sınıfın yeni bir örneğini oluşturarak <xref:System.Threading.Thread?displayProperty=nameWithType> ve oluşturucuya yeni bir iş parçacığında yürütmek istediğiniz yöntemin adını sağlayarak yeni bir iş parçacığı oluşturursunuz. Oluşturulan bir iş parçacığını başlatmak için yöntemini çağırın <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> . Daha fazla bilgi ve örnek için, [Başlangıç zamanında iş parçacığı oluşturma ve veri geçirme](creating-threads-and-passing-data-at-start-time.md) makalesinde ve API Başvurusu ' na bakın <xref:System.Threading.Thread> .

## <a name="how-to-stop-a-thread"></a>Nasıl yapılır: iş parçacığını durdurma

Bir iş parçacığının yürütülmesini sonlandırmak için öğesini kullanın <xref:System.Threading.CancellationToken?displayProperty=nameWithType> . İş parçacıklarını birlikte durdurmak için birleştirilmiş bir yol sağlar. Daha fazla bilgi için bkz. [yönetilen iş parçacıklarında iptal](cancellation-in-managed-threads.md).

Bazen iş parçacığı işbirliği yapmak mümkün değildir, çünkü birlikte çalışma iptali için tasarlanmamış üçüncü taraf kodu çalıştırır. Bu durumda, yürütmesini zorla sonlandırmak isteyebilirsiniz. Bir iş parçacığının yürütülmesini zorla sonlandırmak için .NET Framework ' de <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemini kullanabilirsiniz. Bu yöntem <xref:System.Threading.ThreadAbortException> , üzerinde çağrıldığında bir iş parçacığı oluşturur. Daha fazla bilgi için bkz. [iş parçacıklarını yok](destroying-threads.md)etme. <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Yöntem .NET Core 'da desteklenmez. .NET Core 'da üçüncü taraf kod yürütmeyi zorla sonlandırmak isterseniz, ayrı bir işlemde çalıştırın ve kullanın <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType> .

<xref:System.Threading.CancellationToken?displayProperty=nameWithType>.NET Framework 4 ' den önce kullanılamaz. Eski .NET Framework sürümlerindeki bir iş parçacığını durdurmak için, iş parçacığı eşitleme tekniklerini kullanarak el ile yapılan iptali el ile uygulamalısınız. Örneğin, geçici Boole alanını oluşturabilir `shouldStop` ve bunu durdurulacak iş parçacığı tarafından yürütülen kodu istemek için kullanabilirsiniz. Daha fazla bilgi için bkz. C# başvurusu ve içindeki [volatile](../../csharp/language-reference/keywords/volatile.md) <xref:System.Threading.Volatile?displayProperty=nameWithType> .

<xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>Çağıran iş parçacığını durdurulan iş parçacığının sonlandırmasını beklemek için yöntemini kullanın.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Nasıl yapılır: iş parçacığını duraklatma veya kesme

<xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>Geçerli iş parçacığını belirli bir süre için duraklatmak üzere yöntemini kullanırsınız. Yöntemini çağırarak engellenen bir iş parçacığını kesintiye getirebilirsiniz <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> . Daha fazla bilgi için bkz. [iş parçacıklarını duraklatma ve kesme](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>İş parçacığı özellikleri

Aşağıdaki tabloda bazı <xref:System.Threading.Thread> Özellikler sunulmaktadır:  
  
|Özellik|Açıklama|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|`true`Bir iş parçacığının başlatılmış olması ve henüz normal olarak sonlandırılıp durdurulmadığından, döndürür.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Bir iş parçacığının arka plan iş parçacığı olup olmadığını gösteren bir Boole değeri alır veya ayarlar. Arka plan iş parçacıkları, ön plan iş parçacıkları gibidir, ancak arka plan iş parçacığı bir işlemin durdurulmasına engel olmaz. Bir işleme ait olan tüm ön plan iş parçacıkları durduktan sonra, ortak dil çalışma zamanı, <xref:System.Threading.Thread.Abort%2A> etkin olan arka plan iş parçacıklarında yöntemini çağırarak işlemi sonlandırır. Daha fazla bilgi için bkz. [ön plan ve arka plan Iş parçacıkları](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Bir iş parçacığının adını alır veya ayarlar. Hata ayıkladığınızda bireysel iş parçacıklarını saptamak için en sık kullanılan.|  
|<xref:System.Threading.Thread.Priority%2A>|<xref:System.Threading.ThreadPriority>İş parçacığı zamanlamasını önceliklendirmek için işletim sistemi tarafından kullanılan bir değeri alır veya ayarlar. Daha fazla bilgi için bkz. [iş parçacıklarını](scheduling-threads.md) ve <xref:System.Threading.ThreadPriority> başvuruyu zamanlama.|  
|<xref:System.Threading.Thread.ThreadState%2A>|<xref:System.Threading.ThreadState>Bir iş parçacığının geçerli durumlarını içeren bir değer alır.|  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Paralel programlama](../parallel-programming/index.md)
