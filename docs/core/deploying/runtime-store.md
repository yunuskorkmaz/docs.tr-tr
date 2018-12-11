---
title: Çalışma zamanı Paket Deposu
description: .NET Core tarafından kullanılan hedef bildirimleri için çalışma zamanı Paket Deposu kullanmayı öğrenin.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: a190e148715547fde29d3a852183ea4d75065e79
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170359"
---
# <a name="runtime-package-store"></a>Çalışma zamanı Paket Deposu

.NET Core 2.0 ile başlayarak, paketleme ve dağıtma hedef ortamda mevcut paketleri bilinen bir dizi karşı uygulamalar mümkündür. Daha hızlı dağıtımlar, daha düşük disk alanı kullanımı ve bazı durumlarda geliştirilmiş başlangıç performansı yararlar şunlardır.

Bu özellik olarak uygulanan bir *çalışma zamanı Paket Deposu*, disk paketleri depolandığı bir dizin olan (genellikle en */usr/local/share/dotnet/store* macOS/Linux'ta ve *C: / Program dosyaları/dotnet/deposu* Windows üzerinde). Bu dizin altında mimarileri için alt vardır ve [hedef çerçeveyi](../../standard/frameworks.md). Dosya düzeni benzer şekilde, [NuGet varlıklar düzenlenir diskte](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

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

A *hedef bildirimi* dosyası çalışma zamanı Paket Deposu paketleri listeler. Geliştiriciler, uygulamaları yayımlarken bu bildirimi hedefleyebilirsiniz. Hedef bildirimi genellikle hedeflenen üretim ortamına sahibi tarafından sağlanır.

## <a name="preparing-a-runtime-environment"></a>Bir çalışma zamanı ortamı hazırlama

Bir çalışma zamanı ortam Yöneticisi, bir çalışma zamanı paket deposu ve karşılık gelen hedef bildirim oluşturarak uygulamaları daha hızlı dağıtım ve daha düşük disk alanı kullanımı için iyileştirebilirsiniz.

İlk adım oluşturmaktır bir *Paket Deposu bildirimi* çalışma zamanı paket deposu oluşturma paketlerini listeler. Bu dosya biçimi, proje dosyası biçimi ile uyumlu (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Örnek**

Aşağıdaki örnek Paket Deposu bildirimi (*packages.csproj*) eklemek için kullanılan [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) ve [ `Moq` ](https://www.nuget.org/packages/moq/) çalışma zamanı paket deposu için:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Çalışma zamanı Paket Deposu yürüterek sağlama `dotnet store` Paket Deposu bildirimi, çalışma zamanı ve framework ile:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Örnek**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Tek bir birden çok hedef Paket Deposu bildirim yolları geçirebilirsiniz [ `dotnet store` ](../tools/dotnet-store.md) seçeneği ve Komut yolunda yineleyerek komutu.

Varsayılan olarak, komut çıktısı bir paket altında deposudur *.dotnet depolama* kullanıcının profilini alt dizinidir. Kullanarak farklı bir konum belirtebilirsiniz `--output <OUTPUT_DIRECTORY>` seçeneği. Depo kök dizininde içeren bir hedef bildirime *artifact.xml* dosya. Bu dosya indirme için kullanılabilir hale getirilebilir ve yayımlarken bu depo hedeflemek istediğiniz uygulama yazarları tarafından kullanılabilir.

**Örnek**

Aşağıdaki *artifact.xml* dosya önceki örnekteki çalıştırdıktan sonra oluşturulur. Unutmayın [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) bir bağımlılığı olduğundan `Moq`, otomatik olarak eklemiştir ve görünür *artifacts.xml* bildirim dosyası.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Bir hedef bildirim karşı bir uygulamayı yayımlama

Diskte hedef bir bildirim dosyası varsa, dosya yolunu uygulamanızla yayımlama sırasında belirttiğiniz [ `dotnet publish` ](../tools/dotnet-publish.md) komutu:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Örnek**

```console
dotnet publish --manifest manifest.xml
```

Hedef bildiriminde açıklanan paketleri olan bir ortam elde edilen yayımlanan uygulamayı dağıtın. Bunu yapmazsanız, uygulamanın başlatılması başarısız olur.

Bir uygulamayı yayımlarken seçeneği ve yolu tekrarlayarak birden fazla hedef bildirimleri belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`). Bunu yaptığınızda, uygulama paketleri komutu sağlanan hedef bildirim dosyaları belirtilen birleşimi için kırpılır.

## <a name="specifying-target-manifests-in-the-project-file"></a>Proje dosyasındaki belirten hedef bildirimleri

Hedef belirtmek için alternatif bildirimleri ile [ `dotnet publish` ](../tools/dotnet-publish.md) komutu, proje dosyasında bunları yollarda noktalı virgülle ayrılmış bir listesi olarak belirtmek için bir  **\<TargetManifestFiles >** etiketi.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Yalnızca uygulama için hedef ortam .NET Core projeleri için iyi bilinen, gibi olduğunda proje dosyasında hedef bildirimleri belirtin. Bu, açık kaynak projeleri için durum geçerli değildir. Bir açık kaynak projesi kullanıcıları genellikle farklı üretim ortamlarına dağıtın. Bu üretim ortamları genellikle farklı önceden yüklenmiş paketler vardır. Kullanmanız gerekir bu tür ortamlarda, hedef bildirimi hakkında varsayımlar yapamazsınız `--manifest` seçeneği [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>ASP.NET Core örtük deposu

ASP.NET Core örtük deposu yalnızca ASP.NET Core 2.0 için geçerlidir. Uygulamaları kullanan mu, ASP.NET Core 2.1 ve üzeri, öneririz **değil** örtük deposu kullanın. ASP.NET Core 2.1 ve üzeri, paylaşılan çerçeve kullanın.

Uygulama olarak dağıtıldığında çalışma zamanı Paket Deposu özelliği örtük olarak bir ASP.NET Core uygulaması tarafından kullanılan bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama. Hedeflerin [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) örtük Paket Deposu hedef sistemde başvuran bildirimleri içerir. Ayrıca, bağlı olduğu tüm FDD uygulama `Microsoft.AspNetCore.All` paket uygulama ve varlıklarını ve listelenen paketleri içeren bir yayımlanan uygulama sonuçları `Microsoft.AspNetCore.All` metapackage. Bu paketleri hedef sistemde mevcut olduğundan emin varsayılır.

.NET Core SDK'sı yüklü çalışma zamanı Paket Deposu konakta yüklenir. Diğer yükleyiciler .NET Core SDK'ın Zip/tarball yüklemeleri dahil olmak üzere çalışma zamanı Paket Deposu sağlayabilir `apt-get`, Red Hat Yum paket .NET Core Windows Server barındırma ve el ile çalışma zamanı Paket Deposu yüklemeleri.

Dağıtım yaparken bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama, hedef ortam .NET Core SDK yüklü olduğundan emin olun. Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa belirterek örtük deponun dışında seçebilirsiniz  **\<PublishWithAspNetCoreTargetManifest >** kümesine `false` olarak proje dosyasındaki Aşağıdaki örnekte:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> İçin [müstakil dağıtım (SCD)](index.md#self-contained-deployments-scd) uygulamaları, hedef sistem bildirim gerekli paketleri mutlaka içermiyor varsayılır. Bu nedenle,  **\<PublishWithAspNetCoreTargetManifest >** ayarlanamıyor `true` SCD uygulama.

Uygulamanın dağıtımda mevcut olan bildirim bağımlılığı dağıtırsanız (mevcut bir derlemedir *bin* klasör), çalışma zamanı Paket Deposu *kullanılmayan* o derleme için ana bilgisayarda. *Bin* klasör derleme bakılmaksızın, konaktaki çalışma zamanı Paket Deposu bulunması kullanılır.

Bildirimde belirtilen bağımlılık sürümü, çalışma zamanı Paket Deposu bağımlılığı sürümünü eşleşmelidir. Hedef bildirimde bağımlılık arasında sürüm uyuşmazlığı varsa ve çalışma zamanı paket deposu ve uygulama içinde bulunan sürüm gerekli Paket sürümü, dağıtımda içermez, uygulamayı başlatmak başarısız olur. Özel durum uyuşmazlığı gidermenize yardımcı olur çalışma zamanı Paket Deposu derleme için adlı hedef bildirim adını içerir.

Bir dağıtım olduğunda *kırpılmış* yayımlama sırasında belirttiğiniz bildirim paketler yalnızca belirli sürümlerini yayımlanmış çıktısı uğratılan. Belirtilen sürümleri, paketleri başlatmak için uygulama için ana bilgisayarda bulunması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

* [DotNet-yayımlama](../tools/dotnet-publish.md)  
* [DotNet-store](../tools/dotnet-store.md)  
