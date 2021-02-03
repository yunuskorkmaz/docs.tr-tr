---
title: Ayrıntılı derleme yükleme bilgilerini toplayın-.NET Core
description: .NET Core 'da derleme yükleme bilgilerinin nasıl toplanalınacağını gösteren açıklama
author: elinor-fung
ms.author: elfung
ms.date: 11/17/2020
ms.openlocfilehash: b121982995b440ade6d72190f44f9b9d237c8af6
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506613"
---
# <a name="collect-detailed-assembly-loading-information"></a>Ayrıntılı derleme yükleme bilgilerini topla

.NET 5,0 ' den itibaren, çalışma zamanı, `EventPipe` derleme yükleme sorunlarını tanılamaya yardımcı olmak üzere [yönetilen derleme yükleme](loading-managed.md) hakkında ayrıntılı bilgiler aracılığıyla olayları oluşturabilir. Bu [Olaylar](../../fundamentals/diagnostics/runtime-loader-binder-events.md) `Microsoft-Windows-DotNETRuntime` sağlayıcı tarafından `AssemblyLoader` () anahtar sözcüğü altında dağıtılır `0x4` .

## <a name="prerequisites"></a>Önkoşullar

- [.Net 5,0 SDK](https://dotnet.microsoft.com/download) veya sonraki sürümleri
- [DotNet-Trace](../diagnostics/dotnet-trace.md) aracı.

## <a name="collect-a-trace-with-assembly-loading-events"></a>Derleme yükleme olayları ile bir izleme toplama

Çalışma zamanında derleme yükleme olaylarını etkinleştirmek ve bunların bir izlemesini toplamak için `dotnet-trace` aşağıdaki komutla kullanın:

```console
dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id <pid>
```

Bu, belirtilen bir izleme toplar ve bu, `<pid>` `AssemblyLoader` `Microsoft-Windows-DotNETRuntime` sağlayıcıdaki olayları etkinleştirir. Sonuç bir `.nettrace` dosyadır.

## <a name="view-a-trace"></a>İzleme görüntüleme

Toplanan izleme dosyası, Windows 'da [PerfView](https://github.com/microsoft/perfview)içindeki olaylar görünümü kullanılarak görüntülenebilir. Tüm derleme yükleme olayları ön ekine sahip olacaktır `Microsoft-Windows-DotNETRuntime/AssemblyLoader` .

## <a name="example-on-windows"></a>Örnek (Windows üzerinde)

Bu örnek, [uzantı noktaları örneğini yükleyen derlemeyi](https://github.com/dotnet/samples/tree/master/core/extensions/AssemblyLoading)kullanır. Uygulama bir derlemeyi yüklemeye çalışır `MyLibrary` -uygulama tarafından başvurulmayan bir derleme ve bu nedenle, bir derlemenin uzantı noktası yükleme yüklemesinin başarıyla yüklenmesi gerekir.

### <a name="collect-the-trace"></a>İzlemeyi topla

01. İndirilen örnekteki dizine gidin. Uygulamayı ile oluşturun:

    ```console
    dotnet build
    ```

01. Uygulamayı duraklaması gerektiğini belirten bağımsız değişkenlerle başlatın, anahtar basma için bekleniyor. Devam etmek `AssemblyLoadContext` için, başarılı bir yük için gerekli işleme olmadan derlemeyi varsayılan olarak yüklemeye çalışır. Çıkış dizinine gidin ve şunu çalıştırın:

    ```console
    AssemblyLoading.exe /d default
    ```

01. Uygulamanın işlem KIMLIĞINI bulun.

    ```console
    dotnet-trace ps
    ```

    Çıktı, kullanılabilir işlemlerin listesini listelecektir. Örneğin:

    ```console
    35832 AssemblyLoading C:\src\AssemblyLoading\bin\Debug\net5.0\AssemblyLoading.exe
    ```

01. `dotnet-trace`Çalışan uygulamaya ekleyin.

    ```console
    dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:4 --process-id 35832
    ```

01. Uygulamayı çalıştıran pencerede, programın devam etmesini sağlamak için herhangi bir tuşa basın. Uygulama çıktıktan sonra izleme otomatik olarak durur.

### <a name="view-the-trace"></a>İzlemeyi görüntüleme

Toplanan izlemeyi [PerfView](https://github.com/microsoft/perfview) ' de açın ve olaylar görünümünü açın. Olaylar listesini `Microsoft-Windows-DotNETRuntime/AssemblyLoader` olaylara filtreleyin.

:::image type="content" source="media/collect-details/assembly-loader-filter.png" alt-text="PerfView derleme yükleyicisi filtre resmi":::

İzleme başlatıldıktan sonra uygulamada gerçekleşen tüm derleme yüklemeleri gösterilir. Bu örnek için ilgili derleme için yükleme işlemini incelemek üzere `MyLibrary` daha fazla filtreleme yapabiliriz.

### <a name="assembly-loads"></a>Derleme yükleri

Görünümü [`Start`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstart-event) ve [`Stop`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadstop-event) olayları `Microsoft-Windows-DotNETRuntime/AssemblyLoader` sol taraftaki olay listesini kullanarak filtreleyin. Sütunları, `AssemblyName` `ActivityID` ve `Success` görünümüne ekleyin. İçeren olaylara filtre uygulayın `MyLibrary` .

:::image type="content" source="media/collect-details/start-stop.png" alt-text="PerfView başlatma ve durdurma olayları görüntüsü":::

| Olay Adı             | AssemblyName                                      | ActivityID | Başarılı |
| ---------------------- | ------------------------------------------------- | ---------- | ------- |
| `AssemblyLoader/Start` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     |         |
| `AssemblyLoader/Stop`  | `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     | Yanlış   |

`Start` / `Stop` `Success=False` `Stop` Olayda, yükleme işleminin başarısız olduğunu belirten bir çift görmeniz gerekir. İki olayın aynı etkinlik KIMLIĞINE sahip olduğunu unutmayın. Etkinlik KIMLIĞI, diğer tüm derleme yükleyicisi olaylarını yalnızca bu yükleme işlemine karşılık gelen olanlarla filtrelemek için kullanılabilir.

### <a name="breakdown-of-attempt-to-load"></a>Yükleme denemesinin dökümü

Yükleme işleminin daha ayrıntılı bir dökümü için, görünümü soldaki olay listesini kullanarak altındaki [ `ResolutionAttempted` olaylara](../../fundamentals/diagnostics/runtime-loader-binder-events.md#resolutionattempted-event) filtreleyin `Microsoft-Windows-DotNETRuntime/AssemblyLoader` . Sütunları, `AssemblyName` `Stage` ve `Result` görünümüne ekleyin. Çiftin etkinlik kimliği olan olaylara filtre uygulayın `Start` / `Stop` .

:::image type="content" source="media/collect-details/resolution-attempted.png" alt-text="PerfView Resolutiondenenen olaylar görüntüsü":::

| Olay Adı                           | AssemblyName                                      | Aşama                               | Sonuç             |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `AssemblyNotFound` |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AppDomainAssemblyResolveEvent`     | `AssemblyNotFound` |

Yukarıdaki olaylar, derleme yükleyicisinin geçerli yükleme bağlamına bakarak, yönetilen uygulama derlemeleri için varsayılan yoklama mantığını çalıştırıp, olay için işleyicileri çağırarak <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> ve için işleyicileri çağırarak derlemeyi çözmeyi denediğini gösterir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> . Bu adımların tümü için derleme bulunamadı.

### <a name="extension-points"></a>Uzantı noktaları

Hangi uzantı noktalarının çağırılacağını görmek için, görünümün [`AssemblyLoadContextResolvingHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#assemblyloadcontextresolvinghandlerinvoked-event) [`AppDomainAssemblyResolveHandlerInvoked`](../../fundamentals/diagnostics/runtime-loader-binder-events.md#appdomainassemblyresolvehandlerinvoked-event) sol taraftaki `Microsoft-Windows-DotNETRuntime/AssemblyLoader` olay listesini kullanarak ve altındaki öğesine filtre uygulayın. Sütunları `AssemblyName` ve görünüme ekleyin `HandlerName` . Çiftin etkinlik kimliği olan olaylara filtre uygulayın `Start` / `Stop` .

:::image type="content" source="media/collect-details/extension-point.png" alt-text="PerfView uzantı noktası olayları görüntüsü":::

| Olay Adı                                                  | AssemblyName                                      | HandlerName                      |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` |
| `AssemblyLoader/AppDomainAssemblyResolveHandlerInvoked`     | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAppDomainAssemblyResolve`     |

Yukarıdaki olaylar, `OnAssemblyLoadContextResolving` olay için çağrılan <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> ve `OnAppDomainAssemblyResolve` olay için çağrılan bir işleyici olarak adlandırılan bir işleyicinin olduğunu gösterir <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .

### <a name="collect-another-trace"></a>Başka bir izleme topla

Uygulamayı olay için işleyicisi derlemeyi yükleyecek şekilde bağımsız değişkenlerle çalıştırın <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> `MyLibrary` .

```console
AssemblyLoading /d default alc-resolving
```

`.nettrace` [Yukarıdaki adımları](#collect-the-trace)kullanarak başka bir dosya toplayın ve açın.

`Start`Ve `Stop` olaylarına yeniden filtre uygulayın `MyLibrary` . Aralarında `Start` / `Stop` başka bir çift görmeniz gerekir `Start` / `Stop` . İç yükleme işlemi, ne zaman çağrıldığı için işleyicinin tetiklediği yükü temsil eder <xref:System.Runtime.Loader.AssemblyLoadContext.Resolving?displayProperty=nameWithType> <xref:System.Runtime.Loader.AssemblyLoadContext.LoadFromAssemblyPath%2A?displayProperty=nameWithType> . Bu kez, `Success=True` `Stop` olayda yükleme işleminin başarılı olduğunu belirten bir olay görmeniz gerekir. `ResultAssemblyPath`Alan, sonuçta elde edilen derlemenin yolunu gösterir.

:::image type="content" source="media/collect-details/start-stop-success.png" alt-text="PerfView başarılı başlatma ve durdurma olayları görüntüsü":::

| Olay Adı             | AssemblyName                                                       | ActivityID | Başarılı | ResultAssemblyPath                                      |
| ---------------------- | ------------------------------------------------------------------ |------------|---------| ------------------------------------------------------- |
| `AssemblyLoader/Start` |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     |         |                                                         |
| `AssemblyLoader/Start` | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | 1/2/1/   |         |                                                         |
| `AssemblyLoader/Stop`  | `MyLibrary, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null` | 1/2/1/   | Doğru    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |
| `AssemblyLoader/Stop`  |                  `MyLibrary, Culture=neutral, PublicKeyToken=null` | 1/2/     | Doğru    | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Daha sonra, `ResolutionAttempted` derlemenin başarıyla çözümlenme adımını öğrenmek için dış yükün etkınlık kimliği olan olaylara bakabiliriz. Bu kez, olaylar `AssemblyLoadContextResolvingEvent` aşamanın başarılı olduğunu gösterir. `ResultAssemblyPath`Alan, sonuçta elde edilen derlemenin yolunu gösterir.

:::image type="content" source="media/collect-details/resolution-attempted-success.png" alt-text="PerfView başarıyla Resolutiondenenen olaylar görüntüsü":::

| Olay Adı                           | AssemblyName                                      | Aşama                               | Sonuç             | ResultAssemblyPath |
| ------------------------------------ | ------------------------------------------------- | ----------------------------------- | ------------------ | ------------------ |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `FindInLoadContext`                 | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `ApplicationAssemblies`             | `AssemblyNotFound` |                    |
| `AssemblyLoader/ResolutionAttempted` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `AssemblyLoadContextResolvingEvent` | `Success`          | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

Olaylara bakmak `AssemblyLoadContextResolvingHandlerInvoked` adlı işleyicinin `OnAssemblyLoadContextResolving` çağırılacağını gösterir. `ResultAssemblyPath`Alan, işleyicinin döndürdüğü derlemenin yolunu gösterir.

:::image type="content" source="media/collect-details/extension-point-success.png" alt-text="PerfView başarılı uzantı noktası olayları görüntüsü":::

| Olay Adı                                                  | AssemblyName                                      | HandlerName                      | ResultAssemblyPath |
| ----------------------------------------------------------- | ------------------------------------------------- | -------------------------------- | ------------------ |
| `AssemblyLoader/AssemblyLoadContextResolvingHandlerInvoked` | `MyLibrary, Culture=neutral, PublicKeyToken=null` | `OnAssemblyLoadContextResolving` | *C:\src\AssemblyLoading\bin\Debug\net5.0\MyLibrary.dll* |

`ResolutionAttempted` `AppDomainAssemblyResolveEvent` `AppDomainAssemblyResolveHandlerInvoked` Olayı başlatan yükleme algoritmasındaki adıma ulaşmadan önce, aşama veya herhangi bir olay ile artık bir olay olmadığını unutmayın <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> .

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yükleyici olayları](../../fundamentals/diagnostics/runtime-loader-binder-events.md)
- [dotnet-trace](../diagnostics/dotnet-trace.md)
- [PerfView](https://github.com/microsoft/perfview)
