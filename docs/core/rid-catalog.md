---
title: .NET core çalışma zamanı tanımlayıcı (RID) Kataloğu
description: Çalışma zamanı tanımlayıcı (RID) ve RID'de .NET Core nasıl kullanıldığı hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 07/19/2018
ms.openlocfilehash: ff0449f7c6f878131f0ec4b16d685d2c02d26719
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517385"
---
# <a name="net-core-rid-catalog"></a>.NET core RID Kataloğu

RID kısaltması *çalışma zamanı tanımlayıcısı*. RID değerler, uygulamanın çalıştığı hedef platformları belirlemek için kullanılır.
.NET paketleri tarafından NuGet paketlerini platforma özgü varlıkları temsil etmek için kullanılır. Aşağıdaki değerleri RID'ler örnekleridir: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, veya `osx.10.12-x64`.
Yerel bağımlılıkları olan paketleri için hangi platformlarda paket geri yüklenebilir RID belirler.

Tek bir RID ayarlanabilir `<RuntimeIdentifier>` proje dosyanızın öğesi. Proje dosyasının noktalı virgülle ayrılmış bir liste olarak birden fazla RID tanımlanabilir `<RuntimeIdentifiers>` öğesi. Bunlar ayrıca aracılığıyla kullanılırlar `--runtime` aşağıdaki seçeneğiyle [.NET Core CLI komutları](./tools/index.md):

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Temsil somut işletim sistemleri genellikle bu deseni izlemenizi kurtarmaları: `[os].[version]-[architecture]-[additional qualifiers]` burada:

- `[os]` / platform işletim sistemi addır. Örneğin, `ubuntu`.

- `[version]` işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası. Örneğin, `15.10`.

  - Sürüm **olmamalıdır** pazarlama sürümleri gibi bunlar genellikle ayrı birden çok platformu API yüzey alanı değişen ile işletim sistemi sürümünü temsil eder.

- `[architecture]` İşlemci mimaridir. Örneğin: `x86`, `x64`, `arm`, veya `arm64`.

- `[additional qualifiers]` Daha fazla farklı platformları ayırt. Örneğin: `aot` veya `corert`.

## <a name="rid-graph"></a>RID grafiği

RID grafik veya çalışma zamanı geri dönüş graf birbiriyle uyumlu RID'ler bir listesidir. RID tanımlanan [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paket. Desteklenen RID'ler ve RID grafikte listesini görebilirsiniz [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) adresinde Corefx'te deponun bulunan dosya. Bu dosyada, tüm RID olduğunu, temel bir için içermesi dışında görebilirsiniz bir `"#import"` deyimi. Bu deyimler uyumlu RID'ler gösterir.

NuGet paketleri geri yükler, belirtilen çalışma zamanı için tam bir eşleşme bulmayı dener.
Tam bir eşleşme bulunmazsa, RID grafiğe göre en yakın uyumlu sistemi bulana kadar NuGet geri graf gösterilmektedir.

Aşağıdaki örnek, gerçek girişini `osx.10.12-x64` RID:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Yukarıdaki RID belirten `osx.10.12-x64` aktarır `osx.10.11-x64`. NuGet paketleri geri yükler, bu nedenle, tam bir eşleşme için bulmayı dener `osx.10.12-x64` paketteki. NuGet belirli çalışma zamanı bulamazsanız, belirttiğiniz paketleri geri yükleyebilirsiniz `osx.10.11-x64` örneğin çalışma zamanları.

Aşağıdaki örnek, ayrıca tanımlanan biraz daha büyük bir RID grafiği gösterir. *runtime.json* dosyası:

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

Tüm RID sonunda kök dizinine eşlemek `any` RID.

Bunları ile çalışırken göz önünde bulundurmanız sahip RID'ler hakkında bazı noktalar vardır:

- RID olan **donuk dizeleri** ve kara kutular değerlendirilmelidir.
- RID programlı olarak oluşturmayın.
- Önceden tanımlanmış RID'ler platformu kullanın.
- RID gerçek RID değerinden herhangi bir şey varsaymayın şekilde belirli gerekir.

## <a name="using-rids"></a>RID kullanma

RID kullanabilmek için RID mevcut bilmeniz gerekir. Yeni değerleri, platform için düzenli olarak eklenir.
En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.

.NET core 2.0 SDK'sını taşınabilir RID'ler kavramını sunar. Belirli bir sürümü ya da işletim sistemi dağıtım bağlı olmayan RID grafiğe eklenen yeni değerleri oldukları. Bunlar, birden çok Linux dağıtımları ile ilgilenirken yararlıdır.

Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID'ler gösterir. Ele alınmamıştır `arm` veya `corert` değerleri.

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

Bkz: [Windows üzerinde .NET Core önkoşulları](windows-prerequisites.md) daha fazla bilgi için.

## <a name="linux-rids"></a>Linux RID

- Taşınabilir
  - `linux-x64`
- CentOS
  - `centos-x64`
  - `centos.7-x64`
- Debian
  - `debian-x64`
  - `debian.8-x64`
  - `debian.9-x64` (.NET core 1.1 veya sonraki sürümler)
- Fedora
  - `fedora-x64`
  - `fedora.27-x64`
  - `fedora.28-x64` (.NET core 1.1 veya sonraki sürümler)
- Gentoo (.NET Core 2.0 veya sonraki sürümler)
  - `gentoo-x64`
- openSUSE
  - `opensuse-x64`
  - `opensuse.42.3-x64`
- Oracle Linux
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
  - `ol.7.3-x64`
  - `ol.7.4-x64`
- Red Hat Enterprise Linux
  - `rhel-x64`
  - `rhel.6-x64` (.NET core 2.0 veya sonraki sürümler)
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - `rhel.7.3-x64` (.NET core 2.0 veya sonraki sürümler)
  - `rhel.7.4-x64` (.NET core 2.0 veya sonraki sürümler)
- Tizen (.NET Core 2.0 veya sonraki sürümler)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`
- Ubuntu
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.17.10-x64`
  - `ubuntu.18.04-x64`
- Ubuntu türevleri
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64` (.NET core 2.0 veya sonraki sürümler)
  - `linuxmint.18.1-x64` (.NET core 2.0 veya sonraki sürümler)
  - `linuxmint.18.2-x64` (.NET core 2.0 veya sonraki sürümler)
  - `linuxmint.18.3-x64` (.NET core 2.0 veya sonraki sürümler)
- SUSE Enterprise Linux (SLES) (.NET Core 2.0 veya sonraki sürümler)
  - `sles-x64`
  - `sles.12-x64`
  - `sles.12.1-x64`
  - `sles.12.2-x64`
  - `sles.12.3-x64`
- Alpine Linux'ı (.NET Core 2.1 veya sonraki sürümler)
  - `alpine-x64`
  - `alpine.3.7-x64`

Bkz: [Linux üzerinde .NET Core önkoşulları](linux-prerequisites.md) daha fazla bilgi için.

## <a name="macos-rids"></a>macOS RID

macOS RID'ler eski markalama "OSX" kullanın.

- `osx-x64` (.NET core 2.0 veya sonraki sürümler için en düşük sürüm olan `osx.10.12-x64`)
- `osx.10.10-x64`
- `osx.10.11-x64`
- `osx.10.12-x64` (.NET core 1.1 veya sonraki sürümler)
- `osx.10.13-x64`

Bkz: [macos'ta .NET Core önkoşulları](macos-prerequisites.md) daha fazla bilgi için.

## <a name="android-rids-net-core-20-or-later-versions"></a>Android RID'ler (.NET Core 2.0 veya sonraki sürümler)

- `android`
- `android.21`

## <a name="see-also"></a>Ayrıca bkz.

* [Çalışma zamanı kimlikleri](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
