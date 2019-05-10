---
title: Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d8319424c82327fd9743c573846663bdd76ed1b9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644621"
---
# <a name="managed-threading-best-practices"></a>Yönetilen iş parçacığı oluşturma en iyi yöntemleri
Çoklu iş parçacığı kullanımı dikkatli programlama gerektirir. Çoğu görevler için istediğiniz karmaşıklık yürütme için sıraya alma istekleri tarafından iş parçacığı havuzu iş parçacıkları tarafından azaltabilirsiniz. Birden çok iş parçacığı çalışması koordine veya işleme iş parçacıkları bu blok gibi durumlarda daha zor, bu konuda ele alır.  
  
> [!NOTE]
> .NET Framework 4 ile başlayarak, görev paralel kitaplığı ve PLINQ'da bazı karmaşıklığı ve çok iş parçacıklı programlama risklerini azaltmak API'leri sağlar. Daha fazla bilgi için [.NET paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış durumları  
 Çoklu iş parçacığı kullanımı, aktarım hızı ve yanıt hızını sorunları çözer, ancak bunun yapılması yeni sorunlar sunar: Kilitlenmeler ve yarış durumları.  
  
### <a name="deadlocks"></a>Kilitlenmeler  
 Her iki iş parçacığı diğer zaten kilitli bir kaynak kilitlemek çalıştığında bir kilitlenme oluşur. Her iki iş parçacığı herhangi bir gelişme yapabilirsiniz.  
  
 Yönetilen iş parçacığı sınıfların birçok yöntem zaman aşımlarını kilitlenmeleri algılamanıza yardımcı olarak sağlayın. Örneğin, aşağıdaki kodu adlı bir nesne üzerinde kilit çalışır `lockObject`. Kilit 300 milisaniye cinsinden alınıyorsa değil, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Yarış durumları  
 Bir yarış durumu bir program sonucu, iki veya daha fazla iş parçacıklarının belirli bir kod bloğunun ilk ulaştığında üzerinde bağlı olduğunda oluşan bir hatadır. Birden çok kez programı çalıştırmaya farklı sonuçlar üretir ve herhangi belirli çalıştırma sonucu tahmin edilemez.  
  
 Bir alan artan bir yarış durumu basit bir örneği. Özel bir sınıf sahip olduğunu varsayın **statik** alan (**paylaşılan** Visual Basic'te) gibi kod kullanarak bir sınıf örneği oluşturulduğunda artırılır `objCt++;` (C#) veya `objCt += 1` () Visual Basic). Bu işlem değerinden yükleniyor gerektirir `objCt` artan bir yazmacına değerini ve de depolamak `objCt`.  
  
 Çok iş parçacıklı bir uygulamada, tüm üç adımı gerçekleştirir başka bir iş parçacığı tarafından yüklenen ve değer artan bir iş parçacığı etkisiz hale; ilk iş parçacığında yürütmeyi devam ettirir ve değerini depolar, üzerine yazar `objCt` değeri bu arada değişti gerçeği göz önüne almadan.  
  
 Bu belirli bir yarış durumu yöntemleri kullanılarak kolayca önlenmiş <xref:System.Threading.Interlocked> gibi sınıf <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Birden çok iş parçacığı arasında veri eşitlemek için diğer teknikler hakkında bilgi için bkz [çoklu iş parçacığı kullanımı için veri eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Birden çok iş parçacığı etkinliklerini eşitlediğinizde yarış durumları da meydana gelebilir. Bir satır kod yazdığınızda, ne olacağını dikkate almanız gereken bir iş parçacığı etkisiz satırı yürütülmeden önce (veya herhangi bir satır yukarı olun tek makine yönergelerine önce) ve başka bir iş parçacığı, taşıyorduysa.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeleri ve statik oluşturucular  
 Bir sınıf kendi sınıf oluşturucusunda kadar başlatılmadı (`static` C# ' ta, Oluşturucuda `Shared Sub New` Visual Basic'te) çalışması sona erdi. Başlatılmamış bir tür üzerinde kodun yürütülmesini önlemek için ortak dil çalışma zamanı için diğer iş parçacıklarından tüm çağrıları engeller `static` sınıf üyeleri (`Shared` üyeleri Visual Basic'te) kadar sınıf oluşturucu çalışması sona erdi.  
  
 Örneğin yeni bir iş parçacığı sınıf oluşturucusunu başlatır ve iş parçacığı yordamı çağıran bir `static` üye sınıfının, sınıf oluşturucusu tamamlanıncaya kadar yeni bir iş parçacığını engeller.  
  
 Bu olabilir herhangi bir tür için geçerli bir `static` Oluşturucusu.  

## <a name="number-of-processors"></a>İşlemci sayısı

Kullanılabilir olup olmadığını birden çok işlemci veya tek bir işlemci bir sistemde çok iş parçacıklı mimarisi etkileyebilir. Daha fazla bilgi için [numarası, işlemci](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).

Kullanım <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> özelliği çalışma zamanında kullanılabilir işlemci sayısını belirlemek için.
  
## <a name="general-recommendations"></a>Genel öneriler  
 Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Kullanmayın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> diğer iş parçacıklarını sonlandırma için. Çağırma **iptal** iş parçacığı, hangi iş parçacığı noktası bilmeden, işleme ulaştığını bir özel durum yakındır başka bir iş parçacığında olduğu.  
  
- Kullanmayın <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> birden çok iş parçacığı etkinliklerini eşitlenecek. Kullanma <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.Monitor>.  
  
- Programınızdan (örneğin, olayları kullanarak) ana çalışan iş parçacıklarının yürütülmesini denetlemek yok. Bunun yerine, çalışan iş parçacıkları iş kullanılabilir hale gelene kadar bekleyen, yürütme ve işiniz bittiğinde, programınız diğer bölümlerini bildiren sorumlu olacak şekilde, programınız tasarlayın. İş parçacıklarını engellemez iş parçacığı havuzu iş parçacıkları kullanmayı düşünün. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> Burada blok çalışan iş parçacıkları durumlarda yararlı olur.  
  
- Türleri kilit nesneler olarak kullanmayın. Diğer bir deyişle, kod gibi önlemek `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic veya kullanımını <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ile <xref:System.Type> nesneleri. Verilen tür için yalnızca bir örneği var. <xref:System.Type?displayProperty=nameWithType> her uygulama etki alanı. Bir kilidi almak tür genel ise, kendi dışındaki kod kilitleri üzerinde kilitlenmeler için önde gelen alabilir. Ek sorunlar için bkz: [güvenilirlik en iyi yöntemleri](../../../docs/framework/performance/reliability-best-practices.md).  
  
- Örneğin örneklerinde kilitleme dikkatli `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te. Diğer kod uygulamanızın türü için dış nesne üzerinde bir kilit alırsa, kilitlenmeleri oluşabilir.  
  
- İzleyici olsa da iş parçacığı bir özel durum oluşursa bile bir izleyici her zaman geçtiğini bir iş parçacığı bu izleyiciyi bırakır emin olun. C# [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi sağlamak bu davranışı otomatik olarak kullanan bir **son** emin olmak için blok <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> olduğu çağrılır. Garanti edemez, **çıkış** çağrılır, kullanılacak tasarımınızı değiştirmeyi göz önünde bulundurun **Mutex**. Bir mutex, şu anda sahip iş parçacığı sonlandığında otomatik olarak yayımlanır.  
  
- Birden çok iş parçacığı farklı kaynakları gerektiren görevler için kullanabilir ve tek bir kaynak için birden çok iş parçacığı atamaktan kaçının. Örneğin, g/ç ile ilgili herhangi bir görev kendi iş parçacığı, çünkü iş parçacığı g/ç işlemleri sırasında engelleyin ve bu nedenle diğer iş parçacıklarını yürütmek izin kalmamasını fayda sağlar. Kullanıcı girişi adanmış bir iş parçacığından yarar başka bir kaynaktır. Tek işlemcili bir bilgisayarda, yoğun hesaplama içeren bir görev ve g/ç gerektiren görevleri kullanıcı girişi ile bir arada, ancak birden fazla hesaplama açısından yoğun görevleri birbiriyle azaltması.  
  
- Yöntemlerini kullanmayı <xref:System.Threading.Interlocked> sınıf yerine basit durum değişiklikleri için `lock` deyimi (`SyncLock` Visual Basic'te). `lock` Deyimi, iyi bir genel amaçlı araçtır ancak <xref:System.Threading.Interlocked> sınıfı atomik güncelleştirmeleri için daha iyi performans sağlar. Dahili olarak, hiçbir Çekişme varsa tek kilit önek yürütür. Kod gözden geçirmeleri, kod, aşağıdaki örneklerde gösterildiği gibi izleyin. İlk örnekte, bir durum değişkeninin artırılır:  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     Kullanarak performansı artırabilirsiniz <xref:System.Threading.Interlocked.Increment%2A> yöntemi yerine `lock` aşağıdaki gibi bir deyimi:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2.0 ve sonraki sürümlerinde, kullanın <xref:System.Threading.Interlocked.Add%2A> yöntemi için 1'den daha büyük atomik artırır.  
  
     Yalnızca bir null başvuru ise ikinci örnekte, bir başvuru türü değişkeni güncelleştirilir (`Nothing` Visual Basic'te).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     Performansı geliştirilmiş kullanarak <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi bunun yerine, şu şekilde:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2.0 ile başlayarak <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> yöntemi aşırı yüklemesi, başvuru türleri için tür kullanımı uyumlu bir alternatif sağlar.
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Sınıf kitaplıkları için tasarlarken aşağıdaki yönergeleri göz önünde bulundurun çoklu iş parçacığı kullanımı:  
  
- Eşitleme için gereken mümkün olduğunda kaçının. Bu, özellikle yoğun olarak kullanılan kod için geçerlidir. Örneğin, bir algoritma yerine bir yarış durumu tolere bunu ortadan kaldırmak için ayarlanmış. Gereksiz eşitleme performansı azaltır ve kilitlenmeler ve yarış durumları olasılığını oluşturur.  
  
- Statik veri olun (`Shared` Visual Basic'te) varsayılan olarak güvenli iş parçacığı.  
  
- Örnek veri iş parçacığı, varsayılan olarak güvenli yapmayın. İş parçacığı açısından güvenli kod oluşturmak için kilit ekleme performansınızın, kilit çakışması artırır ve kilitlenmeleri gerçekleşmesi için olasılığını oluşturur. Ortak uygulama modellerini aynı anda yalnızca bir iş parçacığının iş parçacığı güvenliği gereksinimini en aza indirir, kullanıcı kodu yürütür. Bu nedenle, .NET Framework sınıf kitaplıkları, varsayılan olarak güvenli iş parçacığı değildir.  
  
- Statik durumu alter statik yöntemler sağlayan kaçının. Senaryoları sunucusu, birden çok iş parçacığı aynı anda kod yürütebilir anlamına gelir statik durumu istekler arasında paylaşılır. Bu hataların iş parçacığı oluşturma olasılığını açar. İstekler genelinde paylaşılmaz örnekleri içine veri kapsülleyen bir tasarım desenini kullanarak göz önünde bulundurun. Ayrıca, statik veri eşitlenmişse durumu alter statik yöntemler arasındaki çağrıların kilitlenmeleri veya performansını olumsuz yönde etkileyen yedekli eşitleme neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
