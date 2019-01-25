---
title: İş parçacığı kullanma ve iş parçacığı oluşturma
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15f3aa8d2cd7c21fa2b77660cd668d211f8376a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690624"
---
# <a name="using-threads-and-threading"></a>İş parçacığı kullanma ve iş parçacığı oluşturma

.NET ile aynı anda birden çok işlem gerçekleştiren uygulamalar yazabilirsiniz. Diğer işlemlerini tutan, olası işlemleriyle olarak da bilinen bir işlem ayrı iş parçacıkları üzerinde yürütebilir *çoklu iş parçacığı kullanımı* veya *serbest iş parçacığı*.  
  
Çoklu iş parçacığı kullanımı yoğun işlemci kullanımı gerektiren görevleri yürütmek gibi kullanıcı arabirimi etkin kaldığından çünkü kullanıcı girişi için daha hızlı olan uygulamalar, iş parçacıklarını ayırın. Ölçeklenebilir uygulamalar oluşturma iş parçacıkları iş yükü arttıkça eklemek için çoklu iş parçacığı kullanımı da yararlı olur.

> [!NOTE]
> Uygulamanın iş parçacığı davranışı hakkında daha fazla denetime ihtiyacınız varsa, iş parçacıkları kendiniz yönetebilirsiniz. Ancak, .NET Framework 4 ile başlayarak, çok iş parçacıklı programlama büyük ölçüde ile basitleştirilmiştir <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfları [paralel LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md), yeni eşzamanlı koleksiyon sınıflarını içinde <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı ve iş parçacıkları yerine görevleri kavramını temel alarak yeni bir programlama modeli. Daha fazla bilgi için [paralel programlama](../parallel-programming/index.md) ve [görev paralel kitaplığı (TPL)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Nasıl yapılır: Oluşturun ve yeni bir iş parçacığı

Yeni bir örneğini oluşturarak yeni bir iş parçacığı oluşturma <xref:System.Threading.Thread?displayProperty=nameWithType> sınıf ve oluşturucu için yeni bir iş parçacığı üzerinde yürütmek istediğiniz yöntemin adını sağlama. Oluşturulan bir iş parçacığı için çağrı <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi. Daha fazla bilgi ve örnekler için bkz. [iş parçacığı oluşturma ve geçirme verilerini başlangıç zamanı](creating-threads-and-passing-data-at-start-time.md) makale ve <xref:System.Threading.Thread> API Başvurusu.

## <a name="how-to-stop-a-thread"></a>Nasıl yapılır: Bir iş parçacığı Durdur

Bir iş parçacığının yürütülmesini sonlandırmak için kullanmak <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> yöntemi. Bu yöntemi oluşturur bir <xref:System.Threading.ThreadAbortException> üzerinde çağrıldığında iş parçacığı üzerinde. Daha fazla bilgi için [iş parçacıklarını yok etme](destroying-threads.md).

Kullanabileceğiniz .NET Framework 4 ile başlayarak, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> bir iş parçacığı işbirliği içerisinde devamlılığı iptal etmek için. Daha fazla bilgi için [iş parçacıklarını işbirliği ile iptal etme](canceling-threads-cooperatively.md).

Kullanım <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> yöntemini çağıran iş parçacığını yöntemi çağrıldığında iş parçacığının sonlandırılması için bekleyin sağlamak için.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Nasıl yapılır: Duraklatma veya bir iş parçacığı kesme

Kullandığınız <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> belirtilen bir zaman miktarı için geçerli iş parçacığı duraklatmak için yöntemi. Engellenen bir iş parçacığı çağırarak engelleyebilecek <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> yöntemi. Daha fazla bilgi için [duraklatma ve iş parçacıkları engellemeden](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>İş parçacığı özellikleri

Aşağıdaki tabloda bazı sunulmaktadır <xref:System.Threading.Thread> özellikleri:  
  
|Özellik|Açıklama|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Döndürür `true` bir iş parçacığı başlatıldı ve henüz henüz olağan biçimde sona erdi veya iptal edildi.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Alır veya bir iş parçacığı bir arka plan iş parçacığı olup olmadığını belirten Boolean bir değer ayarlar. Arka plan iş parçacığı için ön plan iş parçacığı gibi olsa da, bir arka plan iş parçacığı bir işlem durdurma gelen engellemez. Bir işleme ait tüm ön plan iş parçacığı durdurduktan sonra ortak dil çalışma zamanı işlemi çağırarak sonlandırır <xref:System.Threading.Thread.Abort%2A> hala etkin olan bir arka plan iş parçacığı üzerinde yöntemi. Daha fazla bilgi için [ön plan ve arka plan iş parçacığı](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Alır veya bir iş parçacığının adını ayarlar. Tek tek iş parçacığı hata ayıklama bulmak için en sık kullanılan.|  
|<xref:System.Threading.Thread.Priority%2A>|Alır veya ayarlar bir <xref:System.Threading.ThreadPriority> iş parçacığının'zamanlama önceliğini belirlemek için işletim sistemi tarafından kullanılan bir değer. Daha fazla bilgi için [iş parçacıklarını zamanlama](scheduling-threads.md) ve <xref:System.Threading.ThreadPriority> başvuru.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Alır bir <xref:System.Threading.ThreadState> içeren bir iş parçacığı geçerli durumlarını değeri.|  

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
- [Paralel Programlama](../parallel-programming/index.md)
