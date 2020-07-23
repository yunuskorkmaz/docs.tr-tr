---
title: Bellek sızıntısı öğreticisinde hata ayıklama
description: .NET Core 'da Bellek sızıntısını nasıl ayıklayacağınızı öğrenin.
ms.topic: tutorial
ms.date: 04/20/2020
ms.openlocfilehash: ff684f9b9402cb8b7b648e792a1d37ddcc96b399
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924896"
---
# <a name="debug-a-memory-leak-in-net-core"></a>.NET Core 'da bellek sızıntısı hatalarını ayıklama

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri

Bu öğreticide, .NET Core Bellek sızıntısını çözümlemek için Araçlar gösterilmektedir.

Bu öğreticide, kasıtlı olarak bellek sızıntısı için tasarlanan örnek bir uygulama kullanılmaktadır. Örnek, bir alıştırma olarak sağlanır. Yanlışlıkla bellek sızdıran bir uygulamayı analiz edebilirsiniz.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
>
> - [DotNet-Counters](dotnet-counters.md)ile yönetilen bellek kullanımını inceleyin.
> - Döküm dosyası oluştur.
> - Döküm dosyasını kullanarak bellek kullanımını çözümleyin.

## <a name="prerequisites"></a>Önkoşullar

Öğretici şunları kullanır:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) veya sonraki bir sürümü.
- [DotNet-](dotnet-trace.md) liste süreçlerini izleme.
- [DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar.
- [DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm.
- Tanılama için bir [örnek hata ayıklama hedef](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) uygulaması.

Öğretici, örnek ve araçların yüklendiğini ve kullanıma hazırlandığını varsayar.

## <a name="examine-managed-memory-usage"></a>Yönetilen bellek kullanımını incele

Bu senaryonun köke neden olması için tanılama verileri toplamaya başlamadan önce, aslında bir bellek sızıntısı (bellek büyümesi) gördüğünüzü unutmayın. Doğrulamak için [DotNet-Counters](dotnet-counters.md) aracını kullanabilirsiniz.

Bir konsol penceresi açın ve [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/)indirdiğiniz ve sıkıştırmadan indirdiğiniz dizine gidin. Hedefi Çalıştır:

```dotnetcli
dotnet run
```

Ayrı bir konsoldan, [DotNet-Trace](dotnet-trace.md) aracını kullanarak işlem kimliğini bulun:

```console
dotnet-trace ps
```

Çıktının şuna benzer olması gerekir:

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

Şimdi, [DotNet-Counters](dotnet-counters.md) aracıyla yönetilen bellek kullanımını kontrol edin. `--refresh-interval`Yenilemeler arasındaki saniye sayısını belirtir:

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

Canlı çıktının şuna benzer olması gerekir:

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

Bu satıra odaklanma:

```console
    GC Heap Size (MB)                                  4
```

Yönetilen yığın belleğinin başlangıçtan sonra 4 MB olduğunu görebilirsiniz.

Şimdi URL 'ye basın `https://localhost:5001/api/diagscenario/memleak/20000` .

Bellek kullanımının 30 MB 'a kadar büyüdiğini gözlemleyin.

```console
    GC Heap Size (MB)                                 30
```

Bellek kullanımını izleyerek belleğin büyüdüğünü veya sızmasını güvenli bir şekilde söyleyebilirsiniz. Sonraki adım bellek analizine yönelik doğru verileri toplamaktır.

### <a name="generate-memory-dump"></a>Bellek dökümü oluştur

Olası bellek sızıntılarını analiz edilirken uygulamanın bellek yığınına erişmeniz gerekir. Daha sonra bellek içeriğini çözümleyebilirsiniz. Nesneler arasındaki ilişkilere bakarak belleğin neden serbest bırakılmadığına ilişkin bir kayıt oluşturursunuz. Ortak bir tanılama veri kaynağı, Windows 'da bellek dökümleridir veya Linux üzerinde eşdeğer çekirdek dökümleridir. .NET Core uygulamasının bir dökümünü oluşturmak için [DotNet-dump)](dotnet-dump.md) aracını kullanabilirsiniz.

Önceden başlatılan [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) kullanarak bir Linux core dökümü oluşturmak için aşağıdaki komutu çalıştırın:

```dotnetcli
dotnet-dump collect -p 4807
```

Sonuç, aynı klasörde bulunan temel bir dökümdir.

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a>Başarısız olan işlemi yeniden Başlat

Döküm toplandıktan sonra, başarısız olan işlemi tanılamak için yeterli bilgiye sahip olmanız gerekir. Başarısız işlem bir üretim sunucusunda çalışıyorsa, artık işlemi yeniden başlatarak kısa süreli düzeltmeye yönelik ideal bir süredir.

Bu öğreticide, şimdi [örnek hata ayıklama hedefini](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) tamamladınız ve kapatabilirsiniz. Sunucuyu başlatan terminale gidin ve <kbd>CTRL + C</kbd>tuşlarına basın.

### <a name="analyze-the-core-dump"></a>Çekirdek dökümünü analiz etme

Oluşturulmuş bir temel döküm olduğuna göre, dökümü çözümlemek için [DotNet-dump](dotnet-dump.md) aracını kullanın:

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

`core_20190430_185145`, Analiz etmek istediğiniz temel döküm adıdır.

> [!NOTE]
> *Libdl.so* bulunamadığını belirten bir hata görürseniz, *libc6-dev* paketini yüklemek zorunda kalabilirsiniz. Daha fazla bilgi için bkz. [Linux üzerinde .NET Core önkoşulları](../install/dependencies.md?pivots=os-linux).

SOS komutları girebileceğiniz bir istem sunulur. Genellikle, bakmak istediğiniz ilk şey, yönetilen yığının genel durumudur:

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

Burada nesnelerin ya da nesnelerin olduğunu görebilirsiniz `String` `Customer` .

`dumpheap`Tüm örneklerin bir listesini almak için komutunu Yöntem tablosu (MT) ile birlikte kullanabilirsiniz `String` :

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

Artık `gcroot` `System.String` nesnenin nasıl ve neden kök olarak oluşturulduğunu görmek için bir örnek üzerinde komutunu kullanabilirsiniz. Bu komutun 30 MB 'lik bir yığın ile birkaç dakika sürdüğü için sabırlı olun:

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

`String` `Customer` Nesnesinin doğrudan nesne tarafından ve bir nesne tarafından dolaylı olarak tutulduğundan emin olabilirsiniz `CustomerCache` .

Birçok `String` nesnenin benzer bir düzende izlediğinden emin olmak için nesnelerin dökümünü almaya devam edebilirsiniz. Bu noktada, araştırma kodunuzda kök nedenini belirlemek için yeterli bilgi sağladı.

Bu genel yordam, büyük bellek sızıntılarının kaynağını tanımlamanızı sağlar.

## <a name="clean-up-resources"></a>Kaynakları temizleme

Bu öğreticide, örnek bir Web sunucusu başladıysanız. Bu sunucu, [başarısız Işlem yeniden başlatma](#restart-the-failed-process) bölümünde açıklandığı gibi kapatılmış olmalıdır.

Oluşturulan döküm dosyasını da silebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet-](dotnet-trace.md) liste işlemlerine izleme
- [DotNet-](dotnet-counters.md) yönetilen bellek kullanımını denetlemek için sayaçlar
- [DotNet-](dotnet-dump.md) döküm dosyasını toplamak ve analiz etmek için döküm
- [DotNet/Diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [.NET Core 'da yüksek CPU 'YU hata ayıkla](debug-highcpu.md)
