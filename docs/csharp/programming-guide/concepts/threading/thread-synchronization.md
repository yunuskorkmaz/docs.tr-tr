---
title: İş parçacığı eşitleme (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 138b94ef8ae5fc54e42277127f9b22f88803457f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338617"
---
# <a name="thread-synchronization-c"></a>İş parçacığı eşitleme (C#)
Aşağıdaki bölümlerde, özellikleri ve kaynakları birden çok iş parçacıklı uygulamalarda erişimi eşitlemek için kullanılan sınıflar açıklanmaktadır.  
  
 Bir uygulamada birden çok iş parçacığı kullanmanın avantajları her iş parçacığı zaman uyumsuz olarak yürütür biridir. Windows uygulamaları için bu uygulama penceresi arka planda gerçekleştirilecek uzun süren görevler sağlar ve denetimleri yanıt verebilir durumda kalır. Uygulamaları, çoklu iş parçacığı kullanımı sunucusu için farklı bir iş parçacığıyla her gelen istek işleme yeteneği sağlar. Önceki istek tam memnun olsaydı kadar Aksi durumda, her yeni isteği bakım değil.  
  
 Ancak, zaman uyumsuz yapısı dosya tanıtıcısı, ağ bağlantıları ve bellek gibi kaynaklara erişmek iş parçacığı anlamına gelir, Eşgüdümlü olması gerekir. Aksi durumda, iki veya daha fazla iş parçacığı aynı anda, diğerinin eylemlerini her farkında aynı kaynak erişebilir. Beklenmeyen veri bozulması sonucudur.  
  
 Tam Sayı sayısal veri türleri üzerinde basit işlemleri için iş parçacıklarını eşitleme üyeleriyle gerçekleştirilebilir <xref:System.Threading.Interlocked> sınıfı. İçin tüm diğer veri türleri ve iş parçacığı güvenli olmayan kaynakları, çoklu iş parçacığı kullanımı yalnızca güvenli bir şekilde yapıları bu konudaki kullanılarak gerçekleştirilebilir.  
  
 Birden çok iş parçacıklı programlama hakkında arka plan bilgileri için bkz:  
  
-   [Yönetilen İş Parçacığı Oluşturma Temelleri](../../../../standard/threading/managed-threading-basics.md)  
  
-   [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Yönetilen İş Parçacığı Oluşturma En İyi Yöntemleri](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>Lock anahtar sözcüğü  
 C# `lock` deyimi bir kod bloğu kesintisiz tamamlama çalıştığından emin olmak için kullanılabilir diğer iş parçacıkları tarafından. Bu kod bloğu boyunca belirli bir nesne için karşılıklı dışlama kilidi elde ederek gerçekleştirilir.  
  
 A `lock` deyimi bir nesne bir bağımsız değişken olarak verilen ve aynı anda yalnızca bir iş parçacığı tarafından yürütülecek olan kod bloğu tarafından izlenir. Örneğin:  
  
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
  
 Sağlanan bağımsız değişken `lock` anahtar sözcüğü bir başvuru türüne göre bir nesne olmalıdır ve kilidi kapsamını tanımlamak için kullanılır. Yukarıdaki örnekte, kilit kapsamı çünkü bu işleve sınırlıdır nesnesine başvuru `lockThis` dışında işlevi yok. Böyle bir başvuru yoksa, kilit kapsamı bu nesneye genişletir. NET olarak söylemek sağlanan nesne, yalnızca birden çok iş parçacığı arasında rastgele bir örneği olabilir paylaşılan kaynağı benzersiz şekilde tanımlamak için kullanılır. Uygulamada, ancak bu nesne genellikle hangi iş parçacığı için eşitleme gereklidir kaynak temsil eder. Örneğin, bir kapsayıcı nesne birden çok iş parçacığı tarafından kullanılacak ise kilitlemek için kapsayıcı sonra geçirilebilir ve kilidi aşağıdaki eşitlenmiş kod bloğu kapsayıcı erişir. Başka bir iş parçacığı kilitler sürece aynı erişmeden önce içerecek ardından nesneye erişimi güvenli bir şekilde eşitlenir.  
  
 Genellikle, üzerinde kilitleme önlemek en iyisidir bir `public` türü veya nesne örneklerini uygulamanızı denetiminin dışındadır. Örneğin, `lock(this)` denetiminiz dışında kod nesnesi üzerinde kilit çünkü örneği genel olarak, erişilebiliyorsa sorunlu olabilir. Bu, burada bu sürüm için aynı nesne iki veya daha fazla iş parçacığı bekleyin kilitlenme durumlar oluşturabilirsiniz. Bir nesne aksine bir genel veri türünde kilitleme aynı nedenden dolayı sorunlara neden olabilir. Değişmez değer dizeleri kilitleme özellikle riskli değişmez değer dizeleri olduğundan *interned* ortak dil çalışma zamanı (CLR) tarafından. Bunun anlamı herhangi belirli bir dizeyi bir örneği için tüm program değişmez değer, tüm sabit değeri tam aynı nesneyi temsil uygulama etki alanları, çalışan tüm iş parçacığı üzerinde. Sonuç olarak, kilit aynı içeriği bir dizeyle herhangi bir yerden uygulama işlemi kilitler bu dizeyi uygulamadaki tüm örneklerini yerleştirilmiş. Sonuç olarak, değil interned özel veya korumalı üye kilitlemek en iyisidir. Bazı sınıflar, özellikle kilitleme üyeleri sağlar. <xref:System.Array> Türü, örneğin sağlar <xref:System.Array.SyncRoot%2A>. Birçok koleksiyon türleri sağlayan bir `SyncRoot` de üye.  
  
 Hakkında daha fazla bilgi için `lock` deyimi, aşağıdaki konulara bakın:  
  
-   [lock Deyimi](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>İzlemeler  
 Gibi `lock` anahtar sözcüğü, izleyicileri birden çok iş parçacığı tarafından eşzamanlı yürütülmesini kod bloklarını engellemek. <xref:System.Threading.Monitor.Enter%2A> Yöntemi aşağıdaki deyime devam etmek tek bir iş parçacığı sağlar; diğer tüm iş parçacıklarının kadar yürütme iş parçacığı çağrıları engellenen <xref:System.Threading.Monitor.Exit%2A>. Bu yalnızca gibi kullanmaktır `lock` anahtar sözcüğü. Örneğin:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Bu eşdeğerdir:  
  
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
  
 Kullanarak `lock` anahtar sözcüğü, genellikle tercih edilen kullanarak üzerinden <xref:System.Threading.Monitor> doğrudan, hem de çünkü sınıf `lock` daha kısa olduğundan ve çünkü `lock` korunan kod bile oluşturursa temel İzleyici serbest yöntem başlanmasını sağlar bir özel durum. Bu ile gerçekleştirilir `finally` anahtar sözcüğü olup bir özel durum bağımsız olarak kendi ilişkili kod bloğu yürütür.  
  
## <a name="synchronization-events-and-wait-handles"></a>Eşitleme olayları ve bekleme tanıtıcıları  
 Kilitleme veya İzleyici kullanarak iş parçacığı duyarlı kod bloklarını eşzamanlı yürütülmesini engellemek için yararlıdır, ancak bu yapıları başka bir olay iletişim kurmak bir iş parçacığı izin vermez. Bu gerektirir *eşitleme olayları*, iki durumlu birine sahip nesneleri olduğu iş ve beklemediğiniz iş etkinleştirmek ve iş parçacıklarını askıya almak için kullanılabilir. İş parçacıkları unsignaled bir eşitleme olay beklemeye yapılan tarafından askıya alınabilir ve olay işaret durumuna değiştirerek etkinleştirilebilir. Bir iş parçacığı zaten işareti olaya bekleyin kullanmaya çalışırsa, sonra iş parçacığı gecikme olmadan yürütmeye devam eder.  
  
 Eşitleme olayları iki tür vardır: <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>. Bunlar yalnızca, farklı <xref:System.Threading.AutoResetEvent> değişikliklerden işaret çok unsignaled otomatik olarak herhangi bir zaman, bir iş parçacığı etkinleştirir. Buna karşılık, bir <xref:System.Threading.ManualResetEvent> herhangi bir sayıda iş durumuna göre etkinleştirilmesi için iş parçacığı sağlar ve yalnızca bir unsignaled döner duruma kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır.  
  
 İş parçacığı arama bekleme yöntemlerden biri tarafından olaylarına gibi beklenecek yapılabilir <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, veya <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> tek bir olay işaret hale beklemek için iş parçacığı neden <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> bir veya daha fazla belirtilen olayları işaret hale kadar bir iş parçacığı engeller ve <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> tüm belirtilen olaylar işaret hale kadar iş parçacığı engeller. Bir olay işaret olur, kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi çağrılır.  
  
 Aşağıdaki örnekte, bir iş parçacığı oluşturulur ve başlatan `Main` işlevi. Bir olay kullanarak yeni bir iş parçacığı bekler <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Olay yürütüyor birincil iş parçacığı tarafından işaret hale kadar iş parçacığı askıya `Main` işlevi. Olay işaret hale sonra yardımcı iş parçacığı döndürür. Bu durumda, olay yalnızca bir iş parçacığı etkinleştirme için ya da kullanıldığından <xref:System.Threading.AutoResetEvent> veya <xref:System.Threading.ManualResetEvent> sınıfları kullanılabilirdi.  
  
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
 A *mutex* bir izleme; benzer, eşzamanlı yürütülmesini kod bloğunu birden çok iş parçacığı tarafından aynı anda engeller. Aslında, adı "mutex" kısaltılmış "birbirini dışlayan." terimi biçimidir İzleyicilerin aksine, ancak bir mutex iş parçacığı işlemler arasında eşitlemek için kullanılır. Bir mutex tarafından temsil edilen <xref:System.Threading.Mutex> sınıfı.  
  
 İşlemler arası eşitleme için kullanıldığında, bir mutex adlı bir *mutex adlı* başka bir uygulamada kullanılacak olduğundan ve bu nedenle bir genel veya statik değişken yoluyla paylaşılamaz. İki uygulamanın aynı mutex nesnesi erişebilmesi için bir ad verilmelidir.  
  
 Bir mutex içi işlem iş parçacığı eşitleme için kullanılır ancak kullanarak <xref:System.Threading.Monitor> izleyiciler .NET Framework için özellikle tasarlanmış olması nedeniyle genellikle tercih edilir ve bu nedenle daha iyi kaynak kullanımını olun. Buna karşılık, <xref:System.Threading.Mutex> bir Win32 yapısı için bir sarmalayıcı sınıftır. Bir İzleyici'den daha güçlü olsa da, bir mutex tarafından gerekli olandan daha pkı'ya pahalıdır birlikte çalışma geçişleri gerektirir <xref:System.Threading.Monitor> sınıfı. Bir mutex kullanma örneği için bkz: [zaman uyumu sağlayıcılar](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Interlocked sınıfı  
 Yöntemlerini kullanabilirsiniz <xref:System.Threading.Interlocked> birden çok iş parçacığı aynı anda güncelleştirmek veya aynı değeri karşılaştırmak çalıştığınızda oluşabilecek sorunları önlemek için sınıf. Bu sınıfı yöntemlerinin güvenle artışı sağlar, azaltma, exchange ve herhangi bir iş parçacığı değerleri Karşılaştır.  
  
## <a name="readerwriter-locks"></a>ReaderWriter kilitleri  
 Bazı durumlarda, yalnızca veriler yazılırken zaman bir kaynağı kilitlemek ve birden çok istemciye veri güncelleştirilmiyor eşzamanlı olarak veri okumaya izin vermek isteyebilirsiniz. <xref:System.Threading.ReaderWriterLock> Sınıfı bir iş parçacığı kaynak değiştiriyor, ancak kaynak okunurken özel olmayan erişim sağlayan bir kaynağa özel erişim zorlar. ReaderWriter kilitleri beklemek bile bu iş parçacığı verileri güncelleştirmek gerektiğinde değil başka bir iş parçacığı neden özel kilit kullanışlı bir alternatiftir.  
  
## <a name="deadlocks"></a>Kilitlenmeleri  
 İş parçacığı eşitleme birden çok iş parçacıklı uygulamalarda çok değerli bir kaynak, ancak her zaman oluşturma tehlike bir `deadlock`, burada birden çok iş parçacığı diğer için bekliyor ve bir durmasına uygulama gelir. Kilitlenme araba dört yönlü durağında durdurulur ve her birinin diğeri için gitmek bekliyor. bir durum benzerdir. Kilitlenmeler önleme önemlidir; dikkatli planlama anahtardır. Genellikle, kodlama başlamadan önce birden çok iş parçacıklı uygulamalar diyagram kilitlenme durumlarda tahmin edebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [Birden çok iş parçacıklı uygulamalar (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [lock Deyimi](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [Karşılıklı dışlamalar](../../../../standard/threading/mutexes.md)  
 [Birbirine Kenetlenmiş İşlemler](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Çoklu İş Parçacığı Kullanımı için Veri Eşitleme](../../../../standard/threading/synchronizing-data-for-multithreading.md)
