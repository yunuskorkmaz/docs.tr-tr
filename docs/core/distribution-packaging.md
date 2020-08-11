---
title: .NET Core dağıtımı paketleme
description: Dağıtım için .NET Core 'u paketleme, adlandırma ve sürüm hakkında bilgi edinin.
author: tmds
ms.date: 10/09/2019
ms.openlocfilehash: 3324a6a151fc6dc46a8f13ea17c89da99d108d82
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062892"
---
# <a name="net-core-distribution-packaging"></a>.NET Core dağıtımı paketleme

.NET Core daha fazla ve daha fazla platformda kullanıma sunulduğunda, bu uygulamayı paketleme, adlandırma ve sürüm hakkında bilgi edinmek yararlı olur. Bu şekilde, paket bakım yapanlar, kullanıcıların .NET çalıştırmayı tercih etmeksizin tutarlı bir deneyim sağlanmasına yardımcı olabilir. Bu makale, şu kullanıcılar için yararlıdır:

- Kaynaktan .NET Core oluşturmaya çalışılıyor.
- .NET Core CLI, oluşturulan yerleşimi veya paketleri etkileyebilecek değişiklikler yapmak için önerilir.

## <a name="disk-layout"></a>Disk düzeni

Yüklendiğinde, .NET Core dosya sisteminde aşağıdaki gibi çeşitli bileşenlerden oluşur:

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **DotNet** ana bilgisayar ("muxer" olarak da bilinir) iki ayrı role sahiptir: bir uygulamayı başlatmak için bir çalışma zamanı etkinleştirin ve BIR SDK 'yı ona komut göndermek için etkinleştirin. Ana bilgisayar yerel bir yürütülebilir dosyadır ( `dotnet.exe` ).

Tek bir ana bilgisayar olsa da, diğer bileşenlerin çoğu sürümlü dizinlerde (2, 3, 5, 6) bulunur. Bu, tarafında yan yana yüklendiklerinden bu yana birden çok sürümün mevcut olabileceği anlamına gelir.

- (2) **Host/FXR/ \<fxr version> ** ana bilgisayar tarafından kullanılan çerçeve çözümleme mantığını içerir. Ana bilgisayar, yüklü en son hostfxr 'yi kullanır. Hostfxr, .NET Core uygulaması yürütürken uygun çalışma zamanının seçilmesinden sorumludur. Örneğin, .NET Core 2.0.0 için oluşturulmuş bir uygulama, varsa 2.0.5 çalışma zamanını kullanır. Benzer şekilde, hostfxr geliştirme sırasında uygun SDK 'Yı seçer.

- (3) **SDK/ \<sdk version> ** SDK ("alet oluşturma" olarak da bilinir), .NET Core kitaplıklarını ve uygulamalarını yazmak ve derlemek için kullanılan bir yönetilen araçlar kümesidir. SDK .NET Core CLI, yönetilen diller derleyicileri, MSBuild ve ilişkili derleme görevlerini ve hedeflerini, NuGet, yeni proje şablonlarını vb. içerir.

- (4) **SDK/NuGetFallbackFolder** , veya çalıştırılırken olduğu gibi, geri yükleme işlemi SıRASıNDA bir SDK tarafından kullanılan NuGet paketlerinin bir önbelleğini içerir `dotnet restore` `dotnet build` . Bu klasör yalnızca .NET Core 3,0 ' den önce kullanılır. ' Den önceden oluşturulmuş ikili varlıklar içerdiğinden kaynaktan derlenebilir `nuget.org` .

**Paylaşılan** klasör çerçeveler içerir. Paylaşılan bir çerçeve, farklı uygulamalar tarafından kullanılabilmesi için merkezi bir konumda bir kitaplık kümesi sağlar.

- (5) **paylaşılan/Microsoft. NETCore. app/ \<runtime version> ** Bu çerçeve .NET Core çalışma zamanı içerir ve yönetilen kitaplıkları destekler.

- (6) **paylaşılan/Microsoft. AspNetCore. { Uygulama, tümü}/ \<aspnetcore version> ** ASP.NET Core kitaplıklarını içerir. Altındaki kitaplıklar, `Microsoft.AspNetCore.App` .NET Core projesinin bir parçası olarak geliştirilir ve desteklenir. Altındaki kitaplıklar, `Microsoft.AspNetCore.All` üçüncü taraf kitaplıklarını da içeren bir üst kümesidir.

- (7) **paylaşılan/Microsoft. Desktop. app/ \<desktop app version> ** Windows Masaüstü kitaplıklarını içerir. Bu, Windows dışı platformlarda bulunmaz.

- (8) **LICENSE.txt, ThirdPartyNotices.txt** .NET Core 'ta kullanılan üçüncü taraf kitaplıklarının, sırasıyla .NET Core lisanslarıdır.

- (9, 10) **DotNet. 1. gz, DotNet** , `dotnet.1.gz` DotNet el ile yapılan bir sayfasıdır. `dotnet`, DotNet konağının (1) bir symbağlantıdır. Bu dosyalar, sistem tümleştirmesi için iyi bilinen konumlara yüklenir.

- (11, 12) **Microsoft. NETCore. app. ref, Microsoft. AspNetCore. app. ref** bir `x.y` .NET Core sürümü ve sırasıyla ASP.NET Core API 'sini anlatmaktadır. Bu paketler, bu hedef sürümler için derlenirken kullanılır.

- (13) **Microsoft. NETCore. app. Host. \<rid> ** platform için yerel bir ikili içerir `rid` . Bu ikili, bir .NET Core uygulamasını bu platform için yerel ikilide derlerken kullanılan bir şablondur.

- (14) **Microsoft. windowsdesktop. app. ref** , `x.y` Windows masaüstü uygulamalarının sürümünün API 'sini açıklar. Bu dosyalar, bu hedef için derlenirken kullanılır. Bu, Windows dışı platformlarda sağlanmaz.

- (15) **netstandart. Library. ref** netstandart API 'sini açıklar `x.y` . Bu dosyalar, bu hedef için derlenirken kullanılır.

- (16) **/etc/DotNet/install_location** , için tam yolu içeren bir dosyadır `{dotnet_root}` . Yol, bir yeni satır ile bitemeyebilir. Kök olduğunda bu dosyanın eklenmesi gerekli değildir `/usr/share/dotnet` .

- (17) **şablonları** , SDK tarafından kullanılan şablonları içerir. Örneğin, `dotnet new` burada proje şablonlarını bulur.

İle işaretlenen klasörler `(*)` birden çok paket tarafından kullanılır. Bazı paket biçimleri (örneğin, `rpm` ) bu tür klasörlerin özel işlenmesini gerektirir. Paket bakımınonu bu şekilde ele almalıdır.

## <a name="recommended-packages"></a>Önerilen paketler

.NET Core sürümü oluşturma çalışma zamanı bileşen `[major].[minor]` sürüm numaralarına dayalıdır.
SDK sürümü aynı kullanır `[major].[minor]` ve `[patch]` SDK için özellik ve düzeltme eki semantiğini birleştiren bir bağımsız içerir.
Örneğin: SDK sürümü 2.2.302, SDK 'nın 2,2 çalışma zamanını destekleyen üçüncü Özellik sürümünün ikinci düzeltme eki sürümüdür. Sürüm oluşturma 'nın nasıl çalıştığı hakkında daha fazla bilgi için bkz. [.NET Core sürümü genel bakış](./versions/index.md).

Bazı paketler, kendi adında sürüm numarasının bir parçasını içerir. Bu, belirli bir sürümü yüklemenize olanak sağlar.
Sürümün geri kalanı sürüm adına dahil değildir. Bu, işletim sistemi paket yöneticisinin paketleri güncelleştirmesine izin verir (örneğin, otomatik olarak güvenlik düzeltmelerini yükleme). Desteklenen paket yöneticileri Linux 'a özgüdür.

Önerilen paketleri aşağıda listelenmiştir:

- `dotnet-sdk-[major].[minor]`-Belirli çalışma zamanı için en son SDK 'yı yükleme
  - **Sürüm:**\<sdk version>
  - **Örnek:** DotNet-sdk-2,1
  - **Şunu içerir:** (3), (4)
  - **Bağımlılıklar:** `dotnet-runtime-[major].[minor]` , `aspnetcore-runtime-[major].[minor]` , `dotnet-targeting-pack-[major].[minor]` , `aspnetcore-targeting-pack-[major].[minor]` , `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` , `dotnet-apphost-pack-[major].[minor]` ,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-Belirli bir ASP.NET Core çalışma zamanı yükleme
  - **Sürüm:**\<aspnetcore runtime version>
  - **Örnek:** aspnetcore-runtime-2,1
  - **Şunu içerir:** (6)
  - **Bağımlılıklar:**`dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]`_(Isteğe bağlı)_ -kendi içindeki uygulamaları çalıştırmaya yönelik bağımlılıkları yükleme
  - **Sürüm:**\<runtime version>
  - **Örnek:** DotNet-Runtime-deps-2,1
  - **Bağımlılıklar:** _dağıtıma özgü bağımlılıklar_

- `dotnet-runtime-[major].[minor]`-Belirli bir çalışma zamanını yükleme
  - **Sürüm:**\<runtime version>
  - **Örnek:** DotNet-runtime-2,1
  - **Şunu içerir:** (5)
  - **Bağımlılıklar:** `dotnet-hostfxr-[major].[minor]` ,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr-[major].[minor]`-Dependency
  - **Sürüm:**\<runtime version>
  - **Örnek:** DotNet-hostfxr-3,0
  - **Şunu içerir:** (2)
  - **Bağımlılıklar:**`dotnet-host`

- `dotnet-host`-Dependency
  - **Sürüm:**\<runtime version>
  - **Örnek:** DotNet-konak
  - **İçerir:** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-Dependency
  - **Sürüm:**\<runtime version>
  - **Şunu içerir:** (13)

- `dotnet-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar
  - **Sürüm:**\<runtime version>
  - **Şunu içerir:** (12)

- `aspnetcore-targeting-pack-[major].[minor]`-En son olmayan çalışma zamanının hedeflenmesini sağlar
  - **Sürüm:**\<aspnetcore runtime version>
  - **Şunu içerir:** (11)

- `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`-Netstandard sürümünün hedeflenmesini sağlar
  - **Sürüm:**\<sdk version>
  - **Şunu içerir:** (15)

- `dotnet-templates-[major].[minor]`
  - **Sürüm:**\<sdk version>
  - **Şunu içerir:** (15)

, `dotnet-runtime-deps-[major].[minor]` _Özel olmayan bağımlılıkları_kavramak istiyor. Diski derleme sistemi bunu otomatik olarak türetebildiğinden, paket isteğe bağlıdır; bu durumda bu bağımlılıklar pakete doğrudan eklenir `dotnet-runtime-[major].[minor]` .

Paket içeriği sürümlü bir klasör altında olduğunda, paket adı `[major].[minor]` sürümlü klasör adıyla eşleşir. Dışındaki tüm paketler için, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` Bu, .NET Core sürümü ile de eşleşir.

Paketler arasındaki bağımlılıklar, sürüm gereksinimini _eşit veya daha büyük_ kullanmalıdır. Örneğin, `dotnet-sdk-2.2:2.2.401` gerektirir `aspnetcore-runtime-2.2 >= 2.2.6` . Bu, kullanıcının yüklemelerini bir kök paket aracılığıyla yükseltmesini (örneğin,) mümkün hale getirir `dnf update dotnet-sdk-2.2` .

Çoğu dağıtım, kaynaktan oluşturulacak tüm yapıtları gerektirir. Bu, paketlere bazı etkileri vardır:

- Altındaki üçüncü taraf kitaplıkları `shared/Microsoft.AspNetCore.All` kaynaktan kolayca derlenebilir. Bu nedenle, bu klasör paketten çıkarılır `aspnetcore-runtime` .

- , `NuGetFallbackFolder` Öğesinden ikili yapıtlar kullanılarak doldurulur `nuget.org` . Boş kalmalıdır.

Birden çok `dotnet-sdk` paket için aynı dosyaları sağlayabilir `NuGetFallbackFolder` . Paket Yöneticisi ile ilgili sorunları önlemek için bu dosyaların aynı olması gerekir (sağlama toplamı, değiştirme tarihi vb.).

## <a name="building-packages"></a>Paket oluşturma

[DotNet/Source-Build](https://github.com/dotnet/source-build) deposu .NET Core SDK kaynak tarbol 'in ve tüm bileşenlerinin nasıl oluşturulacağı hakkında yönergeler sağlar. Kaynak-derleme deposunun çıktısı, bu makalenin ilk bölümünde açıklanan düzen ile eşleşir.
