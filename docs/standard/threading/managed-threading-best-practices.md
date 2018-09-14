---
title: Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
ms.date: 11/30/2017
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
ms.openlocfilehash: f95fb3ccab7362021a7a195ea199a1370e003dd2
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619022"
---
# <a name="managed-threading-best-practices"></a>Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
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
  
## <a name="number-of-processors"></a>İşlemci sayısı  
 Çoğu bilgisayarları, tabletler ve telefonlar gibi küçük cihazları dahil birden çok işlemci (Ayrıca çekirdek olarak adlandırılır), artık var. Ayrıca tek işlemcili bilgisayarlarda, bilmeniz gerekir, çoklu iş parçacığı çalıştırılır yazılım geliştiriyor biliyorsanız tek işlemcili bilgisayarlar ve çok işlemcili bilgisayarlar için farklı sorunlarını çözer.  
  
### <a name="multiprocessor-computers"></a>Çok işlemcili bilgisayar  
 Çoklu iş parçacığı kullanımı, daha yüksek işleme düzeyi sağlar. On işlemci on kez on aynı anda çalışıyor, böylece yalnızca iş ayrılır, ancak bir iş yapabilirler. iş parçacıkları iş bölebilir ve ek işlem gücünden yararlanmak için kolay bir yol sağlar. Kullanırsanız, çok işlemcili bir bilgisayarda çoklu iş parçacığı kullanımı:  
  
-   Eşzamanlı olarak çalışabilecek iş parçacığı sayısını işlemci sayısı sınırlıdır.  
  
-   Yalnızca ön plan iş parçacığı yürütme sayısını işlemci sayısından küçük olduğunda bir arka plan iş parçacığı çalıştırır.  
  
-   Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığında iş parçacığı olabilir veya işlemci sayısını ve yürütmek için şu anda bekleyen iş parçacıklarının sayısını bağlı olarak hemen yürütme başlatılamayabilir.  
  
-   Yarış durumları, yalnızca iş parçacıkları beklenmedik bir şekilde etkisiz, ancak iki farklı yürütme iş parçacıkları olduğundan işlemcileri aynı kod bloğu ulaşmak için yarış çünkü ortaya çıkabilir.  
  
### <a name="single-processor-computers"></a>Tek İşlemcili Bilgisayar  
 Çoklu iş parçacığı kullanımı, bilgisayarın kullanıcı için daha fazla duyarlılık sağlar ve arka plan görevleri için boşta kalma süresi kullanır. Kullanıyorsanız tek işlemcili bir bilgisayarda çoklu iş parçacığı kullanımı:  
  
-   Herhangi anı yalnızca bir iş parçacığı çalıştırır.  
  
-   Arka plan iş parçacığı, yalnızca kullanıcının ana iş parçacığı boşta olduğunda çalışır. Sürekli olarak yürütülen bir ön plan iş parçacığı arka plan iş parçacıkları, işlemci zamanının starves.  
  
-   Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığı üzerinde iş parçacığı kadar geçerli iş parçacığını yürütmeye başlamaz verir veya işletim sistemi tarafından etkisiz.  
  
-   Programcı alışılmadık bir şu anda bir iş parçacığı etkisiz, olgu bazen bir kod bloğunun ilk ulaşmak başka bir iş parçacığına izin vererek beklemek yarış durumlarını genellikle oluşur.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeleri ve statik oluşturucular  
 Bir sınıf kendi sınıf oluşturucusunda kadar başlatılmadı (`static` C# ' ta, Oluşturucuda `Shared Sub New` Visual Basic'te) çalışması sona erdi. Başlatılmamış bir tür üzerinde kodun yürütülmesini önlemek için ortak dil çalışma zamanı için diğer iş parçacıklarından tüm çağrıları engeller `static` sınıf üyeleri (`Shared` üyeleri Visual Basic'te) kadar sınıf oluşturucu çalışması sona erdi.  
  
 Örneğin yeni bir iş parçacığı sınıf oluşturucusunu başlatır ve iş parçacığı yordamı çağıran bir `static` üye sınıfının, sınıf oluşturucusu tamamlanıncaya kadar yeni bir iş parçacığını engeller.  
  
 Bu olabilir herhangi bir tür için geçerli bir `static` Oluşturucusu.  
  
## <a name="general-recommendations"></a>Genel öneriler  
 Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
-   Kullanmayın <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> diğer iş parçacıklarını sonlandırma için. Çağırma **iptal** iş parçacığı, hangi iş parçacığı noktası bilmeden, işleme ulaştığını bir özel durum yakındır başka bir iş parçacığında olduğu.  
  
-   Kullanmayın <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> birden çok iş parçacığı etkinliklerini eşitlenecek. Kullanma <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.Monitor>.  
  
-   Programınızdan (örneğin, olayları kullanarak) ana çalışan iş parçacıklarının yürütülmesini denetlemek yok. Bunun yerine, çalışan iş parçacıkları iş kullanılabilir hale gelene kadar bekleyen, yürütme ve işiniz bittiğinde, programınız diğer bölümlerini bildiren sorumlu olacak şekilde, programınız tasarlayın. İş parçacıklarını engellemez iş parçacığı havuzu iş parçacıkları kullanmayı düşünün. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> Burada blok çalışan iş parçacıkları durumlarda yararlı olur.  
  
-   Türleri kilit nesneler olarak kullanmayın. Diğer bir deyişle, kod gibi önlemek `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic veya kullanımını <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ile <xref:System.Type> nesneleri. Verilen tür için yalnızca bir örneği var. <xref:System.Type?displayProperty=nameWithType> her uygulama etki alanı. Bir kilidi almak tür genel ise, kendi dışındaki kod kilitleri üzerinde kilitlenmeler için önde gelen alabilir. Ek sorunlar için bkz: [güvenilirlik en iyi yöntemleri](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Örneğin örneklerinde kilitleme dikkatli `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te. Diğer kod uygulamanızın türü için dış nesne üzerinde bir kilit alırsa, kilitlenmeleri oluşabilir.  
  
-   İzleyici olsa da iş parçacığı bir özel durum oluşursa bile bir izleyici her zaman geçtiğini bir iş parçacığı bu izleyiciyi bırakır emin olun. C# [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi sağlamak bu davranışı otomatik olarak kullanan bir **son** emin olmak için blok <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> olduğu çağrılır. Garanti edemez, **çıkış** çağrılır, kullanılacak tasarımınızı değiştirmeyi göz önünde bulundurun **Mutex**. Bir mutex, şu anda sahip iş parçacığı sonlandığında otomatik olarak yayımlanır.  
  
-   Birden çok iş parçacığı farklı kaynakları gerektiren görevler için kullanabilir ve tek bir kaynak için birden çok iş parçacığı atamaktan kaçının. Örneğin, g/ç ile ilgili herhangi bir görev kendi iş parçacığı, çünkü iş parçacığı g/ç işlemleri sırasında engelleyin ve bu nedenle diğer iş parçacıklarını yürütmek izin kalmamasını fayda sağlar. Kullanıcı girişi adanmış bir iş parçacığından yarar başka bir kaynaktır. Tek işlemcili bir bilgisayarda, yoğun hesaplama içeren bir görev ve g/ç gerektiren görevleri kullanıcı girişi ile bir arada, ancak birden fazla hesaplama açısından yoğun görevleri birbiriyle azaltması.  
  
-   Yöntemlerini kullanmayı <xref:System.Threading.Interlocked> sınıf yerine basit durum değişiklikleri için `lock` deyimi (`SyncLock` Visual Basic'te). `lock` Deyimi, iyi bir genel amaçlı araçtır ancak <xref:System.Threading.Interlocked> sınıfı atomik güncelleştirmeleri için daha iyi performans sağlar. Dahili olarak, hiçbir Çekişme varsa tek kilit önek yürütür. Kod gözden geçirmeleri, kod, aşağıdaki örneklerde gösterildiği gibi izleyin. İlk örnekte, bir durum değişkeninin artırılır:  
  
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
    >  .NET Framework sürüm 2.0 <xref:System.Threading.Interlocked.Add%2A> yöntemi 1'den daha büyük artışlarla atomik güncelleştirmeler sağlar.  
  
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
    >  .NET Framework sürüm 2.0 <xref:System.Threading.Interlocked.CompareExchange%2A> herhangi bir başvuru türü için tür açısından güvenli yerine kullanılabilecek genel bir aşırı yükleme yöntemi vardır.  
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Sınıf kitaplıkları için tasarlarken aşağıdaki yönergeleri göz önünde bulundurun çoklu iş parçacığı kullanımı:  
  
-   Eşitleme için gereken mümkün olduğunda kaçının. Bu, özellikle yoğun olarak kullanılan kod için geçerlidir. Örneğin, bir algoritma yerine bir yarış durumu tolere bunu ortadan kaldırmak için ayarlanmış. Gereksiz eşitleme performansı azaltır ve kilitlenmeler ve yarış durumları olasılığını oluşturur.  
  
-   Statik veri olun (`Shared` Visual Basic'te) varsayılan olarak güvenli iş parçacığı.  
  
-   Örnek veri iş parçacığı, varsayılan olarak güvenli yapmayın. İş parçacığı açısından güvenli kod oluşturmak için kilit ekleme performansınızın, kilit çakışması artırır ve kilitlenmeleri gerçekleşmesi için olasılığını oluşturur. Ortak uygulama modellerini aynı anda yalnızca bir iş parçacığının iş parçacığı güvenliği gereksinimini en aza indirir, kullanıcı kodu yürütür. Bu nedenle, .NET Framework sınıf kitaplıkları, varsayılan olarak güvenli iş parçacığı değildir.  
  
-   Statik durumu alter statik yöntemler sağlayan kaçının. Senaryoları sunucusu, birden çok iş parçacığı aynı anda kod yürütebilir anlamına gelir statik durumu istekler arasında paylaşılır. Bu hataların iş parçacığı oluşturma olasılığını açar. İstekler genelinde paylaşılmaz örnekleri içine veri kapsülleyen bir tasarım desenini kullanarak göz önünde bulundurun. Ayrıca, statik veri eşitlenmişse durumu alter statik yöntemler arasındaki çağrıların kilitlenmeleri veya performansını olumsuz yönde etkileyen yedekli eşitleme neden olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
