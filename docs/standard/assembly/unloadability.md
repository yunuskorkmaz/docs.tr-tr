---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve kaldırmak için toplanabilir bir AssemblyLoadContext ve kaldırma başarısını önlemek için sorunları nasıl ayıklayacağınız hakkında bilgi edinin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 52cd864393342e2bc31f872b9d09cb484c2c8463
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972993"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

.NET Core 3,0 ile başlayarak, bir derleme kümesini yükleme ve daha sonra kaldırma özelliği desteklenir. .NET Framework, bu amaçla özel uygulama etki alanları kullanılmıştır, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.

.NET Core 3,0 ve sonraki sürümleri, aracılığıyla <xref:System.Runtime.Loader.AssemblyLoadContext>tasbilirliğini destekler. Bir dizi derlemeyi toplanabilir `AssemblyLoadContext`bir şekilde yükleyebilir, bunlarda Yöntemler yürütebilir veya yansıma kullanarak bunları inceleyebilirsiniz, son olarak `AssemblyLoadContext`yüklemesini kaldırabilirsiniz. Bu, yüklenmiş `AssemblyLoadContext`derlemeleri kaldırır.

Uygulama etki alanları kullanarak `AssemblyLoadContext` ve kullanarak kaldırma arasında bir sorun olduğunu fark eden bir farklılık vardır. AppDomain ile, kaldırma zorlanır. Kaldırma sırasında, hedef AppDomain 'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain 'de oluşturulan yönetilen COM nesneleri yok edilir vb. İle `AssemblyLoadContext`, kaldırma "işbirliği" dir. <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Yöntemi çağırmak yalnızca kaldırma işlemini başlatır. Kaldırma işlemi şu tarihten sonra bitiyor:

- Hiçbir iş parçacığı, `AssemblyLoadContext` çağrı yığınlarında öğesine yüklenen derlemelerden yöntemlere sahip değildir.
- İçinde `AssemblyLoadContext`yüklü derlemelerden hiçbir türden hiçbirisi, bu türlerin örneklerine ve kendi dışındaki `AssemblyLoadContext` derlemelere şunun tarafından başvuruluyor:
  - Zayıf başvurular haricinde ( `AssemblyLoadContext`<xref:System.WeakReference> veya <xref:System.WeakReference%601>) dışında başvuruları.
  - Güçlü GC tutamaçları (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> ya <xref:System.Runtime.InteropServices.GCHandleType>da<xref:System.Runtime.InteropServices.GCHandleType.Pinned>.), `AssemblyLoadContext`hem içinde hem de dışında.

## <a name="use-collectible-assemblyloadcontext"></a>Toplanabilir AssemblyLoadContext kullanın

Bu bölüm `AssemblyLoadContext`, bir .NET Core uygulamasını toplanabilir bir şekilde yüklemek, giriş noktasını yürütmek ve sonra kaldırmak için basit bir yol gösteren ayrıntılı bir adım adım öğretici içerir. ' De tüm bir örnek [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)bulabilirsiniz.

### <a name="create-a-collectible-assemblyloadcontext"></a>Toplanabilir bir AssemblyLoadContext oluşturma

Sınıfından sınıfınızı <xref:System.Runtime.Loader.AssemblyLoadContext> türetmeniz ve <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodunu aşırı yüklemeniz gerekir. Bu yöntem, yüklenmiş `AssemblyLoadContext`derlemelerin bağımlılıkları olan tüm derlemelere başvuruları çözümler.
Aşağıdaki kod, en basit özel `AssemblyLoadContext`örneğine bir örnektir:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Gördüğünüz gibi, `Load` yöntemi döndürür `null`. Bu, tüm bağımlılık derlemelerinin varsayılan bağlamına yüklendiği ve yeni bağlamın yalnızca açıkça kendisine yüklenmiş derlemeleri içerdiği anlamına gelir.

Bağımlılıkların `AssemblyLoadContext` bir kısmını veya tümünü de yüklemek istiyorsanız, `Load` yöntemi `AssemblyDependencyResolver` içinde kullanabilirsiniz. , `AssemblyDependencyResolver` Derleme adlarını, bağlam içine yüklenen ana derlemenin dizininde bulunan *. Deps. JSON* dosyasını ve bu dizindeki derleme dosyalarını kullanarak mutlak derleme dosya yollarına dönüştürür.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Özel toplanabilir bir AssemblyLoadContext kullanın

Bu bölümde, öğesinin `TestAssemblyLoadContext` daha basit sürümünün kullanıldığını varsayılır.

Özel `AssemblyLoadContext` bir örneği oluşturabilir ve bunu aşağıdaki gibi bir derlemeyi yükleyebilirsiniz:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Yüklenen derleme `TestAssemblyLoadContext.Load` tarafından başvurulan derlemelerin her biri için yöntemi çağrılır, böylece, `TestAssemblyLoadContext` derlemenin nereden alınacağını karar verebilir. Bizim örneğimizde, varsayılan olarak `null` çalışma zamanının derlemeleri yüklemek için kullandığı konumlardan varsayılan bağlamına yüklenmesi gerektiğini göstermek için döndürür.

Bir derleme yüklendikten sonra, bundan sonra bir yöntemi çalıştırabilirsiniz. `Main` Yöntemi çalıştırın:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Yöntem çağrıldıktan sonra, `Unload` yöntemi özel `AssemblyLoadContext` üzerinde çağırarak veya bir başvuruya sahip olduğunuz başvurunun `AssemblyLoadContext`kurtumı aracılığıyla kaldırmayı başlatabilirsiniz. `Main`

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Bu, test derlemesini kaldırmak için yeterlidir. `TestAssemblyLoadContext`, ,Ve`MethodInfo` ( )`Assembly.EntryPoint`öğesinin yığın yuvası başvuruları (gerçek veya JIT tarafından tanıtılan Yereller) tarafından etkin tutulmasını gerektirmediğinden emin olmak için bunu tamamen ayrı bir bağımsız olmayan yönteme yerleştirelim `Assembly`. Bu, `TestAssemblyLoadContext` canlı kalmasını sağlayabilir ve kaldırma özelliğini engelleyebilir.

Ayrıca, daha sonra kaldırma tamamlamayı algılamak için `AssemblyLoadContext` kullanabilmeniz için zayıf bir başvuru döndürün.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Artık derlemeyi yüklemek, çalıştırmak ve kaldırmak için bu işlevi çalıştırabilirsiniz.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ancak, kaldırma hemen tamamlanmaz. Daha önce belirtildiği gibi, test derlemesindeki tüm nesneleri toplamak için GC 'yi kullanır. Çoğu durumda, kaldırma işleminin tamamlanmasını beklemek gerekli değildir. Ancak, kaldırma işlemi bittiğini bilmemiz yararlı olduğu durumlar vardır. Örneğin, diskten özel `AssemblyLoadContext` olarak yüklenen derleme dosyasını silmek isteyebilirsiniz. Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir. Bir GC tetikleyip, özel `AssemblyLoadContext` 'e yönelik zayıf başvuru olarak `null`, hedef nesnenin toplandığını belirten bir döngüde bekleyen sonlandırıcıları bekler. Çoğu durumda döngünün yalnızca bir geçişinin gerekli olduğunu unutmayın. Bununla birlikte, içinde `AssemblyLoadContext` çalışan kod tarafından oluşturulan nesnelerin sonlandırıcılarda olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Kaldırma olayı

Bazı durumlarda, kaldırma işlemi başlatıldığında bir özel `AssemblyLoadContext` öğesine yüklenen kodun bazı temizleme işlemleri gerçekleştirmesi gerekebilir. Örneğin, iş parçacıklarını durdurmalı, bazı güçlü GC tutamaçlarını temizleyebiliyor. `Unloading` Olay bu gibi durumlarda kullanılabilir. Gerekli temizleme işlemini gerçekleştiren bir işleyici bu olaya bağlanabilir.

### <a name="troubleshoot-unloadability-issues"></a>Kaldırma sorunları sorunlarını giderme

Boşaltma 'nın işbirliksel doğası nedeniyle, verileri toplanabilir `AssemblyLoadContext` bir şekilde tutmanın ve kaldırma işlemini engellediği başvuruların hakkında unutmak çok kolay. Bu, başvuruları tutabilecek öğelerin (bazı belirgin olmayan) bir özeti aşağıdadır:

- Bir yığın yuvasında veya bir işlemci kaydındaki saklanan düzenli `AssemblyLoadContext`başvurular (Kullanıcı kodu tarafından açıkça oluşturulan ya da dolaylı olarak JIT tarafından), bir statik değişken veya güçlü/sabitleme GC tutamacı ve geçişli işaret:
  - Toplanabilir öğesine yüklenmiş bir bütünleştirilmiş kod `AssemblyLoadContext`.
  - Bu tür bir derlemeden bir tür.
  - Bu tür bir derlemeden bir türün örneği.
- Toplanabilir öğesine yüklenen bir derlemeden kod çalıştıran iş parçacıkları `AssemblyLoadContext`.
- Toplanabilir içinde oluşturulan özel toplanabilir `AssemblyLoadContext` türlerin örnekleri`AssemblyLoadContext`
- Geri <xref:System.Threading.RegisteredWaitHandle> çağırmaların özel içindeki yöntemlere ayarlandığı bekleyen örnekler`AssemblyLoadContext`

Yığın yuvası/işlemci kaydını bulma ipuçları bir nesneyi kök olarak kaydeder:

- İşlev çağrısı sonuçlarının doğrudan başka bir işleve geçirilmesi, Kullanıcı tarafından oluşturulmuş bir yerel değişken olmasa da kök oluşturabilir.
- Bir nesne başvurusu bir yöntemde herhangi bir noktada kullanılabilirse JıT, başvuruyu, geçerli işlevde istediği sürece bir yığın yuvası/işlemci kaydı içinde tutmaya karar vermiş olabilir.

## <a name="debug-unloading-issues"></a>Hata ayıklama kaldırma sorunları

Kaldırma ile ilgili hata ayıklama sorunları sıkıcı olabilir. `AssemblyLoadContext` Canlı neleri tutabilen, ancak kaldırma başarısız olursa, bu durumlara ulaşabilirsiniz.
Bu, sos eklentisi ile WinDbg (UNIX üzerinde lldb) ile ilgili yardım için en iyi uygulamalar. `LoaderAllocator` Belirli`AssemblyLoadContext` bir canlı kuruluşa ait olanları bulmanız gerekir.
Bu eklenti, GC yığın nesnelerine, hiyerarşilerine ve köklerine bakabilmeniz için izin verir.
Eklentiyi hata ayıklayıcıya yüklemek için, hata ayıklayıcı komut satırına aşağıdaki komutu girin:

WinDbg 'de (.NET Core uygulamasına bölünmediği zaman, WinDbg olarak görünür):

```console
.loadby sos coreclr
```

LLDB 'de:

```console
plugin load /path/to/libsosplugin.so
```

Daha sonra, kaldırma sorunları olan bir örnek programda hata ayıklamaya deneyelim. Kaynak kodu aşağıda verilmiştir. Bunu WinDbg altında çalıştırdığınızda, program, kaldırma başarısını denetlemeye çalıştıktan sonra hata ayıklayıcıya hemen sonra sonlandırır. Daha sonra Bu küller için aramaya başlayabilirsiniz.

UNIX üzerinde lldb kullanarak hata ayıklaması yaparsanız, aşağıdaki örneklerde yer alan sos komutlarının önünde yoktur `!` .

```console
!dumpheap -type LoaderAllocator
```

Bu komut, GC yığınında olan içeren `LoaderAllocator` bir tür adı olan tüm nesneleri döker. Aşağıda bir örnek verilmiştir:

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48     
000002b78000ceb0 00007ffadc93a218       24     

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

Aşağıdaki "İstatistikler:" bölümünde, ilgilendiğimiz nesne olan `MT` öğesine`MethodTable` `System.Reflection.LoaderAllocator`ait olan () öğesini işaretleyin. Ardından, başındaki listede, `MT` eşleşen girdiyi bulun ve nesnenin adresini alın. Bu durumda, "000002b78000ce40"

Artık `LoaderAllocator` nesnenin adresini öğrendiğimiz için, GC köklerinin bulunması için başka bir komut de kullanabiliriz

```console
!gcroot -all 0x000002b78000ce40 
```

Bu komut, `LoaderAllocator` örneğe yol açabilecek nesne başvuruları zincirini döker. Liste, `LoaderAllocator` etkin olan ve bu nedenle hata ayıklaması yaptığınız sorunun çekirdeği olan köküyle başlar. Kök bir yığın yuvası, bir işlemci kaydı, bir GC tanıtıcısı veya statik değişken olabilir.

`gcroot` Komutun çıktısının bir örneği aşağıda verilmiştir:

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

Şimdi, bu işlemi çözebilmeniz için kökün bulunduğu yeri belirlemeniz gerekir. En kolay durum, kök bir yığın yuvası veya bir işlemci kaydı olduğunda olur. Bu durumda, `gcroot` çerçevesi kök içeren ve bu işlevi yürüten iş parçacığı olan işlevin adını gösterir. Zor durum, kökün bir statik değişken veya bir GC tutamacı olması durumunda olur. 

Önceki örnekte, ilk kök, adresindeki `System.Reflection.RuntimeMethodInfo` `rbp-20` işlevin `example.Program.Main(System.String[])` çerçevesinde depolanan tür yereldir (`rbp` işlemci yazmacı `rbp` olur ve-20 Bu kaydın onaltılık bir uzaklığında oluşur).

İkinci kök, `test.Test` sınıfının bir örneğine başvuru tutan normal `GCHandle` (güçlü) bir sınıftır. 

Üçüncü kök sabitlenmiş `GCHandle`bir. Bu, aslında statik bir değişkendir. Ne yazık ki, söylemek için bir yol yoktur. Başvuru türleri için statiği, iç çalışma zamanı yapılarında yönetilen nesne dizisinde depolanır.

Bir iş parçacığının, `AssemblyLoadContext` `AssemblyLoadContext` yığınında üzerine yüklenmiş bir derlemeden bir yöntemi olduğunda bir, öğesinin kaldırılmasını engelleyebilen başka bir durum. Tüm iş parçacıklarının yönetilen çağrı yığınlarının dökümünü yaparak bunu kontrol edebilirsiniz:

```console
~*e !clrstack
```

Komut "tüm iş parçacıkları `!clrstack` için geçerlidir" anlamına gelir. Örnek için bu komutun çıktısı aşağıda verilmiştir. Ne yazık ki, UNIX üzerinde lldb tüm iş parçacıkları için bir komut uygulamak için herhangi bir yola sahip değildir, bu nedenle iş parçacıklarını el ile değiştirmek ve `clrstack` komutu yinelemek için çare olmanız gerekir.
Hata ayıklayıcının "yönetilen yığında ilerleme yapılamıyor" ifadesini belirten tüm iş parçacıklarını yoksayın.

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998] 
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28] 
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0] 
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000 
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568] 
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0] 

```

Gördüğünüz gibi son iş parçacığı `test.Program.ThreadProc()`. Bu, öğesine `AssemblyLoadContext`yüklenen derlemeden bir işlevdir ve bu sayede `AssemblyLoadContext` canlı tutar.

## <a name="example-source-with-unloadability-issues"></a>Loadability sorunları olan örnek kaynak

Aşağıdaki kod, önceki hata ayıklama örneğinde kullanılır.

### <a name="main-testing-program"></a>Ana test programı

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>TestAssemblyLoadContext içine yüklenen program

Aşağıdaki kod, ana test programındaki `ExecuteAndUnload` yöntemine geçirilen *test. dll dosyasını* temsil eder.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
