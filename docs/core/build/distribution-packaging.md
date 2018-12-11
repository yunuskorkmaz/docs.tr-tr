---
title: .NET core dağıtımı paketleme
description: Paketleme hakkında bilgi edinin adı ve sürümü .NET Core dağıtımı.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: be5767351ad1cdac15c73f718f67a0d120cf65b0
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170424"
---
# <a name="net-core-distribution-packaging"></a>.NET core dağıtımı paketleme

.NET Core daha da fazla platformlarda kullanılabilir hale geldiğinde, adı, paket hakkında bilgi edinmek yararlı olur ve sürümü. Bu şekilde, paket maintainers burada .NET çalıştırmak kullanıcıların seçim ne olursa olsun, tutarlı bir deneyim sağlamak yardımcı olabilir.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core gibi dosya sistemi layed kullanıma çeşitli bileşenlerden oluşur:

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
└── shared
    ├── Microsoft.NETCore.App
    │   └── <runtime version>    (5)
    └── Microsoft.AspNetCore.App
        └── <aspnetcore version> (6)
    └── Microsoft.AspNetCore.All
        └── <aspnetcore version> (7)
/
├─usr/share/man/man1
│       └── dotnet.1.gz          (9)
└─usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** ana bilgisayar (diğer adıyla "Karıştırıcı") iki ayrı rol yok: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirme ve komutları ona gönderileceği bir SDK'yı etkinleştirin. Konağın yerel yürütülebilir olduğundan (`dotnet.exe`).

Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu tutulan dizinler (2,3,5,6) aittir. Başka bir deyişle, yüklü yan yana çünkü birden çok sürümü sistemde olabilir.

- (2) **konak/fxr/\<fxr sürüm >** ana bilgisayar tarafından kullanılan çerçeve çözümlemesi mantığı içerir. Ana bilgisayar yüklü en son hostfxr kullanır. Hostfxr uygun çalışma zamanı seçmek için bir .NET Core uygulaması yürütülürken sorumludur. Örneğin, .NET Core 2.0.0 2.0.5 kullanacak oluşturulmuş bir uygulamada kullanılabilir olduğunda çalışma zamanı. Benzer şekilde, hostfxr uygun SDK'sı, geliştirme sırasında seçer.

- (3) **sdk /\<sdk sürümü >** SDK (diğer adıyla "Araçlar"), yazma ve .NET Core kitaplıkları ve uygulamaları oluşturmak için kullanılan yönetilen araçlar kümesi. SDK'sı, CLI, Roslyn derleyici, MSBuild ve ilişkili derleme görevleri ve hedefleri, NuGet, yeni proje şablonları, vb. içerir.

- (4) **sdk/NuGetFallbackFolder** sırasında bir SDK'sı tarafından kullanılan NuGet paketleri önbelleğini içeren `dotnet restore` adım.

**Paylaşılan** klasörü çerçeveleri içerir. Farklı uygulamaları tarafından kullanılabilmesi için merkezi bir konumda bir dizi paylaşılan bir çerçeve sağlar.

- (5) **shared/Microsoft.NETCore.App/\<çalışma zamanı sürümü >** bu framework, .NET Core çalışma zamanı ve yönetilen kütüphanelerinizi destek içerir.

- (6,7) **shared/Microsoft.AspNetCore. { Uygulama, tüm} /\<aspnetcore sürüm >** ASP.NET Core kitaplıkları içerir. Kitaplıklar `Microsoft.AspNetCore.App` geliştirilen ve .NET Core projesinin bir parçası desteklenir. Kitaplıklar `Microsoft.AspNetCore.All` olan 3. taraf kitaplıkların da içeren bir üst kümesidir.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** .NET Core lisans ve üçüncü taraf kitaplıkların .NET Core içinde kullanılan lisanslar.

- (9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` dotnet man sayfasıdır. `dotnet` dotnet host(1) için hedefine sembolik bağlantı olur. Bu dosyalar, sistem tümleştirme için iyi bilinen konumlara yüklenir.

## <a name="recommended-packages"></a>Önerilen paketleri

.NET core sürüm çalışma zamanı bileşeni temel `[major].[minor]` sürüm numaraları.
Aynı SDK sürümünü kullanan `[major].[minor]` ve bağımsız `[patch]` için SDK'sı özelliği ve düzeltme eki semantiği birleştirir.
Örneğin: SDK'sı sürüm 2.2.302 bir 2,2 çalışma zamanını destekleyen SDK'sı 3 özelliği sürümünü 2 düzeltme eki sürümü.

Bazı paketler, adında sürüm numarasının bölümü içerir. Bu, belirli bir sürümünü yüklemek son kullanıcı sağlar.
Kalan sürümünün sürüm adı dahil edilmez. Bu işletim sistemi Paket Yöneticisi'ni (örneğin güvenlik otomatik olarak yükleme düzeltir) paketleri güncelleştir sağlar.

Aşağıdaki tablolarda, önerilen paketler gösterilmektedir.

| Ad                                    | Örnek                | Kullanım örneği: Yükle...           | İçerir           | Bağımlılıkları                                   | Sürüm            |
|-----------------------------------------|------------------------|---------------------------------|--------------------|------------------------------------------------|--------------------|
| dotnet-sdk-[major]                      | dotnet-sdk-2           | Çalışma zamanı ana için en son SDK'sı    |                    | DotNet - sdk-[major]. [latestminor]               | \<SDK sürümü >     |
| DotNet - sdk-[major]. [minor]              | DotNet sdk 2.1         | Belirli bir çalışma zamanı için en son SDK'sı |                    | DotNet - sdk-[major]. [minor]. [en son SDK'sı feat] xx | \<SDK sürümü >     |
| DotNet - sdk-[major]. [minor]. [sdk feat] xx | DotNet sdk 2.1.3xx     | Belirli bir sdk özellik yayını    | (3),(4)            | aspnetcore - çalışma zamanı-[major]. [minor]             | \<SDK sürümü >     |
| aspnetcore - çalışma zamanı-[major]. [minor]      | aspnetcore çalışma zamanı 2.1 | Belirli bir ASP.NET Core çalışma zamanı   | (6),[(7)]          | DotNet - çalışma zamanı-[major]. [minor]                 | \<çalışma zamanı sürüm > |
| DotNet - çalışma zamanı-[major]. [minor]          | DotNet çalışma zamanı 2.1     | Belirli bir çalışma zamanı                | (5)                | konak fxr:\<çalışma zamanı sürümü > +                   | \<çalışma zamanı sürüm > |
| dotnet-host-fxr                         | dotnet-host-fxr        | _Bağımlılık_                    | (2)                | konak:\<çalışma zamanı sürümü > +                       | \<çalışma zamanı sürüm > |
| DotNet-host                             | DotNet-host            | _Bağımlılık_                    | (1),(8),(9),(10)   |                                                | \<çalışma zamanı sürüm > |

Çoğu dağıtımları kaynağından oluşturulacak tüm yapıtlar gerektirir. Bu bazı paketlere etkisi:

- 3 şahıs kitaplıklardaki altında `shared/Microsoft.AspNetCore.All` kaynaktan kolayca oluşturulamıyor. Bu klasöre gelen atlanmış biçimde `aspnetcore-runtime` paket.

- `NuGetFallbackFolder` İkili yapılardan kullanarak doldurulur `nuget.org`. Boş kalmalıdır.

Birden çok `dotnet-sdk` paketler için de indirdiğiniz dosyaları sağlayabilir `NuGetFallbackFolder`. Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyalar aynı olmalıdır (sağlama toplamı, değiştirilme tarihi,...).

#### <a name="preview-versions"></a>Önizleme sürümleri

Paket maintainers Önizleme sürümleri paylaşılan çerçeve ve SDK sağlar karar verebilirsiniz. Önizleme sürümleri kullanılarak sağlanmalıdır `dotnet-sdk-[major].[minor].[sdk feat]xx`, `aspnetcore-runtime-[major].[minor]`, `dotnet-runtime-[major].[minor]` paketleri. Önizleme sürümleri için ana Paket sürümü sıfır olarak ayarlamanız gerekir. Bu şekilde son sürümü yükseltme paketi olarak yüklenir.

#### <a name="patch-packages"></a>Düzeltme eki paketleri

Bir paket bir düzeltme eki sürümü bozucu bir değişikliğe neden olduğundan, bir paket Bakımcı sağlamak isteyebilirsiniz _paketleri düzeltme eki_. Bu paketler, otomatik olarak yükseltilmez belirli yama sürümü yüklemek için sağlar. Yükseltilen (güvenlik) ile düzeltmeleri olmayacak düzeltme eki paketler yalnızca nadir durumlarda kullanılmalıdır.

Önerilen paketleri aşağıdaki tabloda gösterir ve **paketleri düzeltme eki**.

| Ad                                           | Örnek                  | İçerir         | Bağımlılıkları                                              |
|------------------------------------------------|--------------------------|------------------|-----------------------------------------------------------|
| dotnet-sdk-[major]                             | dotnet-sdk-2             |                  | DotNet - sdk-[major]. [küçük en son sdk]                     |
| DotNet - sdk-[major]. [minor]                     | DotNet sdk 2.1           |                  | DotNet - sdk-[major]. [minor]. [en son SDK'sı feat] xx            |
| DotNet - sdk-[major]. [minor]. [sdk feat] xx        | DotNet sdk 2.1.3xx       |                  | DotNet - sdk-[major]. [minor]. [son sdk yolu]             |
| **DotNet - sdk-[major]. [minor]. [düzeltme]**         | DotNet sdk 2.1.300       | (3),(4)          | aspnetcore - çalışma zamanı-[major]. [minor]. [sdk düzeltme çalışma zamanı]    |
| aspnetcore - çalışma zamanı-[major]. [minor]             | aspnetcore çalışma zamanı 2.1   |                  | aspnetcore - çalışma zamanı-[major]. [minor]. [en son düzeltme çalışma zamanı] |
| **aspnetcore - çalışma zamanı-[major]. [minor]. [düzeltme]** | aspnetcore çalışma zamanı 2.1.0 | (6),[(7)]        | DotNet - çalışma zamanı-[major]. [minor]. [düzeltme]                    |
| DotNet - çalışma zamanı-[major]. [minor]                 | DotNet çalışma zamanı 2.1       |                  | DotNet - çalışma zamanı-[major]. [minor]. [en son düzeltme çalışma zamanı]     |
| **DotNet - çalışma zamanı-[major]. [minor]. [düzeltme]**     | DotNet çalışma zamanı 2.1.0     | (5)              | konak fxr:\<çalışma zamanı sürümü > +                              |
| dotnet-host-fxr                                | dotnet-host-fxr          | (2)              | konak:\<çalışma zamanı sürümü > +                                  |
| DotNet-host                                    | DotNet-host              | (1),(8),(9),(10) |                                                           |

Düzeltme eki paketleri bir alternatifidir _sabitleme_ Paket Yöneticisi'ni kullanarak belirli bir sürümü için paketleri. Diğer uygulamalar/kullanıcıları etkilemeden önlemek için bu tür uygulamalar oluşturulabilen ve bir kapsayıcıda dağıtılır.

## <a name="building-packages"></a>Yapı paketleri

[Kaynak/dotnet-derleme](https://github.com/dotnet/source-build) depo, bir .NET Core SDK'sını ve tüm bileşenlerinin kaynak tarball derleme hakkında yönergeler sağlar. Kaynak derleme deposu çıktısını bu makalenin ilk bölümünde açıklanan düzenini eşleşir.
