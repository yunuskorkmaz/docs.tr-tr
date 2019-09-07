---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394155"
---
# <a name="net-core-distribution-packaging"></a>.NET Core dağıtımı paketleme

.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur. Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir. Bu makale, şu kullanıcılar için yararlıdır:

- Kaynaktan .NET Core oluşturmaya çalışılıyor.
- .NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:

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
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin. Ana bilgisayar yerel bir yürütülebilir dosyadır (`dotnet.exe`).

Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur. Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.

- (2) **Host/FXR/\<FXR sürümü >** ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir. Ana bilgisayar, yüklü en son hostfxr 'yi kullanır. Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur. Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır. Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.

- (3) SDK **/\<SDK sürümü >** SDK ("araç oluşturma" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir. SDK, .NET Core komut satırı arabirimi (CLı), yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevleri ile hedefleri, NuGet, yeni proje şablonları vb. içerir.

- (4) **SDK/nugetfallbackfolder** , veya `dotnet restore` `dotnet build /t:Restore`çalıştırılırken olduğu gibi, geri yükleme işlemi sırasında bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir. Bu klasör yalnızca .NET Core 3,0 ' den önce kullanılır. ' Den `nuget.org`önceden oluşturulmuş ikili varlıklar içerdiğinden kaynaktan derlenebilir.

**Paylaşılan** klasör çerçeveler içerir. Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.

- (5) **paylaşılan/Microsoft. netcore. app/\<Runtime sürümü >** bu çerçeve .NET Core çalışma zamanı ve yönetilen kitaplıkları destekler.

- (6) **paylaşılan/Microsoft. AspNetCore. { App, All}/\<aspnetcore sürüm >** ASP.NET Core kitaplıklarını içerir. Altındaki `Microsoft.AspNetCore.App` kitaplıklar, .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir. Altındaki `Microsoft.AspNetCore.All` kitaplıklar, üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.

- (7) **paylaşılan/Microsoft. Desktop. app/\<Desktop uygulama sürümü >** Windows Masaüstü kitaplıklarını içerir. Bu, Windows dışı platformlarda bulunmaz.

- (8) **LICENSE. txt, üçüncü taraf bildirimleri. txt** , .NET Core 'un sırasıyla kullanıldığı üçüncü taraf kitaplıkların .NET Core lisansı ve lisanslarıdır.

- (9, 10) **DotNet. 1. gz, DotNet** `dotnet.1.gz` , DotNet el ile yapılan bir sayfasıdır. `dotnet`, DotNet konağının (1) bir symbağlantıdır. Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.

- (11, 12) **Microsoft. netcore. app. ref, Microsoft. aspnetcore. app. ref** bir `x.y` .NET Core sürümü ve sırasıyla ASP.NET Core API 'sini anlatmaktadır. Bu paketler, bu hedef sürümler için derlenirken kullanılır.

- (13) **Microsoft. NETCore. app. Host.\< RID >** , Platform `rid`için yerel bir ikili içerir. Bu ikili, bir .NET Core uygulamasını bu platform için yerel ikilide derlerken kullanılan bir şablondur.

- (14) **Microsoft. windowsdesktop. app. ref** , Windows masaüstü uygulamalarının `x.y` sürümünün API 'sini açıklar. Bu dosyalar, bu hedef için derlenirken kullanılır. Bu, Windows dışı platformlarda sağlanmaz.

- (15) **netstandart. Library. ref** netstandart `x.y` API 'sini açıklar. Bu dosyalar, bu hedef için derlenirken kullanılır.

- (16) **/etc/DotNet/ınstall_location** , `dotnet` ana bilgisayar ikilisini içeren klasörün tam yolunu içeren bir dosyadır. Yol, bir yeni satır ile sonlandırılmış olabilir. Kök olduğunda bu dosyanın eklenmesi gerekli değildir `/usr/share/dotnet`.

- (17) **şablonları** , SDK tarafından kullanılan şablonları içerir. Örneğin, `dotnet new` burada proje şablonlarını bulur.

## <a name="recommended-packages"></a>Önerilen paketler

.NET Core sürümü oluşturma çalışma zamanı bileşen `[major].[minor]` sürüm numaralarına dayalıdır.
SDK sürümü aynı `[major].[minor]` kullanır ve SDK için özellik ve düzeltme `[patch]` eki semantiğini birleştiren bir bağımsız içerir.
Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür. Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](../versions/index.md).

Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir. Bu, belirli bir sürümü yüklemenize olanak sağlar.
Sürümün geri kalanı sürüm adına dahil değildir. Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme). Desteklenen paket yöneticileri Linux 'a özgüdür.

Önerilen paketleri aşağıda listelenmiştir:

- `dotnet-sdk-[major].[minor]`-Belirli çalışma zamanı için en son SDK 'yı yükleme
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Örnek:** DotNet-sdk-2,1
  - **Vardır** (3), (4)
  - **Bağımlılıklar:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-Belirli bir ASP.NET Core çalışma zamanı yükleme
  - **Sürüm:** \<aspnetcore çalışma zamanı sürüm >
  - **Örnek:** aspnetcore-runtime-2,1
  - **Vardır** (6)
  - **Bağımlılıklar:** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(Isteğe bağlı)_ -kendi içindeki uygulamaları çalıştırmaya yönelik bağımlılıkları yükleme
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Örnek:** DotNet-Runtime-deps-2,1
  - **Bağımlılıklar:** _özel olmayan bağımlılıklar_

- `dotnet-runtime-[major].[minor]`-Belirli bir çalışma zamanını yükleme
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Örnek:** DotNet-runtime-2,1
  - **Vardır** (5)
  - **Bağımlılıklar:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr`-Dependency
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Örnek:** DotNet-hostfxr
  - **Vardır** (2)
  - **Bağımlılıklar:** `host:<runtime version>+`

- `dotnet-host`-Dependency
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Örnek:** DotNet-konak
  - **Vardır** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-Dependency
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Vardır** hatası

- `dotnet-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar
  - **Sürüm:** \<çalışma zamanı sürüm >
  - **Vardır** +

- `aspnetcore-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar
  - **Sürüm:** \<aspnetcore çalışma zamanı sürüm >
  - **Vardır** üst

- `netstandard-targeting-pack-[major].[minor]`-Netstandard sürümünün hedeflenmesini sağlar
  - **Sürüm:** \<SDK sürüm >
  - **Vardır** aşamaz

- `dotnet-templates-[major].[minor]`
  - **Sürüm:** \<SDK sürüm >
  - **Vardır** aşamaz

, `dotnet-runtime-deps-[major].[minor]` _Özel olmayan bağımlılıkların_anlaşılmasına gerek duyar. Diski derleme sistemi bunu otomatik olarak türetebildiğinden, paket isteğe bağlıdır; bu durumda bu bağımlılıklar `dotnet-runtime-[major].[minor]` pakete doğrudan eklenir.

Paket içeriği sürümlü bir klasör altında olduğunda, paket adı `[major].[minor]` sürümlü klasör adıyla eşleşir. Dışındaki `netstandard-targeting-pack-[major].[minor]`tüm paketler için, bu, .NET Core sürümü ile de eşleşir.

Paketler arasındaki bağımlılıklar, sürüm gereksinimini _eşit veya daha büyük_ kullanmalıdır. Örneğin, `dotnet-sdk-2.2:2.2.401` gerektirir `aspnetcore-runtime-2.2 >= 2.2.6`. Bu, kullanıcının yüklemelerini bir kök paket (ör. `dnf update dotnet-sdk-2.2`) aracılığıyla yükseltmesini mümkün hale getirir.

Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir. Bu, paketlere bazı etkileri vardır:

- Altındaki `shared/Microsoft.AspNetCore.All` üçüncü taraf kitaplıkları kaynaktan kolayca derlenebilir. Bu nedenle, bu klasör `aspnetcore-runtime` paketten çıkarılır.

- , `NuGetFallbackFolder` Öğesinden`nuget.org`ikili yapıtlar kullanılarak doldurulur. Boş kalmalıdır.

Birden `dotnet-sdk` çok paket `NuGetFallbackFolder`için aynı dosyaları sağlayabilir. Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).

## <a name="building-packages"></a>Paket oluşturma

[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar. Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.
