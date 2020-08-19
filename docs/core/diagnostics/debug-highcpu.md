---
title: Yüksek CPU kullanımı hata ayıkla-.NET Core
description: .NET Core 'da yüksek CPU kullanımında hata ayıklama konusunda size yol gösteren bir öğretici.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 93076bbce3baf3a219b25c927d2aba3d2d57456f
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557808"
---
# <a name="debug-high-cpu-usage-in-net-core"></a>.NET Core 'da yüksek CPU kullanımını hata ayıkla

**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,1 SDK ve sonraki sürümleri

Bu öğreticide, aşırı CPU kullanımı senaryosunda hata ayıklamayı öğreneceksiniz. [Web uygulaması](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) kaynak kodu deposu ASP.NET Core sunulan örneği kullanarak, kasıtlı olarak bir kilitlenmeye neden olabilirsiniz. Uç nokta, askıda kalma ve iş parçacığı birikmesi ile karşılaşacaktır. Çeşitli araçları kullanarak bu senaryoyu tanılama verilerinin çeşitli önemli parçalarından nasıl tanınbileceğinizi öğreneceksiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
>
> - Yüksek CPU kullanımını araştır
> - [DotNet sayaçları](dotnet-counters.md) ile CPU kullanımını belirleme
> - İzleme oluşturma için [DotNet-Trace](dotnet-trace.md) kullanın
> - PerfView 'da profil performansı
> - Aşırı CPU kullanımını Tanıla ve çöz

## <a name="prerequisites"></a>Ön koşullar

Öğretici şunları kullanır:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.
- Senaryonun tetiklenmesi için [örnek hata ayıklama hedefi](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) .
- [DotNet-](dotnet-trace.md) işlem listelemek ve bir profil oluşturmak için izleyin.
- [DotNet sayaçları](dotnet-counters.md) , CPU kullanımını izlemeye yönelik sayaçlardır.

## <a name="cpu-counters"></a>CPU sayaçları

Tanılama verilerini toplamayı denemeden önce, yüksek bir CPU koşulu gözlemleyebilirsiniz. Proje kök dizininde aşağıdaki komutu kullanarak [Örnek uygulamayı](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) çalıştırın.

```dotnetcli
dotnet run
```

İşlem KIMLIĞINI bulmak için aşağıdaki komutu kullanın:

```dotnetcli
dotnet-trace ps
```

Komut çıktıınızdan işlem KIMLIĞI ' ni bir yere göz atın. İşlem KIMLIĞINIZ idi `22884` , ancak sizinki farklı olacak. Geçerli CPU kullanımını denetlemek için [DotNet-Counters](dotnet-counters.md) aracı komutunu kullanın:

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

, `refresh-interval` Sayaç yoklama CPU değerleri arasındaki saniye sayısıdır. Çıktının aşağıdakine benzer olması gerekir:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

Web uygulaması çalışırken, başlangıçtan hemen sonra CPU tüketilmez ve tarihinde raporlanır `0%` . Rota `api/diagscenario/highcpu` parametresi olarak bulunan yola gidin `60000` :

`https://localhost:5001/api/diagscenario/highcpu/60000`

Şimdi [DotNet-Counters](dotnet-counters.md) komutunu yeniden çalıştırın. Yalnızca öğesini izlemek için `cpu-usage` `System.Runtime[cpu-usage]` komutunun bir parçası olarak belirtin.

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

CPU kullanımında aşağıda gösterildiği gibi bir artış görmeniz gerekir:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

İstek süresince CPU kullanımı %25 ' in üzerine gelmeyecektir. Konak makinesine bağlı olarak, değişen CPU kullanımı beklenir.

> [!TIP]
> Daha yüksek bir CPU kullanımını görselleştirmek için, bu uç noktayı birden çok tarayıcı sekmesinde aynı anda kullanabilirsiniz.

Bu noktada, CPU 'nun beklediğinizden daha yüksek bir şekilde çalıştığını söyleyebilirsiniz.

## <a name="trace-generation"></a>İzleme oluşturma

Yavaş bir istek analiz edilirken, kodun yaptığına ilişkin Öngörüler sağlayabilen bir tanılama aracına ihtiyacınız vardır. Olağan seçim bir profil oluşturucu ve aralarından seçim yapabileceğiniz farklı profil Oluşturucu seçenekleri vardır.

### <a name="linux"></a>[Linux](#tab/linux)

`perf`Araç .NET Core uygulama profilleri oluşturmak için kullanılabilir. [Örnek hata ayıklama hedefinin](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)önceki örneğinden çıkın.

`COMPlus_PerfMapEnabled`.NET Core uygulamasının dizinde bir dosya oluşturmasını sağlamak için ortam değişkenini ayarlayın `map` `/tmp` . Bu `map` dosya tarafından, `perf` CPU adresini JIT tarafından oluşturulan işlevlere ada göre eşlemek için kullanılır. Daha fazla bilgi için bkz. [yazma perf Map](../run-time-config/debugging-profiling.md#write-perf-map).

[Örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) aynı Terminal oturumunda çalıştırın.

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

Yüksek CPU API uç noktasını ( `https://localhost:5001/api/diagscenario/highcpu/60000` ) yeniden deneyin. 1 dakikalık istek içinde çalışırken, `perf` Işlem Kimliğinizle komutunu çalıştırın:

```bash
sudo perf record -p 2266 -g
```

`perf`Komut, performans toplama işlemini başlatır. 20-30 saniye boyunca çalışmasına izin verin ve ardından, koleksiyon işleminden çıkmak için <kbd>CTRL + C</kbd> tuşlarına basın. `perf`İzlemenin çıkışını görmek için aynı komutu kullanabilirsiniz.

```bash
sudo perf report -f
```

Aşağıdaki komutları kullanarak bir _Flame grafiği_ de oluşturabilirsiniz:

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

Bu komut `flamegraph.svg` , tarayıcıda görüntüleyebilmeniz için performans sorununu araştırmak üzere bir oluşturur:

[![Flame grafiği SVG resmi](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)

### <a name="windows"></a>[Windows](#tab/windows)

Windows 'da, [DotNet-Trace](dotnet-trace.md) aracını bir profil oluşturucu olarak kullanabilirsiniz. Önceki [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios)kullanarak, yüksek CPU uç noktasını ( `https://localhost:5001/api/diagscenario/highcpu/60000` ) yeniden deneyin. 1 dakikalık istek içinde çalışırken `collect` komutunu aşağıdaki gibi kullanın:

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

20-30 saniye boyunca [DotNet-Trace](dotnet-trace.md) çalışmasına izin verin ve ardından <kbd>ENTER</kbd> tuşuna basarak koleksiyondan çıkın. Sonuç, `nettrace` aynı klasörde bulunan bir dosyadır. `nettrace`Dosyalar, Windows 'da mevcut analiz araçlarını kullanmanın harika bir yoludur.

Öğesini `nettrace` [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) aşağıda gösterildiği gibi açın.

[![PerfView resmi](media/perfview.jpg)](media/perfview.jpg#lightbox)

---

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet-](dotnet-trace.md) liste işlemlerine izleme
- [DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar
- [DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm
- [DotNet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Core 'da kilitlenmeyle hata ayıklama](debug-deadlock.md)
