---
title: Çalışma zamanı paket deposu
description: .NET Core tarafından kullanılan bildirimleri hedeflemek için çalışma zamanı paket deposunu nasıl kullanacağınızı öğrenin.
ms.date: 08/12/2017
ms.openlocfilehash: e9e27ef535dbd9e7197c323f7e49a9960aeff0f9
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608355"
---
# <a name="runtime-package-store"></a>Çalışma zamanı paket deposu

.NET Core 2,0 ' den itibaren, uygulamaları paketleyebilir ve hedef ortamda mevcut olan bilinen bir paket kümesine dağıtabilirsiniz. Avantajlar, bazı durumlarda daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve geliştirilmiş başlangıç performanslarıdır.

Bu özellik, paketlerin depolandığı disk üzerindeki bir dizin olan bir *çalışma zamanı paket deposu*olarak uygulanır (genellikle MacOS/Linux ve *C:/Program Files/Windows üzerinde/Program Files/DotNet/Store* *üzerinde/* Bu dizin altında mimariler ve [hedef çerçeveler](../../standard/frameworks.md)için alt dizinler vardır. Dosya düzeni, [NuGet varlıklarının diskte düzenlendiği](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)yönteme benzer:

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

Bir *hedef bildirim* dosyası, çalışma zamanı paket deposundaki paketleri listeler. Geliştiriciler, uygulamasını yayımlarken bu bildirimi hedefleyebilir. Hedef bildirim genellikle hedeflenen üretim ortamının sahibi tarafından sağlanır.

## <a name="preparing-a-runtime-environment"></a>Çalışma zamanı ortamı hazırlama

Bir çalışma zamanı ortamının Yöneticisi, bir çalışma zamanı paket deposu ve ilgili hedef bildirimi oluşturarak daha hızlı dağıtımlar ve daha düşük disk alanı kullanımı için uygulamaları iyileştirebilirler.

İlk adım, çalışma zamanı paket deposunu oluşturan paketleri listeleyen bir *paket deposu bildirimi* oluşturmaktır. Bu dosya biçimi, proje dosyası biçimi (*csproj*) ile uyumludur.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Örnek**

Aşağıdaki örnek paket deposu bildirimi (*Packages. csproj*), [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) [`Moq`](https://www.nuget.org/packages/moq/) bir çalışma zamanı paket deposu eklemek için kullanılır:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

`dotnet store`Paket deposu bildirimi, çalışma zamanı ve Framework ile yürüterek çalışma zamanı paket deposunu sağlayın:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Örnek**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Komutta seçeneğini ve yolunu yineleyerek tek bir komuta birden çok hedef paket deposu bildirim yolu geçirebilirsiniz [`dotnet store`](../tools/dotnet-store.md) .

Varsayılan olarak, komutun çıktısı Kullanıcı profilinin *. DotNet/Store* alt dizininin altında bulunan bir paket deposudur. Seçeneğini kullanarak farklı bir konum belirtebilirsiniz `--output <OUTPUT_DIRECTORY>` . Deponun kök dizini bir hedef bildirim *artifact.xml* dosyası içeriyor. Bu dosya indirilmek üzere kullanılabilir hale getirilebilir ve yayımlarken bu depoyu hedeflemek isteyen uygulama yazarları tarafından kullanılabilir.

**Örnek**

Aşağıdaki *artifact.xml* dosyası, önceki örnek çalıştırıldıktan sonra üretilir. [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/)Uygulamasının bağımlılığı olduğunu `Moq` , bu nedenle otomatik olarak dahil edildiğini ve *artifacts.xml* bildirim dosyasında göründüğünü unutmayın.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Hedef bildiriminde uygulama yayımlama

Diskte bir hedef bildirim dosyanız varsa, şu komutla uygulamanızı yayımlarken dosyanın yolunu belirtirsiniz [`dotnet publish`](../tools/dotnet-publish.md) :

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Örnek**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Ortaya çıkan yayımlanmış uygulamayı, hedef bildiriminde tanımlanan paketlere sahip bir ortama dağıtırsınız. Bunun başarısız olması, uygulamanın başlamamasına neden olur.

Bir uygulamayı yayımlarken, seçeneğini ve yolunu yineleyerek birden çok hedef bildirimi belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml` ). Bunu yaptığınızda, uygulama, komuta sunulan hedef bildirim dosyalarında belirtilen paketlerin birleşimi için kırpılır.

Dağıtımda mevcut olan bir bildirim bağımlılığıyla bir uygulama dağıtırsanız (derleme *bin* klasöründe bulunur), çalışma zamanı paket deposu bu derleme için konakta *kullanılmaz* . *Bin* klasörü derlemesi, konaktaki çalışma zamanı paket deposundaki varlığına bakılmaksızın kullanılır.

Bildirimde belirtilen bağımlılığın sürümü, çalışma zamanı paket deposundaki bağımlılığın sürümüyle eşleşmelidir. Hedef bildirimde bağımlılık ile çalışma zamanı paket deposunda bulunan sürüm arasında bir sürüm uyumsuzluğu varsa ve uygulama, dağıtımda paketin gerekli sürümünü içermiyorsa, uygulama başlatılamaz. Özel durum, uyuşmazlığın giderilmesine yardımcı olan çalışma zamanı paket deposu derlemesi için çağıran hedef bildirimin adını içerir.

Dağıtım yayımlandığında *kırpıldıysa* , yalnızca belirttiğiniz bildirim paketlerinin belirli sürümleri, yayımlanan çıktıdan alınır. Uygulamanın başlaması için belirtilen sürümlerdeki paketlerin konakta mevcut olması gerekir.

## <a name="specifying-target-manifests-in-the-project-file"></a>Proje dosyasında hedef bildirimleri belirtme

Komut ile hedef bildirimleri belirtmenin bir alternatifi, [`dotnet publish`](../tools/dotnet-publish.md) bunları proje dosyasında, bir etiket altında bir noktalı virgülle ayrılmış yol listesi olarak belirtmektir **\<TargetManifestFiles>** .

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Yalnızca uygulamanın hedef ortamı, .NET Core projeleri için gibi iyi bilindiğinde, hedef bildirimleri proje dosyasında belirtin. Bu, açık kaynaklı projelerde bu durum değildir. Açık kaynaklı bir projenin kullanıcıları genellikle farklı üretim ortamlarına dağıtır. Bu üretim ortamları genellikle önceden yüklenmiş farklı paket kümelerine sahiptir. Bu tür ortamlarda hedef bildirimle ilgili varsayımlar yapamazsınız, bu nedenle seçeneğini kullanmanız gerekir `--manifest` [`dotnet publish`](../tools/dotnet-publish.md) .

## <a name="aspnet-core-implicit-store-net-core-20-only"></a>ASP.NET Core örtük depo (yalnızca .NET Core 2,0)

ASP.NET Core örtük depo yalnızca ASP.NET Core 2,0 için geçerlidir. Uygulamaların, örtük mağazayı kullanmayan ASP.NET Core 2,1 ve **üstünü kullanmasını önemle** öneririz. ASP.NET Core 2,1 ve üzeri, paylaşılan çerçeveyi kullanır.

.NET Core 2,0 için, uygulama [çerçeveye bağlı bir dağıtım](index.md#publish-framework-dependent) uygulaması olarak dağıtıldığında, çalışma zamanı paket deposu özelliği örtük olarak bir ASP.NET Core uygulaması tarafından kullanılır. İçindeki hedefler, [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) Hedef sistemdeki örtük paket deposuna başvuran bildirimleri içerir. Ayrıca, pakete bağlı olan çerçeveye bağımlı uygulamalar, `Microsoft.AspNetCore.All` meta pakette listelenen paketleri değil, yalnızca uygulamayı ve varlıklarını içeren yayımlanmış bir uygulamayla sonuçlanır `Microsoft.AspNetCore.All` . Bu paketlerin hedef sistemde bulunduğu varsayılır.

Çalışma zamanı paket deposu, .NET Core SDK yüklendiği zaman konağa yüklenir. Diğer yükleyiciler, .NET Core SDK ZIP/tarbol yüklemeleri, `apt-get` Red Hat Yıum, .NET Core Windows Server barındırma paketi ve el ile çalışma zamanı paket deposu yüklemeleri de dahil olmak üzere çalışma zamanı paket deposunu sağlayabilir.

[Çerçeveye bağımlı bir dağıtım](index.md#publish-framework-dependent) uygulaması dağıttığınızda, hedef ortamda .NET Core SDK yüklü olduğundan emin olun. Uygulama, ASP.NET Core içermeyen bir ortama dağıtılırsa,  **\<PublishWithAspNetCoreTargetManifest>** `false` Aşağıdaki örnekte olduğu gibi proje dosyasında olarak ayarla ' yı belirterek örtük depoyu devre dışı bırakabilirsiniz:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> [Kendi kendine kapsanan dağıtım](index.md#publish-self-contained) uygulamaları için, hedef sistemin gerekli bildirim paketlerini içermesi gerekmez. Bu nedenle, **\<PublishWithAspNetCoreTargetManifest>** `true` kendi içinde olan bir uygulama için olarak ayarlanamaz.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet-Yayımla](../tools/dotnet-publish.md)
- [DotNet-mağaza](../tools/dotnet-store.md)
