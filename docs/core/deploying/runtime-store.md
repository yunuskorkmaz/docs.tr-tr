---
title: Çalışma zamanı paket deposu
description: .NET Core tarafından kullanılan bildirimleri hedeflemek için çalışma zamanı paket deposunu nasıl kullanacağınızı öğrenin.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 8a8d2d3298f144347c36c640700a1e578dc14715
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116542"
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
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Örnek**

Aşağıdaki örnek paket deposu bildirimi (*Packages. csproj*), bir çalışma zamanı paket [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) deposu [`Moq`](https://www.nuget.org/packages/moq/) eklemek için kullanılır:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Paket deposu bildirimi, çalışma zamanı ve `dotnet store` Framework ile yürüterek çalışma zamanı paket deposunu sağlayın:

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Örnek**

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Komutta seçeneğini ve yolunu yineleyerek tek [`dotnet store`](../tools/dotnet-store.md) bir komuta birden çok hedef paket deposu bildirim yolu geçirebilirsiniz.

Varsayılan olarak, komutun çıktısı Kullanıcı profilinin *. DotNet/Store* alt dizininin altında bulunan bir paket deposudur. `--output <OUTPUT_DIRECTORY>` Seçeneğini kullanarak farklı bir konum belirtebilirsiniz. Deponun kök dizini bir hedef bildirim *yapıtı. xml* dosyası içeriyor. Bu dosya indirilmek üzere kullanılabilir hale getirilebilir ve yayımlarken bu depoyu hedeflemek isteyen uygulama yazarları tarafından kullanılabilir.

**Örnek**

Önceki örnek çalıştırıldıktan sonra aşağıdaki *yapıt. xml* dosyası oluşturulur. Uygulamasının bağımlılığı olduğunu, bu nedenle otomatik olarak dahil edildiğini ve *yapılar. xml* bildirim dosyasında göründüğünü unutmayın. `Moq` [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/)

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Hedef bildiriminde uygulama yayımlama

Diskte bir hedef bildirim dosyanız varsa, şu [`dotnet publish`](../tools/dotnet-publish.md) komutla uygulamanızı yayımlarken dosyanın yolunu belirtirsiniz:

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Örnek**

```dotnetcli
dotnet publish --manifest manifest.xml
```

Ortaya çıkan yayımlanmış uygulamayı, hedef bildiriminde tanımlanan paketlere sahip bir ortama dağıtırsınız. Bunun başarısız olması, uygulamanın başlamamasına neden olur.

Bir uygulamayı yayımlarken, seçeneğini ve yolunu yineleyerek birden çok hedef bildirimi belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`). Bunu yaptığınızda, uygulama, komuta sunulan hedef bildirim dosyalarında belirtilen paketlerin birleşimi için kırpılır.

## <a name="specifying-target-manifests-in-the-project-file"></a>Proje dosyasında hedef bildirimleri belirtme

[`dotnet publish`](../tools/dotnet-publish.md) Komut ile hedef bildirimleri belirtmenin bir alternatifi, bunları proje dosyasında bir  **\<targetmanifestfiles >** etiketi altındaki noktalı virgülle ayrılmış bir yol listesi olarak belirtmektir.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Yalnızca uygulamanın hedef ortamı, .NET Core projeleri için gibi iyi bilindiğinde, hedef bildirimleri proje dosyasında belirtin. Bu, açık kaynaklı projelerde bu durum değildir. Açık kaynaklı bir projenin kullanıcıları genellikle farklı üretim ortamlarına dağıtır. Bu üretim ortamları genellikle önceden yüklenmiş farklı paket kümelerine sahiptir. Bu tür ortamlarda hedef bildirimle ilgili varsayımlar yapamazsınız, bu nedenle `--manifest` [`dotnet publish`](../tools/dotnet-publish.md)seçeneğini kullanmanız gerekir.

## <a name="aspnet-core-implicit-store"></a>ASP.NET Core örtük mağaza

ASP.NET Core örtük depo yalnızca ASP.NET Core 2,0 için geçerlidir. Uygulamaların, örtük mağazayı kullanmayan ASP.NET Core 2,1 ve **üstünü kullanmasını önemle** öneririz. ASP.NET Core 2,1 ve üzeri, paylaşılan çerçeveyi kullanır.

Çalışma zamanı paket deposu özelliği, uygulama [Framework 'e bağımlı bir dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulaması olarak dağıtıldığında ASP.NET Core bir uygulama tarafından örtük olarak kullanılır. İçindeki [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) hedefler, hedef sistemdeki örtük paket deposuna başvuran bildirimleri içerir. Ayrıca, `Microsoft.AspNetCore.All` pakete bağlı olan tüm FDD uygulamaları, `Microsoft.AspNetCore.All` metapackage 'de listelenen paketleri değil, yalnızca uygulamayı ve varlıklarını içeren yayımlanmış bir uygulamayla sonuçlanır. Bu paketlerin hedef sistemde bulunduğu varsayılır.

Çalışma zamanı paket deposu, .NET Core SDK yüklendiği zaman konağa yüklenir. Diğer yükleyiciler, .NET Core SDK `apt-get`ZIP/tarbol yüklemeleri, Red Hat yıum, .NET Core Windows Server barındırma paketi ve el ile çalışma zamanı paket deposu yüklemeleri de dahil olmak üzere çalışma zamanı paket deposunu sağlayabilir.

[Çerçeveye bağımlı bir dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulaması dağıttığınızda, hedef ortamda .NET Core SDK yüklü olduğundan emin olun. Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa, aşağıdaki örnekte olduğu gibi  **\<publishwithaspnetcoretargetmanifest >** öğesini proje dosyasında olarak ayarlanmış şekilde `false` belirterek örtük depoyu devre dışı bırakabilirsiniz :

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> [Kendi kendine içerilen dağıtım (SCD)](index.md#self-contained-deployments-scd) uygulamaları için, hedef sistemin gerekli bildirim paketlerini içermesi gerekmediği varsayılır. Bu nedenle,  **\<publishwithaspnetcoretargetmanifest >** , bir SCD `true` uygulaması için olarak ayarlanamaz.

Dağıtımda mevcut olan bir bildirim bağımlılığıyla bir uygulama dağıtırsanız (derleme *bin* klasöründe bulunur), çalışma zamanı paket deposu bu derleme için konakta *kullanılmaz* . *Bin* klasörü derlemesi, konaktaki çalışma zamanı paket deposundaki varlığına bakılmaksızın kullanılır.

Bildirimde belirtilen bağımlılığın sürümü, çalışma zamanı paket deposundaki bağımlılığın sürümüyle eşleşmelidir. Hedef bildirimde bağımlılık ile çalışma zamanı paket deposunda bulunan sürüm arasında bir sürüm uyumsuzluğu varsa ve uygulama, dağıtımda paketin gerekli sürümünü içermiyorsa, uygulama başlatılamaz. Özel durum, uyuşmazlığın giderilmesine yardımcı olan çalışma zamanı paket deposu derlemesi için çağıran hedef bildirimin adını içerir.

Dağıtım yayımlandığında *kırpıldıysa* , yalnızca belirttiğiniz bildirim paketlerinin belirli sürümleri, yayımlanan çıktıdan alınır. Uygulamanın başlaması için belirtilen sürümlerdeki paketlerin konakta mevcut olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet-Yayımla](../tools/dotnet-publish.md)
- [DotNet-mağaza](../tools/dotnet-store.md)
