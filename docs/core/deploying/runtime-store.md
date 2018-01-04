---
title: "Çalışma zamanı Paket Deposu"
description: "Bu konuda çalışma zamanı paket deposu ve hedef bildirimleri .NET Core tarafından kullanılan açıklanmaktadır."
keywords: ".NET, .NET core dotnet deposu, çalışma zamanı Paket Deposu"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.workload: dotnetcore
ms.openlocfilehash: de1aa4d29abae6bc6c26c0686bafe9bd9cc10ee1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="runtime-package-store"></a>Çalışma zamanı Paket Deposu

.NET Core 2.0 ile başlayarak, paket ve hedef ortamda mevcut paketleri bilinen bir dizi uygulamaları dağıtmak mümkündür. Daha hızlı dağıtımlar, daha düşük disk alanı kullanımını ve bazı durumlarda geliştirilmiş başlangıç performans yararlar şunlardır.

Bu özellik olarak uygulanan bir *çalışma zamanı Paket Deposu*, paketleri depolandığı disk üzerindeki bir dizin olduğu (genellikle en */usr/local/share/dotnet/store* macOS/Linux üzerinde ve *C: / Program dosyaları/dotnet/deposu* Windows'da). Bu dizin altında mimarileri için alt dizinler vardır ve [hedef çerçeveler](../../standard/frameworks.md). Dosya düzeni benzer şekilde, [NuGet varlıklar düzenlenir diskte](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):

\dotnet   
&nbsp;&nbsp;\store   
&nbsp;&nbsp;&nbsp;&nbsp;\x64   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   
&nbsp;&nbsp;&nbsp;&nbsp;\x86   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.applicationinsights   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\Microsoft.aspnetcore   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...   

A *hedef bildirimi* dosya çalışma zamanı paketi deposundaki paketlerini listeler. Geliştiriciler, kendi uygulama yayımlarken bu bildirimi hedefleyebilirsiniz. Hedef bildirimi genellikle hedeflenen üretim ortamına sahibi tarafından sağlanır.

## <a name="preparing-a-runtime-environment"></a>Çalışma zamanı ortamı hazırlama

Çalışma zamanı ortamı yönetici uygulamaları daha hızlı dağıtımları ve daha düşük disk alanı kullanımı için bir çalışma zamanı paket deposu ve karşılık gelen hedef bildirimi oluşturarak en iyi duruma getirebilirsiniz.

İlk adım oluşturmaktır bir *Paket Deposu bildirimi* çalışma zamanı paket deposu oluşturma paketlerini listeler. Bu dosya biçimi proje dosyası biçimiyle uyumlu değil (*csproj*).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

**Örnek**

Aşağıdaki örnek Paket Deposu bildirimi (*packages.csproj*) eklemek için kullanılan [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) ve [ `Moq` ](https://www.nuget.org/packages/moq/) bir çalışma zamanı paket deposu için:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

Çalışma zamanı Paket Deposu yürüterek sağlamak `dotnet store` Paket Deposu bildirimi, çalışma zamanı ve framework ile:

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

**Örnek**

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

Tek bir birden çok hedef Paket Deposu bildirim yollarını geçirebilirsiniz [ `dotnet store` ](../tools/dotnet-store.md) yinelenen seçeneği ve Komut yolunda tarafından komutu.

Varsayılan olarak, komut çıktısı bir paket altında deposudur *.dotnet/deposu* kullanıcının profilini alt. Kullanarak farklı bir konum belirtebilirsiniz `--output <OUTPUT_DIRECTORY>` seçeneği. Depo kök dizininde içeren bir hedef bildirime *artifact.xml* dosya. Bu dosya indirme için kullanılabilir hale getirilebilir ve bu depo yayımlarken hedeflemek istediğiniz uygulama yazarlar tarafından kullanılıyor.

**Örnek**

Aşağıdaki *artifact.xml* dosyası, önceki örnekte çalıştırdıktan sonra oluşturulur. Unutmayın [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) bir bağımlılığıdır `Moq`, böylece otomatik olarak eklenen ve görünür *artifacts.xml* bildirim dosyası.

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a>Bir hedef bildirimi karşı bir uygulama yayımlama

Diskte hedef bildirim dosyası varsa, dosyanın yolu ile uygulamanızı yayımlama sırasında belirttiğiniz [ `dotnet publish` ](../tools/dotnet-publish.md) komutu:

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

**Örnek**

```console
dotnet publish --manifest manifest.xml
```

Hedef bildiriminde açıklanan paketleri bir ortam için sonuçta elde edilen yayımlanan uygulamayı dağıtın. Bunu yapmazsanız başlatılamamasına uygulamada sonuçlanır.

Bir uygulama seçeneği ve yolu tekrarlayarak yayımlarken birden çok hedef bildirimleri belirtin (örneğin, `--manifest manifest1.xml --manifest manifest2.xml`). Bunu yaptığınızda, uygulama paketleri komutu sağlanan hedef bildirim dosyaları belirtilen birleşimi için kırpılır.

## <a name="specifying-target-manifests-in-the-project-file"></a>Proje dosyasında belirten hedef bildirimleri

Hedef belirtme alternatif bildirimleri ile [ `dotnet publish` ](../tools/dotnet-publish.md) komuttur bunları yollarının altında noktalı virgülle ayrılmış liste olarak proje dosyasında belirtmek için bir  **\<TargetManifestFiles >** etiketi.

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

Yalnızca hedef ortam uygulama için .NET Core projeleri için iyi bilinen, gibi olduğunda hedef bildirimleri proje dosyası belirtin. Bu, açık kaynaklı proje söz konusu değildir. Bir açık kaynak projesi kullanıcıları genellikle farklı üretim ortamlarına dağıtın. Bu üretim ortamlarında genellikle önceden yüklenen paketler farklı kümelerini sahiptir. Kullanmanız gereken şekilde bu tür ortamlarda varsayımlar hedef bildirimi hakkında yapamazsınız `--manifest` seçeneği [ `dotnet publish` ](../tools/dotnet-publish.md).

## <a name="aspnet-core-implicit-store"></a>ASP.NET Core örtük deposu

Uygulama olarak dağıtıldığında çalışma zamanı paketi depolama özelliğini örtük olarak ASP.NET Core uygulama tarafından kullanılan bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama. Hedeflerin [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) hedef sistemde örtük Paket Deposu başvuran bildirimlerini içerir. Ayrıca, bağımlı herhangi FDD uygulama `Microsoft.AspNetCore.All` paketini yalnızca uygulama ve varlıklarını ve değil listelenen paketler içeren yayımlanan bir uygulamanın sonuçlarında `Microsoft.AspNetCore.All` metapackage. Bu paketleri hedef sistemde mevcut olduğu varsayılır.

.NET Core SDK yüklendiğinde çalışma zamanı Paket Deposu ana bilgisayarda yüklü. Diğer yükleyicileri .NET Core SDK Zip/tarball yüklemeleri dahil olmak üzere çalışma zamanı Paket Deposu sağlayabilir `apt-get`, Red Hat Yum, .NET Core Windows Server barındırma paket ve el ile çalışma zamanı Paket Deposu yüklemeleri.

Dağıtırken bir [framework bağımlı dağıtım (FDD)](index.md#framework-dependent-deployments-fdd) uygulama, hedef ortam .NET Core SDK yüklü olduğundan emin olun. Uygulama ASP.NET Core içermeyen bir ortama dağıtılırsa belirterek dışında örtük deposu seçebilirsiniz  **\<PublishWithAspNetCoreTargetManifest >** kümesine `false` proje dosyasında olarak Aşağıdaki örnek:

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> İçin [müstakil dağıtım (SCD)](index.md#self-contained-deployments-scd) uygulamaları varsayılır hedef sistem gerekli bildirim paketlerini mutlaka içermiyor. Bu nedenle,  **\<PublishWithAspNetCoreTargetManifest >** ayarlanamıyor `true` SCD uygulama.

Dağıtımda mevcut bir bildirim bağımlılık uygulamayla dağıtırsanız (derleme mevcut *bin* klasör), çalışma zamanı Paket Deposu *kullanılmaz* bu derleme için konakta. *Bin* klasörü derleme ana bilgisayarda çalışma zamanı paketi deposundaki varlığını bağımsız olarak kullanılır.

Bildiriminde belirtilen bağımlılık sürümü çalışma zamanı paketi deposundaki bağımlılık sürümü aynı olmalıdır. Hedef bildiriminde bağımlılık arasında sürüm uyuşmazlığı varsa ve çalışma zamanı paket deposu ve uygulama mevcut sürümü, dağıtım paketi gerekli sürümü içermez, uygulamayı başlatmak başarısız olur. Özel durum uyuşmazlığı gidermenize yardımcı çalışma zamanı Paket Deposu derleme için adlı hedef bildirim adını içerir.

Dağıtım olduğunda *kırpılmış* şunu yayımlanan çıkışı gösterdiğiniz bildirim paketler yalnızca belirli sürümlerini geri çekildi. Belirtilen sürümleri adresindeki paketleri başlatmak için uygulama için ana bilgisayarda mevcut olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
 [DotNet-yayımlama](../tools/dotnet-publish.md)  
 [DotNet deposu](../tools/dotnet-store.md)  
