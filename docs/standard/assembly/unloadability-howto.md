---
title: Nasıl kullanılacağını ve hata ayıklama derlemesi unloadability .NET core'da
description: Toplanabilir AssemblyLoadContext yönetilen derlemeleri yükleme ve kaldırma ve kaldırma başarılı engelleyen sorunları hata ayıklamak nasıl kullanılacağını öğrenin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627791"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Nasıl kullanılacağını ve hata ayıklama derlemesi unloadability .NET core'da

.NET Core 3.0 ile başlayarak, yükleme ve daha sonra bir derleme kümesi kaldırma olanağı desteklenir. .NET Framework'teki özel uygulama etki alanları bu amaç için kullanılan, ancak .NET Core, yalnızca tek bir varsayılan uygulama etki alanını destekler.

.NET core 3.0 ve sonraki sürümleri destekler unloadability aracılığıyla <xref:System.Runtime.Loader.AssemblyLoadContext>. Bir derleme kümesi toplanabilir yükleyebilir `AssemblyLoadContext`, bunları bir yöntem yürütülemez veya yalnızca bunları inceleyin yansıma kullanarak ve son olarak kaldırma `AssemblyLoadContext`. Yüklenen derlemeler bellekten `AssemblyLoadContext`.

Kaldırma kullanarak arasında önemli bir fark `AssemblyLoadContext` ve uygulama etki alanları kullanma. Uygulama etki alanları ile kaldırma zorlanır. Unload zaman hedef AppDomain tüm iş parçacıkları iptal edilir, yönetilen vb. AppDomain yok edilir hedef oluşturulan COM nesnelerini. İle `AssemblyLoadContext`, kaldırma "" ortaktır. Çağırma <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> yöntemi yalnızca başlatır kaldırma. Kaldırma tamamlandıktan sonra:

- İş parçacığı içine yüklenen derlemeler yöntemlerinden sahip `AssemblyLoadContext` çağrı yığınlarıyla üzerinde.
- Yüklenen derlemeler türlerden hiçbiri `AssemblyLoadContext`, bu türleri ve derlemeleri örnekleri dışında `AssemblyLoadContext` tarafından başvurulan:
  - Dışında başvuran `AssemblyLoadContext`, hariç zayıf başvurular (<xref:System.WeakReference> veya <xref:System.WeakReference%601>).
  - Güçlü GC tutamaçlarını (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal> veya <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) hem Azure içindeki hem de dışında `AssemblyLoadContext`.

## <a name="using-collectible-assemblyloadcontext"></a>Toplanabilir AssemblyLoadContext kullanma

Bu bölüm .NET Core uygulamasını toplanabilir yüklemek için basit bir yol gösteren ayrıntılı adım adım bir öğretici içerir `AssemblyLoadContext`, kendi giriş noktası yürütün ve bunu kaldırın. Bir tam örneğini şurada bulabilirsiniz <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.

### <a name="create-a-collectible-assemblyloadcontext"></a>Toplanabilir AssemblyLoadContext oluşturma

Sizin sınıfınızdan türetmek gereken <xref:System.Runtime.Loader.AssemblyLoadContext> ve aşırı yükleme, <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> yöntemi. Yöntemi, yüklenen derlemelerin bağımlılıklar tüm derlemeleri başvuruları çözümleniyor `AssemblyLoadContext`.
Aşağıdaki kod, en basit özel örneğidir `AssemblyLoadContext`:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Gördüğünüz gibi `Load` yöntemi döndürür `null`. Bu, tüm bağımlılık derlemelerin varsayılan bağlamına yüklü olduğundan ve yalnızca açıkça içine yüklenen derlemeler yeni bağlam içeren anlamına gelir.

Bazı veya tüm bağımlılıklarınızı yüklemek istiyorsanız `AssemblyLoadContext` de kullanabileceğiniz `AssemblyDependencyResolver` içinde `Load` yöntemi. `AssemblyDependencyResolver` Kullanarak mutlak derleme dosya yolları için derleme adlarını çözümleyen `*.deps.json` ana derleme bağlamı ve derleme dosyaları dizindeki kullanarak yüklenen dizininde yer alan dosya.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Özel bir toplanabilir AssemblyLoadContext kullanın

Bu bölümde daha basit sürümü varsayılır `TestAssemblyLoadContext` kullanılıyor.

Özel bir örneğini oluşturabilirsiniz `AssemblyLoadContext` ve bir derleme içine aşağıdaki gibi yükleyin:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Her yüklenen derlemesi tarafından başvurulan derlemelerin `TestAssemblyLoadContext.Load` yöntemi çağrıldığında böylece `TestAssemblyLoadContext` derlemeden nereden karar verebilirsiniz. Bu örnekte, döndürür `null` bu derlemeleri yüklemeye çalışma zamanı kullanan konumlardan varsayılan bağlamına varsayılan yükleneceğini göstermek için.

Bir derleme yüklendi, ondan bir yöntem yürütebilir. Çalıştırma `Main` yöntemi:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Sonra `Main` yöntemi döndürür, ya da çağrısı yaparak eklentiyi başlatabilirsiniz `Unload` özel metodunda `AssemblyLoadContext` veya zorunda başvurunun doğurduğu israftan `AssemblyLoadContext`:

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Bu test derlemesini kaldırmak yeterli olur. Şimdi tüm emin olmak için ayrı bir inlineable olmayan yönteme gerçekten put `TestAssemblyLoadContext`, `Assembly`, ve `MethodInfo` ( `Assembly.EntryPoint`) yığını yuvası başvuruları (gerçek veya JIT sunulan Yereller) tarafından etkin tutulan bağlantıyı destekliyorsa tutulması olamaz. Tutun `TestAssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa ve yüklemelerini kaldırma engelleyebilir.

Ayrıca, zayıf bir başvuru döndürmeyi `AssemblyLoadContext` böylece bunu daha sonra kaldırma tamamlama algılamak için kullanabilirsiniz.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Artık, yükleme, yürütme ve derlemeyi kaldırmak için bu işlevi çalıştırabilirsiniz.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ancak, kaldırma, hemen tamamlanmıyor. Daha önce belirtildiği gibi tüm nesneleri test derlemesinden toplanacak GC kullanır. Çoğu durumda, kaldırma tamamlanmasını beklemeniz gerekmez. Ancak, kaldırma işleminin tamamlandığını bilmek de yararlı olduğu durumlar da vardır. Örneğin, özel yüklenen derleme dosyasını silmek isteyebilirsiniz `AssemblyLoadContext` diskten. Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir. GC tetikler ve bir döngüde sonlandırıcılar bekleyen özel zayıf başvuruyu kadar bekler `AssemblyLoadContext` ayarlanır `null`, hedef nesneyi gösteren toplanmıştır. Çoğu durumda, yalnızca tek seferde döngü gerekli olduğunu unutmayın. Ancak, nesne oluşturulduğu çalışan kod tarafından daha karmaşık durumlarda `AssemblyLoadContext` Sonlandırıcıları sahip daha fazla geçiş gerekli olabilir.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Unloading olay

Bazı durumlarda, bir özel yüklenen kod için gerekli olabilir `AssemblyLoadContext` kaldırma başlatıldığında bazı temizleme işlemleri gerçekleştirmek için. Örneğin, gereksinim duymayabilirsiniz iş parçacıklarını durdurma, temiz bazı güçlü GC tanıtıcıları, vb. `Unloading` Olay bu gibi durumlarda kullanılabilir. Bu olay için gerekli temizleme işlemini gerçekleştiren bir işleyici bağlanabilir.

### <a name="troubleshoot-unloadability-issues"></a>Unloadability sorunlarını giderme

İşbirlikçi yapısı nedeniyle, eklentiyi, her şeyi bir toplanabilir tutma başvurular hakkında unutmak çok kolaydır `AssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa ve engelleme kaldırma. Başvuruları tutabilen ve nesnelerin interneti (bunlardan bazıları belirgin olmayan) bir özeti aşağıda verilmiştir:

- Normal başvuruları tutulan gelen toplanabilir dışında `AssemblyLoadContext`, yığın yuvası veya işlemci kaydı (ya da kullanıcı kod tarafından veya örtük olarak JIT tarafından açıkça oluşturulan yöntemi Yereller), bir statik değişken veya bir güçlü / sabitleme GC tanıtıcı depolanır ve geçişli işaret eden:
  - Bir derleme yüklenen toplanabilir `AssemblyLoadContext`.
  - Böyle bir derlemeden bir tür.
  - Böyle bir derlemeden bir tür örneği.
- Bir derlemeye ait kod çalıştıran iş parçacığı toplanabilir yüklenen `AssemblyLoadContext`.
- Özel toplanabilir olmayan örneklerini `AssemblyLoadContext` toplanabilir içinde oluşturulan türleri `AssemblyLoadContext`
- Bekleyen <xref:System.Threading.RegisteredWaitHandle> geri çağırmaları örnekleriyle ayarlanmış özel yöntemler `AssemblyLoadContext`

Yığın yuvası bulmak için ipuçları işlemci Register nesneyi kök dizini değiştirme:

- İşlev çağrısı sonuçları doğrudan başka bir işlev için hiçbir kullanıcı tarafından oluşturulan yerel değişken olsa bile bir kök oluşturabilir geçirme.
- Bir nesneye bir başvuru bir yöntem herhangi bir noktada mevcut olduğunda, JIT yığın yuvasında başvurusunu korumanız karar verdiğiniz / işlemcisi kaydetmek için geçerli işlevde istediği sürece.

## <a name="debug-unloading-issues"></a>Kaldırma sorunlarında hata ayıklama

Hata ayıklama kaldırma sorunlarını can sıkıcı olabilir. Burada bilmediğiniz ne bulunduran durumlarda alabileceğiniz bir `AssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa, ancak kaldırma başarısız olur.
İle yardımcı olması için en iyi Silah WinDbg (LLDB UNIX üzerinde) ile SOS eklentisidir. Tutuyor mu bulmanız gereken bir `LoaderAllocator` belirli ait `AssemblyLoadContext` tutma.
Bu eklenti, GC yığın nesnelerini, hiyerarşiler ve kökleri aramak sağlar.
Eklenti hata ayıklayıcısına yüklemek için hata ayıklayıcı komut satırında aşağıdaki komutu girin:

(WinDbg otomatik olarak .NET Core uygulamasına bozucu olduğunda yapan görünüyor) WinDbg içinde:

```console
.loadby sos coreclr
```

LLDB içinde:

```console
plugin load /path/to/libsosplugin.so
```

Örnek kaldırma sorunları olan bir programı hata ayıklama deneyelim. Kaynak kodu, aşağıda yer almaktadır. WinDbg altında çalıştırdığınızda, programın kaldırma başarı için denetlenecek denemeden sonra hata ayıklayıcı sağındaki keser. Ardından, culprits için arama da başlatabilirsiniz.

Aşağıdaki örneklerde SOS komutlarının LLDB UNIX kullanarak hata ayıklama, yüklü olmadığını unutmayın `!` bunları önünde.

```console
!dumpheap -type LoaderAllocator
```

Bu komut tüm nesneleri içeren bir tür adı ile dökümleri `LoaderAllocator` GC yığınında olan. Aşağıda bir örnek verilmiştir:

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

İçinde "istatistikleri:" bölümü altındaki onay `MT` (`MethodTable`) ait `System.Reflection.LoaderAllocator`, biz önem verdiğiniz nesne olduğu. Ardından girişle başında listede bulun `MT` tek eşleştirme ve nesnenin adresini alın. Bu örnekte, "000002b78000ce40" olduğu

Biz adresini öğrendiğinize göre `LoaderAllocator` , GC kökleri bulmak için başka bir komuta kullanabileceğiniz nesnesi

```console
!gcroot -all 0x000002b78000ce40 
```

Bu komut zincirini neden nesne başvuruları dökümleri `LoaderAllocator` örneği. Listenin tutan bir varlık kök ile başlar bizim `LoaderAllocator` etkin tutulan bağlantıyı destekliyorsa ve bu nedenle hata ayıklama sorunun temel. Kök yığın yuvası, işlemci kaydı, GC tanıtıcısı veya statik değişken olabilir.

İşte bir örnek çıktısı `gcroot` komutu:

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

Şimdi Bunu düzeltmek için kök bulunduğu kullanıma şekil gerekir. Kök yığın yuvası ya da bir işlemci kayıt olduğunda kolay durum geçerlidir. Bu durumda, `gcroot` olan çerçeveyi içeren kök ve bu işlev yürütme iş parçacığı işlevin adını gösterir. Kök statik bir değişken veya GC tanıtıcı olduğunda zor bir durumdur. 

Önceki örnekte, ilk kök yerel bir tür olan `System.Reflection.RuntimeMethodInfo` işlevi çerçevede depolanan `example.Program.Main(System.String[])` adresindeki `rbp-20` (`rbp` işlemci kaydıdır `rbp` ve -20 Bu kayıt onaltılık bir uzaklık).

İkinci köküdür (güçlü) normal `GCHandle` örneğine bir başvuru tutan `test.Test` sınıfı. 

Üçüncü kök sabitlenmiş olan `GCHandle`. Bu, aslında bir statik değişken ' dir. Ne yazık ki bildirmek için hiçbir yolu yoktur. Başvuru türleri için statikler iç çalışma zamanı yapılardaki bir yönetilen nesne dizisindeki depolanır.

Yüklemesini kaldırmak engelleyebilecek başka bir örneği bir `AssemblyLoadContext` bir iş parçacığı bir metodun çerçeve sahip olduğunda bir derleme yüklenen `AssemblyLoadContext` , yığında. Yönetilen dökme tüm iş parçacığı yığınları çağırın denetleyebilirsiniz:

```console
~*e !clrstack
```

Komut anlamına gelir "tüm iş parçacıkları için geçerli `!clrstack` komut". Örneğin bu komutun çıktısı aşağıda verilmiştir. Ne yazık ki LLDB UNIX üzerinde el ile geçiş iş parçacıkları ve yinelenen başvurmadan gerekecek bir komutu tüm iş parçacıkları için uygulamak için herhangi bir şekilde yok `clrstack` komutu.
Burada "Yönetilen yığın yol alınamıyor." hata ayıklayıcı'ifadesini içeren tüm iş parçacıklarının yoksay

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

Gördüğünüz gibi son iş parçacığı vardır `test.Program.ThreadProc()`. Bu derlemeden yüklenen işlevdir `AssemblyLoadContext`, ve sürdürür böylece `AssemblyLoadContext` tutma.

## <a name="example-source-with-unloadability-issues"></a>Örnek kaynak unloadability sorunları

Aşağıdaki kod, önceki örnekte hata ayıklama kullanılır.

### <a name="main-testing-program"></a>Test ana program

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>Program TestAssemblyLoadContext yüklendi

Aşağıdaki kod temsil `test.dll` geçirilen `ExecuteAndUnload` test eden ana program yöntemi.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
