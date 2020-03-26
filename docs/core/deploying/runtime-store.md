---
title: Çalışma zamanı paket deposu
description: .NET Core tarafından kullanılan bildirimleri hedeflemek için çalışma zamanı paket deposunu nasıl kullanacağınızı öğrenin.
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134270"
---
# <a name="runtime-package-store"></a>Çalışma zamanı paket deposu

.NET Core 2.0 ile başlayarak, uygulamaları hedef ortamda bulunan bilinen paketlere karşı paketleyip dağıtmak mümkündür. Avantajları daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve bazı durumlarda geliştirilmiş başlangıç performansıdır.

Bu özellik, paketlerin depolandığı diskteki bir dizin olan *çalışma zamanı paket deposu*olarak uygulanır (genellikle macOS/Linux ve *C:/Program Files/dotnet/store* on Windows'da */usr/local/share/dotnet/store* adresinde). Bu dizin altında, mimariler ve [hedef çerçeveler](../../standard/frameworks.md)için alt dizinler vardır. Dosya [düzeni, NuGet varlıklarının diskte düzenlenmesine](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)benzer:

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

*Hedef bildirim* dosyası, çalışma zamanı paket deposundaki paketleri listeler. Geliştiriciler uygulamalarını yayınlarken bu bildirimi hedefleyebilirler. Hedef bildirim genellikle hedeflenen üretim ortamının sahibi tarafından sağlanır.

## <a name="preparing-a-runtime-environment"></a>Çalışma zamanı ortamı hazırlama

Çalışma zamanı ortamının yöneticisi, bir çalışma zamanı paket deposu ve ilgili hedef bildirimi oluşturarak uygulamaları daha hızlı dağıtımlar ve daha düşük disk alanı kullanımı için optimize edebilir.

İlk adım, çalışma zamanı paket deposunu oluşturan paketleri listeleyen bir *paket deposu bildirimi* oluşturmaktır. Bu dosya biçimi proje dosya biçimi *(csproj)* ile uyumludur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Örnek**

Aşağıdaki örnek paket deposu bildirimi *(packages.csproj)* [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) [`Moq`](https://www.nuget.org/packages/moq/) eklemek ve bir çalışma zamanı paket deposuna kullanılır:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Paket deposu bildirimi, çalışma `dotnet store` zamanı ve çerçeve ile yürütülerek çalışma zamanı paket deposunu sağlama:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Örnek**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Komuttaki seçeneği ve yolu yineleyerek [`dotnet store`](../tools/dotnet-store.md) birden çok hedef paket deposu bildirim yolunu tek bir komuta geçirebilirsiniz.

Varsayılan olarak, komutun çıktısı kullanıcıprofilinin *.dotnet/store* alt dizini altında bir paket deposudur. `--output <OUTPUT_DIRECTORY>` Seçeneği kullanarak farklı bir konum belirtebilirsiniz. Mağazanın kök dizini bir hedef bildirimi *artifakı.xml* dosyası içerir. Bu dosya indirilebilmek için kullanılabilir hale getirilebilir ve yayımlarken bu mağazayı hedeflemek isteyen uygulama yazarları tarafından kullanılabilir.

**Örnek**

Aşağıdaki *artifact.xml* dosyası önceki örnek çalıştırdıktan sonra üretilir. Bu [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) bir bağımlılık olduğunu `Moq`unutmayın , bu yüzden otomatik olarak dahil ve *artifakı.xml* bildirim dosyasında görünür.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Bir uygulamayı hedef bildirime karşı yayımlama

Diskte bir hedef bildirim dosyanız varsa, uygulamanızı [`dotnet publish`](../tools/dotnet-publish.md) komutla yayınlarken dosyaya giden yolu belirtirsiniz:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Örnek**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Ortaya çıkan yayınlanmış uygulamayı, hedef bildirimde açıklanan paketlerin olduğu bir ortama dağıtırsınız. Bunu yapamamak, uygulamanın başlayamamasına neden oluyor.

Seçeneği ve yolu yineleyerek bir uygulamayı yayınlarken birden çok `--manifest manifest1.xml --manifest manifest2.xml`hedef bildirimi belirtin (örneğin, ). Bunu yaptığınızda, uygulama komuta sağlanan hedef bildirim dosyalarında belirtilen paketlerin birleşimi için kırpılır.

## <a name="specifying-target-manifests-in-the-project-file"></a>Proje dosyasında hedef bildirimlerinin belirtilmesi

Komutla hedef bildirimleri belirtmenin [`dotnet publish`](../tools/dotnet-publish.md) alternatifi, bunları proje dosyasında ** \<TargetManifestFiles>** etiketi altında yarı sütunlu ayrılmış bir yol listesi olarak belirtmektir.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Proje dosyasındaki hedef bildirimlerini yalnızca uygulamanın hedef ortamı .NET Core projeleri gibi iyi bilindiğinde belirtin. Bu açık kaynak projeleri için durum böyle değildir. Açık kaynak proje kullanıcıları genellikle farklı üretim ortamlarına dağıtılır. Bu üretim ortamları genellikle önceden yüklenmiş farklı paket kümeleri vardır. Bu tür ortamlarda hedef bildirimi hakkında varsayımlarda bulunamazsınız, `--manifest` bu [`dotnet publish`](../tools/dotnet-publish.md)nedenle .

## <a name="aspnet-core-implicit-store"></a>ASP.NET Çekirdek örtük mağaza

ASP.NET Core örtülü deposu yalnızca core 2.0 ASP.NET için geçerlidir. Uygulamaların core 2.1 ve sonrası ASP.NET kullanmalarını şiddetle öneririz, bu da örtük depoyu **kullanmaz.** ASP.NET Core 2.1 ve daha sonra paylaşılan çerçeveyi kullanın.

Çalışma zamanı paket deposu özelliği, uygulama [çerçeveye bağımlı dağıtım (FDD)](index.md#publish-runtime-dependent) uygulaması olarak dağıtıldığında, ASP.NET Core uygulaması tarafından örtülü olarak kullanılır. Hedefler, [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) hedef sistemdeki örtülü paket deposuna atıfta bulunan bildirimleri içerir. Ayrıca, `Microsoft.AspNetCore.All` paket sonuçlarına bağlı olan herhangi bir FDD uygulaması, meta pakette listelenen paketleri değil, `Microsoft.AspNetCore.All` yalnızca uygulamayı ve varlıklarını içeren yayınlanmış bir uygulamadır. Bu paketlerin hedef sistemde olduğu varsayılıyor.

.NET Core SDK yüklendiğinde çalışma zamanı paket deposu ana bilgisayara yüklenir. Diğer yükleyiciler,.NET Core SDK, Red Hat Yum, `apt-get`.NET Core Windows Server Hosting paketi ve manuel çalışma zamanı paket mağaza yüklemeleri zip/tarball yüklemeleri de dahil olmak üzere çalışma zamanı paket deposu sağlayabilir.

Çerçeveye bağımlı bir [dağıtım (FDD)](index.md#publish-runtime-dependent) uygulaması dağıtırken, hedef ortamın .NET Core SDK yüklü olduğundan emin olun. Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa, aşağıdaki örnekte olduğu gibi proje `false` dosyasında>** \<PublishWithAspNetCoreTargetManifest'i** belirterek örtülü mağazayı devre dışı bırakabilirsiniz:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> [Bağımsız dağıtım (SCD)](index.md#publish-self-contained) uygulamaları için, hedef sistemin gerekli bildirim paketlerini içermediği varsayılır. Bu nedenle, ** \<PublishWithAspNetCoreTargetManifest**>`true` bir SCD uygulaması için ayarlanamaz.

Dağıtımda bulunan bir bildirim bağımlılığı olan bir uygulama dağıtırsanız (derleme *çöp kutusu* klasöründe bulunur), çalışma zamanı paket deposu bu derlemeiçin ana bilgisayarda *kullanılmaz.* *Depo kutusu* klasörü derlemesi, ana bilgisayardaki çalışma zamanı paket deposundaki varlığından bağımsız olarak kullanılır.

Bildirimde belirtilen bağımlılığın sürümü, çalışma zamanı paket deposundaki bağımlılığın sürümüyle eşleşmelidir. Hedef bildirimdeki bağımlılık ile çalışma zamanı paket deposunda bulunan sürüm arasında bir sürüm uyuşmazlığı varsa ve uygulama dağıtımında paketin gerekli sürümünü içermiyorsa, uygulama başlatılamıyorsa. Özel durum, çalışma zamanı paket deposu montajını çağıran hedef bildiriminin adını içerir ve bu da uyuşmazlığı gidermenize yardımcı olur.

Dağıtım yayımlamada *kırpıldığında,* yalnızca belirttiğiniz bildirim paketlerinin belirli sürümleri yayımlanmış çıktıdan uzak tutulur. Uygulamanın başlatabilmesi için belirtilen sürümlerde paketler inanılması için ana bilgisayarda bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet-yayımla](../tools/dotnet-publish.md)
- [dotnet mağaza](../tools/dotnet-store.md)
