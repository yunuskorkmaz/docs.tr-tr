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
ms.openlocfilehash: a76cc40f308ac2f636a650cd4a17da0e94e23a34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160267"
---
# <a name="managed-threading-best-practices"></a>Yönetilen iş parçacığı en iyi uygulamalar
Multithreading dikkatli programlama gerektirir. Çoğu görev için, iş parçacığı havuzu iş parçacıkları tarafından yürütme isteklerini sıraya alarak karmaşıklığı azaltabilirsiniz. Bu konu, birden çok iş parçacığının çalışmasını koordine etmek veya engelleyen iş parçacıklarını işlemek gibi daha zor durumları gidermektedir.  
  
> [!NOTE]
> .NET Framework 4'ten başlayarak, Görev Paralel Kitaplığı ve PLINQ, çok iş parçacığı lı programlamanın karmaşıklığını ve risklerini azaltan API'ler sağlar. Daha fazla bilgi için [.NET'teki Paralel Programlama'ya](../../../docs/standard/parallel-programming/index.md)bakın.  
  
## <a name="deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış koşulları  
 Multithreading, iş gücü ve yanıt verme ile ilgili sorunları çözer, ancak bunu yaparken yeni sorunlar sunar: kilitlenmeler ve Yarış koşulları.  
  
### <a name="deadlocks"></a>Kilitlenmeleri  
 İki iş parçacığının her biri diğerinin kilitlemiş olduğu bir kaynağı kilitlemeye çalıştığında kilitlenme oluşur. Ne iş parçacığı daha fazla ilerleme yapabilir.  
  
 Yönetilen iş parçacığı sınıflarının birçok yöntemi, kilitlenmeleri algılamanıza yardımcı olmak için zaman zaman larını sağlar. Örneğin, aşağıdaki kod adlı `lockObject`bir nesne üzerinde kilit elde etmeye çalışır. Kilit 300 milisaniye içinde elde <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> edilmezse, döndürür. `false`  
  
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
  
### <a name="race-conditions"></a>Yarış koşulları  
 Yarış koşulu, bir programın sonucu iki veya daha fazla iş parçacığının önce belirli bir kod bloğuna eriştiğine bağlı olduğunda oluşan bir hatadır. Programı birçok kez çalıştırmak farklı sonuçlar üretir ve belirli bir çalıştırmanın sonucu tahmin edilemez.  
  
 Bir yarış koşulu basit bir örnek bir alan artış olduğunu. Bir sınıfın (C#) `objCt++;` veya `objCt += 1` (Visual Basic) gibi kodlar kullanılarak sınıfın her örneğinde artılan özel bir **statik** alanı (Visual Basic'te**Paylaşılan)** olduğunu varsayalım. Bu işlem, değeri `objCt` bir kasaya yüklemeyi, değeri artarak ve `objCt`'de depolamayı gerektirir.  
  
 Çok iş parçacığı uygulamasında, değeri yüklemiş ve artan bir iş parçacığı, üç adımı da gerçekleştiren başka bir iş parçacığı tarafından engellenebilir; ilk iş parçacığı yürütme devam eder ve değerini `objCt` depolar, bu değer geçici olarak değişti gerçeğini dikkate almadan üzerine yazar.  
  
 Bu özel yarış koşulu gibi <xref:System.Threading.Interlocked> sınıfın yöntemleri kullanılarak kolayca <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>önlenir. Birden çok iş parçacığı arasında veri eşitleme için diğer teknikler hakkında okumak [için, Multithreading için Veri Eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)bakın.  
  
 Birden çok iş parçacığının etkinliklerini eşitlediğinizde yarış koşulları da oluşabilir. Bir kod satırı yazdığınızda, satırı yürütmeden önce (veya satırı oluşturan tek tek makine yönergelerinden herhangi biri) ve başka bir iş parçacığı nın önüne geçtiğinde ne olabileceğini göz önünde bulundurmanız gerekir.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeler ve statik yapıcılar  
 Bir sınıf, sınıf oluşturucusu (Visual`static` `Shared Sub New` Basic'te C#'daki oluşturucu) çalışma tamamlanana kadar başharfe fişi değildir. Başharflere geçirilmeyen bir türde kodun yürütülmesini önlemek için, ortak dil `static` çalışma süresi,`Shared` sınıf oluşturucu çalışmaya devam edene kadar diğer iş parçacıklarından sınıf üyelerine (Visual Basic'teki üyeler) tüm çağrıları engeller.  
  
 Örneğin, bir sınıf oluşturucu yeni bir iş parçacığı başlatır ve iş parçacığı yordamı sınıfın bir `static` üyesiçağırırsa, sınıf oluşturucu tamamlanana kadar yeni iş parçacığı engeller.  
  
 Bu, bir oluşturucu olabilir `static` herhangi bir tür için geçerlidir.  

## <a name="number-of-processors"></a>İşlemci sayısı

Birden çok işlemci veya bir sistemde yalnızca bir işlemci olup olmadığını çok iş parçacığı mimarisi etkileyebilir. Daha fazla bilgi için [İşlemci Sayısı'na](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors)bakın.

Çalışma <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> zamanında kullanılabilen işlemci sayısını belirlemek için özelliği kullanın.
  
## <a name="general-recommendations"></a>Genel öneriler  
 Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Diğer iş <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> parçacıklarını sonlandırmak için kullanmayın. **Abort'u** başka bir iş parçacığıüzerinde çağırmak, iş parçacığının işlenmesinde hangi noktaya ulaştığını bilmeden bu iş parçacığına özel bir özel durum atmaya benzer.  
  
- Birden çok <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> iş <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> parçacığının etkinliklerini kullanmayın ve eşitlemayın. , <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent> <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.Monitor>ve .  
  
- Ana programınızdan (örneğin olayları kullanarak) çalışan iş parçacıklarının yürütülmesini denetlemeyin. Bunun yerine, çalışma kullanılabilir olana kadar beklemek, çalıştırın ve bittiğinde programın diğer bölümlerini bildirmekiçin çalışan iş parçacıklarının sorumlu olması için programınızı tasarla. Alt iş parçacığınız engellemiyorsa, iş parçacığı havuzu iş parçacıklarını kullanmayı düşünün. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>işçi iş parçacıklarının engellendiği durumlarda yararlıdır.  
  
- Türleri kilit nesnesi olarak kullanmayın. Diğer bir deyişle, `lock(typeof(X))` C# veya `SyncLock(GetType(X))` Visual Basic gibi kodlardan veya <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nesnelerle <xref:System.Type> kullanmaktan kaçının. Belirli bir tür için, uygulama <xref:System.Type?displayProperty=nameWithType> etki alanı başına yalnızca bir örnek vardır. Kilitlediğiniz tür herkese açıksa, sizinki dışındaki kod kilitler alabilir ve bu da kilitlenmeye yol açabilir. Ek sorunlar için Güvenilirlik [En İyi Uygulamaları'na](../../../docs/framework/performance/reliability-best-practices.md)bakın.  
  
- Örneğin `lock(this)` C# veya `SyncLock(Me)` Visual Basic'te gibi örnekleri kilitlerken dikkatli olun. Uygulamanızdaki diğer kod, türün dışında, nesneye kilitlenirse, kilitlenmeler oluşabilir.  
  
- İzparçacığı monitördeyken bir özel durum oluşsa bile, monitöre giren bir iş parçacığının her zaman bu monitörden ayrıldığından emin olun. C# [kilit](../../csharp/language-reference/keywords/lock-statement.md) deyimi ve Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimi bu davranışı **finally** otomatik olarak <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> sağlar ve bu davranışı n için çağrıldığından emin olmak için son bir blok kullanır. **Exit'in** çağrılmasını sağlayamazsanız, **Mutex'i**kullanmak için tasarımınızı değiştirmeyi düşünün. Şu anda sahibi olan iş parçacığı sona erdiğinde bir mutex otomatik olarak serbest bırakılır.  
  
- Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve tek bir kaynağa birden çok iş parçacığı atamaktan kaçının. Örneğin, G/Ç içeren herhangi bir görev kendi iş parçacığına sahip olmaktan yararlanır, çünkü bu iş parçacığı G/Ç işlemleri sırasında engellenir ve böylece diğer iş parçacıklarının yürütülmesine izin verir. Kullanıcı girişi, özel bir iş parçacığından yararlanan başka bir kaynaktır. Tek işlemcili bir bilgisayarda, yoğun hesaplama içeren bir görev, kullanıcı girişi ve G/Ç içeren görevlerle bir arada bulunur, ancak birden çok hesaplama yoğun görev birbiriyle uğraşır.  
  
- İfadeyi <xref:System.Threading.Interlocked> (Visual `lock` `SyncLock` Basic'te) kullanmak yerine basit durum değişiklikleri için sınıfın yöntemlerini kullanmayı düşünün. `lock` İfade iyi bir genel amaçlı araçtır, ancak <xref:System.Threading.Interlocked> sınıf atomik olması gereken güncelleştirmeler için daha iyi performans sağlar. İçsel olarak, çekişme yoksa tek bir kilit öneki yürütür. Kod incelemelerinde, aşağıdaki örneklerde gösterilen gibi kodlara dikkat edin. İlk örnekte, bir durum değişkeni artımlı:  
  
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
  
     Aşağıdaki gibi, deyimi <xref:System.Threading.Interlocked.Increment%2A> yerine yöntemi kullanarak performansı artırabilirsiniz: `lock`  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2.0 ve sonraki <xref:System.Threading.Interlocked.Add%2A> durumlarda, 1'den büyük atomik artışlar için yöntemi kullanın.  
  
     İkinci örnekte, bir başvuru türü değişkeni yalnızca null`Nothing` reference (Visual Basic'te) ise güncelleştirilir.  
  
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
            x ??= y;
        }  
    }  
    ```  
  
     Performans, aşağıdaki gibi, <xref:System.Threading.Interlocked.CompareExchange%2A> bunun yerine yöntem kullanılarak artırılabilir:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2.0 ile <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> başlayarak, yöntem aşırı başvuru türleri için tür güvenli bir alternatif sağlar.
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Çok iş parçacığı için sınıf kitaplıkları tasarlarken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Mümkünse eşitleme gereksiniminden kaçının. Bu, özellikle ağır kullanılan kod için geçerlidir. Örneğin, bir algoritma bir yarış koşulunu ortadan kaldırmak yerine tolere etmek için ayarlanabilir. Gereksiz eşitleme performansı düşürür ve kilitlenmeler ve yarış koşulları olasılığını oluşturur.  
  
- Statik verileri`Shared` (Visual Basic'te) varsayılan olarak güvenli hale getirin.  
  
- Örnek veri iş parçacığı varsayılan olarak güvenli yapmayın. İş parçacığı güvenli kod oluşturmak için kilitler eklemek performansı azaltır, kilit çekişmesini artırır ve kilitlenmelerin oluşma olasılığını oluşturur. Yaygın uygulama modellerinde, aynı anda yalnızca bir iş parçacığı kullanıcı kodunu yürütür ve bu da iş parçacığı güvenliği gereksinimini en aza indirir. Bu nedenle, .NET Framework sınıf kitaplıkları varsayılan olarak iş parçacığı güvenli değildir.  
  
- Statik durumu değiştiren statik yöntemler sağlamaktan kaçının. Yaygın sunucu senaryolarında statik durum istekler arasında paylaşılır, bu da birden çok iş parçacığının bu kodu aynı anda yürütebileceği anlamına gelir. Bu, hataların iş parçacığı olasılığını açar. Verileri istekler arasında paylaşılmayan örneklere kapsülleyen bir tasarım deseni kullanmayı düşünün. Ayrıca, statik veriler eşitlenirse, durumu değiştiren statik yöntemler arasındaki çağrılar kilitlenmeye veya gereksiz eşitlemeyle sonuçlanabilir ve performansı olumsuz yönde etkiler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
