---
title: Hata ayıklama bir bellek sızıntısı öğretici
description: .NET Core'da bellek sızıntısını nasıl hata ayıklayın öğrenin.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: d47992bab9dab64cf7f88ff679eef407dd891b5a
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021366"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a>Öğretici: .NET Core'da bellek sızıntısını hata ayıklama

**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler

Bu öğretici, bir .NET Core bellek sızıntısıanaliz etmek için araçları gösterir.

Bu öğretici, kasıtlı olarak bellek sızdırmak için tasarlanmış bir örnek uygulama kullanır. Örnek bir egzersiz olarak sağlanmaktadır. İstemeden bellek sızdıran bir uygulamayı da analiz edebilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
>
> - Yönetilen bellek kullanımını [dotnet sayaçları](dotnet-counters.md)ile inceleyin.
> - Bir döküm dosyası oluşturun.
> - Döküm dosyasını kullanarak bellek kullanımını çözümle.

## <a name="prerequisites"></a>Ön koşullar

Öğretici kullanır:

- [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya daha sonraki bir sürüm.
- [nokta-izleme](dotnet-trace.md) liste işlemleri için.
- yönetilen bellek kullanımını denetlemek için [dotnet sayaçları.](dotnet-counters.md)
- bir döküm dosyasını toplamak ve çözümlemek için [dotnet-dökümü.](dotnet-dump.md)
- Tanılamak için [örnek hata ayıklama hedef](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) uygulaması.

Öğretici, örnek ve araçların yüklü ve kullanıma hazır olduğunu varsayar.

## <a name="examine-managed-memory-usage"></a>Yönetilen bellek kullanımını inceleme

Bu senaryoya neden olmamıza yardımcı olacak tanılama verilerini toplamaya başlamadan önce, gerçekten bir bellek sızıntısı (bellek büyümesi) gördüğünüzden emin olmanız gerekir. Bunu doğrulamak için [dotnet sayaçları](dotnet-counters.md) aracını kullanabilirsiniz.

Bir konsol penceresi açın ve [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)indirip fermuarını açtığınız dizine gidin. Hedefi çalıştırın:

```dotnetcli
dotnet run
```

Ayrı bir konsoldan, [dotnet izleme](dotnet-trace.md) aracını kullanarak işlem kimliğini bulun:

```console
dotnet-trace ps
```

Çıktı aşağıdakilere benzer olmalıdır:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Şimdi, [dotnet sayaçları](dotnet-counters.md) aracıyla yönetilen bellek kullanımını kontrol edin. Yenilemeler `--refresh-interval` arasındaki saniye sayısını belirtir:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Canlı çıktı aşağıdakilere benzer olmalıdır:

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

Bu satıra odaklanarak:

```console
    GC Heap Size (MB)                                  4
```

Yönetilen yığın belleği başlatmadan hemen sonra 4 MB olduğunu görebilirsiniz.

Şimdi, URL'ye `http://localhost:5000/api/diagscenario/memleak/20000`vur.

Bellek kullanımının 30 MB'a kadar büyüdüğünü gözlemleyin.

```console
    GC Heap Size (MB)                                 30
```

Bellek kullanımını izleyerek, belleğin büyüdüğünü veya sızdırdığını rahatlıkla söyleyebilirsiniz. Bir sonraki adım bellek analizi için doğru verileri toplamaktır.

### <a name="generate-memory-dump"></a>Bellek dökümü oluşturma

Olası bellek sızıntılarını analiz ederken, uygulamanın bellek yığınına erişmeniz gerekir. Sonra bellek içeriğini analiz edebilirsiniz. Nesneler arasındaki ilişkilere baktığınızda, belleğin neden serbest bırakılmadığını niçin oluşturduğuna dair teoriler oluşturursunuz. Ortak bir tanılama veri kaynağı, Windows'daki bir bellek dökümü veya Linux'taki eşdeğer çekirdek dökümüdür. .NET Core uygulamasının dökümdöküm'ü oluşturmak için [dotnet dökümü aracını](dotnet-dump.md) kullanabilirsiniz.

Daha önce başlatılan [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) kullanarak, linux çekirdek dökümü oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet-dump collect -p 4807
```

Sonuç, aynı klasörde bulunan bir çekirdek dökümüdür.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Başarısız işlemi yeniden başlatma

Döküm toplandıktan sonra, başarısız işlemi tanılamak için yeterli bilgiye sahip olmalısınız. Başarısız olan işlem bir üretim sunucusunda çalışıyorsa, şimdi işlemi yeniden başlatarak kısa vadeli düzeltme için ideal bir zaman.

Bu öğreticide, artık [Örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) bitirdiniz ve kapatabilirsiniz. Sunucuyu başlatan terminale gidin `Control-C`ve 'ye basın.

### <a name="analyze-the-core-dump"></a>Çekirdek dökümünün analizi

Artık bir çekirdek dökümü oluşturuldu, dökümü analiz etmek için [dotnet-dökümü](dotnet-dump.md) aracını kullanın:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

Analiz `core_20190430_185145` etmek istediğiniz çekirdek dökümünün adı nerede?

> [!NOTE]
> *libdl.so* bulunamaz şikayet eden bir hata görürseniz, *libc6-dev* paketini yüklemeniz gerekebilir. Daha fazla bilgi [için Linux'ta .NET Core için Ön koşullara](../install/dependencies.md?pivots=os-linux)bakın.

SOS komutlarını girebileceğiniz bir istem sunulur. Genellikle, bakmak istediğiniz ilk şey yönetilen yığının genel durumudur:

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

Burada çoğu nesnenin veya `String` `Customer` nesnenin olduğunu görebilirsiniz.

Tüm `String` örneklerin `dumpheap` listesini almak için yöntem tablosu (MT) ile komutu yeniden kullanabilirsiniz:

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

Nesnenin `gcroot` nasıl ve neden `System.String` köksünün dayandığını görmek için artık bir örnekteki komutu kullanabilirsiniz. Bu komut 30 MB'lık bir yığınla birkaç dakika aldığından sabırlı olun:

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

Doğrudan nesne tarafından `String` tutulduğunu `Customer` ve dolaylı olarak bir `CustomerCache` nesne tarafından tutulduğunu görebilirsiniz.

Çoğu `String` nesnenin benzer bir deseni takip ettiğini görmek için nesneleri boşaltmaya devam edebilirsiniz. Bu noktada, araştırma kodunuzda kök nedeni belirlemek için yeterli bilgi sağladı.

Bu genel yordam, büyük bellek sızıntılarının kaynağını belirlemenize olanak tanır.

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticide, örnek bir web sunucusu başlattınız. Bu sunucu, başarısız işlemi yeniden [başlat](#restart-the-failed-process) bölümünde açıklandığı gibi kapatılmış olmalıdır.

Oluşturulan döküm dosyasını da silebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğretici tamamladıktan sonra tebrikler.

Hala daha fazla tanı lama eğitimi yayınlıyoruz. Taslak sürümleri [dotnet/teşhis](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) deposunda okuyabilirsiniz.

Bu öğretici, anahtar .NET tanılama araçlarının temellerini kapsamaktadır. Gelişmiş kullanım için aşağıdaki başvuru belgelerine bakın:

* [nokta-izleme](dotnet-trace.md) liste işlemleri için.
* yönetilen bellek kullanımını denetlemek için [dotnet sayaçları.](dotnet-counters.md)
* bir döküm dosyasını toplamak ve çözümlemek için [dotnet-dökümü.](dotnet-dump.md)
