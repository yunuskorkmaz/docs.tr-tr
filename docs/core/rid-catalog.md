---
title: ".NET çekirdeği çalışma zamanı tanımlayıcı (RID) Kataloğu"
description: "Çalışma zamanı tanımlayıcı (RID) ve RID .NET Core nasıl kullanıldığı hakkında bilgi edinin."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a>.NET core RID Kataloğu

RID kısaltması *çalışma zamanı tanımlayıcı*. RID değerler, uygulamanın çalıştığı Hedef platformlar tanımlamak için kullanılır.
.NET paketleri tarafından bunlar NuGet paketlerini platforma özgü varlıkları temsil etmek için kullanılır. Aşağıdaki değerleri RID örnekleri şunlardır: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, veya `osx.10.12-x64`.
Yerel bağımlılıkları olan paketleri için hangi platformlarda paketi geri yüklemesi RID belirler.

RID ayarlanabilir `<RuntimeIdentifier>` proje dosyanızı öğesidir. Ayrıca aracılığıyla kullanıldıklarından `--runtime` aşağıdaki seçeneğiyle [.NET Core CLI komutları](./tools/index.md):

- [DotNet derleme](./tools/dotnet-build.md)
- [DotNet Temizle](./tools/dotnet-clean.md)
- [DotNet paketi](./tools/dotnet-pack.md)
- [DotNet yayımlama](./tools/dotnet-publish.md)
- [DotNet geri yükleme](./tools/dotnet-restore.md)
- [dotnet çalıştırın](./tools/dotnet-run.md)
- [DotNet deposu](./tools/dotnet-store.md)

Temsil somut işletim sistemleri genellikle bu deseni izlemenizi kurtarmaları: `[os].[version]-[architecture]-[additional qualifiers]` burada:

- `[os]`platform/işletim sistemi addır. Örneğin, `ubuntu`.

- `[version]`işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası. Örneğin, `15.10`.

  - Sürüm **döndürmemelidir** pazarlama sürümleri, bunlar genellikle birden fazla ayrı platform API yüzey alanını değişen ile işletim sistemi sürümünü temsil.

- `[architecture]`İşlemci mimarisi ' dir. Örneğin: `x86`, `x64`, `arm`, veya `arm64`.

- `[additional qualifiers]`Daha fazla farklı platformlarda ayırt. Örneğin: `aot` veya `corert`.

## <a name="rid-graph"></a>RID grafiği

RID grafik veya çalışma zamanı geri dönüş grafik birbiriyle uyumlu RID listesidir. RID tanımlanan [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paket. Desteklenen RID'ler ve RID grafikte listesini görebilir [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) CoreFX depodaki bulunduğu dosya. Bu dosyada, tüm RID olduğunu, temel biri için içeren dışında görebilirsiniz bir `"#import"` deyimi. Bu deyimler uyumlu RID gösterir.

NuGet paketleri geri yüklerken belirtilen çalışma zamanı için tam bir eşleşme bulmaya çalışır.
Tam bir eşleşme bulunmazsa RID grafik göre en yakın uyumlu sistem bulana kadar NuGet geri grafiği anlatılmaktadır.

Aşağıdaki örnek için gerçek giriştir `osx.10.12-x64` RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Yukarıdaki RID belirleyen `osx.10.12-x64` alır `osx.10.11-x64`. NuGet paketleri geri yüklerse, bu nedenle, onu için tam bir eşleşme bulmaya çalışır `osx.10.12-x64` paketinde. NuGet belirli çalışma zamanı bulamazsanız, belirttiğiniz paketler geri yükleyebilirsiniz `osx.10.11-x64` örneğin çalışma zamanları.

Aşağıdaki örnek, ayrıca tanımlanan biraz daha büyük bir RID grafik gösterir *runtime.json* dosyası:

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

Tüm RID sonunda kök geri eşlemek `any` RID.

Bunları ile çalışırken göz önünde bulundurmanız gereken RID hakkında bazı noktalar vardır:

- RID olan **donuk dizeleri** ve siyah kutular değerlendirilmelidir.
- RID program aracılığıyla yapı yok.
- Önceden tanımlanmış RID platformu için kullanın.
- RID herhangi bir şeyin gerçek RID değer varsaymayın şekilde belirli olması gerekir.

## <a name="using-rids"></a>RID kullanma

RID kullanmak, RID mevcut bilmeniz gerekir. Yeni değerler düzenli aralıklarla platforma eklenir.
En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) CoreFX depodaki dosyada.

.NET core 2.0 SDK taşınabilir RID kavramını sunmaktadır. Belirli bir sürüm ya da işletim sistemi dağıtım bağlı olmayan RID grafiğe eklenen yeni değerleri oldukları. Bunlar, birden çok Linux distro'lar ile ilgilenirken yararlıdır.

Aşağıdaki liste, her işletim sistemi için kullanılan en yaygın RID gösterir. Bu kapsamıyordur `arm` veya `corert` değerleri.

## <a name="windows-rids"></a>Windows RID

- Taşınabilir
  - `win-x86`
  - `win-x64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
- Windows 8 / Windows Server 2012
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- Windows 8.1 / Windows Server 2012 R2
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- Windows 10 / Windows Server 2016
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

Bkz: [.NET Core Windows önkoşulları](windows-prerequisites.md) daha fazla bilgi için.

## <a name="linux-rids"></a>Linux RID

- Taşınabilir
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
- Fedora
  - `fedora-x64`
  - `fedora.24-x64`
  - `fedora.25-x64`(.NET core 2.0 veya sonraki sürümler)
  - `fedora.26-x64`(.NET core 2.0 veya sonraki sürümler)
- Gentoo (.NET Core 2.0 veya sonraki sürümler)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64`(.NET core 2.0 veya sonraki sürümler)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64`(.NET core 2.0 veya sonraki sürümler)
  - `rhel.7.4-x64`(.NET core 2.0 veya sonraki sürümler)
- Tizen (.NET Core 2.0 veya sonraki sürümler)
  - `tizen`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- Ubuntu türevleri
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - `linuxmint.18.1-x64`(.NET core 2.0 veya sonraki sürümler)

Bkz: [.NET Core Linux önkoşulları](linux-prerequisites.md) daha fazla bilgi için.

## <a name="macos-rids"></a>macOS RID

macOS RID eski markalama "OSX" kullanın.

- `osx-x64`(.NET core 2.0 veya sonraki sürümler, en düşük sürüm olan `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64`(.NET core 1.1 veya sonraki sürümler)
- `osx.10.13-x64`

Bkz: [.NET Core üzerinde macOS önkoşulları](macos-prerequisites.md) daha fazla bilgi için.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android RID (.NET Core 2.0 veya sonraki sürümler)

- `android`
- `android.21`

## <a name="see-also"></a>Ayrıca bkz.

[Çalışma zamanı kimlikleri](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
