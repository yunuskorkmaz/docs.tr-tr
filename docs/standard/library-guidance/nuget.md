---
title: NuGet ve .NET kitaplıkları
description: .NET kitaplıkları için NuGet ile paketleme için en iyi yöntem önerileri.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731379"
---
# <a name="nuget"></a>NuGet

NuGet, .NET ekosistemi için bir paket yöneticisidir ve geliştiricilerin .NET açık kaynaklı kitaplıklarını bulmasına ve almasına yönelik birincil yoldur. NuGet paketlerini barındırmak için Microsoft tarafından sunulan ücretsiz bir hizmet olan [NuGet.org](https://www.nuget.org/), genel NuGet paketlerine yönelik birincil ana makinedir, ancak [myget](https://www.myget.org/) ve [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/)gibi özel NuGet hizmetlerine yayımlayabilirsiniz.

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>NuGet paketi oluşturma

Bir NuGet paketi (`*.nupkg`), .NET derlemelerini ve ilişkili meta verileri içeren bir zip dosyasıdır.

Bir NuGet paketi oluşturmanın iki ana yolu vardır. Daha yeni ve önerilen yol, bir SDK stili projeden paket oluşturmaktır (içeriği `<Project Sdk="Microsoft.NET.Sdk">`ile başlayan proje dosyası). Derlemeler ve hedefler pakete otomatik olarak eklenir ve geri kalan meta veriler, paket adı ve sürüm numarası gibi MSBuild dosyasına eklenir. [`dotnet pack`](../../core/tools/dotnet-pack.md) komutuyla derlemek, derlemeler yerine bir `*.nupkg` dosyası çıkışı verir.

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

NuGet paketi oluşturmanın daha eski yolu, bir `*.nuspec` dosyası ve `nuget.exe` komut satırı aracıdır. Bir nuspec dosyası harika denetim sağlar ancak son NuGet paketine hangi derlemeleri ve hedefleri dahil edileceğini dikkatle belirtmeniz gerekir. Bir hata yapmak veya birisinin değişiklik yaparken nuspec 'i güncelleştirmeyi unutmaları çok kolay. Bir nuspec 'in avantajı, henüz bir SDK stili proje dosyasını desteklemeyen çerçeveler için NuGet paketleri oluşturmayı kullanabilir.

✔️ NuGet paketini oluşturmak için SDK stili bir proje dosyası kullanmayı düşünün.

## <a name="package-dependencies"></a>Paket bağımlılıkları

NuGet paketi bağımlılıkları, [Bağımlılıklar](./dependencies.md) makalesinde ayrıntılı olarak ele alınmıştır.

## <a name="important-nuget-package-metadata"></a>Önemli NuGet paketi meta verileri

Bir NuGet paketi birçok [meta veri özelliğini](/nuget/reference/nuspec)destekler. Aşağıdaki tabloda, NuGet.org üzerindeki her paketin sağlaması gereken çekirdek meta veriler yer almaktadır:

| MSBuild özellik adı              | Nuspec adı              | Açıklama  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Paket tanımlayıcısı. Tanımlayıcıdan bir önek, [ölçütlere](/nuget/reference/id-prefix-reservation)uyuyorsa ayrılabilir. |
| `PackageVersion`                   | `version`                  | NuGet paket sürümü. Daha fazla bilgi için bkz. [NuGet paket sürümü](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Paketin insan dostu bir başlığı. Varsayılan olarak `PackageId`.             |
| `Description`                      | `description`              | Kullanıcı arabiriminde görüntülenmekte olan paketin uzun açıklaması.             |
| `Authors`                          | `authors`                  | Nuget.org üzerindeki profil adlarıyla eşleşen paket yazarları için virgülle ayrılmış bir liste.             |
| `PackageTags`                      | `tags`                     | Paketi tanımlayan etiketlerin ve anahtar sözcüklerin boşlukla ayrılmış bir listesi. Etiketler, paketler aranırken kullanılır.             |
| `PackageIconUrl`                   | `iconUrl`                  | Paket için simge olarak kullanılacak bir görüntünün URL 'SI. URL HTTPS olmalıdır ve görüntü 64x64 olmalı ve saydam bir arka plana sahip olmalıdır.             |
| `PackageProjectUrl`                | `projectUrl`               | Proje giriş sayfası veya Kaynak deposu için bir URL.             |
| `PackageLicenseExpression`         | `license`                  | Proje lisansının [Spdx tanımlayıcısı](https://spdx.org/licenses/). Yalnızca OSı ve FSF onaylı lisanslar bir tanımlayıcı kullanabilir. Diğer lisanslar `PackageLicenseFile`kullanmalıdır. [`license` meta verileri](/nuget/reference/nuspec#license)hakkında daha fazla bilgi edinin. |

> [!IMPORTANT]
> Lisansı olmayan bir proje, özel bir [telif hakkı](https://choosealicense.com/no-permission/)için varsayılan olarak, diğer kişilerin kullanması mümkün değildir.

✔️ NuGet 'in önek ayırma [ölçütlerine](/nuget/reference/id-prefix-reservation)uyan bir ön ek Içeren bir NuGet paketi adı seçmeyi düşünün.

✔️ paket simgenizin HTTPS href 'i kullanır.

> HTTPS ile NuGet.org Run ve HTTPS olmayan bir görüntü görüntüleme gibi siteler, karışık bir içerik uyarısı oluşturur.

✔️, 64x64 olan ve sonuçların en iyi şekilde görüntülenmesi için saydam bir arka plana sahip olan bir paket simge görüntüsünü kullanır.

✔️ derlemelerinize ve NuGet paketinize kaynak denetimi meta verileri eklemek için [kaynak bağlantısı](./sourcelink.md) kurmayı düşünün.

> Kaynak bağlantısı, NuGet paketine `RepositoryUrl` ve `RepositoryType` meta verileri otomatik olarak ekler. Kaynak bağlantısı, paketin oluşturulduğu tam kaynak kodu hakkında bilgi de ekler. Örneğin, bir git deposundan oluşturulan bir pakette, işlem karması meta veriler olarak eklenir.

## <a name="pre-release-packages"></a>Yayın öncesi paketler

Sürüm sonekine sahip NuGet paketleri [yayın öncesi](/nuget/create-packages/prerelease-packages)olarak kabul edilir. Varsayılan olarak, NuGet Paket Yöneticisi kullanıcı ARABIRIMI, bir Kullanıcı paketleri ön serbest bırakma paketleri, sınırlı Kullanıcı testi için ideal hale getirmediği takdirde kararlı yayınlar gösterir.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Kararlı bir paket, yayın öncesi paketine bağımlı olamaz. Kendi paketinizi yayın öncesi yapmanız veya daha eski bir kararlı sürüme bağlı olmanız gerekir.

![NuGet yayın öncesi paket bağımlılığı](./media/nuget/nuget-prerelease-package.png "NuGet yayın öncesi paket bağımlılığı")

✔️, test etme, önizleme veya deneme yaparken yayın öncesi paketi yayımlamaktır.

✔️, diğer kararlı paketlerin buna başvurabilmesi için kararlı bir paket yayımlamaktır.

## <a name="symbol-packages"></a>Sembol paketleri

Sembol dosyaları (`*.pdb`) derlemelerle birlikte .NET derleyicisi tarafından üretilir. Sembol dosyaları, yürütme konumlarını özgün kaynak koduna eşler, böylece bir hata ayıklayıcı kullanarak çalışırken kaynak kodu adım adım ilerleyebilir. NuGet, .NET derlemeleri içeren ana paketin yanı sıra sembol dosyalarını içeren [ayrı bir sembol paketi (`*.snupkg`) oluşturmayı](/nuget/create-packages/symbol-packages-snupkg) destekler. Sembol paketlerinin fikri, bir sembol sunucusunda barındırıldığından ve yalnızca isteğe bağlı Visual Studio gibi bir araç tarafından indirilir.

NuGet.org kendi [sembolleri sunucu deposunu](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server)barındırır. Geliştiriciler, [Visual Studio 'daki sembol kaynaklarına](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger)`https://symbols.nuget.org/download/symbols` ekleyerek NuGet.org symbol sunucusunda yayınlanan sembolleri kullanabilir.

> [!IMPORTANT]
> NuGet.org symbol sunucusu yalnızca SDK stili projeler tarafından oluşturulan yeni [Taşınabilir sembol dosyalarını](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) destekler.
>
> .NET kitaplığı 'nda hata ayıklarken NuGet.org symbol sunucusunu kullanmak için, geliştiriciler Visual Studio 2017 sürüm 15,9 veya üzeri bir sürüme sahip olmalıdır.

Sembol paketi oluşturmanın bir alternatifi, sembol dosyalarını ana NuGet paketine katıştırmaya yönelik bir alternatiftir. Ana NuGet paketi daha büyük olacaktır, ancak katıştırılmış sembol dosyaları, geliştiricilerin NuGet.org symbol sunucusunu yapılandırmasına gerek duymayacağı anlamına gelir. NuGet paketinizi bir SDK stili proje kullanarak oluşturuyorsanız, `AllowedOutputExtensionsInPackageBuildOutputFolder` özelliğini ayarlayarak sembol dosyalarını ekleyebilirsiniz:

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

Sembol dosyalarını gömmenin dezavantajı, SDK stilindeki projeler kullanılarak derlenen .NET kitaplıkları için paket boyutunu %30 oranında artırdı. Paket boyutu bir sorun oluşturacaksa, sembolleri bir sembol paketinde yayımlamanız gerekir.

✔️ sembolleri bir sembol paketi olarak yayımlamayı düşünün (`*.snupkg`) NuGet.org

> Sembol paketleri (`*.snupkg`), geliştiricilere ana paket boyutunu ayıklamadan ve NuGet paketinde hata ayıklamaya yönelik geri yükleme performansını etkilemeden iyi bir istek üzerine hata ayıklama deneyimi sağlar.
>
> Desteklenmediği uyarısıyla, kullanıcıların sembol dosyalarını almak için IDE (tek seferlik kurulum olarak) içinde NuGet sembol sunucusunu bulması ve yapılandırması gerekebilecek bir işlem olabilir. Visual Studio 2019 sürüm 16,1 varsayılan sembol sunucuları listesine NuGet. org 'ın sembol sunucusunu ekledi.

>[!div class="step-by-step"]
>[Önceki](strong-naming.md)
>[İleri](dependencies.md)
