---
title: Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri
description: .NET ' te yönetilen iş parçacığı en iyi uygulamalarını öğrenin. Birçok iş parçacığını koordine etme veya engelleme iş parçacıklarını işleme gibi zor durumlarla çalışın.
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
ms.openlocfilehash: 8d5c37bf2ed80e9b6ea071fcd2080c43be8f6247
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546373"
---
# <a name="managed-threading-best-practices"></a>Yönetilen iş parçacığı en iyi uygulamaları
Çoklu iş parçacığı dikkatli bir programlama gerektirir. Çoğu görev için, iş parçacığı havuzu iş parçacıklarının yürütülmesi için istekleri sıraya alarak karmaşıklığı azaltabilirsiniz. Bu konu, birden çok iş parçacığının çalışmasını koordine etme ya da engelleyen iş parçacıklarını işleme gibi daha zor durumları ele almaktadır.  
  
> [!NOTE]
> .NET Framework 4 ' te başlayarak, paralel kitaplığı ve PLıNQ görevi, çok iş parçacıklı programlamaya ait karmaşıklığın ve risklerden bazılarını azaltan API 'Ler sağlar. Daha fazla bilgi için bkz. [.net 'Te paralel programlama](../parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış koşulları  
 Çoklu iş parçacığı işleme ve yanıt verme sorunlarını çözer, ancak bunu yaparken yeni sorunlar ortaya koymaktadır: Kilitlenmeler ve yarış koşulları.  
  
### <a name="deadlocks"></a>Çık  
 İki iş parçacığının her biri zaten kilitlediği bir kaynağı kilitlemeyi denediğinde bir kilitlenme oluşur. Ne iş parçacığı başka bir işlem yapabilir.  
  
 Yönetilen iş parçacığı sınıflarının birçok yöntemi, kilitlenmeleri tespit etmenize yardımcı olmak için zaman aşımı sağlar. Örneğin, aşağıdaki kod adlı bir nesne üzerinde bir kilit edinmeye çalışır `lockObject` . Kilit 300 milisaniye içinde alınamıyorsa, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> döndürür `false` .  
  
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
 Yarış durumu, bir programın sonucu, ilk olarak iki veya daha fazla iş parçacığının belirli bir kod bloğuna eriştiği durumlarda oluşan hatadır. Programı birçok kez çalıştırmak farklı sonuçlar üretir ve belirli bir çalıştırmanın sonucu tahmin edilemez.  
  
 Yarış koşulunun basit bir örneği bir alanı artırdığında. Bir sınıfın bir örneği oluşturulduğunda (Visual Basic**paylaşılan** ), **static** `objCt++;` (C#) veya `objCt += 1` (Visual Basic) gibi bir kod kullanarak, sınıfın bir örneği oluşturulduğu her seferinde artan bir özel statik alana sahip olduğunu varsayalım. Bu işlem, değeri `objCt` bir kayda yüklemeyi, değeri arttırmanızı ve içinde depolamayı gerektirir `objCt` .  
  
 Çok iş parçacıklı bir uygulamada, değeri yüklemiş ve arttırılan bir iş parçacığı, üç adımı da gerçekleştiren başka bir iş parçacığı tarafından önlenebilir. ilk iş parçacığı yürütmeyi sürdürür ve değerini depoladığında `objCt` değeri, değerin geçici olarak değiştiğini dikkate almadan geçersiz kılar.  
  
 Bu belirli yarış durumu, sınıfının yöntemleri kullanılarak kolayca kaçınılmaz <xref:System.Threading.Interlocked> <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> . Birden çok iş parçacığı arasında verileri eşitlemeye yönelik diğer teknikler hakkında bilgi edinmek için bkz. [Çoklu Iş parçacıklı verileri eşitleme](synchronizing-data-for-multithreading.md).  
  
 Yarış durumları, birden çok iş parçacığının etkinliklerini eşitlediğinizde de gerçekleşebilir. Her bir kod satırı yazdığınızda, bir iş parçacığının satırı yürütmeden önce (veya satırı oluşturan tek bir makine yönergelerinden önce) önceden atıldıktan sonra ne olabileceğini göz önünde bulundurmanız gerekir.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeler ve statik oluşturucular  
 Sınıf Oluşturucusu (C# ' deki `static` oluşturucu `Shared Sub New` Visual Basic) çalışmayı bitirene kadar bir sınıf başlatılmaz. Başlatılmamış bir türdeki kodun yürütülmesini engellemek için, ortak dil çalışma zamanı, sınıf oluşturucusunun çalışmayı bitirene kadar diğer iş parçacıklarından gelen tüm çağrıları `static` sınıf üyelerine ( `Shared` Visual Basic Üyeler) engeller.  
  
 Örneğin, bir sınıf Oluşturucusu yeni bir iş parçacığı başlatır ve iş parçacığı yordamı sınıfının bir üyesini çağırırsa `static` , sınıf oluşturucusu tamamlanana kadar yeni iş parçacığı engeller.  
  
 Bu, Oluşturucusu olan herhangi bir tür için geçerlidir `static` .  

## <a name="number-of-processors"></a>İşlemci sayısı

Birden çok işlemci olup olmadığı veya sistemde yalnızca bir işlemcinin kullanılabilir olması çok iş parçacıklı mimariyi etkileyebilir. Daha fazla bilgi için bkz. [Işlemci sayısı](/previous-versions/dotnet/netframework-1.1/1c9txz50(v=vs.71)#number-of-processors).

<xref:System.Environment.ProcessorCount?displayProperty=nameWithType>Çalışma zamanında kullanılabilir işlemcilerin sayısını öğrenmek için özelliğini kullanın.
  
## <a name="general-recommendations"></a>Genel öneriler  
 Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>Diğer iş parçacıklarını sonlandırmak için kullanmayın. Başka bir iş parçacığında **iptali** çağırmak, bu iş parçacığı üzerinde bir özel durum oluşturmak için, iş parçacığının işleme göre hangi noktaya ulaşılmadığını bilmeksizin kaydedilir.  
  
- <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> Birden çok iş parçacığının etkinliklerini eşitlememe ve kullanma. ,, <xref:System.Threading.Mutex> <xref:System.Threading.ManualResetEvent> Ve kullanın <xref:System.Threading.AutoResetEvent> <xref:System.Threading.Monitor> .  
  
- Ana programınızdaki çalışan iş parçacıklarının yürütülmesini denetleme (örneğin, olayları kullanarak). Bunun yerine, programınızı, çalışan iş parçacıklarının iş için kullanılabilir olana kadar beklemekten sorumlu olması, yürütülmesi ve işiniz bittiğinde programınızın diğer bölümlerine bildirimde bulunmak için tasarlayın. Çalışan iş parçacılarınız engellenmiyor ise, iş parçacığı havuzu iş parçacıklarını kullanmayı göz önünde bulundurun. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> , çalışan iş parçacıklarının engel olduğu durumlarda faydalıdır.  
  
- Türleri kilit nesneleri olarak kullanmayın. Diğer bir deyişle, `lock(typeof(X))` C# veya Visual Basic gibi koddan `SyncLock(GetType(X))` ya da <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> nesneleri ile kullanımını önleyin <xref:System.Type> . Belirli bir tür için, <xref:System.Type?displayProperty=nameWithType> uygulama etki alanı başına yalnızca bir örnek vardır. Bir kilidi aldığınız tür herkese açık ise, kendi dışında bir kod, kilitlenmeleri için bir kilit alabilir. Ek sorunlar için bkz. [Güvenilirlik En Iyi uygulamaları](../../framework/performance/reliability-best-practices.md).  
  
- Örneğin, C# veya Visual Basic gibi örneklerde kilitleme yaparken dikkatli olun `lock(this)` `SyncLock(Me)` . Uygulamanızdaki diğer kod, türü dışında, nesne üzerinde bir kilit alırsa, kilitlenmeler meydana gelebilir.  
  
- İş parçacığı izleyicisinde olduğunda bir özel durum olsa bile, bir izleyici girmiş olan bir iş parçacığının her zaman bu izleyiciden ayrılmasından emin olun. C# [Lock](../../csharp/language-reference/keywords/lock-statement.md) ve Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimleri, bir **finally** bloğu kullanarak bu davranışı otomatik olarak sağlar <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> . **Çıkış** çağrısı yapıldığından emin değilseniz, tasarımınızı **mutex**kullanacak şekilde değiştirmeyi düşünün. Şu anda sahibi olan iş parçacığı sonlandırıldığında bir mutex otomatik olarak serbest bırakılır.  
  
- Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve tek bir kaynağa birden çok iş parçacığı atamaktan kaçının. Örneğin, iş parçacığı g/ç işlemleri sırasında engelleyecağından ve bu nedenle diğer iş parçacıklarının yürütülmesine izin vereceğinden, g/ç 'nin sağladığı her türlü görev kendi iş parçacığına sahip olur. Kullanıcı girişi, adanmış bir iş parçacığından faydalanan başka bir kaynaktır. Tek işlemcili bir bilgisayarda, Kullanıcı girişiyle ve g/ç içeren görevlerle yoğun bir hesaplama birlikte bulunur, ancak birden fazla hesaplama yoğun görev, birbirleriyle devam eden bir görevdir.  
  
- <xref:System.Threading.Interlocked>İfadesini kullanmak yerine, basit durum değişiklikleri için sınıfın yöntemlerini kullanmayı düşünün `lock` ( `SyncLock` Visual Basic). `lock`İfade, iyi bir genel amaçlı araçtır, ancak <xref:System.Threading.Interlocked> sınıfı atomik olması gereken güncelleştirmeler için daha iyi performans sağlar. Bir çekişme yoksa, dahili olarak tek bir kilit öneki yürütür. Kod İncelemeleri bölümünde aşağıdaki örneklerde gösterildiği gibi kodu izleyin. İlk örnekte, bir durum değişkeni artırılır:  
  
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
  
     <xref:System.Threading.Interlocked.Increment%2A>Aşağıdaki gibi, yöntemi yerine yöntemini kullanarak performansı artırabilirsiniz `lock` :  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2,0 ve sonrasında, <xref:System.Threading.Interlocked.Add%2A> 1 ' den büyük atomik artışlarla yöntemi kullanın.  
  
     İkinci örnekte, bir başvuru türü değişkeni yalnızca bir null başvurusu ( `Nothing` Visual Basic) ise güncelleştirilir.  
  
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
  
     <xref:System.Threading.Interlocked.CompareExchange%2A>Aşağıdaki gibi yöntemi kullanılarak performans artırılabilir:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2,0 ' den başlayarak, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> yöntem aşırı yüklemesi başvuru türleri için tür açısından güvenli bir alternatif sağlar.
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Çoklu iş parçacığı için sınıf kitaplıkları tasarlarken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Mümkünse eşitleme gereksinimini önleyin. Bu, özellikle de yoğun olarak kullanılan kod için geçerlidir. Örneğin, bir algoritma ortadan kaldırmak yerine bir yarış durumuna göre ayarlanabilir. Gereksiz eşitleme performansı düşürür ve Kilitlenmeler ve yarış koşullarından oluşan olasılığı oluşturur.  
  
- Statik verileri ( `Shared` Visual Basic) iş parçacığında varsayılan olarak güvenli hale getirin.  
  
- Örnek veri parçacığını varsayılan olarak güvenli hale getirme. İş parçacığı açısından güvenli kod oluşturmak için kilitlerin eklenmesi performansı düşürür, kilit çekişmesini artırır ve kilitlenmeleri oluşma olasılığını oluşturur. Ortak uygulama modellerinde, aynı anda yalnızca bir iş parçacığı Kullanıcı kodunu yürütür ve bu da iş parçacığı güvenliği gereksinimini en aza indirir. Bu nedenle, .NET Framework sınıf kitaplıkları varsayılan olarak iş parçacığı güvenli değildir.  
  
- Statik durumu değiştirecek statik yöntemler sağlamaktan kaçının. Ortak sunucu senaryolarında, statik durum istekler arasında paylaşılır, bu da birden çok iş parçacığının aynı anda bu kodu yürütebileceği anlamına gelir. Bu, hataları iş parçacığı olma olasılığını açar. İstekler arasında paylaşılmayan örneklere veri kapsülleyen bir tasarım kalıbı kullanmayı düşünün. Ayrıca, statik veriler eşitlenirse, durumu alter static Yöntemler arasındaki çağrılar kilitlenmeleri veya yedekli eşitlemeye neden olabilir ve bu da performansı olumsuz etkileyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Oluşturma](index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](threads-and-threading.md)
