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
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160267"
---
# <a name="managed-threading-best-practices"></a>Yönetilen iş parçacığı en iyi uygulamaları
Çoklu iş parçacığı dikkatli bir programlama gerektirir. Çoğu görev için, iş parçacığı havuzu iş parçacıklarının yürütülmesi için istekleri sıraya alarak karmaşıklığı azaltabilirsiniz. Bu konu, birden çok iş parçacığının çalışmasını koordine etme ya da engelleyen iş parçacıklarını işleme gibi daha zor durumları ele almaktadır.  
  
> [!NOTE]
> .NET Framework 4 ' te başlayarak, paralel kitaplığı ve PLıNQ görevi, çok iş parçacıklı programlamaya ait karmaşıklığın ve risklerden bazılarını azaltan API 'Ler sağlar. Daha fazla bilgi için bkz. [.net 'Te paralel programlama](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Kilitlenmeler ve yarış koşulları  
 Çoklu iş parçacığı işleme ve yanıt verme sorunlarını çözer, ancak bunu yaparken yeni sorunlar ortaya koymaktadır: Kilitlenmeler ve yarış koşulları.  
  
### <a name="deadlocks"></a>Çık  
 İki iş parçacığının her biri zaten kilitlediği bir kaynağı kilitlemeyi denediğinde bir kilitlenme oluşur. Ne iş parçacığı başka bir işlem yapabilir.  
  
 Yönetilen iş parçacığı sınıflarının birçok yöntemi, kilitlenmeleri tespit etmenize yardımcı olmak için zaman aşımı sağlar. Örneğin, aşağıdaki kod `lockObject`adlı bir nesne üzerinde bir kilit edinmeye çalışır. Kilit 300 milisaniye içinde alınamıyorsa <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> `false`döndürür.  
  
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
  
 Yarış koşulunun basit bir örneği bir alanı artırdığında. Bir sınıfın bir örneği oluşturulduğu her seferinde (Visual Basic**paylaşılan** ), `objCt++;` (C#) veya `objCt += 1` (Visual Basic) gibi bir kod kullanarak bir sınıf için bir özel **statik** alana sahip olduğunu varsayalım. Bu işlem, değerin `objCt` bir kayda yüklenmesini, değerin artırılmasına ve `objCt`depolanmasını gerektirir.  
  
 Çok iş parçacıklı bir uygulamada, değeri yüklemiş ve arttırılan bir iş parçacığı, üç adımı da gerçekleştiren başka bir iş parçacığı tarafından önlenebilir. ilk iş parçacığı yürütmeyi sürdürür ve değerini depoladığında, değerin geçici olarak değiştiğini dikkate almadan `objCt` üzerine yazar.  
  
 Bu belirli yarış durumu, <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>gibi <xref:System.Threading.Interlocked> sınıfının yöntemleri kullanılarak kolayca kaçınılmaz. Birden çok iş parçacığı arasında verileri eşitlemeye yönelik diğer teknikler hakkında bilgi edinmek için bkz. [Çoklu Iş parçacıklı verileri eşitleme](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Yarış durumları, birden çok iş parçacığının etkinliklerini eşitlediğinizde de gerçekleşebilir. Her bir kod satırı yazdığınızda, bir iş parçacığının satırı yürütmeden önce (veya satırı oluşturan tek bir makine yönergelerinden önce) önceden atıldıktan sonra ne olabileceğini göz önünde bulundurmanız gerekir.  
  
## <a name="static-members-and-static-constructors"></a>Statik üyeler ve statik oluşturucular  
 Sınıf Oluşturucusu (içindeki C#`static` oluşturucu `Shared Sub New` Visual Basic) çalışmayı tamamlayana kadar bir sınıf başlatılamaz. Başlatılmamış bir türdeki kodun yürütülmesini engellemek için, ortak dil çalışma zamanı, sınıf oluşturucusunun çalışmayı bitirene kadar diğer iş parçacıklarından gelen tüm çağrıları, sınıfın `static` (Visual Basic`Shared` üyeleri) olarak engeller.  
  
 Örneğin, bir sınıf Oluşturucusu yeni bir iş parçacığı başlatır ve iş parçacığı yordamı sınıfının `static` bir üyesini çağırırsa, sınıf oluşturucusu tamamlanana kadar yeni iş parçacığı engeller.  
  
 Bu, `static` oluşturucusuna sahip olan herhangi bir tür için geçerlidir.  

## <a name="number-of-processors"></a>İşlemci sayısı

Birden çok işlemci olup olmadığı veya sistemde yalnızca bir işlemcinin kullanılabilir olması çok iş parçacıklı mimariyi etkileyebilir. Daha fazla bilgi için bkz. [Işlemci sayısı](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).

Çalışma zamanında kullanılabilir işlemcilerin sayısını öğrenmek için <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> özelliğini kullanın.
  
## <a name="general-recommendations"></a>Genel öneriler  
 Birden çok iş parçacığı kullanırken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Diğer iş parçacıklarını sonlandırmak için <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> kullanmayın. Başka bir iş parçacığında **iptali** çağırmak, bu iş parçacığı üzerinde bir özel durum oluşturmak için, iş parçacığının işleme göre hangi noktaya ulaşılmadığını bilmeksizin kaydedilir.  
  
- Birden çok iş parçacığının etkinliklerini eşitlemeye yönelik <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> kullanmayın. <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>ve <xref:System.Threading.Monitor>kullanın.  
  
- Ana programınızdaki çalışan iş parçacıklarının yürütülmesini denetleme (örneğin, olayları kullanarak). Bunun yerine, programınızı, çalışan iş parçacıklarının iş için kullanılabilir olana kadar beklemekten sorumlu olması, yürütülmesi ve işiniz bittiğinde programınızın diğer bölümlerine bildirimde bulunmak için tasarlayın. Çalışan iş parçacılarınız engellenmiyor ise, iş parçacığı havuzu iş parçacıklarını kullanmayı göz önünde bulundurun. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>, çalışan iş parçacıklarının engel olduğu durumlarda faydalıdır.  
  
- Türleri kilit nesneleri olarak kullanmayın. Diğer bir deyişle, Visual Basic C# veya `SyncLock(GetType(X))` `lock(typeof(X))` gibi koddan veya <xref:System.Type> nesneleriyle <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> kullanılmasına engel olur. Belirli bir tür için, uygulama etki alanı başına <xref:System.Type?displayProperty=nameWithType> yalnızca bir örneği vardır. Bir kilidi aldığınız tür herkese açık ise, kendi dışında bir kod, kilitlenmeleri için bir kilit alabilir. Ek sorunlar için bkz. [Güvenilirlik En Iyi uygulamaları](../../../docs/framework/performance/reliability-best-practices.md).  
  
- Örneklere kilitleme sırasında dikkatli olun, örneğin Visual Basic içindeki C# veya `SyncLock(Me)` `lock(this)`. Uygulamanızdaki diğer kod, türü dışında, nesne üzerinde bir kilit alırsa, kilitlenmeler meydana gelebilir.  
  
- İş parçacığı izleyicisinde olduğunda bir özel durum olsa bile, bir izleyici girmiş olan bir iş parçacığının her zaman bu izleyiciden ayrılmasından emin olun. C# [Kilit](../../csharp/language-reference/keywords/lock-statement.md) ve Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) deyimleri, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> çağrıldığından emin olmak için **finally** bloğu kullanan bu davranışı otomatik olarak sağlar. **Çıkış** çağrısı yapıldığından emin değilseniz, tasarımınızı **mutex**kullanacak şekilde değiştirmeyi düşünün. Şu anda sahibi olan iş parçacığı sonlandırıldığında bir mutex otomatik olarak serbest bırakılır.  
  
- Farklı kaynaklar gerektiren görevler için birden çok iş parçacığı kullanın ve tek bir kaynağa birden çok iş parçacığı atamaktan kaçının. Örneğin, iş parçacığı g/ç işlemleri sırasında engelleyecağından ve bu nedenle diğer iş parçacıklarının yürütülmesine izin vereceğinden, g/ç 'nin sağladığı her türlü görev kendi iş parçacığına sahip olur. Kullanıcı girişi, adanmış bir iş parçacığından faydalanan başka bir kaynaktır. Tek işlemcili bir bilgisayarda, Kullanıcı girişiyle ve g/ç içeren görevlerle yoğun bir hesaplama birlikte bulunur, ancak birden fazla hesaplama yoğun görev, birbirleriyle devam eden bir görevdir.  
  
- `lock` deyimin (`SyncLock` Visual Basic) kullanılması yerine basit durum değişiklikleri için <xref:System.Threading.Interlocked> sınıfının yöntemlerini kullanmayı göz önünde bulundurun. `lock` deyimleri, iyi bir genel amaçlı araçtır, ancak <xref:System.Threading.Interlocked> sınıfı atomik olması gereken güncelleştirmeler için daha iyi performans sağlar. Bir çekişme yoksa, dahili olarak tek bir kilit öneki yürütür. Kod İncelemeleri bölümünde aşağıdaki örneklerde gösterildiği gibi kodu izleyin. İlk örnekte, bir durum değişkeni artırılır:  
  
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
  
     Aşağıdaki gibi `lock` bildiri yerine <xref:System.Threading.Interlocked.Increment%2A> yöntemini kullanarak performansı artırabilirsiniz:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2,0 ve sonrasında, 1 ' den büyük atomik artışlarla <xref:System.Threading.Interlocked.Add%2A> yöntemini kullanın.  
  
     İkinci örnekte, bir başvuru türü değişkeni yalnızca bir null başvurusu (Visual Basic`Nothing`) ise güncelleştirilir.  
  
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
  
     Aşağıdaki gibi <xref:System.Threading.Interlocked.CompareExchange%2A> yöntemi kullanılarak performans artırılabilir:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > .NET Framework 2,0 ' den başlayarak, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> yöntemi aşırı yüklemesi başvuru türleri için tür açısından güvenli bir alternatif sağlar.
  
## <a name="recommendations-for-class-libraries"></a>Sınıf kitaplıkları için öneriler  
 Çoklu iş parçacığı için sınıf kitaplıkları tasarlarken aşağıdaki yönergeleri göz önünde bulundurun:  
  
- Mümkünse eşitleme gereksinimini önleyin. Bu, özellikle de yoğun olarak kullanılan kod için geçerlidir. Örneğin, bir algoritma ortadan kaldırmak yerine bir yarış durumuna göre ayarlanabilir. Gereksiz eşitleme performansı düşürür ve Kilitlenmeler ve yarış koşullarından oluşan olasılığı oluşturur.  
  
- Statik verileri (Visual Basic`Shared`) iş parçacığında varsayılan olarak güvenli hale getirin.  
  
- Örnek veri parçacığını varsayılan olarak güvenli hale getirme. İş parçacığı açısından güvenli kod oluşturmak için kilitlerin eklenmesi performansı düşürür, kilit çekişmesini artırır ve kilitlenmeleri oluşma olasılığını oluşturur. Ortak uygulama modellerinde, aynı anda yalnızca bir iş parçacığı Kullanıcı kodunu yürütür ve bu da iş parçacığı güvenliği gereksinimini en aza indirir. Bu nedenle, .NET Framework sınıf kitaplıkları varsayılan olarak iş parçacığı güvenli değildir.  
  
- Statik durumu değiştirecek statik yöntemler sağlamaktan kaçının. Ortak sunucu senaryolarında, statik durum istekler arasında paylaşılır, bu da birden çok iş parçacığının aynı anda bu kodu yürütebileceği anlamına gelir. Bu, hataları iş parçacığı olma olasılığını açar. İstekler arasında paylaşılmayan örneklere veri kapsülleyen bir tasarım kalıbı kullanmayı düşünün. Ayrıca, statik veriler eşitlenirse, durumu alter static Yöntemler arasındaki çağrılar kilitlenmeleri veya yedekli eşitlemeye neden olabilir ve bu da performansı olumsuz etkileyebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
- [İş Parçacıkları ve İş Parçacığı Oluşturma](../../../docs/standard/threading/threads-and-threading.md)
