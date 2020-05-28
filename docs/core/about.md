---
title: .NET Core’a genel bakış
description: .NET Core 'un özellikleri ve kompozisyonu hakkında bilgi edinin ve diğer .NET uygulamalarıyla karşılaştırın.
ms.date: 03/26/2020
ms.openlocfilehash: e57451968ed8c4d5457acea084d3c6c9f998b8da
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144532"
---
# <a name="net-core-overview"></a>.NET Core’a genel bakış

.NET Core aşağıdaki özelliklere sahiptir:

- **Platformlar arası:** Windows, macOS ve Linux [işletim sistemlerinde](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)çalışır.
- **Açık Kaynak:** .NET Core Framework, MıT ve Apache 2 lisansları kullanılarak [açık kaynaktır](https://github.com/dotnet/core). .NET Core, bir [.net Foundation](https://dotnetfoundation.org/) projem.
- **Modern:** Zaman uyumsuz programlama gibi modern paradigmalarına uygular, yapıları kullanarak hiçbir kopyalama düzeni ve kapsayıcılar için kaynak İdaresi.
- **Performans:**  [Donanım iç](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/)bilgileri, [katmanlı derleme](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)ve [ \<T> yayılma](../standard/memory-and-spans/index.md)gibi özelliklerle [yüksek performans](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) sunar.
- **Ortamlar arasında tutarlı:** Kodunuzu, x64, x86 ve ARM dahil olmak üzere birden çok işletim sistemi ve mimaride aynı davranışla çalıştırır.
- **Komut satırı araçları:**  , Yerel geliştirme ve sürekli tümleştirme için kullanılabilecek kullanımı kolay komut satırı araçları içerir.
- **Esnek dağıtım:** Uygulamanıza .NET Core dahil edebilir veya yan yana (Kullanıcı genelindeki veya sistem genelindeki Yüklemeler) yükleyebilirsiniz. [Docker kapsayıcılarıyla](docker/introduction.md)birlikte kullanılabilir.

## <a name="languages"></a>Diller

[C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)ve [F #](../fsharp/index.yml) dilleri, .NET Core için uygulama ve kitaplıkları yazmak üzere kullanılabilir. Bu diller, en sevdiğiniz metin düzenleyicisinde veya tümleşik geliştirme ortamında (IDE) birlikte kullanılabilir:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

Düzenleyici tümleştirmesi, kapsamında, [Omnisharp](https://www.omnisharp.net/) ve [ıonıde](https://ionide.io) projelerinin katkıda bulunanlar tarafından sağlanır.

## <a name="apis"></a>API'ler

.NET Core, her türlü uygulamayı oluşturmak için çerçeveler sunar:

* [ASP.NET Core](/aspnet/core/) ile bulut uygulamaları
* [Xamarin](/xamarin) ile mobil uygulamalar
* [System. Device. GıO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) ile IoT uygulamaları
* [WPF](../desktop-wpf/overview/index.md) ve Windows Forms Windows istemci uygulamaları
* Machine Learning [ml.net](../machine-learning/index.yml)

Ortak ihtiyaçları karşılayan birçok API dahildir:

- Ve gibi temel türler <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType> .
- Ve gibi koleksiyonlar <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> .
- , Ve gibi yardımcı program türleri <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> <xref:System.IO.FileStream?displayProperty=nameWithType> .
- Ve gibi veri türleri <xref:System.Data.DataSet?displayProperty=nameWithType> <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> .
- , Ve işlem hatları gibi yüksek performanslı <xref:System.Span%601?displayProperty=nameWithType> türler <xref:System.Numerics.Vector?displayProperty=nameWithType> . [Pipelines](../standard/io/pipelines.md)

.NET Core, [.NET Standard](../standard/net-standard.md) belirtimini uygulayarak .NET Framework ve mono API 'leri ile uyumluluk sağlar.

## <a name="composition"></a>Birleşim

.NET Core aşağıdaki bölümlerden oluşur:

- Bir tür sistemi, derleme yükleme, çöp toplayıcı, yerel birlikte çalışma ve diğer temel hizmetler sağlayan [.NET Core çalışma zamanı](https://github.com/dotnet/runtime/tree/master/src/coreclr). [.NET Core Framework kitaplıkları](https://github.com/dotnet/runtime/tree/master/src/libraries) temel veri türleri, uygulama bileşim türleri ve temel yardımcı programları sağlar.
- Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi modern, bulut tabanlı, internet 'e bağlı uygulamalar oluşturmaya yönelik bir çerçeve sağlayan [ASP.NET Core çalışma zamanı](https://github.com/dotnet/aspnetcore).
- .NET Core geliştirici deneyimini etkinleştiren [.NET Core SDK](https://github.com/dotnet/sdk) ve dil derleyicileri ([Roslyn](https://github.com/dotnet/roslyn) ve [F #](https://github.com/microsoft/visualfsharp)).
- .NET Core uygulamalarını ve CLı komutlarını başlatmak için kullanılan [DotNet komutu](./tools/dotnet.md). Çalışma zamanını seçer ve barındırır, bir derleme yükleme ilkesi sağlar ve uygulamaları ve araçları başlatır.

### <a name="open-source"></a>Açık kaynak

[.NET Core](about.md) , [Açık kaynaklı](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), genel amaçlı bir geliştirme platformudur. X64, x86, ARM32 ve ARM64 işlemciler için Windows, macOS ve Linux için .NET Core uygulamaları oluşturabilirsiniz. Çerçeveler ve API 'Ler [bulut](/aspnet/core/), [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [istemci kullanıcı arabirimi](../desktop-wpf/overview/index.md)ve [makine öğrenimi](../machine-learning/index.yml)için sağlanır.

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux 'ta [Microsoft tarafından desteklenir](https://dotnet.microsoft.com/platform/support/policy) . Güvenlik ve kalite için düzenli olarak güncelleştirilir (her ayın ikinci Salı günü).

Microsoft 'un .NET Core ikili dağıtımları, Azure 'da Microsoft tarafından korunan sunucularda oluşturulup test edilir ve Microsoft mühendislik ve güvenlik uygulamalarını izler.

[Red Hat](https://developers.redhat.com/topics/dotnet/) Red Hat Enterprise Linux (RHEL) üzerinde .NET Core 'u destekler. Red hat, kaynaktan .NET Core 'u oluşturur ve [Red Hat yazılım koleksiyonlarında](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core 'un RHEL üzerinde iyi çalıştığından emin olmak için işbirliği sağlar.

Tizen, Tizen platformlarında [.NET Core 'u destekler](https://developer.tizen.org/development/training/.net-application) .
