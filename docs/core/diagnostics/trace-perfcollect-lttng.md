---
title: PerfCollect ile .NET uygulamalarını izleme.
description: .NET ' te PerfCollect ile izleme toplama konusunda size kılavuzluk eden bir öğretici.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 20e1bf56714fb32b5231d45b0ba35cdfcedaea2e
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103189936"
---
# <a name="trace-net-applications-with-perfcollect"></a>PerfCollect ile .NET uygulamalarını izleme

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 2,1 SDK ve sonraki sürümleri

Linux üzerinde performans sorunlarıyla karşılaşıldığında, bir izleme toplama, `perfcollect` performans sorunu sırasında makinede neler olduğunu hakkında ayrıntılı bilgi toplamak için kullanılabilir.

`perfcollect`, çalışma zamanının veya herhangi bir [EventSource](xref:System.Diagnostics.Tracing.EventListener)'dan yazılmış olayları toplamak Için [Linux izleme Tookit-Next oluşturma (lttng)](https://lttng.org) kullanan bir bash betiğidir ve hedef işlemin CPU örneklerini toplamak için [perf](https://perf.wiki.kernel.org/) kullanır.

## <a name="prepare-your-machine"></a>Makinenizi hazırlama

Makinenizi ile bir performans izlemesi toplayacak şekilde hazırlamak için aşağıdaki adımları izleyin `perfcollect` .

> [!NOTE]
> Bir kapsayıcı ortamındaysanız, kapsayıcının özelliği olması gerekir `SYS_ADMIN` . PerfCollect kullanarak kapsayıcılardaki uygulamaları izleme hakkında daha fazla bilgi için bkz. [kapsayıcılarda tanılamayı toplama](./diagnostics-in-containers.md).

1. İndirin `perfcollect` .

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. Betiği çalıştırılabilir yapın.

    > ```bash
    > chmod +x perfcollect
    > ```

3. İzleme önkoşullarını yükler-bunlar gerçek izleme kitaplıklarıdır.

    > ```bash
    > sudo ./perfcollect install
    > ```

    Bu işlem makinenize aşağıdaki önkoşulları yükler:

    1. `perf`: Linux performans olayları alt sistemi ve yardımcı Kullanıcı modu koleksiyonu/görüntüleyici uygulaması. `perf` , Linux çekirdek kaynağının bir parçasıdır, ancak genellikle varsayılan olarak yüklenmez.

    2. `LTTng`: Çalışma zamanında, CoreCLR tarafından yayılan olay verilerini yakalamak için kullanılır. Bu veriler daha sonra GC, JıT ve iş parçacığı havuzu gibi çeşitli çalışma zamanı bileşenlerinin davranışını çözümlemek için kullanılır.

.NET Core 'un son sürümleri ve Linux performans aracı, çerçeve kodu için yöntem adlarının otomatik olarak çözümlenmesini destekler. .NET Core sürüm 3,1 veya daha az bir sürümle çalışıyorsanız, ek bir adım gereklidir. Ayrıntılar için bkz. [çerçeve sembollerini çözme](#resolve-framework-symbols) .

Yerel çalışma zamanı dll 'Lerinin (örneğin, libcoreclr.so) yöntem adlarını çözümlemek için, `perfcollect` verileri dönüştürürken, ancak yalnızca bu ikililerin sembolleri varsa, simgeler için sembolleri çözer. Ayrıntılar için bkz. [yerel çalışma zamanı Için semboller alma](#get-symbols-for-the-native-runtime) bölümü.

## <a name="collect-a-trace"></a>İzleme topla

1. , [ **Trace]** olarak adlandırılan ve uygulamayı çalıştırmak Için [ **Uygulama]** olarak adlandırılan iki kabuizin vardır.

2. **[Trace]** Koleksiyonu başlatın.

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    Beklenen Çıktı:

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. **[Uygulama]** Uygulama kabuğunu aşağıdaki ortam değişkenleriyle ayarlama-bu, CoreCLR 'in izlenmesini izleme imkanı sunar.

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. **[Uygulama]** Uygulamayı çalıştırın-performans sorununu yakalamak için ihtiyacınız olduğu sürece çalışmasına izin verin. Tam Uzunluk, araştırmak istediğiniz performans sorununun gerçekleştiği zaman penceresini yeterince yakaladığı sürece gereksinim duyduğunuz kadar kısa olabilir.

    > ```bash
    > dotnet run
    > ```

5. **[Trace]** Toplamayı durdur-isabet CTRL + C.

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    Sıkıştırılmış izleme dosyası artık geçerli çalışma dizininde depolanıyor.

## <a name="view-a-trace"></a>İzleme görüntüleme

Toplanan izlemeyi görüntülemek için çeşitli seçenekler vardır. İzlemeler, Windows üzerinde [PerfView](https://aka.ms/perfview) kullanılarak en iyi şekilde görüntülenebilir, ancak kendi veya kullanan Linux üzerinde doğrudan görüntülenebilirler `PerfCollect` `TraceCompass` .

### <a name="use-perfcollect-to-view-the-trace-file"></a>İzleme dosyasını görüntülemek için PerfCollect kullanın

Topladığımız izlemeyi görüntülemek için PerfCollect kendisini kullanabilirsiniz. Bunu yapmak için aşağıdaki komutu kullanın:

```bash
./perfcollect view sampleTrace.trace.zip
```

Bu, varsayılan olarak, kullanılarak uygulamanın CPU izlemesini gösterir `perf` .

Aracılığıyla toplanan olaylara bakmak için `LTTng` , `-viewer lttng` tek tek olayları görmek için bayrağını geçirebilirsiniz:

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

Bu işlem `babeltrace` , olay yükünü yazdırmak için görüntüleyiciyi kullanır:

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a>İzleme dosyasını açmak için PerfView kullanın

Hem CPU örneğinin hem de olaylarının toplam görünümünü görmek için, `PerfView` bir Windows makinesinde kullanabilirsiniz.

1. trace.zip dosyasını Linux 'tan bir Windows makinesine kopyalayın.

2. PerfView öğesini öğesinden indirin <https://aka.ms/perfview> .

3. PerfView.exe Çalıştır

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

PerfView, izleme dosyasında bulunan verilere göre desteklenen görünümlerin listesini görüntüler.

- CPU araştırmaları için **CPU yığınları**' nı seçin.

- Ayrıntılı GC bilgileri için **GCStats** öğesini seçin.

- İşlem başına/modül/Yöntem JıT bilgileri için, **Jınstats**' ı seçin.

- İhtiyacınız olan bilgiler için bir görünüm yoksa ham olaylar görünümündeki olayları aramaya çalışırsınız.  **Olayları** seçin.

PerfView içindeki görünümleri yorumlama hakkında daha fazla bilgi için bkz. görünümdeki yardım bağlantıları veya PerfView 'daki ana pencereden **Yardım->kullanıcıları Kılavuzu**' nu seçin.

> [!NOTE]
> API aracılığıyla yazılan olaylar <xref:System.Diagnostics.Tracing.EventSource?displayProperty=nameWithType> (Framework 'ün olayları dahil), sağlayıcı adının altında gösterilmez. Bunun yerine, `EventSourceEvent` sağlayıcı altında olay olarak yazılır `Microsoft-Windows-DotNETRuntime` ve yükleri JSON serileştirilir.

### <a name="use-tracecompass-to-open-the-trace-file"></a>İzleme dosyasını açmak için Tracepusula kullanma

[Çakışan Küreler Tracepusula](https://www.eclipse.org/tracecompass/) , izlemeleri görüntülemek için kullanabileceğiniz başka bir seçenektir. `TraceCompass` , Linux makinelerinde da çalışarak, izinizi bir Windows makinesine taşımanıza gerek kalmaz. `TraceCompass`İzleme Dosyanızı açmak için kullanmak üzere dosyayı sıkıştırmayı açmanız gerekir.

```bash
unzip myTrace.trace.zip
```

`perfcollect` , toplanan LTTng izlemesini içindeki bir alt dizinde CTF dosya biçiminde kaydeder `lttngTrace` . Özel olarak, CTF dosyası gibi görünen bir dizinde yer alır `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` .

' İ seçerek CTF izleme dosyasını açın `TraceCompass` `File -> Open Trace` ve `metadata` dosyayı seçin.

Daha fazla ayrıntı için lütfen [ `TraceCompass` belgelere](https://www.eclipse.org/tracecompass/)bakın.

## <a name="resolve-framework-symbols"></a>Çerçeve sembollerini çözümle

Çerçeve simgelerinin, izlemenin toplandığı sırada el ile oluşturulması gerekir. Uygulama kodu tam zamanında derlenirken çerçeve önceden derlendiği için uygulama düzeyi sembollerine göre farklılık vardır. Yerel koda önceden derlenmiş çerçeve kodu için, `crossgen` yerel koddan yöntemlerin adına eşlemenin nasıl oluşturulacağını bilen bir çağrı yapmanız gerekir.

`perfcollect` , sizin için ayrıntıların çoğunu işleyebilir, ancak kullanılabilir olması gerekir `crossgen` . Varsayılan olarak .NET dağıtımı ile birlikte yüklenmez. Orada yoksa sizi `crossgen` `perfcollect` uyarır ve sizi bu yönergelere başvurur. Kullanmakta olduğunuz çalışma zamanına ilişkin çapraz genel sürümü tam olarak getirmek için ihtiyaç duyduğunuz şeyleri düzeltir. Çapraz genel aracı 'nı .NET çalışma zamanı dll 'Leriyle aynı dizine yerleştirirseniz (örneğin, libcoreclr.so), `perfcollect` bunu bulabilir ve izleme dosyasına çerçeve sembolleri ekleyebilirsiniz.

Normalde, bir .NET uygulaması oluşturduğunuzda, Rest için çalışma zamanının paylaşılan bir kopyasını kullanarak yazdığınız kod için DLL 'yi oluşturur.   Ancak, bir uygulamanın ' kendine ait ' bir sürümü olarak adlandırılan ' i de oluşturabilirsiniz ve bu, tüm çalışma zamanı dll 'Leri içerir. `crossgen` , kendi kendine içerilen uygulamalar oluşturmak için kullanılan NuGet paketinin bir parçasıdır. bu nedenle, doğru sürümünü almanın bir yolu, `crossgen` uygulamanızın kendine dahil edilen bir paketini oluşturmaktır.

Örnek:

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

Bu, yeni bir Merhaba Dünya uygulaması oluşturur ve bunu kendi kendine içerilen bir uygulama olarak oluşturur.

Kendi içinde kapsanan uygulamayı oluşturmanın yan etkisi olarak, DotNet Aracı, Runtime. Linux-x64. Microsoft. netcore. app adlı bir NuGet paketini indirir ve ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION dizinine yerleştirirken, sürüm .NET Core çalışma zamanının sürüm numarasıdır (örneğin, 2.1.0). Bu, öğesinin altında bir araçlar dizinidir ve ihtiyacınız olan çapraz genel araç vardır. .NET Core 3,0 ile başlayarak, paket konumu ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.

`crossgen`Aracın, uygulamanız tarafından gerçekten kullanılan çalışma zamanının yanına alınması gerekir. Genellikle uygulamanız .NET Core 'un/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION adresinde yüklü olan paylaşılan sürümünü kullanır; burada sürüm .NET çalışma zamanının sürüm numarasıdır. Bu paylaşılan bir konumdur, bu nedenle değiştirmek için süper kullanıcı olmanız gerekir. SÜRÜM 2.1.0 ise güncelleştirme komutları `crossgen` şöyle olacaktır:

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

Bunu yaptıktan sonra, `perfcollect` çerçeve sembolleri dahil etmek için çapraz gen kullanacaktır. `perfcollect`Sorun için kullanılan uyarı, dışarıda olmalıdır. Bu, makine başına yalnızca bir kez olmalıdır (çalışma alanınızı güncelleştirene kadar).

### <a name="alternative-turn-off-use-of-precompiled-code"></a>Alternatif: önceden derlenmiş kodun kullanımını devre dışı bırakın

.NET çalışma zamanını (eklemek için) güncelleştiremezseniz `crossgen` veya yukarıdaki yordam bazı nedenlerle çalışmazsa, çerçeve sembolleri almaya yönelik başka bir yaklaşım vardır. Çalışma zamanına yalnızca önceden derlenmiş Framework kodunu kullanmamalıdır. Kod, tam zamanında derlenir ve `crossgen` gerekli değildir.

> [!NOTE]
> Bu yaklaşım seçildiğinde uygulamanızın başlama süresi artırılabilir.

Bunu yapmak için aşağıdaki ortam değişkenini ekleyebilirsiniz:

```bash
export COMPlus_ZapDisable=1
```

Bu değişiklik ile tüm .NET kodu için sembolleri almanız gerekir.

## <a name="get-symbols-for-the-native-runtime"></a>Yerel çalışma zamanı için sembolleri al

Çoğu zaman kendi kodunuzla ilgileniyorsunuz. Bu, `perfcollect` Varsayılan olarak çözümlenir. Bazen, .NET DLL 'leri içinde neler olduğunu (son bölümün yaklaşık olarak) görmek yararlıdır, ancak bazen yerel çalışma zamanı dll 'lerinde (genellikle libcoreclr.so) neler olursa olsun.  `perfcollect` , yalnızca bu yerel dll sembolleri varsa (ve bunların kendisi için oldukları kitaplığın yanında ise) sembolleri dönüştürür.

Bunu yapan [DotNet-symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) adlı bir genel komut vardır. Yerel çalışma zamanı sembolleri almak için DotNet-symbol kullanmak için:

1. `dotnet-symbol` yükleme:

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. Sembolleri indirin. .NET Core çalışma zamanının yüklü sürümü 2.1.0 ise, bunu yapmak için komut şu şekilde olur:

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. Sembolleri doğru yere kopyalayın.

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    Uygun dizine yazma erişiminizin olmadığı için bu işlem yapılacağından, `perf buildid-cache` sembolleri eklemek için kullanabilirsiniz.

Bundan sonra, çalıştırdığınızda yerel dll 'ler için simgesel adlar almalısınız `perfcollect` .

## <a name="collect-in-a-docker-container"></a>Bir Docker kapsayıcısında toplayın

Kapsayıcı ortamlarında kullanma hakkında daha fazla bilgi için `perfcollect` bkz. [kapsayıcılarda tanılamayı toplama](./diagnostics-in-containers.md).

## <a name="learn-more-about-collection-options"></a>Koleksiyon seçenekleri hakkında daha fazla bilgi edinin

`perfcollect`Tanılama gereksinimlerinize daha iyi uyacak şekilde, aşağıdaki isteğe bağlı bayrakları belirtebilirsiniz.

### <a name="collect-for-a-specific-duration"></a>Belirli bir süre için topla

Belirli bir süre için bir izleme toplamak istediğinizde, `-collectsec` ve için bir izlemenin toplanacağı toplam saniyeyi belirten bir sayı olan seçeneğini kullanabilirsiniz.

### <a name="collect-threadtime-traces"></a>İşParçacığıSüresi izlemelerini topla

`-threadtime`İle belirtmek `perfcollect` iş parçacığı başına CPU kullanım verilerini toplamanıza olanak tanır. Bu, her iş parçacığının CPU süresini hangi noktada harcamalarından analiz etmenizi sağlar.

### <a name="collect-traces-for-managed-memory-and-garbage-collector-performance"></a>Yönetilen bellek ve çöp toplayıcı performansı için izlemeleri toplayın

Aşağıdaki seçenekler, GC olaylarını özel olarak çalışma zamanından toplamanızı sağlar.

* `perfcollect collect -gccollectonly`

Yalnızca minimal bir GC toplama olayları kümesi toplayın. Bu, hedef uygulamanın performansına en düşük etkisi olan en az ayrıntılı GC olay toplama profilidir. Bu komut `PerfView.exe /GCCollectOnly collect` PerfView komutuna benzer.

* `perfcollect collect -gconly`

JıT, yükleyici ve özel durum olaylarıyla daha ayrıntılı GC toplama olayları toplayın. Bu, daha ayrıntılı Olaylar (örneğin, ayırma bilgileri ve GC JOIN bilgileri) ister ve hedef uygulamanın performansına göre daha fazla etkiye sahip olacaktır `-gccollectonly` . Bu komut `PerfView.exe /GCOnly collect` PerfView komutuna benzer.

* `perfcollect collect -gcwithheap`

En ayrıntılı GC toplama olaylarını toplayın. Bu, yığın daha fazla sonuç ve hareketlerini de izler. Bu, GC davranışının derinlemesine analizini sağlar ancak her GC ikiden fazla kez daha uzun sürebileceğinden yüksek performans maliyeti olur. Üretim ortamlarında izlerken bu izleme seçeneğini kullanmanın performansını anlamanız önerilir.
