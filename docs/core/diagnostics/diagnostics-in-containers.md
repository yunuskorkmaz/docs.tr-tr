---
title: Kapsayıcılarda tanılamayı toplayın
description: Bu makalede, .NET Core tanılama araçları 'nın Docker kapsayıcılarında nasıl kullanılabileceğini öğreneceksiniz.
ms.date: 09/01/2020
ms.openlocfilehash: e57f3696433bbf6f35b2e3e5d1e72ae8b1e3eeb3
ms.sourcegitcommit: b4a46f6d7ebf44c0035627d00924164bcae2db30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91451093"
---
# <a name="collect-diagnostics-in-containers"></a>Kapsayıcılarda tanılamayı toplayın

Diğer senaryolarda .NET Core sorunlarını tanılamak için yararlı olan aynı tanılama araçları, Docker kapsayıcılarında de çalışır. Ancak bazı araçların bir kapsayıcıda çalışması için özel adımlar gerekir. Bu makalede, performans izlemelerinin toplanması ve dökümleri toplama araçlarının Docker kapsayıcılarında nasıl kullanılabileceği ele alınmaktadır.

## <a name="using-net-core-cli-tools-in-a-container"></a>Kapsayıcıda .NET Core CLI araçları kullanma

**Bu araçlar için geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri

.NET Core küresel CLI tanılama araçları ( [`dotnet-counters`](dotnet-counters.md) ,, [`dotnet-dump`](dotnet-dump.md) [`dotnet-gcdump`](dotnet-gcdump.md) ve), [`dotnet-trace`](dotnet-trace.md) çok çeşitli ortamlarda çalışacak şekilde tasarlanmıştır ve tüm doğrudan Docker kapsayıcılarında çalışır. Bu nedenle, bu araçlar, kapsayıcılardaki .NET Core 3,0 veya üstünü (ya da 3,1 veya üzeri) hedefleyen .NET Core senaryoları için tanılama bilgilerini toplamanın tercih edilen yöntemidir `dotnet-gcdump` .

Bir kapsayıcıda bu araçların kullanıldığı tek karmaşıktonlu etken, .NET Core SDK birlikte yüklendiklerinden ve .NET Core SDK mevcut olmadan birçok Docker kapsayıcısı çalıştırdıklarından. Bu soruna yönelik bir kolay çözüm, araçları ilk Docker görüntüsüne yüklemektir. Araçların çalışması için, yalnızca yüklenmek üzere .NET Core SDK gerekmez. Bu nedenle, araçları bir yapı aşamasına yükleyen (.NET Core SDK bulunan) ve ardından ikili dosyaları son görüntüye kopyalayan [çok aşamalı bir yapıda](https://docs.docker.com/develop/develop-images/multistage-build/) Dockerfile oluşturmak mümkündür. Bu yaklaşımın tek yanından yalnızca Docker görüntü boyutu artar.

```dockerfile
# In build stage
# Install desired .NET CLI diagnostics tools
RUN dotnet tool install --tool-path /tools dotnet-trace
RUN dotnet tool install --tool-path /tools dotnet-counters
RUN dotnet tool install --tool-path /tools dotnet-dump

...

# In final stage
# Copy diagnostics tools
WORKDIR /tools
COPY --from=build /tools .
```

Alternatif olarak, CLı araçlarını yüklemek için gerektiğinde .NET Core SDK bir kapsayıcıya yüklenebilir. .NET Core SDK yüklemesinin .NET Core çalışma zamanını yeniden yüklemenin yan etkisi olacağını unutmayın. Bu nedenle, kapsayıcıda bulunan çalışma zamanına uyan SDK sürümünü yüklediğinizden emin olun.

### <a name="using-net-core-global-cli-tools-in-a-sidecar-container"></a>.NET Core küresel CLı araçlarını bir sepet kapsayıcısında kullanma

Farklı bir kapsayıcıdaki işlemlerin tanılanması için .NET Core küresel CLı tanılama araçlarını kullanmak istiyorsanız, aşağıdaki ek gereksinimleri göz önünde bulundurun:

1. Kapsayıcılar [bir işlem ad alanını paylaşmalıdır](https://docs.docker.com/engine/reference/run/#pid-settings---pid) (böylece sepet kapsayıcısındaki araçların hedef kapsayıcıdaki işlemlere erişebilmesi için).
2. .NET Core küresel CLı tanılama araçları, .NET Core çalışma zamanının/tmp dizinine yazdığı dosyalara erişmesi gerekir, bu nedenle/tmp dizini bir birim bağlama aracılığıyla hedef ve sepet kapsayıcısı arasında paylaşılmalıdır. Bu, örneğin, kapsayıcıların ortak bir [birimi](https://docs.docker.com/storage/volumes/#create-and-manage-volumes) veya Kubernetes [emptydir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) birimini paylaşmasını sağlayarak yapılabilir. /Tmp dizinini paylaşmadan bir sepet kapsayıcısından tanılama araçlarını kullanmayı denerseniz, "uyumlu .NET çalışma zamanı çalışmıyor" işlemiyle ilgili bir hata alırsınız.

## <a name="using-perfcollect-in-a-container"></a>`PerfCollect`Kapsayıcıda kullanma

**Bu araç şu şekilde geçerlidir: ✔️** .net Core 2,1 ve sonraki sürümleri

[`PerfCollect`](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/linux-performance-tracing.md)Betik, performans izlemelerini toplamak için faydalıdır ve .NET Core 3,0 ' den önce izlemeleri toplamak için önerilen araçtır. `PerfCollect`Bir kapsayıcıda kullanıyorsanız, aşağıdaki gereksinimleri göz önünde bulundurun:

1. `PerfCollect`[ `SYS_ADMIN` özelliği](https://man7.org/linux/man-pages/man7/capabilities.7.html) gerektirir (aracı çalıştırmak için `perf` ), kapsayıcının [Bu özellik ile başlatıldığından](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)emin olun.
2. `PerfCollect` profil oluşturmanın başladığı uygulamadan önce bazı ortam değişkenlerinin ayarlanmasını gerektirir. Bunlar bir [Dockerfile](https://docs.docker.com/engine/reference/builder/#env) içinde ya da [kapsayıcı başlatılırken](https://docs.docker.com/engine/reference/run/#env-environment-variables)ayarlanabilir. Bu değişkenlerin normal üretim ortamlarında ayarlanmaması gerektiğinden, profili oluşturulacak bir kapsayıcıyı başlatırken yalnızca eklemeniz yaygındır. PerfCollect 'in gerektirdiği iki değişken şunlardır:
    1. COMPlus_PerfMapEnabled = 1
    1. COMPlus_EnableEventLog = 1

### <a name="using-perfcollect-in-a-sidecar-container"></a>`PerfCollect`Bir sepet kapsayıcısında kullanma

`PerfCollect`Farklı bir kapsayıcıda .NET Core işleminin profilini oluşturmak için tek bir kapsayıcıda çalıştırmak istiyorsanız, deneyim Şu farklar dışında neredeyse aynıdır:

1. Daha önce bahsedilen ortam değişkenleri (COMPlus_PerfMapEnabled ve COMPlus_EnableEventLog) hedef kapsayıcı için ayarlanmalıdır (çalışmıyor `PerfCollect` ).
2. Çalışan kapsayıcının `PerfCollect` `SYS_ADMIN` özelliği olmalıdır (hedef kapsayıcı değil).
3. İki kapsayıcı [bir işlem ad alanını paylaşmalıdır](https://docs.docker.com/engine/reference/run/#pid-settings---pid).

## <a name="using-createdump-in-a-container"></a>`createdump`Kapsayıcıda kullanma

**Bu araç şu şekilde geçerlidir: ✔️** .net Core 2,1 ve sonraki sürümleri

Bir alternatifi `dotnet-dump` , [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) hem yerel hem de yönetilen bilgileri içeren Linux üzerinde temel dökümler oluşturmak için kullanılabilir. `createdump`Araç .NET Core çalışma zamanı ile yüklenir ve libcoreclr.so ' nin yanında (genellikle "/usr/share/DotNet/Shared/Microsoft.NETCore.app/[Version]" içinde) bulunabilir. Araç, kapsayıcı olmayan Linux ortamlarında aynı şekilde, aracın [ `SYS_PTRACE` özelliği](https://man7.org/linux/man-pages/man7/capabilities.7.html)gerektirdiği tek bir özel durum ile aynı şekilde çalışmaya devam eder, bu nedenle Docker kapsayıcısının [Bu yetenek ile başlatılması](https://docs.docker.com/engine/reference/run/#runtime-privilege-and-linux-capabilities)gerekir.

### <a name="using-createdump-in-a-sidecar-container"></a>`createdump`Bir sepet kapsayıcısında kullanma

`createdump`Farklı bir kapsayıcıda bir işlemden döküm oluşturmak için kullanmak istiyorsanız, deneyim Şu farklar dışında neredeyse aynıdır:

1. Çalışan kapsayıcının `createdump` `SYS_PTRACE` özelliği olmalıdır (hedef kapsayıcı değil).
2. İki kapsayıcı [bir işlem ad alanını paylaşmalıdır](https://docs.docker.com/engine/reference/run/#pid-settings---pid).
