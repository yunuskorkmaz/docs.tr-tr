---
title: NuGet ve .NET kitaplıkları
description: En iyi yöntem önerileri paketleme için NuGet ile .NET kitaplıkları.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 479d1786c232ef1f843877169954e847453681c9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185634"
---
# <a name="nuget"></a>NuGet

NuGet için .NET ekosisteminin bir paket yöneticisidir ve birincil yolu geliştiriciler keşfedin ve .NET açık kaynak kitaplıklarını edinebilir. [NuGet.org](https://www.nuget.org/), NuGet paketlerini barındırmak için Microsoft tarafından sağlanan ücretsiz bir hizmet olduğundan birincil konak genel NuGet paketleri için ancak gibi özel NuGet hizmetlerine yayımlayabilirsiniz [MyGet](https://www.myget.org/) ve [Azure Yapıtları ](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Bir NuGet paketi oluşturma

Bir NuGet paketi (`*.nupkg`) .NET derlemelerini ve ilişkili meta verileri içeren bir zip dosyasıdır.

Bir NuGet paketi oluşturmak için iki ana yolu vardır. Yeni ve önerilen bir SDK stilinde projeden bir paketi oluşturmak için yoludur (proje dosyası içerikleri ile başlayan `<Project Sdk="Microsoft.NET.Sdk">`). Derlemeler ve hedefleri paketi otomatik olarak eklenir ve meta verileri kalan paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir. İle derlerken [ `dotnet pack` ](../../core/tools/dotnet-pack.md) çıktılar komut bir `*.nupkg` derlemeler yerine dosya.

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

Bir NuGet paketi oluşturma eski yöntem, bir `*.nuspec` dosya ve `nuget.exe` komut satırı aracı. Soubor nuspec çok denetimi verir ancak hangi derlemelerin ve hedefleri son NuGet paket içerisine dâhil etmek dikkatli bir şekilde belirtmeniz gerekir. Bir hata yapmak kolaydır veya birinin değişiklikler yaparken nuspec güncelleştirilecek unutmayın. Kullanabilirsiniz bir nuspec avantajlarındandır henüz bir SDK stilinde proje dosyası desteklemeyen çerçeveler için NuGet paketleri oluşturun.

**✔️ DÜŞÜNÜN** NuGet paketi oluşturmak için bir SDK stilinde proje dosyasını kullanarak.

**✔️ DÜŞÜNÜN** NuGet paketi ve derlemeler için kaynak denetimi meta verilerini eklemek için SourceLink ayarlama.

## <a name="package-dependencies"></a>Paket bağımlılıkları

NuGet Paket bağımlılıklarını ayrıntılı olarak ele alınmıştır [bağımlılıkları](./dependencies.md) makalesi.

## <a name="important-nuget-package-metadata"></a>Önemli NuGet paketi meta verileri

Bir NuGet paketi birçok destekler [meta veri özelliklerini](/nuget/reference/nuspec). Aşağıdaki tabloda her bir açık kaynak proje sağlamalıdır çekirdek meta veriler içerir:

| MSBuild özellik adı              | Nuspec adı              | Açıklama  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Paket tanımlayıcısı. Bunu karşılıyorsa tanımlayıcı önekten ayrılabileceğini [ölçütleri](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | NuGet Paket sürümü. Daha fazla bilgi için [NuGet paketi sürüm](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Paket bir insan dostu başlığı. Varsayılan `PackageId`.             |
| `Description`                      | `description`              | Kullanıcı Arabiriminde görüntülenen paketinin uzun açıklaması.             |
| `Authors`                          | `authors`                  | Nuget.org profil adları eşleşen, paket yazarlarının virgülle ayrılmış listesi.             |
| `PackageTags`                      | `tags`                     | Etiketleri ve paket tanımlayan anahtar sözcükleri boşlukla ayrılmış listesi. Etiketleri paketler için arama yaparken de kullanılır.             |
| `PackageIconUrl`                   | `iconUrl`                  | Paket için simge olarak kullanılacak bir URL için bir görüntü. HTTPS URL'si olmalıdır ve görüntü 64 x 64 olmalıdır ve saydam bir arka plana sahip.             |
| `PackageProjectUrl`                | `projectUrl`               | Proje giriş sayfası veya kaynak havuzu için bir URL.             |
| `PackageLicenseUrl`                | `licenseUrl`               | Proje lisans URL'si. URL için `LICENSE` dosyası kaynak denetiminde.             |

**✔️ DÜŞÜNÜN** NuGet'ın ön eki ayırma karşılayan bir önek ile NuGet paket adı seçerek [ölçütleri](/nuget/reference/id-prefix-reservation).

**✔️ DÜŞÜNÜN** kullanarak `LICENSE` dosya kaynak denetimine eklememelisiniz `LicenseUrl`. Örneğin, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).

> [!IMPORTANT]
> Bir proje için varsayılan olarak bir lisans olmadan [özel telif hakkı](https://choosealicense.com/no-permission/), diğer kişilerin kullanmasına imkansızdır.

**✔️ YAPMAK** paket simge için bir HTTPS href kullanın.

> İle HTTPS etkin site NuGet.org gibi çalıştırın ve HTTPS olmayan bir resim görüntüleyen bir karışık içerik uyarı oluşturur.

**✔️ YAPMAK** 64 x 64 ve en iyi sonuçları görüntülemek için saydam bir arka plana sahip bir paket simge görüntüsü kullanın.

## <a name="pre-release-packages"></a>Yayın öncesi paketleri

NuGet paketlerini sürüm sonekine sahip olarak kabul edilir [yayın öncesi](/nuget/create-packages/prerelease-packages). Bir kullanıcı kabul eder yayın öncesi paketleri, yayın öncesi paketleri sınırlı kullanıcı test için ideal hale açma sürece varsayılan olarak, NuGet Paket Yöneticisi UI kararlı yayınları gösterir.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Bir kararlı paket bir yayın öncesi pakete bağımlı olamaz. Yayın öncesi kendi paket yapmak veya eski bir kararlı sürüme bağlı.

![NuGet yayın öncesi paket bağımlılığı](./media/nuget/nuget-prerelease-package.png "NuGet yayın öncesi paket bağımlılığı")

**✔️ YAPMAK** test etme, Önizleme veya deneme yayın öncesi paket yayımlama.

**✔️ YAPMAK** , hazır, bu nedenle diğer kararlı paketleri başvuruda bulunduğunuzda bir kararlı paket yayımlama.

## <a name="symbol-packages"></a>Sembol paketleri

Sembol dosyaları (`*.pdb`) derlemeleri yanı sıra .NET derleyici tarafından üretilen. Sembol dosyaları harita yürütme konumu özgün kaynak kodu, kaynak kodu olarak aracılığıyla girmek için bir hata ayıklayıcıyı kullanarak çalışıyor. NuGet destekler [ayrı sembol paketi oluşturuluyor](/nuget/create-packages/symbol-packages) .NET derlemelerini içeren ana paket yanı sıra sembol dosyalarını içeren. Sembol paketleri fikri bir sembol sunucusunda barındırılan ve yalnızca Visual Studio gibi bir araçla isteğe bağlı olarak yüklenen değildir.

Şu anda genel ana sembolleri - [SymbolSource](http://www.symbolsource.org/) -yeni desteklemiyor [taşınabilir sembol dosyalarını](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) SDK stili projeleri tarafından oluşturulan ve sembol paketleri kullanışlı değildir. Sembol paketleri için önerilen bir ana kadar sembol dosyaları ana NuGet paketinin eklenebilir. NuGet paketiniz, katıştırabilir bir SDK stilinde projesi kullanarak sembol dosyalarını ayarlayarak derliyorsanız `AllowedOutputExtensionsInPackageBuildOutputFolder` özelliği: 

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

**✔️ DÜŞÜNÜN** sembol dosyaları ana NuGet paketini ekleme.

**❌ KAÇININ** sembol dosyalarını içeren bir sembol paketi oluşturuluyor.

>[!div class="step-by-step"]
[Önceki](./strong-naming.md)
[İleri](./dependencies.md)
