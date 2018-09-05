---
title: İş parçacığı eşitleme (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 6f0fe42c06b27369612cf586c7a93ce098822162
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509392"
---
# <a name="thread-synchronization-c"></a>İş parçacığı eşitleme (C#)
Aşağıdaki bölümlerde, özellikleri ve kaynakları birden çok iş parçacıklı uygulamalarda erişimi eşitlemek için kullanılan sınıflar açıklanmaktadır.  
  
 Bir uygulamada birden çok iş parçacığı kullanmanın avantajları her iş parçacığı zaman uyumsuz olarak yürütür biridir. Windows uygulamaları için bu uygulama penceresinin arka planda gerçekleştirilecek zaman alan görevlerin sağlar ve denetimleri yanıt verebilir durumda kalması. Uygulamalar, çoklu iş parçacığı kullanımı, sunucu için farklı bir iş parçacığına gelen her bir istekle işleyebilme yeteneği sağlar. Önceki istek tam olarak memnun kadar Aksi takdirde, her yeni isteği verilemeyen.  
  
 Ancak, zaman uyumsuz dosya tanıtıcıları, ağ bağlantıları ve bellek gibi kaynaklara erişen iş parçacığı anlamına gelir yapısını koordine edilmelidir. Aksi takdirde, iki veya daha fazla iş parçacığı aynı zamanda, diğer kişinin eylemlerini her farkında aynı kaynağa erişebilir. Beklenmeyen veri bozulması sonucudur.  
  
 Tamsayı sayısal veri türleri üzerinde basit işlemleri için iş parçacığı eşitleme üyeleriyle gerçekleştirilebilir <xref:System.Threading.Interlocked> sınıfı. İçin tüm diğer veri türleri ve iş parçacığı güvenli olmayan kaynaklar, çoklu iş parçacığı kullanımı yalnızca güvenli bir şekilde bu konudaki yapıları kullanarak gerçekleştirilebilir.  
  
 Çok iş parçacıklı programlama hakkında bilgi için bkz:  
  
-   [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../../standard/threading/managed-threading-basics.md)  
  
-   [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Lock anahtar sözcüğü  
 C# `lock` deyimi bir kod bloğu kesintisiz tamamlanması için çalıştığından emin olmak için kullanılabilir başka iş parçacıklarının engellemelerinden. Bu işlem, kod bloğunun süresi için karşılıklı dışlama kilidini belirli nesne elde ederek gerçekleştirilir.  
  
 A `lock` deyimi bir nesne bir bağımsız değişken olarak verilir ve bir kerede yalnızca bir iş parçacığı tarafından yürütülecek bir kod bloğu tarafından izlenir. Örneğin:  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 Sağlanan bağımsız değişken `lock` anahtar sözcüğü bir başvuru türüne göre bir nesne olmalıdır ve kilit kapsamını tanımlamak için kullanılır. Yukarıdaki örnekte, kilit kapsamı olduğundan bu işleve sınırlıdır nesnesine başvuru `lockThis` dışında işlev yok. Böyle bir başvuruyu eksik, kilit kapsamı bu nesneye kapsayacak şekilde genişletilebilir. NET olarak söylemek gerekirse, sağlanan nesne, yalnızca rastgele sınıfı örneğini olabilmeleri birden çok iş parçacıkları arasında paylaşılan kaynağı benzersiz şekilde tanımlamak için kullanılır. Uygulamada, ancak bu nesne genellikle hangi iş parçacığı için eşitleme gereklidir kaynak temsil eder. Örneğin, bir kapsayıcı nesnesi birden çok iş parçacıkları tarafından kullanılacaksa, kilitlemek için kapsayıcı ardından geçirilebilir ve kilit aşağıdaki eşitlenmiş kod bloğu kapsayıcı erişir. Diğer iş parçacıklarını kilit üzerinde sürece aynı erişmeden önce içeren ve ardından nesnesine erişimi güvenli bir şekilde eşitlenir.  
  
 Genel olarak, üzerinde kilitlenmesini önlemek en iyi bir `public` türü veya uygulamanızı kontrolü nesne örneği. Örneğin, `lock(this)` denetiminiz dışında kod nesne üzerinde kilit çünkü örnek bir genel olarak, erişilebiliyorsa sorunlara neden olabilir. Bu, burada iki veya daha fazla iş parçacığı aynı nesne sürümü beklemenize kilitlenme durumlar oluşturabilir. Bir nesne yerine bir genel veri türü üzerinde kilitleme aynı nedenden dolayı sorunlara neden olabilir. Değişmez değer dizeleri kilitleme özellikle riskli değişmez değer dizeleri olduğundan *interned* ortak dil çalışma zamanı (CLR) tarafından. Herhangi bir dize örneği için tüm programı sabit değeri, değişmez değer tüm tam aynı nesneyi temsil yani uygulama etki alanları, tüm iş parçacıkları üzerinde çalışıyor. Sonuç olarak, bir kilit aynı içeriğe sahip bir dize herhangi bir uygulama işlemi kilitler o dizeyi uygulamanın tüm örneklerini yerleştirildiği. Sonuç olarak değil interned özel veya korumalı bir üye kilitlemek en iyisidir. Bazı sınıflar, özellikle kilitlemek için üyeleri sağlar. <xref:System.Array> Türü, örneğin sağlar <xref:System.Array.SyncRoot%2A>. Çok sayıda koleksiyon türleri sağlar bir `SyncRoot` üyesi de.  
  
 Hakkında daha fazla bilgi için `lock` deyimi, aşağıdaki konulara bakın:  
  
-   [lock Deyimi](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>İzlemeler  
 Gibi `lock` anahtar sözcüğü, izleyiciler, birden çok iş parçacığı tarafından kod eş zamanlı yürütme taşları önlemek. <xref:System.Threading.Monitor.Enter%2A> Yöntemi aşağıdaki deyimleri devam etmek bir ve yalnızca bir iş parçacığı sağlar; diğer tüm iş parçacıklarının yürütme iş parçacığı çağrı kadar engellenir <xref:System.Threading.Monitor.Exit%2A>. Bu, yalnızca kullanma gibi `lock` anahtar sözcüğü. Örneğin:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Bu eşdeğerdir.  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 Kullanarak `lock` anahtar sözcüğü, genellikle tercih edilen yerine <xref:System.Threading.Monitor> hem doğrudan, çünkü sınıf `lock` daha kısa olduğundan ve çünkü `lock` bile korunan kod oluşturur, temel alınan İzleyici yayımlanan oluşturmasını sağlar bir özel durum. Bu ile gerçekleştirilir `finally` anahtar sözcüğü bir özel durum olup bağımsız olarak, ilişkili kod bloğunu yürütür.  
  
## <a name="synchronization-events-and-wait-handles"></a>Eşitleme olayları ve bekleme tanıtıcıları  
 Bir kilit ya da izleyiciyi kullanarak eşzamanlı iş parçacığı duyarlı kod bloklarının yürütülmesini önlemek için yararlıdır, ancak bu yapıları başka bir olaya iletişim kurmak bir iş parçacığı izin verme. Bu gerektirir *eşitleme olayları*, iki durumdan birinde olan nesneleri olan sinyal ve geri dönmesine etkinleştirmek ve iş parçacıklarını askıya almak için kullanılabilir. İş parçacıkları unsignaled bir eşitleme olay beklemek için yapılan tarafından askıya alınabilir ve sinyal olay durumu değiştirerek etkinleştirilebilir. Ardından bir iş parçacığı zaten işareti olaya beklenecek çalışırsa, iş parçacığı gecikme olmadan yürütme devam eder.  
  
 Eşitleme olayları iki tür vardır: <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>. Yalnızca, farklı <xref:System.Threading.AutoResetEvent> değişikliklerden sinyal çok unsignaled otomatik olarak istediğiniz zaman, bir iş parçacığı etkinleştirir. Buna karşılık, bir <xref:System.Threading.ManualResetEvent> herhangi bir sayıda sinyal durumuna göre etkinleştirilmesi için iş parçacığı verir ve yalnızca bir unsignaled döner durumuna kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır.  
  
 İş parçacıkları olayları bekleme yöntemleri çağıran bir tarafından gibi bekleyin yapılabilir <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, veya <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> tek bir olay sinyal haline gelir kadar beklenecek iş parçacığının neden <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> bir veya daha fazla belirtilen olayları sinyal haline kadar bir iş parçacığını engeller ve <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> belirtilen olayların tümünü sinyal haline kadar iş parçacığını engeller. Bir olayın sinyal haline gelir, kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi çağrılır.  
  
 Aşağıdaki örnekte, bir iş parçacığı oluşturulur ve başlangıç `Main` işlevi. Yeni iş parçacığı kullanarak bir olay bekler <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Yürütülmekte olan birincil iş parçacığı tarafından olayın sinyal haline gelir kadar iş parçacığı askıda `Main` işlevi. Olayın sinyal haline gelir sonra ikincil iş parçacığı döndürür. Bu durumda, olay yalnızca tek bir iş parçacığı etkinleştirme için ya da kullanıldığından <xref:System.Threading.AutoResetEvent> veya <xref:System.Threading.ManualResetEvent> sınıfları kullanılabilir.  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Mutex nesnesi  
 A *mutex* bir izleme; benzer, kod bloğunun aynı anda yürütülmesini birden fazla iş parçacığı tarafından aynı anda engeller. Aslında, adı "mutex" bir "birbirini." terimi kısaltılmış biçimindedir İzleyicilerin aksine, ancak iş parçacıkları süreçler arasında eşitlemek için bir mutex kullanılabilir. Bir mutex tarafından temsil edilen <xref:System.Threading.Mutex> sınıfı.  
  
 İşlemler arası eşitleme için kullanıldığında, bir mutex olarak adlandırılan bir *adlandırılmış mutex* , başka bir uygulamada kullanılmak üzere olduğundan ve bu nedenle bir genel veya statik değişken yoluyla paylaşılamaz. Her iki uygulama aynı mutex nesnesi erişebilmesi için bir ad verilmelidir.  
  
 İşlem içi iş parçacığı eşitleme için bir mutex kullanılabilse kullanarak <xref:System.Threading.Monitor> izleyiciler .NET Framework için özellikle tasarlanmış için genellikle tercih edilir ve bu nedenle daha iyi kaynak kullanımını olun. Buna karşılık, <xref:System.Threading.Mutex> bir Win32 yapısı için bir sarmalayıcı sınıftır. Bir izleyici daha güçlü olsa da, bir mutex tarafından gerekli olandan daha fazla hesaplama açısından pahalıdır birlikte çalışma geçişleri gerektirir <xref:System.Threading.Monitor> sınıfı. Bir mutex kullanılması, bir örnek için bkz. [mutex'ler](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked sınıfı  
 Yöntemlerini kullanabilirsiniz <xref:System.Threading.Interlocked> birden çok iş parçacığı aynı anda güncelleştirme ya da aynı değeri ile karşılaştırmak istediğinizde oluşabilecek sorunları önlemek için sınıf. Bu sınıftaki yöntemleri güvenli bir şekilde artışı sağlar, azaltma, exchange ve herhangi bir iş parçacığı değerlerini karşılaştırın.  
  
## <a name="readerwriter-locks"></a>ReaderWriter kilitleri  
 Bazı durumlarda, yalnızca veri yazılmakta olan, bir kaynak kilidi ve birden çok istemciye veri güncelleştirilmiyor aynı anda verilerini okumaya izin vermek isteyebilirsiniz. <xref:System.Threading.ReaderWriterLock> Sınıfı bir iş parçacığı kaynak değiştiriyor, ancak kaynağı okunurken münhasır olmayan erişim sağlayan bir kaynağa özel erişim zorlar. ReaderWriter kilitleri beklemek bile, bu iş parçacıkları verileri güncelleştirmek gerekmez, diğer iş parçacıklarını neden özel bir kilit kullanışlı bir alternatiftir.  
  
## <a name="deadlocks"></a>Kilitlenmeler  
 Çok iş parçacıklı uygulamalarda çok iş parçacığı eşitleme, ancak her zaman oluşturma olma tehlikesi yoktur bir `deadlock`burada diğer için bekleyen birden çok iş parçacığı ve uygulama bir durmasına gelir. Bir dört yönlü durağında otomobiller durdurulur ve her kişinin diğer gitmek bekleyen bir duruma yönelik bir kilitlenme benzerdir. Kilitlenmeler kaçınmak önemlidir; dikkatli planlama anahtardır. Kodlama başlamadan önce çok iş parçacıklı uygulamalar diyagram tarafından kilitlenmesi durumda genellikle tahmin edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Threading.Thread>  
- <xref:System.Threading.WaitHandle.WaitOne%2A>  
- <xref:System.Threading.WaitHandle.WaitAny%2A>  
- <xref:System.Threading.WaitHandle.WaitAll%2A>  
- <xref:System.Threading.Thread.Join%2A>  
- <xref:System.Threading.Thread.Start%2A>  
- <xref:System.Threading.Thread.Sleep%2A>  
- <xref:System.Threading.Monitor>  
- <xref:System.Threading.Mutex>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Interlocked>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading>  
- <xref:System.Threading.EventWaitHandle.Set%2A>  
- <xref:System.Threading.Monitor>  
- [lock Deyimi](../../../../csharp/language-reference/keywords/lock-statement.md)  
- [Karşılıklı dışlamalar](../../../../standard/threading/mutexes.md)  
- [Birbirine Kenetlenmiş İşlemler](../../../../standard/threading/interlocked-operations.md)  
- [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
- [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../../standard/threading/synchronizing-data-for-multithreading.md)
