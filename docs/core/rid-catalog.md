---
title: .NET core çalışma zamanı tanımlayıcı (RID) Kataloğu
description: Çalışma zamanı tanımlayıcı (RID) ve RID'de .NET Core nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663082"
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

- `[os]` / platform işletim sistemi addır. Örneğin: `ubuntu`

- `[version]` işletim sistemi sürümü biçiminde noktalı virgülle ayrılmış (`.`) sürüm numarası. Örneğin: `15.10`

  - Sürüm **olmamalıdır** pazarlama sürümleri gibi bunlar genellikle ayrı birden çok platformu API yüzey alanı değişen ile işletim sistemi sürümünü temsil eder.

- `[architecture]` İşlemci mimaridir. Örneğin: `x86`, `x64`, `arm`, veya `arm64`.

- `[additional qualifiers]` Daha fazla farklı platformları ayırt. Örneğin: `aot`

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

.NET core 2.0 SDK'sını taşınabilir RID'ler kavramını sunar. Bunlar, belirli bir sürümü ya da işletim sistemi dağıtım bağlı değil ve .NET Core 2.0 ve üzeri kullanıyorsanız tercih RID grafiğe eklenen yeni değerlerdir. Birden çok Linux dağıtım paketlerini dağıtım RID'ler çoğu bu yana uğraşmanızı eşlendi olduğunda taşınabilir RID'ler için yararlıdır.

Aşağıdaki liste, her bir işletim sistemi için kullanılan en yaygın RID'ler küçük bir kısmı gösterir.

## <a name="windows-rids"></a>Windows RID

Yalnızca ortak değerleri listelenmektedir. En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.

- Taşınabilir (.NET Core 2.0 veya sonraki sürümler)
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- Windows 7 / Windows Server 2008 R2
  - `win7-x64`
  - `win7-x86`
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

Yalnızca ortak değerleri listelenmektedir. En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası. Aşağıdaki listede bulunmayan bir dağıtım çalıştıran cihazlar, taşınabilir RID'ler biri ile çalışabilir. Örneğin, listede olmayan bir Linux dağıtımı çalıştıran Raspberry Pi cihazlar ile hedeflenebilir `linux-arm`.

- Taşınabilir (.NET Core 2.0 veya sonraki sürümler)
  - `linux-x64` (CentOS, Debian, Fedora, Ubuntu ve türevleri çoğu masaüstü dağıtımları ister)
  - `linux-musl-x64` (Kullanan basit dağıtımlar [musl](https://wiki.musl-libc.org/projects-using-musl.html) ister Alpine Linux)
  - `linux-arm` (ARM üzerinde çalışan Linux dağıtımları, Raspberry Pi gibi)
- Red Hat Enterprise Linux
  - `rhel-x64` (Yerini `linux-x64` RHEL sürümünden sonraki bir sürümü 6'için)
  - `rhel.6-x64` (.NET core 2.0 veya sonraki sürümler)
- Tizen (.NET Core 2.0 veya sonraki sürümler)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Bkz: [Linux üzerinde .NET Core önkoşulları](linux-prerequisites.md) daha fazla bilgi için.

## <a name="macos-rids"></a>macOS RID

macOS RID'ler eski markalama "OSX" kullanın. Yalnızca ortak değerleri listelenmektedir. En son ve tam sürümü için bkz: [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) Corefx'te depo dosyası.

- Taşınabilir (.NET Core 2.0 veya sonraki sürümler)
  - `osx-x64` (En düşük işletim sistemi sürümü olan macOS 10.12 Sierra)
- macOS 10.10 Yosemite
  - `osx.10.10-x64`
- macOS 10.11 El Capitan
  - `osx.10.11-x64`
- macOS 10.12 Sierra (.NET Core 1.1 veya sonraki sürümler)
  - `osx.10.12-x64`
- macOS 10.13 High Sierra (.NET Core 1.1 veya sonraki sürümler)
  - `osx.10.13-x64`
- macOS 10.14 Mojave (.NET Core 1.1 veya sonraki sürümler)
  - `osx.10.14-x64`

Bkz: [macos'ta .NET Core önkoşulları](macos-prerequisites.md) daha fazla bilgi için.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı kimlikleri](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
