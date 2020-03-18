---
title: NuGet ve .NET kitaplıkları
description: .NET kitaplıkları için NuGet ile paketleme için en iyi uygulama önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400521"
---
# <a name="nuget"></a>NuGet

NuGet ,NET ekosistemi için bir paket yöneticisidir ve geliştiricilerin .NET açık kaynak kitaplıklarını keşfetmesinin ve edinmesinin birincil yoludur. [NuGet.org,](https://www.nuget.org/)Microsoft tarafından NuGet paketlerini barındırmak için sağlanan ücretsiz bir hizmet, genel NuGet paketleri için birincil ana bilgisayardır, ancak [MyGet](https://www.myget.org/) ve [Azure Yapıları](https://azure.microsoft.com/services/devops/artifacts/)gibi özel NuGet hizmetlerine yayınlayabilirsiniz.

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>NuGet paketi oluşturma

NuGet paketi`*.nupkg`( ) .NET derlemeleri ve ilişkili meta verileri içeren bir zip dosyasıdır.

NuGet paketi oluşturmanın iki ana yolu vardır. Daha yeni ve önerilen yol, SDK tarzı bir projeden (içeriği içeriği `<Project Sdk="Microsoft.NET.Sdk">`yle başlayan proje dosyası) bir paket oluşturmaktır. Derlemeler ve hedefler otomatik olarak pakete eklenir ve kalan meta veriler paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir. [`dotnet pack`](../../core/tools/dotnet-pack.md) Komutla derleme derlemeler `*.nupkg` yerine bir dosya çıktırıyor.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

NuGet paketi oluşturmanın eski yolu `*.nuspec` bir dosya `nuget.exe` ve komut satırı aracıdır. Nuspec dosyası size büyük denetim sağlar, ancak son NuGet paketine hangi derlemeleri ve hedefleri dahil edebilirsiniz dikkatle belirtmeniz gerekir. Hata yapmak veya birisinin değişiklik yaparken nükspec'i güncellemeyi unutması kolaydır. Nuspec'in avantajı, henüz SDK tarzı bir proje dosyasını desteklemeyen çerçeveler için NuGet paketleri oluşturmasını kullanabilirsiniz.

✔️ NuGet paketini oluşturmak için SDK tarzı bir proje dosyası kullanmayı düşünün.

## <a name="package-dependencies"></a>Paket bağımlılıkları

NuGet paket bağımlılıkları [Bağımlılıklar](./dependencies.md) makalesinde ayrıntılı olarak ele alınmıştır.

## <a name="important-nuget-package-metadata"></a>Önemli NuGet paketi meta verileri

NuGet paketi birçok [meta veri özelliğini](/nuget/reference/nuspec)destekler. Aşağıdaki tablo, NuGet.org her paketin sağlaması gereken temel meta verileri içerir:

| MSBuild Özellik adı              | Nuspec adı              | Açıklama  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Paket tanımlayıcısı. Tanımlayıcıdan bir [önek, ölçütleri](/nuget/reference/id-prefix-reservation)karşılıyorsa rezerve edilebilir. |
| `PackageVersion`                   | `version`                  | NuGet paket sürümü. Daha fazla bilgi için [NuGet paket sürümüne](./versioning.md#nuget-package-version)bakın.             |
| `Title`                            | `title`                    | Paketin insan dostu bir başlığı. Bu varsayılan `PackageId`.             |
| `Description`                      | `description`              | UI'de görüntülenen paketin uzun bir açıklaması.             |
| `Authors`                          | `authors`                  | nuget.org'daki profil adlarıyla eşleşen, paket yazarlarının virgülle ayrılmış listesi.             |
| `PackageTags`                      | `tags`                     | Paketi açıklayan etiketlerin ve anahtar kelimelerin yerdeki sınırlı listesi. Etiketler paketleri ararken kullanılır.             |
| `PackageIconUrl`                   | `iconUrl`                  | Paketin simgesi olarak kullanılacak bir görüntünün URL'si. URL HTTPS olmalı ve görüntü 64x64 olmalı ve saydam bir arka plana sahip olmalıdır.             |
| `PackageProjectUrl`                | `projectUrl`               | Proje ana sayfası veya kaynak deposu için bir URL.             |
| `PackageLicenseExpression`         | `license`                  | Proje lisansının [SPDX tanımlayıcısı.](https://spdx.org/licenses/) Yalnızca OSI ve FSF onaylı lisanslar tanımlayıcı kullanabilir. Diğer lisanslar `PackageLicenseFile`kullanmalıdır. [ `license` Meta veriler](/nuget/reference/nuspec#license)hakkında daha fazla bilgi edinin. |

> [!IMPORTANT]
> Lisansı olmayan bir proje, [diğer](https://choosealicense.com/no-permission/)kişilerin kullanmasını yasal olarak imkansız hale getirir.

✔️ NuGet'in öneki rezervasyon [ölçütlerini](/nuget/reference/id-prefix-reservation)karşılayan bir önek içeren bir NuGet paket adı seçmeyi düşünün.

✔️ PAKET simgenize bir HTTPS href kullanın.

> https NuGet.org etkin ve HTTPS olmayan bir görüntü görüntülemek gibi siteler karışık içerik uyarısı oluşturur.

✔️ DO 64x64 ve en iyi görüntüleme sonuçları için şeffaf bir arka plan olan bir paket simgesi görüntü kullanın.

✔️ Derlemelerinize ve NuGet paketinize kaynak denetimi meta verileri eklemek için [Kaynak Bağlantı'yı](./sourcelink.md) ayarlamayı düşünün.

> Kaynak Bağlantı, `RepositoryUrl` NuGet paketine otomatik olarak `RepositoryType` ve meta veriler ekler. Kaynak Bağlantı ayrıca paketin tam olarak oluşturuladığı kaynak kodu hakkında bilgi ekler. Örneğin, git deposundan oluşturulan bir paket, işleme karmasını meta veri olarak ekleyecek.

## <a name="pre-release-packages"></a>Ön sürüm paketleri

Sürüm soneki olan NuGet paketleri [ön sürüm](/nuget/create-packages/prerelease-packages)olarak kabul edilir. Varsayılan olarak, Kullanıcı ön sürüm paketlerini seçmediği sürece NuGet Package Manager Kullanıcı Arabirimi kararlı sürümler gösterir ve ön sürüm paketlerini sınırlı kullanıcı testi için ideal hale getirir.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Kararlı bir paket, ön sürüm paketine bağlı olamaz. Ya kendi paketi ön sürüm yapmak ya da eski bir kararlı sürümü bağlıdır.

![NuRelease öncesi paket bağımlılığını elde edin](./media/nuget/nuget-prerelease-package.png "NuRelease öncesi paket bağımlılığını elde edin")

do ✔️ sınama, önizleme veya deneme yaparken bir ön sürüm paketi yayımlar.

✔️ DO, diğer kararlı paketlerin başvuruda bulunabilmesi için hazır olduğunda kararlı bir paket yayımlar.

## <a name="symbol-packages"></a>Sembol paketleri

Sembol dosyaları`*.pdb`( ) derlemelerin yanında .NET derleyicisi tarafından üretilir. Sembol dosyaları, hata ayıklayıcı kullanarak çalışırken kaynak koduna adım atabilmeniz için yürütme konumlarını özgün kaynak koduna eşler. NuGet, .NET derlemelerini içeren ana paketin yanında sembol dosyaları içeren [ayrı bir sembol paketi ()`*.snupkg`oluşturmayı](/nuget/create-packages/symbol-packages-snupkg) destekler. Sembol paketleri fikri, bir sembol sunucusunda barındırılan konum ve sadece isteğe bağlı Visual Studio gibi bir araç tarafından indirilir.

NuGet.org kendi [sembolleri sunucu deposu](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)nu barındırar. Geliştiriciler Visual Studio kendi [sembol kaynaklarına](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger) `https://symbols.nuget.org/download/symbols` ekleyerek NuGet.org sembol sunucusuna yayınlanan sembolleri kullanabilirsiniz.

> [!IMPORTANT]
> NuGet.org sembol sunucusu yalnızca SDK tarzı`*.pdb`projeler tarafından oluşturulan yeni taşınabilir sembol [dosyalarını](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) destekler.
>
> bir .NET kitaplığı hata ayıklama NuGet.org sembol sunucusunu kullanmak için geliştiricilerin Visual Studio 2017 sürüm 15.9 veya sonraki sürümlerine sahip olması gerekir.

Sembol paketi oluşturmanın alternatifi, sembol dosyalarını ana NuGet paketine katıştırmaktır. Ana NuGet paketi daha büyük olacaktır, ancak katıştırılmış sembol dosyaları geliştiricilerin NuGet.org sembol sunucusunu yapılandırmaları gerekolmadığı anlamına gelir. NuGet paketinizi SDK tarzı bir proje kullanarak oluşturuyorsanız, `AllowedOutputExtensionsInPackageBuildOutputFolder` özelliği ayarlayarak simge dosyalarını gömebilirsiniz:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Simge dosyaları gömmenin dezavantajı, SDK tarzı projeler kullanılarak derlenen .NET kitaplıkları için paket boyutunu yaklaşık %30 artırmalarıdır. Paket boyutu bir sorunsa, bunun yerine sembolleri bir sembol paketinde yayımlamalısınız.

✔️ sembolleri bir sembol`*.snupkg`paketi olarak NuGet.org düşünün

> Sembol paketleri`*.snupkg`( ) geliştiricilere ana paket boyutunu şişirmeden ve NuGet paketini hata ayıklamak istemeyenler için geri yükleme performansını etkilemeden iyi bir isteğe bağlı hata ayıklama deneyimi sağlar.
>
> Uyarı, kullanıcıların simge dosyalarını almak için IDE'lerinde (tek seferlik kurulum olarak) NuGet sembol sunucusunu bulmaları ve yapılandırmaları gerekebileceğidir. Visual Studio 2019 sürüm 16.1, NuGet.org'un sembol sunucusunu varsayılan sembol sunucular listesine ekledi.

>[!div class="step-by-step"]
>[Önceki](strong-naming.md)
>[Sonraki](dependencies.md)
