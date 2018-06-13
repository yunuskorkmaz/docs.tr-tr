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
ms.openlocfilehash: 15261291f40b6a41e0d6033fb92e1b23b4042019
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592476"
---
# <a name="managed-threading-best-practices"></a>Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
Çoklu iş parçacığı kullanımı dikkatli programlama gerektirir. Çoğu görevlerde, karmaşıklık yürütme için sıraya alma istekleri iş parçacığı havuzu iş parçacıkları tarafından azaltabilir. Bu konuda, birden çok iş parçacığı iş Eşgüdümleme veya iş parçacığı, blok işleme gibi daha zor durumlarda giderir.  
  
> [!NOTE]
> .NET Framework 4 ile başlayarak, görev paralel kitaplığı ve PLINQ'da bazı karmaşıklık ve çok iş parçacıklı programlama risklerini azaltmak API'ler sağlar. Daha fazla bilgi için bkz: [.NET paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış durumları  
 Çoklu iş parçacığı kullanımı üretilen iş ve yanıt hızını sorunlarını çözer, ancak bunu yaparken yeni sorunları sunar: Kilitlenmeler ve yarış durumları.  
  
### <a name="deadlocks"></a>Kilitlenmeleri  
 Her iki iş parçacığı diğer zaten kilitli bir kaynak kilitlemek çalıştığında bir kilitlenme oluşur. Hiçbir iş parçacığı herhangi gelişme yapabilirsiniz.  
  
 Yönetilen iş parçacığı sınıfların birçok yöntem kilitlenmeleri belirlemenize yardımcı olmak için zaman aşımlarını sağlar. Örneğin, aşağıdaki kodu adlı bir nesne üzerinde bir kilit edinmeye çalışır `lockObject`. Kilit 300 milisaniye cinsinden alınıyorsa değil, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false`.  
  
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
 Bir yarış durumu, iki veya daha fazla iş parçacığı belirli bir kod bloğu ilk ulaştığında üzerinde bir program sonucunu bağlı olduğunda oluşan bir hatadır. Birçok kez programı çalıştırma farklı sonuçlar üretir ve belirli bir çalıştırma sonucu tahmin edilemez.  
  
 Bir yarış durumu basit bir örneği bir alan artırma. Özel bir sınıf sahip olduğunu varsayın **statik** alan (**paylaşılan** Visual Basic'te) sınıfının bir örneği, kod gibi kullanılarak oluşturulan her zaman artar `objCt++;` (C#) veya `objCt += 1` () Visual Basic). Bu işlem değerinden yüklenmesini gerektirir `objCt` bir kasada, artan değeri ve de depolamak `objCt`.  
  
 Birden çok iş parçacıklı bir uygulamada, tüm üç adımı gerçekleştiren başka bir iş parçacığı tarafından yüklenen ve değer artan bir iş parçacığı etkisiz; ilk iş parçacığı yürütme devam eder ve değerini depolar, bu raporun üzerine `objCt` değeri geçici değiştirildi olgu dikkate alarak olmadan.  
  
 Bu belirli yarış durumu yöntemlerini kullanarak kolayca kaçınılması <xref:System.Threading.Interlocked> gibi sınıfı <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Çoklu iş parçacıkları arasında veri eşitlemek için başka teknikler hakkında edinmek için bkz [çoklu iş parçacığı kullanımı için veri eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Birden çok iş parçacığı etkinliklerini eşitlediğinizde yarış durumları da oluşabilir. Bir kod satırı yazdığınızda, ne gerçekleşebilir dikkate almanız gereken bir iş parçacığı etkisiz satır yürütmeden önce (veya çizgiyi oluşturan tek tek makine yönergeleri hiçbirini önce) ve onu başka bir iş parçacığı taşıyorduysa.  
  
## <a name="number-of-processors"></a>İşlemci sayısı  
 Çoğu bilgisayar artık tabletler ve telefonlar gibi küçük aygıtlar bile (çekirdek da denir), birden çok işlemci yok. Ayrıca tek işlemcili bilgisayarlarda, farkında olmalıdır, çoklu iş parçacığı çalıştırılır yazılım geliştirirken biliyorsanız tek işlemcili bilgisayarlar ve çok işlemcili bilgisayarlar için farklı sorunu çözer.  
  
### <a name="multiprocessor-computers"></a>Çok işlemcili bilgisayarlar  
 Çoklu iş parçacığı kullanımı büyük verimi sağlar. On işlemciler on kez on aynı anda çalışıyor bir yalnızca iş ayrılmıştır varsa ancak bir iş yapabilirsiniz; iş parçacığı işi bölün ve ek işlem gücü yararlanmak için kolay bir yol sağlar. Kullanırsanız, çok işlemcili bir bilgisayarda çoklu iş parçacığı kullanımı:  
  
-   Aynı anda yürütülebilecek iş parçacığı sayısını işlemci sayısıyla sınırlıdır.  
  
-   Yalnızca çalışan ön plan iş parçacıklarının sayısını işlemci sayısından küçük olduğunda bir arka plan iş parçacığı yürütür.  
  
-   Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığı üzerinde o iş parçacığı olabilir veya işlemci sayısını ve çalıştırmak için şu anda bekleyen iş parçacığı sayısı bağlı olarak hemen yürütme başlatılamayabilir.  
  
-   Yarış durumları yalnızca iş parçacığı beklenmedik bir şekilde etkisiz, ancak iki farklı yürütme iş parçacıkları olduğundan işlemcileri aynı kod bloğunda ulaşması yarış çünkü oluşabilir.  
  
### <a name="single-processor-computers"></a>Tek işlemcili bilgisayarlar  
 Çoklu iş parçacığı kullanımı bilgisayar kullanıcı büyük yanıtlama hızı sağlar ve arka plan görevleri için boşta kalma süresi kullanır. Kullanırsanız, bir tek işlemcili bilgisayarda çoklu iş parçacığı kullanımı:  
  
-   Yalnızca bir iş parçacığı herhangi bir anlık çalışır.  
  
-   Arka plan iş parçacığı, yalnızca ana kullanıcı iş parçacığı boştayken çalıştırılır. Sürekli olarak yürüten bir ön plan iş parçacığı arka plan iş parçacıkları işlemci zamanını starves.  
  
-   Çağırdığınızda <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi bir iş parçacığında iş parçacığı kadar geçerli iş parçacığını yürütmek başlamıyor verir veya işletim sistemi tarafından etkisiz.  
  
-   Programcı alışılmadık bir anda bir iş parçacığı etkisiz olduğunu olgu bazen kod bloğu ilk ulaşmak başka bir iş parçacığı izin verme öngörememiştir yarış durumları genellikle oluşur.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeler ve statik oluşturucular  
 Bir sınıf kadar sınıf oluşturucusu başlatılmadı (`static` C# ' ta, Oluşturucusu `Shared Sub New` Visual Basic'te) çalışması sona erdi. Başlatılmamış bir türündeki kodun yürütülmesini engellemek için ortak dil çalışma zamanı için diğer iş parçacıklarından tüm çağrıları engeller `static` sınıf üyeleri (`Shared` üyeleri Visual Basic'te) sınıfı oluşturucusu çalışan tamamlanana kadar.  
  
 Örneğin, yeni bir iş parçacığı bir sınıf oluşturucu başlar ve iş parçacığı yordamı çağıran bir `static` sınıfı oluşturucusu tamamlanana kadar yeni bir iş parçacığı blokları sınıf üyesi.  
  
 Bu olabilir herhangi bir türü için geçerlidir bir `static` Oluşturucusu.  
  
## <a name="general-recommendations"></a>Genel öneriler  
 Çoklu iş parçacıkları kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
-   Kullanmayan <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> başka bir iş parçacığı sonlandırılacak. Çağırma **Abort** iş parçacığı, ne o iş parçacığı noktası bilmeden kendi işleme sınırına ulaşmış olması bir özel durum atma benzer başka bir iş parçacığı üzerinde değil.  
  
-   Kullanmayan <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> birden çok iş parçacığı etkinliklerini eşitlenecek. Kullanmak <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.Monitor>.  
  
-   Çalışan iş parçacıkları (olaylar, örneğin kullanarak), ana programdan yürütülmesi denetim yok. Bunun yerine, çalışan iş parçacığı iş kullanılabilir hale gelene kadar bekleyen, yürütülmekte ve diğer bölümleri bittiğinde programınızın bildiren sorumlu; böylece programınızı tasarlayın. Çalışan iş parçacığı engellemez, iş parçacığı havuzu iş parçacıkları kullanmayı düşünün. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> Burada blok çalışan iş parçacıkları durumlarda faydalıdır.  
  
-   Türleri kilit nesneler olarak kullanmayın. Diğer bir deyişle, kod gibi kaçının `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic veya kullanımını <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> ile <xref:System.Type> nesneleri. Belirli bir türde için yalnızca bir örneği var. <xref:System.Type?displayProperty=nameWithType> uygulama etki alanı başına. Bir kilit etkinleştirilir türü ortak ise, kendi dışındaki kod kilitleri üzerinde kilitlenmeye baştaki alabilir. Ek sorunlar için bkz: [güvenilirlik en iyi yöntemleri](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Örneklerinde, örneğin kilitleme dikkatli `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te. Diğer kodu, uygulamanızda türüne dış nesne üzerinde bir kilit alırsa, kilitlenmeleri meydana gelebilir.  
  
-   İş parçacığı İzleyicisi'nde olsa da bir özel durum oluşursa bile bir izleyici her zaman geçtiğini bir iş parçacığı bu İzleyici bırakır emin olun. C# [kilit](~/docs/csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) deyimi sağlamak Bu davranış otomatik olarak kullanan bir **son** emin olmak için blok <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> olduğu çağrılır. Garanti edemez, **çıkış** çağrılacağı, kullanılacak tasarımınızı değiştirmeyi göz önünde bulundurun **Mutex**. Şu anda sahip iş parçacığı sonlandırıldığında bir mutex otomatik olarak yayımlanır.  
  
-   Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve birden çok iş parçacığı için tek kaynak atamaktan kaçının. Örneğin, g/ç içeren herhangi bir görev kendi iş parçacığı, çünkü o iş parçacığı g/ç işlemleri sırasında engellemek ve böylece yürütmek başka bir iş parçacığı izin kalmaktan fayda sağlar. Kullanıcı girişi adanmış bir iş parçacığından avantaj başka bir kaynak değil. Bir tek işlemcili bilgisayarda yoğun hesaplama içeren bir görev g/ç ile ilgili görevleri ve kullanıcı girişi ile birlikte var, ancak birden fazla hesaplama yoğunluklu görevleri birbiriyle yüklüyorsa.  
  
-   Yöntemleri kullanmayı <xref:System.Threading.Interlocked> kullanmak yerine basit durum değişiklikleri için sınıf `lock` deyimi (`SyncLock` Visual Basic'te). `lock` Açıklamadır iyi genel amaçlı bir aracı, ancak <xref:System.Threading.Interlocked> sınıfı atomik güncelleştirmeler için daha iyi performans sağlar. Dahili olarak, hiçbir Çekişme varsa tek kilit önek yürütür. Aşağıdaki örneklerde gösterildiği gibi kodu için kod incelemeleri içinde izleyin. Bu örnekte, bir durum değişkeninin artırılır:  
  
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
  
     Kullanarak performansı artırabilir <xref:System.Threading.Interlocked.Increment%2A> yöntemi yerine `lock` şekilde deyimi:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  .NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.Add%2A> yöntemi 1'den büyük artışlarla atomik güncelleştirmeler sağlar.  
  
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
  
     Performans geliştirilmiş kullanarak <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi bunun yerine, aşağıdaki gibi:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  .NET Framework sürüm 2.0, <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi herhangi bir başvuru türü tür kullanımı uyumlu yapabilmek için kullanılabilir bir genel aşırı sahiptir.  
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Sınıf kitaplıkları için tasarlarken aşağıdaki yönergeleri dikkate alın çoklu iş parçacığı kullanımı:  
  
-   Eşitleme, gereksinimini mümkünse kaçının. Bu, özellikle yoğun olarak kullanılan kod için geçerlidir. Örneğin, bir algoritma yerine bir yarış durumu tolerans onu ortadan kaldırmak için ayarlanmış. Gereksiz eşitleme performansı düşürür ve kilitlenmeler ve yarış durumları olasılığını oluşturur.  
  
-   Statik verileri yap (`Shared` Visual Basic'te) varsayılan olarak güvenli iş parçacığı.  
  
-   Örnek veri iş parçacığı varsayılan olarak güvenli yapmayın. İş parçacığı kodu oluşturmak için kilitler ekleme performans azaltır, kilit çakışması artırır ve gerçekleşmesi kilitlenmeleri olasılığı oluşturur. Ortak uygulama modelleri, aynı anda yalnızca bir iş parçacığı iş parçacığı güvenliği gereksinimini en aza indirir kullanıcı kodu yürütür. Bu nedenle, .NET Framework sınıf kitaplıkları iş parçacığı varsayılan olarak güvenli değildir.  
  
-   Statik durumu alter statik yöntemler sağlayan kaçının. Yaygın olarak kullanılan sunucu senaryosu, birden çok iş parçacığı aynı anda kod yürütebilir anlamına gelir statik durumu istekler arasında paylaşılır. Bu hataların iş parçacığı oluşturma olasılığını açar. Veri istekler arasında paylaşılmayan örnekleri halinde yalıtan bir tasarım deseni kullanmayı düşünün. Ayrıca, statik verileri eşitlenirse durumu alter statik yöntemler arasındaki çağrıları kilitlenmeleri veya performansını olumsuz yönde etkileyen yedekli eşitleme neden olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
