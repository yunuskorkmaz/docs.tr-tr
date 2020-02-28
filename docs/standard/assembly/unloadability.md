---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve kaldırmak için toplanabilir bir AssemblyLoadContext ve kaldırma başarısını önlemek için sorunları nasıl ayıklayacağınız hakkında bilgi edinin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159747"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

.NET Core 3,0 ile başlayarak, bir derleme kümesini yükleme ve daha sonra kaldırma özelliği desteklenir. .NET Framework, bu amaçla özel uygulama etki alanları kullanılmıştır, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.

.NET Core 3,0 ve sonraki sürümleri, <xref:System.Runtime.Loader.AssemblyLoadContext>aracılığıyla bir unkullanılabilirliği destekler. Bir dizi derlemeyi toplanabilir bir `AssemblyLoadContext`yükleyebilir, bunlarda Yöntemler yürütebilir veya yansıma kullanarak bunları inceleyebilirsiniz, son olarak da `AssemblyLoadContext`kaldırabilirsiniz. Bu, `AssemblyLoadContext`yüklenen derlemeleri kaldırır.

`AssemblyLoadContext` kullanarak ve AppDomain kullanarak kaldırma arasında bir çok fark vardır. AppDomain ile, kaldırma zorlanır. Kaldırma sırasında, hedef AppDomain 'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain 'te oluşturulan yönetilen COM nesneleri yok edilir ve bu şekilde devam eder. `AssemblyLoadContext`, kaldırma "işbirliği" dir. <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> yöntemini çağırmak, kaldırmayı yalnızca başlatır. Kaldırma işlemi şu tarihten sonra bitiyor:

- Hiçbir iş parçacığı, çağrı yığınlarında `AssemblyLoadContext` yüklenen derlemelerden yöntemlere sahip değildir.
- `AssemblyLoadContext`yüklenmeyen derlemelerden türlerin hiçbiri, bu türlerin örneklerine ve derlemelerin kendileri tarafından başvuruluyor:
  - Zayıf başvurular (<xref:System.WeakReference> veya <xref:System.WeakReference%601>) dışında `AssemblyLoadContext`dışında başvurular.
  - `AssemblyLoadContext`içindeki ve dışındaki güçlü çöp toplayıcı (GC) tutamaçları ([GCHandleType. normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) veya [GCHandleType. sabitlenmiş](xref:System.Runtime.InteropServices.GCHandleType.Pinned)).

## <a name="use-collectible-assemblyloadcontext"></a>Toplanabilir AssemblyLoadContext kullanın

Bu bölümde, bir .NET Core uygulamasını toplanabilir bir `AssemblyLoadContext`yüklemek, giriş noktasını yürütmek ve sonra kaldırmak için kullanabileceğiniz basit bir yol gösteren ayrıntılı bir adım adım öğretici yer almaktadır. [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)' de tüm bir örnek bulabilirsiniz.

### <a name="create-a-collectible-assemblyloadcontext"></a>Toplanabilir bir AssemblyLoadContext oluşturma

<xref:System.Runtime.Loader.AssemblyLoadContext> sınıfınızı türetmeniz ve <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodunu aşırı yüklemeniz gerekir. Bu yöntem, bu `AssemblyLoadContext`yüklenen derlemelerin bağımlılıkları olan tüm derlemelere yönelik başvuruları çözer.

Aşağıdaki kod, en basit özel `AssemblyLoadContext`örneğidir:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Gördüğünüz gibi `Load` yöntemi `null`döndürür. Bu, tüm bağımlılık derlemelerinin varsayılan bağlamına yüklendiği ve yeni bağlamın yalnızca açıkça kendisine yüklenmiş derlemeleri içerdiği anlamına gelir.

Bağımlılıkların bir kısmını veya tümünü `AssemblyLoadContext` yüklemek istiyorsanız, `Load` yönteminde `AssemblyDependencyResolver` kullanabilirsiniz. `AssemblyDependencyResolver`, derleme adlarını mutlak derleme dosyası yollarına çözümler. Çözümleyici, bağlamına yüklenen ana derlemenin dizinindeki *. Deps. JSON* dosyasını ve derleme dosyalarını kullanır.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Özel toplanabilir bir AssemblyLoadContext kullanın

Bu bölüm `TestAssemblyLoadContext` 'in daha basit sürümünün kullanıldığını varsayar.

Özel `AssemblyLoadContext` bir örneğini oluşturabilir ve buna aşağıdaki gibi bir derlemeyi yükleyebilirsiniz:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Yüklenen derleme tarafından başvurulan derlemelerin her biri için `TestAssemblyLoadContext.Load` yöntemi, `TestAssemblyLoadContext` derlemenin nereden alınacağını seçebilir. Bizim örneğimizde, varsayılan olarak çalışma zamanının derlemeleri yüklemek için kullandığı konumlardan varsayılan bağlamına yüklenmesi gerektiğini göstermek için `null` döndürür.

Bir derleme yüklendikten sonra, bundan sonra bir yöntemi çalıştırabilirsiniz. `Main` yöntemini çalıştırın:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

`Main` yöntemi çağrıldıktan sonra, özel `AssemblyLoadContext` `Unload` yöntemini çağırarak veya `AssemblyLoadContext`sahip olduğunuz başvurunun kurtumı aracılığıyla kaldırma işlemini başlatabilirsiniz:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Bu, test derlemesini kaldırmak için yeterlidir. `TestAssemblyLoadContext`, `Assembly`ve `MethodInfo` (`Assembly.EntryPoint`) yığın yuvası başvuruları (gerçek veya JıT tarafından tanıtılan Yereller) tarafından etkin tutulabileceğinden emin olmak için bunu tamamen ayrı bir bağımsız olmayan yönteme koyalım. Bu, `TestAssemblyLoadContext` canlı tutabilir ve kaldırma özelliğini engelleyebilir.

Ayrıca, daha sonra kaldırma tamamlamayı algılamak üzere kullanabilmek için `AssemblyLoadContext` zayıf bir başvuru döndürün.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Artık derlemeyi yüklemek, çalıştırmak ve kaldırmak için bu işlevi çalıştırabilirsiniz.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ancak, kaldırma hemen tamamlanmaz. Daha önce belirtildiği gibi, tüm nesneleri test derlemesinden toplamak için çöp toplayıcıyı kullanır. Çoğu durumda, kaldırma işleminin tamamlanmasını beklemek gerekli değildir. Ancak, kaldırma işlemi bittiğini bilmemiz yararlı olduğu durumlar vardır. Örneğin, diskten özel `AssemblyLoadContext` yüklenen derleme dosyasını silmek isteyebilirsiniz. Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir. Çöp toplamayı tetikler ve özel `AssemblyLoadContext` zayıf başvurusu, hedef nesnenin toplandığını belirten `null`olarak ayarlanana kadar bir döngüde bekleyen sonlandırıcıları bekler. Çoğu durumda, yalnızca bir geçiş döngüsü gerekir. Ancak, `AssemblyLoadContext` çalışan kod tarafından oluşturulan nesnelerin sonlandırıcılarda olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Kaldırma olayı

Bazı durumlarda, kaldırma işlemi başlatıldığında bazı temizleme işlemleri gerçekleştirmek için özel bir `AssemblyLoadContext` yüklenen kod için gerekli olabilir. Örneğin, iş parçacıklarını durdurmanız veya güçlü GC tutamaçları temizlemesi gerekebilir. `Unloading` olay bu gibi durumlarda kullanılabilir. Gerekli temizleme işlemini gerçekleştiren bir işleyici bu olaya bağlanabilir.

### <a name="troubleshoot-unloadability-issues"></a>Kaldırma sorunları sorunlarını giderme

Boşaltma 'nın işbirliğinin doğası gereği, bir toplanabilir `AssemblyLoadContext` canlı bir şekilde korunmuş ve kaldırma işlemini engellediği başvuruları unutmak kolaydır. Aşağıda, başvuruları tutabilecek varlıkların (bazı belirgin olmayan) bir özeti verilmiştir:

- Bir yığın yuvasında veya bir işlemci kaydındaki (Kullanıcı kodu tarafından açıkça oluşturulan veya örtük olarak tam zamanında (JıT) derleyici), statik bir değişken ya da güçlü (sabitleme) bir GC tutamacı veya bir güçlü (sabitleme) `AssemblyLoadContext`
  - Toplanabilir `AssemblyLoadContext`yüklenmiş bir bütünleştirilmiş kod.
  - Bu tür bir derlemeden bir tür.
  - Bu tür bir derlemeden bir türün örneği.
- Toplanabilir `AssemblyLoadContext`yüklenmiş bir derlemeden kod çalıştıran iş parçacıkları.
- Toplanabilir `AssemblyLoadContext`içinde oluşturulan özel, toplanabilir olmayan `AssemblyLoadContext` türlerinin örnekleri.
- Geri çağırmalar içeren <xref:System.Threading.RegisteredWaitHandle> örnekleri, özel `AssemblyLoadContext`metotlar olarak ayarlanmıştır.

> [!TIP]
> Yığın yuvaları veya işlemci kayıtları 'nda depolanan ve bir `AssemblyLoadContext` kaldırılmasını engelleyebilecek nesne başvuruları aşağıdaki durumlarda oluşabilir:
>
> - İşlev çağırma sonuçları, Kullanıcı tarafından oluşturulan yerel değişken olmasa bile, doğrudan başka bir işleve geçirilir.
> - JıT derleyicisi, bir yöntemde bir noktada kullanılabilir olan bir nesneye bir başvuru tutar.

## <a name="debug-unloading-issues"></a>Hata ayıklama kaldırma sorunları

Kaldırma ile ilgili hata ayıklama sorunları sıkıcı olabilir. `AssemblyLoadContext` canlı olarak neler yapabileceğini bildiğiniz durumlara ulaşabilirsiniz, ancak kaldırma başarısız olur. Bu, sos eklentisi ile WinDbg (UNIX üzerinde lldb) ile ilgili yardım için en iyi uygulamalar. Belirli `AssemblyLoadContext` canlı olan `LoaderAllocator` tutmayı bulmanız gerekir. SOS eklentisi, GC yığın nesnelerine, hiyerarşilerine ve köklerine bakabilmeniz için izin verir.

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
> UNIX üzerinde LLDB kullanarak hata ayıklaması yaparsanız, aşağıdaki örneklerde yer alan SOS komutlarının önünde `!` yoktur.

```console
!dumpheap -type LoaderAllocator
```

Bu komut, GC yığınındaki `LoaderAllocator` içeren bir tür adına sahip tüm nesneleri döker. Örnek aşağıda verilmiştir:

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

Aşağıdaki "Istatistikler:" bölümünde, ilgilendiğimiz nesne olan `System.Reflection.LoaderAllocator`ait `MT` (`MethodTable`) kontrol edin. Ardından, başındaki listede, kendisiyle eşleşen `MT` olan girdiyi bulun ve nesnenin adresini alın. Bu durumda, "000002b78000ce40" olur.

Artık `LoaderAllocator` nesnesinin adresini öğrendiğimiz için, GC köklerinin bulmak için başka bir komut de kullanabiliriz:

```console
!gcroot -all 0x000002b78000ce40
```

Bu komut, `LoaderAllocator` örneğine yol açabilecek nesne başvuruları zincirini döker. Liste, `LoaderAllocator` etkin tutan ve bu nedenle sorunun temel aldığı varlık olan kökle başlar. Kök bir yığın yuvası, bir işlemci kaydı, bir GC tanıtıcısı veya statik değişken olabilir.

`gcroot` komutunun çıktısının bir örneği aşağıda verilmiştir:

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

Sonraki adım, kökün nerede olduğunu anlamak için, onu düzeltemedi. En kolay durum, kök bir yığın yuvası veya bir işlemci kaydı olduğunda olur. Bu durumda `gcroot`, çerçevesi kök içeren ve bu işlevi yürüten iş parçacığı olan işlevin adını gösterir. Zor durum, kökün bir statik değişken veya bir GC tutamacı olması durumunda olur.

Önceki örnekte, ilk kök, `System.Reflection.RuntimeMethodInfo` `example.Program.Main(System.String[])` işlevin çerçevesinde depolanan bir tür yereldir `rbp-20` (`rbp`, işlemci yazmacı `rbp` ve-20 Bu kaydın onaltılık bir uzaklığında oluşur).

İkinci kök, `test.Test` sınıfının bir örneğine başvuru tutan bir normal (güçlü) `GCHandle`.

Üçüncü kök sabitlenmiş bir `GCHandle`. Bu, aslında statik bir değişkendir, ancak ne yazık ki, söylemek için bir yol yoktur. Başvuru türleri için statiği, iç çalışma zamanı yapılarında yönetilen nesne dizisinde depolanır.

Bir `AssemblyLoadContext` kaldırılmasını engelleyebilecek başka bir durum, bir iş parçacığı, yığınında `AssemblyLoadContext` yüklenen bir derlemeden bir yöntem çerçevesine sahip olduğunda olabilir. Tüm iş parçacıklarının yönetilen çağrı yığınlarının dökümünü yaparak bunu kontrol edebilirsiniz:

```console
~*e !clrstack
```

Komutu, "`!clrstack` komutuna tüm iş parçacıkları için geçerlidir" anlamına gelir. Örnek için bu komutun çıktısı aşağıda verilmiştir. Ne yazık ki, UNIX üzerinde LLDB, tüm iş parçacıklarına komut uygulamak için herhangi bir yola sahip değildir, bu nedenle iş parçacıklarını el ile geçmeniz ve `clrstack` komutunu tekrarlamanız gerekir. Hata ayıklayıcının "yönetilen yığında ilerleme yapılamıyor" ifadesini belirten tüm iş parçacıklarını yoksayın.

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

Gördüğünüz gibi, son iş parçacığında `test.Program.ThreadProc()`vardır. Bu, `AssemblyLoadContext`yüklenen derlemeden bir işlevdir ve `AssemblyLoadContext` canlı tutar.

## <a name="example-source-with-unloadability-issues"></a>Loadability sorunları olan örnek kaynak

Aşağıdaki kod, önceki hata ayıklama örneğinde kullanılır.

### <a name="main-testing-program"></a>Ana test programı

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>TestAssemblyLoadContext içine yüklenen program

Aşağıdaki kod, ana test programındaki `ExecuteAndUnload` metoduna geçirilen *test. dll dosyasını* temsil eder.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
