---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve boşaltmak için tahsil edilebilir AssemblyLoadContext'ı nasıl kullanacağınızı ve boşaltma başarısını engelleyen sorunları nasıl hata ayıkleyeceğinizi öğrenin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159747"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama

.NET Core 3.0 ile başlayarak, bir dizi derlemeyi yükleme ve daha sonra boşaltma olanağı desteklenir. .NET Framework'de bu amaç için özel uygulama etki alanları kullanıldı, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.

.NET Core 3.0 ve sonraki sürümler üzerinden <xref:System.Runtime.Loader.AssemblyLoadContext>yüklenebilirliği destekler. Bir koleksiyon içine derlemeler bir dizi `AssemblyLoadContext`yükleyebilir, onları yöntemleri yürütmek ya da sadece `AssemblyLoadContext`yansıma kullanarak bunları incelemek ve nihayet boşaltmak . Bu, yüklenen montajları `AssemblyLoadContext`boşaltıyor.

AppDomains kullanarak `AssemblyLoadContext` boşaltma ve kullanma arasında kayda değer bir fark vardır. AppDomains ile, boşaltma zorlanır. Boşaltma zamanında, hedef AppDomain'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain'de oluşturulan yönetilen COM nesneleri yok edilir ve böyle devam eder. Ile `AssemblyLoadContext`, boşaltma "kooperatif". <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Yöntemi çağırmak sadece boşaltmayı başlatır. Boşaltma aşağıdakilerden sonra sona erer:

- Hiçbir iş parçacığı, çağrı yığınlarına `AssemblyLoadContext` yüklenen derlemelerden gelen yöntemleri yoktur.
- Bu tür, örneklere `AssemblyLoadContext`yüklenen derlemelerden hiçbirtürü ve derlemelerin kendileri aşağıdakiler tarafından başvurulan değildir:
  - Zayıf `AssemblyLoadContext`referanslar dışında referanslar<xref:System.WeakReference> ( <xref:System.WeakReference%601>veya ).
  - Güçlü çöp toplayıcı (GC) kolları[(GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) veya [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned) `AssemblyLoadContext`hem içinden hem de dışından .

## <a name="use-collectible-assemblyloadcontext"></a>Tahsil Edilebilir AssemblyLoadContext kullanın

Bu bölümde, bir .NET Core uygulamasını koleksiyona `AssemblyLoadContext`yüklemenin, giriş noktasını çalıştırmanın ve sonra boşaltmanın basit bir yolunu gösteren ayrıntılı bir adım adım öğretici içerir. Tam bir örnek [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)bulabilirsiniz.

### <a name="create-a-collectible-assemblyloadcontext"></a>Tahsil edilebilir bir AssemblyLoadContext oluşturun

Sınıfınızı kendi <xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> yönteminden türemiş ve aşırı yüklemeniz gerekir. Bu yöntem, bu `AssemblyLoadContext`bağlı bağlı meclislerin bağımlılıkları olan tüm derlemelere yapılan başvuruları çözer.

Aşağıdaki kod en basit özel `AssemblyLoadContext`bir örnektir:

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

Gördüğünüz gibi, `Load` yöntem döndürür. `null` Bu, tüm bağımlılık derlemelerinin varsayılan içeriğe yüklendiği ve yeni bağlamın yalnızca açıkça yüklenen derlemeleri içerdiği anlamına gelir.

Bağımlılıkların bir kısmını veya tamamını `AssemblyLoadContext` çok yüklemek istiyorsanız, `AssemblyDependencyResolver` `Load` yöntemde kullanabilirsiniz. Derleme `AssemblyDependencyResolver` adlarını mutlak derleme dosya yollarına giderir. Çözümleyici, bağlama yüklenen ana derlemenin dizininde *.deps.json* dosyasını ve derleme dosyalarını kullanır.

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a>Özel bir tahsil AssemblyLoadContext kullanın

Bu bölümde kullanılan basit sürümü `TestAssemblyLoadContext` varsayar.

Özel `AssemblyLoadContext` bir örnek oluşturabilir ve aşağıdaki gibi bir derleme yükleyebilirsiniz:

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

Yüklenen derleme tarafından başvurulan derlemelerin her `TestAssemblyLoadContext.Load` biri için, derlemenin nereden alınacağına karar `TestAssemblyLoadContext` verebilmeleri için yöntem çağrılır. Bizim durumumuzda, `null` çalışma zamanı varsayılan olarak derlemeleri yüklemek için kullandığı konumlardan varsayılan içeriğe yüklenmesi gerektiğini belirtmek için döner.

Artık bir derleme yüklendiğine göre, ondan bir yöntem uygulayabilirsiniz. Yöntemi `Main` çalıştırın:

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

Yöntem döndükten sonra, özel `AssemblyLoadContext` yöntem ekime `Unload` göre arayarak veya aşağıdakilere sahip olduğunuz `AssemblyLoadContext`başvurudan kurtularak boşaltma işlemini başlatabilirsiniz: `Main`

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

Bu, test montajını boşaltmak için yeterlidir. Tüm bunları, yığın yuvası referansları (gerçek veya JIT tarafından `TestAssemblyLoadContext` `Assembly`tanıtılan `MethodInfo` yerel `Assembly.EntryPoint`halklar) tarafından canlı tutulamadığından emin olmak için ayrı bir inlineable olmayan yönteme koyalım. Bu hayatta `TestAssemblyLoadContext` kalabilir ve boşaltmayı önleyebilir.

Ayrıca, daha sonra boşaltma `AssemblyLoadContext` tamamlama algılamak için kullanabilirsiniz böylece zayıf bir başvuru döndürün.

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

Artık bu işlevi derlemeyi yüklemek, yürütmek ve boşaltmak için çalıştırabilirsiniz.

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

Ancak, boşaltma hemen tamamlanmaz. Daha önce de belirtildiği gibi, test derlemetüm nesneleri toplamak için çöp toplayıcı güveniyor. Çoğu durumda, boşaltma nın tamamlanmasını beklemek gerekmez. Ancak, boşaltmanın bittiğini bilmenin yararlı olduğu durumlar vardır. Örneğin, özel `AssemblyLoadContext` ekine yüklenen derleme dosyasını diskten silmek isteyebilirsiniz. Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir. Çöp toplamayı tetikler ve özele `AssemblyLoadContext` zayıf başvuru ayarlanana kadar bekleyen sonlandırıcıları bir döngüiçinde `null`bekler, hedef nesnenin toplandığını gösterir. Çoğu durumda, döngü den sadece bir geçiş gereklidir. Ancak, kod tarafından oluşturulan nesnelerin sonlandırıcılara `AssemblyLoadContext` sahip olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a>Boşaltma olayı

Bazı durumlarda, özel bir `AssemblyLoadContext` koda yüklenen kodun, boşaltma başlatıldığında bazı temizleme işlemleri gerçekleştirmesi gerekebilir. Örneğin, iş parçacıklarını durdurması veya güçlü GC tutamaçları temizlemesi gerekebilir. Olay `Unloading` bu gibi durumlarda kullanılabilir. Gerekli temizlemeyi gerçekleştiren bir işleyici bu olaya bağlanabilir.

### <a name="troubleshoot-unloadability-issues"></a>Sorun giderme yüklenebilirlik sorunları

Boşaltma nın işbirlikçi doğası nedeniyle, bir koleksiyon `AssemblyLoadContext` da canlı şeyler tutmak ve boşaltma önleme olabilir referansları unutmak kolaydır. Burada, referansları tutabilen varlıkların (bazıları açık olmayan) bir özeti ver:

- Bir yığın yuvasında veya `AssemblyLoadContext` işlemci kaydında depolanan koleksiyon dışından tutulan düzenli başvurular (kullanıcı kodu tarafından açıkça oluşturulan veya tam zamanında (JIT) derleyici tarafından dolaylı olarak oluşturulan yöntem yerlileri), statik bir değişken veya güçlü (sabitleme) GC tutamacı ve geçişli olarak işaret eden:
  - Tahsil edilen ekime `AssemblyLoadContext`yüklenen bir montaj.
  - Böyle bir derlemeden bir tür.
  - Böyle bir derleme bir tür örneği.
- Tahsil edilen bir derlemeden kod çalıştıran iş `AssemblyLoadContext`parçacıkları.
- Özel örnekleri, tahsil olmayan `AssemblyLoadContext` türlerinde koleksiyon `AssemblyLoadContext`içinde oluşturulan.
- Özel <xref:System.Threading.RegisteredWaitHandle> `AssemblyLoadContext`yöntemlere ayarlanmış geri aramabekleyen örnekleri.

> [!TIP]
> Yığın yuvalarında veya işlemci kayıtlarında depolanan ve aşağıdaki durumlarda bir `AssemblyLoadContext` nesnenin boşaltılmasını önleyebilecek nesne başvuruları:
>
> - Kullanıcı tarafından oluşturulan yerel değişken olmamasına rağmen, işlev çağrı sonuçları doğrudan başka bir işleve geçirildiğinde.
> - JIT derleyicisi bir yöntemde bir noktada kullanılabilir bir nesneye bir başvuru tutar.

## <a name="debug-unloading-issues"></a>Hata ayıklama sorunları

Boşaltma ile ilgili hata ayıklama sorunları sıkıcı olabilir. Bir `AssemblyLoadContext` canlı tutan ne olduğunu bilmiyorum durumlara girebilirsiniz, ama boşaltma başarısız olur. Bu konuda yardımcı olmak için en iyi silah WINDbg (LLDB Unix üzerinde) SOS eklentisi ile. Bir `LoaderAllocator` ait olanı `AssemblyLoadContext` canlı tutan şeyi bulmalısın. SOS eklentisi GC yığın nesneleri, hiyerarşileri ve kökleri bakmak için izin verir.

Eklentiyi hata ayıkleyiciye yüklemek için hata ayıklama komut satırına aşağıdaki komutu girin:

WinDbg (WinDbg otomatik olarak .NET Core uygulamasına girerken yapar gibi görünüyor):

```console
.loadby sos coreclr
```

LLDB olarak:

```console
plugin load /path/to/libsosplugin.so
```

Boşaltma ile ilgili sorunları olan bir örnek programı hata ayıklayalım. Kaynak kodu aşağıda yer almaktadır. WinDbg altında çalıştırdığınızda, program boşaltma başarısını denetlemeye çalıştıktan hemen sonra hata ayıklamaya girer. Daha sonra suçluları aramaya başlayabilirsiniz.

> [!TIP]
> Unix'te LLDB kullanarak hata ayıklama ederseniz, aşağıdaki örneklerdeki `!` SOS komutlarının önünde yoktur.

```console
!dumpheap -type LoaderAllocator
```

Bu komut, GC yığınında bulunan `LoaderAllocator` bir tür adı içeren tüm nesneleri atar. Örnek aşağıda verilmiştir:

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

Aşağıdaki "İstatistikler:" bölümünde, `MT` önemsediğimiz nesneolan `System.Reflection.LoaderAllocator`nesneye ait (`MethodTable`) bölümünü kontrol edin. Daha sonra, başlangıçtaki listede, bu `MT` ile eşleşen girişi bulmak ve nesnenin kendisi adresini almak. Bizim durumumuzda, "000002b78000ce40".

Artık `LoaderAllocator` nesnenin adresini bildiğimize göre, GC köklerini bulmak için başka bir komut kullanabiliriz:

```console
!gcroot -all 0x000002b78000ce40
```

Bu komut, örneğine yol açan nesne `LoaderAllocator` başvuruları zincirini çöpe atar. Liste kökle başlar, ki bu bizim `LoaderAllocator` canlı tutan varlıktır ve böylece sorunun özüdür. Kök bir yığın yuvası, bir işlemci kaydı, bir GC tutamacı veya statik bir değişken olabilir.

Aşağıda `gcroot` komutun çıktısının bir örneği verilmiştir:

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

Bir sonraki adım, kökün nerede olduğunu bulmak, böylece onu düzeltebilirsiniz. En kolay durum, kök bir yığın yuvası veya işlemci kaydı olduğunda. Bu durumda, `gcroot` çerçeve kök ve bu işlevi yürüten iş parçacığı içeren işlevin adını gösterir. Zor durumda kök statik bir değişken veya GC kolu olduğunda.

Önceki örnekte, ilk kök adresteki `System.Reflection.RuntimeMethodInfo` `example.Program.Main(System.String[])` `rbp-20` işlevçerçevesinde depolanan tür yereldir`rbp` (işlemci kaydıdır `rbp` ve -20 bu kayıttan bir hexadecimal ofsettir).

İkinci kök, `GCHandle` `test.Test` sınıfın bir örneğine başvuru tutan normal (güçlü) bir köktür.

Üçüncü kök sabitlenmiş. `GCHandle` Bu aslında statik bir değişken, ama ne yazık ki, bunu söylemenin bir yolu yok. Başvuru türleri için statik, iç çalışma zamanı yapılarında yönetilen bir nesne dizisinde depolanır.

Bir `AssemblyLoadContext` iş parçacığının boşaltılmasını önleyebilecek başka bir örnek de, bir `AssemblyLoadContext` iş parçacığının yığınına yüklenen bir derlemeden bir yöntem çerçevesine sahip olmasıdır. Tüm iş parçacıklarının yönetilen çağrı yığınlarını damping tarafından kontrol edebilirsiniz:

```console
~*e !clrstack
```

Komut , "tüm iş parçacıkları `!clrstack` komutu için geçerli" anlamına gelir. Aşağıdaki örnek için bu komutun çıktısi. Ne yazık ki, Unix LLDB tüm iş parçacıkları için bir komut uygulamak için herhangi bir `clrstack` yolu yoktur, bu yüzden el ile iş parçacığı geçiş ve komutu tekrarlamalısınız. Hata ayıklamanın "Yönetilen yığında yürüyemiyor" dediği tüm iş parçacıklarını yoksayın.

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

Gördüğünüz gibi, son iş `test.Program.ThreadProc()`parçacığı . Bu, montajdan `AssemblyLoadContext`yüklenen bir fonksiyondur ve bu `AssemblyLoadContext` yüzden canlı tutar.

## <a name="example-source-with-unloadability-issues"></a>Yüklenebilirlik sorunları olan örnek kaynak

Önceki hata ayıklama örneğinde aşağıdaki kod kullanılır.

### <a name="main-testing-program"></a>Ana test programı

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a>TestAssemblyLoadContext'a yüklenen program

Aşağıdaki kod, ana test programında `ExecuteAndUnload` yönteme geçen *test.dll'yi* temsil eder.

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
