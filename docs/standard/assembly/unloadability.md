---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve kaldırmak için toplanabilir bir AssemblyLoadContext ve kaldırma başarısını önlemek için sorunları nasıl ayıklayacağınız hakkında bilgi edinin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 9d1f604816dcbd7a84a3692b3cfd24481532789a
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865352"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

.NET Core 3,0 ile başlayarak, bir derleme kümesini yükleme ve daha sonra kaldırma özelliği desteklenir. .NET Framework, bu amaçla özel uygulama etki alanları kullanılmıştır, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.

.NET Core 3,0 ve sonraki sürümleri, aracılığıyla tasbilirliğini destekler <xref:System.Runtime.Loader.AssemblyLoadContext> . Bir dizi derlemeyi toplanabilir bir `AssemblyLoadContext` şekilde yükleyebilir, bunlarda Yöntemler yürütebilir veya yansıma kullanarak bunları inceleyebilirsiniz, son olarak yüklemesini kaldırabilirsiniz `AssemblyLoadContext` . Bu, öğesine yüklenen derlemeleri kaldırır `AssemblyLoadContext` .

Uygulama etki alanları kullanarak ve kullanarak kaldırma arasında bir sorun olduğunu fark eden bir farklılık vardır `AssemblyLoadContext` . AppDomain ile, kaldırma zorlanır. Kaldırma sırasında, hedef AppDomain 'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain 'te oluşturulan yönetilen COM nesneleri yok edilir ve bu şekilde devam eder. İle `AssemblyLoadContext` , kaldırma "işbirliği" dir. Yöntemi çağırmak <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> yalnızca kaldırma işlemini başlatır. Kaldırma işlemi şu tarihten sonra bitiyor:

- Hiçbir iş parçacığı, çağrı yığınlarında öğesine yüklenen derlemelerden yöntemlere sahip değildir `AssemblyLoadContext` .
- ' A yüklenmeyen derlemelerden türlerin hiçbiri, `AssemblyLoadContext` Bu türlerin örneklerine ve derlemelerinin kendisine göre başvuruluyor:
  - `AssemblyLoadContext`Zayıf başvurular haricinde ( <xref:System.WeakReference> veya) dışında başvuruları <xref:System.WeakReference%601> .
  - Güçlü çöp toplayıcı (GC) tutamaçları ([GCHandleType. normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) veya [GCHandleType. sabitlenmiş](xref:System.Runtime.InteropServices.GCHandleType.Pinned)), ikisinin içinde ve dışında `AssemblyLoadContext` .

## <a name="use-collectible-assemblyloadcontext"></a>Toplanabilir AssemblyLoadContext kullanın

Bu bölüm, bir .NET Core uygulamasını toplanabilir bir şekilde yüklemek `AssemblyLoadContext` , giriş noktasını yürütmek ve sonra kaldırmak için basit bir yol gösteren ayrıntılı bir adım adım öğretici içerir. ' De tüm bir örnek bulabilirsiniz [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading) .

### <a name="create-a-collectible-assemblyloadcontext"></a>Toplanabilir bir AssemblyLoadContext oluşturma

Sınıfından sınıfınızı türetmeniz <xref:System.Runtime.Loader.AssemblyLoadContext> ve metodunu geçersiz kılmanız gerekir <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> . Bu yöntem, yüklenmiş derlemelerin bağımlılıkları olan tüm derlemelere başvuruları çözümler `AssemblyLoadContext` .

Aşağıdaki kod, en basit özel örneğine bir örnektir `AssemblyLoadContext` :

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Gördüğünüz gibi, `Load` yöntemi döndürür `null` . Bu, tüm bağımlılık derlemelerinin varsayılan bağlamına yüklendiği ve yeni bağlamın yalnızca açıkça kendisine yüklenmiş derlemeleri içerdiği anlamına gelir.

Bağımlılıkların bir kısmını veya tümünü de yüklemek istiyorsanız, `AssemblyLoadContext` `AssemblyDependencyResolver` yöntemi içinde kullanabilirsiniz `Load` . , `AssemblyDependencyResolver` Derleme adlarını mutlak derleme dosyası yollarına çözümler. Çözümleyici, bağlamı içine yüklenen ana derlemenin dizinindeki dosya ve derleme dosyalarında *.deps.js* kullanır.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Özel toplanabilir bir AssemblyLoadContext kullanın

Bu bölümde, öğesinin daha basit sürümünün `TestAssemblyLoadContext` kullanıldığını varsayılır.

Özel bir örneği oluşturabilir `AssemblyLoadContext` ve bunu aşağıdaki gibi bir derlemeyi yükleyebilirsiniz:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Yüklenen derleme tarafından başvurulan derlemelerin her biri için `TestAssemblyLoadContext.Load` yöntemi çağrılır, böylece, `TestAssemblyLoadContext` derlemenin nereden alınacağını karar verebilir. Bizim örneğimizde, varsayılan `null` olarak çalışma zamanının derlemeleri yüklemek için kullandığı konumlardan varsayılan bağlamına yüklenmesi gerektiğini göstermek için döndürür.

Bir derleme yüklendikten sonra, bundan sonra bir yöntemi çalıştırabilirsiniz. Yöntemi çalıştırın `Main` :

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Yöntem çağrıldıktan sonra `Main` , `Unload` yöntemi özel üzerinde çağırarak `AssemblyLoadContext` veya bir başvuruya sahip olduğunuz başvurunun kurtumı aracılığıyla kaldırmayı başlatabilirsiniz `AssemblyLoadContext` .

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Bu, test derlemesini kaldırmak için yeterlidir. `TestAssemblyLoadContext`,, `Assembly` Ve `MethodInfo` ( `Assembly.EntryPoint` ) öğesinin yığın yuvası BAŞVURULARı (gerçek veya JIT tarafından tanıtılan Yereller) tarafından etkin tutulmasını gerektirmediğinden emin olmak için bunu tamamen ayrı bir bağımsız olmayan yönteme yerleştirelim. Bu, canlı kalmasını sağlayabilir `TestAssemblyLoadContext` ve kaldırma özelliğini engelleyebilir.

Ayrıca, `AssemblyLoadContext` daha sonra kaldırma tamamlamayı algılamak için kullanabilmeniz için zayıf bir başvuru döndürün.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Artık derlemeyi yüklemek, çalıştırmak ve kaldırmak için bu işlevi çalıştırabilirsiniz.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ancak, kaldırma hemen tamamlanmaz. Daha önce belirtildiği gibi, tüm nesneleri test derlemesinden toplamak için çöp toplayıcıyı kullanır. Çoğu durumda, kaldırma işleminin tamamlanmasını beklemek gerekli değildir. Ancak, kaldırma işlemi bittiğini bilmemiz yararlı olduğu durumlar vardır. Örneğin, diskten özel olarak yüklenen derleme dosyasını silmek isteyebilirsiniz `AssemblyLoadContext` . Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir. Çöp toplamayı tetikler ve özel 'e yönelik zayıf başvuru, `AssemblyLoadContext` `null` hedef nesnenin toplandığını belirten olarak, bir döngüde bekleyen sonlandırıcıları bekler. Çoğu durumda, yalnızca bir geçiş döngüsü gerekir. Bununla birlikte, içinde çalışan kod tarafından oluşturulan nesnelerin sonlandırıcılarda olduğu daha karmaşık durumlarda `AssemblyLoadContext` daha fazla geçiş gerekebilir.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Kaldırma olayı

Bazı durumlarda, kaldırma işlemi başlatıldığında bir özel öğesine yüklenen kodun `AssemblyLoadContext` bazı temizleme işlemleri gerçekleştirmesi gerekebilir. Örneğin, iş parçacıklarını durdurmanız veya güçlü GC tutamaçları temizlemesi gerekebilir. `Unloading`Olay bu gibi durumlarda kullanılabilir. Gerekli temizleme işlemini gerçekleştiren bir işleyici bu olaya bağlanabilir.

### <a name="troubleshoot-unloadability-issues"></a>Kaldırma sorunları sorunlarını giderme

Boşaltma 'nın işbirliğinin doğası gereği, öğeleri toplanabilir bir şekilde koruyan ve kaldırmayı engelleyen başvuruları unutmak kolaydır `AssemblyLoadContext` . Aşağıda, başvuruları tutabilecek varlıkların (bazı belirgin olmayan) bir özeti verilmiştir:

- `AssemblyLoadContext`Bir yığın yuvasında veya bir işlemci kaydındaki (Kullanıcı kodu tarafından açıkça oluşturulan veya örtük olarak tam zamanında (JIT) derleyici), statik bir değişken ya da güçlü (sabitleme) BIR GC tanıtıcısı veya bir güçlü (sabitleme) GC tutamacı saklanan toplanabilir dışında tutulan normal başvurular:
  - Toplanabilir öğesine yüklenmiş bir bütünleştirilmiş kod `AssemblyLoadContext` .
  - Bu tür bir derlemeden bir tür.
  - Bu tür bir derlemeden bir türün örneği.
- Toplanabilir öğesine yüklenen bir derlemeden kod çalıştıran iş parçacıkları `AssemblyLoadContext` .
- Toplanmasız şekilde oluşturulan özel, toplanabilir olmayan `AssemblyLoadContext` türlerin örnekleri `AssemblyLoadContext` .
- <xref:System.Threading.RegisteredWaitHandle>Geri çağırmaların, özel içindeki yöntemlere ayarlandığı bekleyen örnekler `AssemblyLoadContext` .

> [!TIP]
> Yığın yuvaları veya işlemci kayıtları 'nda depolanan ve bir öğesinin kaldırılmasını engelleyebilecek nesne başvuruları `AssemblyLoadContext` aşağıdaki durumlarda oluşabilir:
>
> - İşlev çağırma sonuçları, Kullanıcı tarafından oluşturulan yerel değişken olmasa bile, doğrudan başka bir işleve geçirilir.
> - JıT derleyicisi, bir yöntemde bir noktada kullanılabilir olan bir nesneye bir başvuru tutar.

## <a name="debug-unloading-issues"></a>Hata ayıklama kaldırma sorunları

Kaldırma ile ilgili hata ayıklama sorunları sıkıcı olabilir. Canlı neleri tutabilen `AssemblyLoadContext` , ancak kaldırma başarısız olursa, bu durumlara ulaşabilirsiniz. Bu, sos eklentisi ile WinDbg (UNIX üzerinde lldb) ile ilgili yardım için en iyi uygulamalar. Belirli bir canlı kuruluşa ait olanları bulmanız gerekir `LoaderAllocator` `AssemblyLoadContext` . SOS eklentisi, GC yığın nesnelerine, hiyerarşilerine ve köklerine bakabilmeniz için izin verir.

Eklentiyi hata ayıklayıcıya yüklemek için, hata ayıklayıcı komut satırına aşağıdaki komutu girin:

WinDbg 'de (.NET Core uygulamasına bölünmediği zaman, WinDbg olarak görünür):

```console
.loadby sos coreclr
```

LLDB 'de:

```console
plugin load /path/to/libsosplugin.so
```

Daha sonra, kaldırma sorunları olan bir örnek programda hata ayıklaması yapmanızı sağlar. Kaynak kodu aşağıda verilmiştir. Bunu WinDbg altında çalıştırdığınızda, program, kaldırma başarısını denetlemeye çalıştıktan sonra hata ayıklayıcıya hemen sonra sonlandırır. Daha sonra Bu küller için aramaya başlayabilirsiniz.

> [!TIP]
> UNIX üzerinde LLDB kullanarak hata ayıklaması yaparsanız, aşağıdaki örneklerde yer alan SOS komutlarının `!` önünde yoktur.

```console
!dumpheap -type LoaderAllocator
```

Bu komut, GC yığınında olan içeren bir tür adı olan tüm nesneleri döker `LoaderAllocator` . Aşağıda bir örnek verilmiştir:

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

Aşağıdaki "Istatistikler:" bölümünde, `MT` `MethodTable` ilgilendiğimiz nesne olan öğesine ait olan () öğesini işaretleyin `System.Reflection.LoaderAllocator` . Ardından, başındaki listede, eşleşen girdiyi bulun `MT` ve nesnenin adresini alın. Bu durumda, "000002b78000ce40" olur.

Artık nesnenin adresini öğrendiğimiz `LoaderAllocator` için, GC köklerinin bulmak için başka bir komut de kullanabiliriz:

```console
!gcroot -all 0x000002b78000ce40
```

Bu komut, örneğe yol açabilecek nesne başvuruları zincirini döker `LoaderAllocator` . Liste, `LoaderAllocator` etkin olan ve bu nedenle sorunun temel aldığı varlık olan kökle başlar. Kök bir yığın yuvası, bir işlemci kaydı, bir GC tanıtıcısı veya statik değişken olabilir.

Komutun çıktısının bir örneği aşağıda verilmiştir `gcroot` :

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

Sonraki adım, kökün nerede olduğunu anlamak için, onu düzeltemedi. En kolay durum, kök bir yığın yuvası veya bir işlemci kaydı olduğunda olur. Bu durumda, `gcroot` çerçevesi kök içeren ve bu işlevi yürüten iş parçacığı olan işlevin adını gösterir. Zor durum, kökün bir statik değişken veya bir GC tutamacı olması durumunda olur.

Önceki örnekte, ilk kök, `System.Reflection.RuntimeMethodInfo` adresindeki işlevin çerçevesinde depolanan tür yereldir `example.Program.Main(System.String[])` `rbp-20` ( `rbp` işlemci yazmacı olur `rbp` ve-20 Bu kaydın onaltılık bir uzaklığında oluşur).

İkinci kök, `GCHandle` sınıfının bir örneğine başvuru tutan normal (güçlü) bir `test.Test` sınıftır.

Üçüncü kök sabitlenmiş bir `GCHandle` . Bu, aslında statik bir değişkendir, ancak ne yazık ki, söylemek için bir yol yoktur. Başvuru türleri için statiği, iç çalışma zamanı yapılarında yönetilen nesne dizisinde depolanır.

Bir `AssemblyLoadContext` iş parçacığının, yığınında üzerine yüklenmiş bir derlemeden bir yöntemi olduğunda bir, öğesinin kaldırılmasını engelleyebilen başka bir durum `AssemblyLoadContext` . Tüm iş parçacıklarının yönetilen çağrı yığınlarının dökümünü yaparak bunu kontrol edebilirsiniz:

```console
~*e !clrstack
```

Komut "tüm iş parçacıkları için geçerlidir" anlamına gelir `!clrstack` . Örnek için bu komutun çıktısı aşağıda verilmiştir. Ne yazık ki, UNIX üzerinde LLDB, tüm iş parçacıklarına komut uygulamak için herhangi bir yola sahip değildir, bu nedenle iş parçacıklarını el ile geçmeniz ve komutu tekrarlamanız gerekir `clrstack` . Hata ayıklayıcının "yönetilen yığında ilerleme yapılamıyor" ifadesini belirten tüm iş parçacıklarını yoksayın.

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

Gördüğünüz gibi son iş parçacığı `test.Program.ThreadProc()` . Bu, öğesine yüklenen derlemeden bir işlevdir `AssemblyLoadContext` ve bu sayede `AssemblyLoadContext` canlı tutar.

## <a name="example-source-with-unloadability-issues"></a>Loadability sorunları olan örnek kaynak

Aşağıdaki kod, önceki hata ayıklama örneğinde kullanılır.

### <a name="main-testing-program"></a>Ana test programı

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>TestAssemblyLoadContext içine yüklenen program

Aşağıdaki kod, *test.dll* `ExecuteAndUnload` ana test programındaki yöntemine geçirilentest.dlltemsil eder.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
