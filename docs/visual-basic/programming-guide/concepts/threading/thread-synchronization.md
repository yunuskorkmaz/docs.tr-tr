---
title: "İş parçacığı eşitleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04f485d1-8333-4510-9e72-c334e7427e7e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 643dbb6fdceb4e1cfd074d3a532787562dbfd03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-synchronization-visual-basic"></a>İş parçacığı eşitleme (Visual Basic)
Aşağıdaki bölümlerde, özellikleri ve kaynakları birden çok iş parçacıklı uygulamalarda erişimi eşitlemek için kullanılan sınıflar açıklanmaktadır.  
  
 Bir uygulamada birden çok iş parçacığı kullanmanın avantajları her iş parçacığı zaman uyumsuz olarak yürütür biridir. Windows uygulamaları için bu uygulama penceresi arka planda gerçekleştirilecek uzun süren görevler sağlar ve denetimleri yanıt verebilir durumda kalır. Uygulamaları, çoklu iş parçacığı kullanımı sunucusu için farklı bir iş parçacığıyla her gelen istek işleme yeteneği sağlar. Önceki istek tam memnun olsaydı kadar Aksi durumda, her yeni isteği bakım değil.  
  
 Ancak, zaman uyumsuz yapısı dosya tanıtıcısı, ağ bağlantıları ve bellek gibi kaynaklara erişmek iş parçacığı anlamına gelir, Eşgüdümlü olması gerekir. Aksi durumda, iki veya daha fazla iş parçacığı aynı anda, diğerinin eylemlerini her farkında aynı kaynak erişebilir. Beklenmeyen veri bozulması sonucudur.  
  
 Tam Sayı sayısal veri türleri üzerinde basit işlemleri için iş parçacıklarını eşitleme üyeleriyle gerçekleştirilebilir <xref:System.Threading.Interlocked> sınıfı. İçin tüm diğer veri türleri ve iş parçacığı güvenli olmayan kaynakları, çoklu iş parçacığı kullanımı yalnızca güvenli bir şekilde yapıları bu konudaki kullanılarak gerçekleştirilebilir.  
  
 Birden çok iş parçacıklı programlama hakkında arka plan bilgileri için bkz:  
  
-   [Yönetilen iş parçacığı oluşturma temelleri](../../../../standard/threading/managed-threading-basics.md)  
  
-   [İş parçacığı kullanma ve iş parçacığı oluşturma](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Yönetilen iş parçacığı oluşturma en iyi uygulamalar](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-and-synclock-keywords"></a>Kilit ve SyncLock anahtar sözcükler  
 Visual Basic `SyncLock` deyimi bir kod bloğu kesintisiz tamamlama çalıştığından emin olmak için kullanılabilir diğer iş parçacıkları tarafından. Bu kod bloğu boyunca belirli bir nesne için karşılıklı dışlama kilidi elde ederek gerçekleştirilir.  
  
 A `SyncLock` deyimi bir nesne bir bağımsız değişken olarak verilen ve aynı anda yalnızca bir iş parçacığı tarafından yürütülecek olan kod bloğu tarafından izlenir. Örneğin:  
  
```vb  
Public Class TestThreading  
    Dim lockThis As New Object  
  
    Public Sub Process()  
        SyncLock lockThis  
            ' Access thread-sensitive resources.  
        End SyncLock  
    End Sub  
End Class  
```  
  
 Sağlanan bağımsız değişken `SyncLock` anahtar sözcüğü bir başvuru türüne göre bir nesne olmalıdır ve kilidi kapsamını tanımlamak için kullanılır. Yukarıdaki örnekte, kilit kapsamı çünkü bu işleve sınırlıdır nesnesine başvuru `lockThis` dışında işlevi yok. Böyle bir başvuru yoksa, kilit kapsamı bu nesneye genişletir. NET olarak söylemek sağlanan nesne, yalnızca birden çok iş parçacığı arasında rastgele bir örneği olabilir paylaşılan kaynağı benzersiz şekilde tanımlamak için kullanılır. Uygulamada, ancak bu nesne genellikle hangi iş parçacığı için eşitleme gereklidir kaynak temsil eder. Örneğin, bir kapsayıcı nesne birden çok iş parçacığı tarafından kullanılacak ise kilitlemek için kapsayıcı sonra geçirilebilir ve kilidi aşağıdaki eşitlenmiş kod bloğu kapsayıcı erişir. Başka bir iş parçacığı kilitler sürece aynı erişmeden önce içerecek ardından nesneye erişimi güvenli bir şekilde eşitlenir.  
  
 Genellikle, üzerinde kilitleme önlemek en iyisidir bir `public` türü veya nesne örneklerini uygulamanızı denetiminin dışındadır. Örneğin, `lockThis` denetiminiz dışında kod nesnesi üzerinde kilit çünkü örneği genel olarak, erişilebiliyorsa sorunlu olabilir. Bu, burada bu sürüm için aynı nesne iki veya daha fazla iş parçacığı bekleyin kilitlenme durumlar oluşturabilirsiniz. Bir nesne aksine bir genel veri türünde kilitleme aynı nedenden dolayı sorunlara neden olabilir. Değişmez değer dizeleri kilitleme özellikle riskli değişmez değer dizeleri olduğundan *interned* ortak dil çalışma zamanı (CLR) tarafından. Bunun anlamı herhangi belirli bir dizeyi bir örneği için tüm program değişmez değer, tüm sabit değeri tam aynı nesneyi temsil uygulama etki alanları, çalışan tüm iş parçacığı üzerinde. Sonuç olarak, kilit aynı içeriği bir dizeyle herhangi bir yerden uygulama işlemi kilitler bu dizeyi uygulamadaki tüm örneklerini yerleştirilmiş. Sonuç olarak, değil interned özel veya korumalı üye kilitlemek en iyisidir. Bazı sınıflar, özellikle kilitleme üyeleri sağlar. <xref:System.Array> Türü, örneğin sağlar <xref:System.Array.SyncRoot%2A>. Birçok koleksiyon türleri sağlayan bir `SyncRoot` de üye.  
  
 Hakkında daha fazla bilgi için `SyncLock` deyimi, aşağıdaki konulara bakın:  
  
-   [SyncLock deyimi](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>İzlemeler  
 Gibi `SyncLock` anahtar sözcüğü, izleyicileri birden çok iş parçacığı tarafından eşzamanlı yürütülmesini kod bloklarını engellemek. <xref:System.Threading.Monitor.Enter%2A> Yöntemi aşağıdaki deyime devam etmek tek bir iş parçacığı sağlar; diğer tüm iş parçacıklarının kadar yürütme iş parçacığı çağrıları engellenen <xref:System.Threading.Monitor.Exit%2A>. Bu yalnızca gibi kullanmaktır `SyncLock` anahtar sözcüğü. Örneğin:  
  
```vb  
SyncLock x  
    DoSomething()  
End SyncLock  
```  
  
 Bu eşdeğerdir:  
  
```vb  
Dim obj As Object = CType(x, Object)  
System.Threading.Monitor.Enter(obj)  
Try  
    DoSomething()  
Finally  
    System.Threading.Monitor.Exit(obj)  
End Try  
```  
  
 Kullanarak `SyncLock` anahtar sözcüğü, genellikle tercih edilen kullanarak üzerinden <xref:System.Threading.Monitor> doğrudan, hem de çünkü sınıf `SyncLock` daha kısa olduğundan ve çünkü `SyncLock` korunan kod bile oluşturursa temel İzleyici serbest yöntem başlanmasını sağlar bir özel durum. Bu ile gerçekleştirilir `Finally` anahtar sözcüğü olup bir özel durum bağımsız olarak kendi ilişkili kod bloğu yürütür.  
  
## <a name="synchronization-events-and-wait-handles"></a>Eşitleme olayları ve bekleme tanıtıcıları  
 Kilitleme veya İzleyici kullanarak iş parçacığı duyarlı kod bloklarını eşzamanlı yürütülmesini engellemek için yararlıdır, ancak bu yapıları başka bir olay iletişim kurmak bir iş parçacığı izin vermez. Bu gerektirir *eşitleme olayları*, iki durumlu birine sahip nesneleri olduğu iş ve beklemediğiniz iş etkinleştirmek ve iş parçacıklarını askıya almak için kullanılabilir. İş parçacıkları unsignaled bir eşitleme olay beklemeye yapılan tarafından askıya alınabilir ve olay işaret durumuna değiştirerek etkinleştirilebilir. Bir iş parçacığı zaten işareti olaya bekleyin kullanmaya çalışırsa, sonra iş parçacığı gecikme olmadan yürütmeye devam eder.  
  
 Eşitleme olayları iki tür vardır: <xref:System.Threading.AutoResetEvent>, ve <xref:System.Threading.ManualResetEvent>. Bunlar yalnızca, farklı <xref:System.Threading.AutoResetEvent> değişikliklerden işaret çok unsignaled otomatik olarak herhangi bir zaman, bir iş parçacığı etkinleştirir. Buna karşılık, bir <xref:System.Threading.ManualResetEvent> herhangi bir sayıda iş durumuna göre etkinleştirilmesi için iş parçacığı sağlar ve yalnızca bir unsignaled döner duruma kendi <xref:System.Threading.EventWaitHandle.Reset%2A> yöntemi çağrılır.  
  
 İş parçacığı arama bekleme yöntemlerden biri tarafından olaylarına gibi beklenecek yapılabilir <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, veya <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>tek bir olay işaret hale beklemek için iş parçacığı neden <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> bir veya daha fazla belirtilen olayları işaret hale kadar bir iş parçacığı engeller ve <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> tüm belirtilen olaylar işaret hale kadar iş parçacığı engeller. Bir olay işaret olur, kendi <xref:System.Threading.EventWaitHandle.Set%2A> yöntemi çağrılır.  
  
 Aşağıdaki örnekte, bir iş parçacığı oluşturulur ve başlatan `Main` işlevi. Bir olay kullanarak yeni bir iş parçacığı bekler <xref:System.Threading.WaitHandle.WaitOne%2A> yöntemi. Olay yürütüyor birincil iş parçacığı tarafından işaret hale kadar iş parçacığı askıya `Main` işlevi. Olay işaret hale sonra yardımcı iş parçacığı döndürür. Bu durumda, olay yalnızca bir iş parçacığı etkinleştirme için ya da kullanıldığından <xref:System.Threading.AutoResetEvent> veya <xref:System.Threading.ManualResetEvent> sınıfları kullanılabilirdi.  
  
```vb  
Imports System.Threading  
  
Module Module1  
    Dim autoEvent As AutoResetEvent  
  
    Sub DoWork()  
        Console.WriteLine("   worker thread started, now waiting on event...")  
        autoEvent.WaitOne()  
        Console.WriteLine("   worker thread reactivated, now exiting...")  
    End Sub  
  
    Sub Main()  
        autoEvent = New AutoResetEvent(False)  
  
        Console.WriteLine("main thread starting worker thread...")  
        Dim t As New Thread(AddressOf DoWork)  
        t.Start()  
  
        Console.WriteLine("main thread sleeping for 1 second...")  
        Thread.Sleep(1000)  
  
        Console.WriteLine("main thread signaling worker thread...")  
        autoEvent.Set()  
    End Sub  
End Module  
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
 [Birden çok iş parçacıklı uygulamalar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [SyncLock deyimi](../../../../visual-basic/language-reference/statements/synclock-statement.md)  
 [Zaman uyumu sağlayıcılar](../../../../standard/threading/mutexes.md)  
 [Birbirine kenetlenmiş işlemler](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [İçin Veri Eşitleme çoklu iş parçacığı kullanımı](../../../../standard/threading/synchronizing-data-for-multithreading.md)
