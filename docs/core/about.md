---
title: .NET Core’a genel bakış
description: .NET Core'un özellikleri ve bileşimi hakkında bilgi edinin ve diğer .NET uygulamalarıyla karşılaştırın.
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391175"
---
# <a name="net-core-overview"></a>.NET Core’a genel bakış

.NET Core aşağıdaki özelliklere sahiptir:

- **Çapraz platform:** Windows, macOS ve Linux [işletim sistemlerinde](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)çalışır.
- **Açık kaynak:** .NET Core çerçevesi, MIT ve Apache 2 lisanslarını kullanarak [açık kaynak kodludur.](https://github.com/dotnet/core) .NET Core bir [.NET Vakfı](https://dotnetfoundation.org/) projesidir.
- **Modern:** Eşzamanlı programlama, yapı kullanma dansı olmayan desenler ve kapsayıcılar için kaynak yönetimi gibi modern paradigmaları uygular.
- **Performans:**  [Donanım içsellikleri,](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/) [katmanlı derleme](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)ve Span [\<T>](../standard/memory-and-spans/index.md)gibi özelliklerle yüksek [performans](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) sunar.
- **Ortamlar arasında tutarlı:** Kodunuzu x64, x86 ve ARM dahil olmak üzere birden çok işletim sistemi ve mimaride aynı davranışla çalıştırır.
- **Komut satırı araçları:**  Yerel geliştirme ve sürekli tümleştirme için kullanılabilecek kullanımı kolay komut satırı araçlarını içerir.
- **Esnek dağıtım:** .NET Core'u uygulamanıza ekleyebilir veya yan yana yükleyebilirsiniz (kullanıcı çapında veya sistem genelinde yüklemeler). [Docker konteynerleri](docker/introduction.md)ile kullanılabilir.

## <a name="languages"></a>Diller

[C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)ve [F#](../fsharp/index.yml) dilleri .NET Core için uygulama ve kitaplık yazmak için kullanılabilir. Bu diller, aşağıdakiler dahil olmak üzere en sevdiğiniz metin düzenleyicisinde veya Tümleşik Geliştirme Ortamında (IDE) kullanılabilir:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

Editör entegrasyonu, kısmen [OmniSharp](https://www.omnisharp.net/) ve [Ionide](http://ionide.io) projelerinin katkıda bulunanları tarafından sağlanmaktadır.

## <a name="apis"></a>API'ler

.NET Core, her türlü uygulamayı oluşturmak için çerçeveleri ortaya çıkarır:

* [ASP.NET Core](/aspnet/core/) ile bulut uygulamaları
* [Xamarin](/xamarin) ile mobil uygulamalar
* [System.Device.GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) ile IoT uygulamaları
* [WPF](../desktop-wpf/overview/index.md) ve Windows Formlarına sahip Windows istemci uygulamaları
* Makine öğrenimi [ML.NET](../machine-learning/index.yml)

Ortak gereksinimleri karşılayan birçok API dahildir:

- İlkel türleri, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>gibi ve .
- Koleksiyonlar, gibi <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>ve .
- Gibi yardımcı program <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>türleri, ve <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Veri türleri, <xref:System.Data.DataSet?displayProperty=nameWithType>gibi <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>, ve .
- , ve <xref:System.Numerics.Vector?displayProperty=nameWithType> [Pipelines](../standard/io/pipelines.md) <xref:System.Span%601?displayProperty=nameWithType>gibi yüksek performanslı türleri.

.NET [Core,.NET Standart](../standard/net-standard.md) belirtimini uygulayarak .NET Framework ve Mono API'ler ile uyumluluk sağlar.

## <a name="composition"></a>Birleşim

.NET Core aşağıdaki bölümlerden oluşmaktadır:

- Bir tür sistemi, montaj yükleme, çöp toplayıcı, yerel interop ve diğer temel hizmetleri sağlayan [.NET Core çalışma zamanı.](https://github.com/dotnet/runtime/tree/master/src/coreclr) [.NET Core framework kitaplıkları](https://github.com/dotnet/runtime/tree/master/src/libraries) ilkel veri türleri, uygulama kompozisyonu türleri ve temel yardımcı programlar sağlar.
- Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi modern, bulut tabanlı, internete bağlı uygulamalar oluşturmak için bir çerçeve sağlayan [ASP.NET Core çalışma süresi.](https://github.com/dotnet/aspnetcore)
- .NET Core geliştirici deneyimini sağlayan [.NET Core SDK](https://github.com/dotnet/sdk) ve dil derleyicileri[(Roslyn](https://github.com/dotnet/roslyn) ve [F#](https://github.com/microsoft/visualfsharp)).
- .NET Core uygulamalarını ve CLI komutlarını başlatmak için kullanılan [dotnet komutu.](./tools/dotnet.md) Çalışma saatini seçer ve barındırıyor, bir montaj yükleme ilkesi sağlar ve uygulamaları ve araçları başlatıyor.

### <a name="open-source"></a>Açık kaynak

[.NET Core](about.md) [açık kaynak kodlu,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)genel amaçlı bir geliştirme platformudur. X64, x86, ARM32 ve ARM64 işlemciler için Windows, macOS ve Linux için .NET Core uygulamaları oluşturabilirsiniz. Çerçeveler ve API'ler [bulut,](/aspnet/core/) [IoT,](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0) [istemci UI](../desktop-wpf/overview/index.md)ve [makine öğrenimi](../machine-learning/index.yml)için sağlanmaktadır.

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux'ta [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy) Güvenlik ve kalite için düzenli olarak güncellenir (her ayın ikinci Salı günü).

Microsoft'un .NET Core ikili dağıtımları, Azure'da Microsoft tarafından tutulan sunucularda oluşturulur ve test edilir ve Microsoft mühendislik ve güvenlik uygulamalarını izler.

Red Hat, Red Hat Enterprise Linux (RHEL) üzerinde [.NET Core'u destekler.](http://redhatloves.net/) Red Hat kaynaktan .NET Core oluşturur ve [Red Hat Yazılım Koleksiyonları'nda](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core'un RHEL'de iyi çalışmasını sağlamak için işbirliği içindedir.

[Tizen, Tizen](https://developer.tizen.org/development/training/.net-application) platformlarında .NET Core'u destekler.
