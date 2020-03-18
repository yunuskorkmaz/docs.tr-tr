---
title: .NET Core Runtime Tanımlayıcı (RID) kataloğu
description: Runtime Tanımlayıcı (RID) ve RID'lerin .NET Core'da nasıl kullanıldığı hakkında bilgi edinin.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451739"
---
# <a name="net-core-rid-catalog"></a>.NET Core RID Kataloğu

RID, *Runtime Tanımlayıcı'nın kısaltmasıdır.* RID değerleri, uygulamanın çalıştığı hedef platformları tanımlamak için kullanılır.
.NET paketleri tarafından NuGet paketlerinde platforma özgü varlıkları temsil etmek için kullanılırlar. Aşağıdaki değerler, RID'lere `linux-x64`örnektir: `win7-x64`, `osx.10.12-x64`, `ubuntu.14.04-x64`veya .
Yerel bağımlılıkları olan paketler için RID, paketin hangi platformlarda geri yüklenebileceğini belirler.

Proje dosyanızın `<RuntimeIdentifier>` öğesinde tek bir RID ayarlanabilir. Birden çok RID, proje dosyasının `<RuntimeIdentifiers>` öğesinde yarı sütunlu sınırlı bir liste olarak tanımlanabilir. Ayrıca aşağıdaki `--runtime` [.NET Core CLI komutları](./tools/index.md)ile seçenek üzerinden kullanılır:

- [dotnet build](./tools/dotnet-build.md)
- [dotnet clean](./tools/dotnet-clean.md)
- [dotnet pack](./tools/dotnet-pack.md)
- [dotnet publish](./tools/dotnet-publish.md)
- [dotnet restore](./tools/dotnet-restore.md)
- [dotnet run](./tools/dotnet-run.md)
- [dotnet store](./tools/dotnet-store.md)

Beton işletim sistemlerini temsil eden RID'ler genellikle şu deseni izler: `[os].[version]-[architecture]-[additional qualifiers]` aşağıdakiler:

- `[os]`işletim/platform sistem takma adıdır. Örneğin, `ubuntu`.

- `[version]`nokta ayrılmış (`.`) sürüm numarası şeklinde işletim sistemi sürümüdür. Örneğin, `15.10`.

  - Sürüm pazarlama sürümleri **olmamalıdır,** çünkü bunlar genellikle farklı platform API yüzey alanına sahip işletim sisteminin birden fazla ayrı sürümünü temsil eder.

- `[architecture]`işlemci mimarisidir. Örneğin: `x86`, `x64` `arm`, `arm64`, veya .

- `[additional qualifiers]`farklı platformları daha da farklılaştırmak. Örneğin: `aot`.

## <a name="rid-graph"></a>RID grafiği

RID grafiği veya çalışma zamanı geri dönüş grafiği, birbiriyle uyumlu OLAN RID'lerin listesidir. RID'ler [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) paketinde tanımlanır. Desteklenen RID'lerin listesini ve depoda bulunan [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasında RID grafiğini `dotnet/runtime` görebilirsiniz. Bu dosyada, temel bir hariç tüm RID'lerin bir `"#import"` deyim içerdiğini görebilirsiniz. Bu ifadeler uyumlu RID'leri gösterir.

NuGet paketleri geri yüklediğinde, belirtilen çalışma süresi için tam bir eşleşme bulmaya çalışır.
Tam bir eşleşme bulunamazsa, NuGet RID grafiğine göre en yakın uyumlu sistemi bulana kadar grafiği geri alır.

Aşağıdaki örnek `osx.10.12-x64` RID için gerçek giriştir:

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

Yukarıdaki RID bu `osx.10.12-x64` ithalat `osx.10.11-x64`belirtir. Bu nedenle, NuGet paketleri geri yüklediğinde, pakettekilerle `osx.10.12-x64` tam olarak eşleşmeye çalışır. NuGet belirli çalışma zamanını bulamıyorsa, örneğin `osx.10.11-x64` çalışma sürelerini belirten paketleri geri yükleyebilir.

Aşağıdaki örnek, *runtime.json* dosyasında da tanımlanan biraz daha büyük bir RID grafiği ni gösterir:

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

Tüm RID'ler sonunda kök `any` RID geri eşler.

RID'ler hakkında onlarla çalışırken göz önünde bulundurmanız gereken bazı hususlar vardır:

- RID'ler **opak dizeleri** ve kara kutular olarak kabul edilmelidir.
- PROGRAMLI RİD'ler oluşturmayın.
- Platform için zaten tanımlanmış OLAN RID'leri kullanın.
- RID'lerin belirli olması gerekir, bu nedenle gerçek RID değerinden hiçbir şey varsayma.

## <a name="using-rids"></a>RID'leri kullanma

RID'leri kullanabilmek için, hangi RID'lerin var olduğunu bilmeniz gerekir. Platforma düzenli olarak yeni değerler eklenir.
En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın.

.NET Core 2.0 SDK taşınabilir RED kavramını tanıttı. Rid grafiğine belirli bir sürüme veya işletim sistemi dağıtımına bağlı olmayan yeni değerlerdir ve .NET Core 2.0 ve üzeri ni kullanırken tercih edilen değerlerdir. Çoğu dağıtım RID'si taşınabilir RID'lere eşlendiğinden, birden fazla Linux dağıtımıyla uğraşırken özellikle yararlıdırlar.

Aşağıdaki liste, her işletim sistemi için kullanılan en yaygın RID'lerin küçük bir alt kümesini gösterir.

## <a name="windows-rids"></a>Windows RID'leri

Yalnızca ortak değerler listelenir. En son ve tam sürüm için, depodaki `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına bakın.

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

Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-windows)

## <a name="linux-rids"></a>Linux RID'leri

Yalnızca ortak değerler listelenir. En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın. Aşağıda listelenmemiş bir dağıtım çalıştıran aygıtlar Taşınabilir KOPYALARDAN biriyle çalışabilir. Örneğin, listelenmemiş bir Linux dağıtımı çalıştıran Raspberry `linux-arm`Pi cihazları .

- Taşınabilir (.NET Core 2.0 veya sonraki sürümler)
  - `linux-x64`(CentOS, Debian, Fedora, Ubuntu ve türevleri gibi çoğu masaüstü dağıtımı)
  - `linux-musl-x64`(Alpine Linux gibi [musl](https://wiki.musl-libc.org/projects-using-musl.html) kullanarak hafif dağıtımlar)
  - `linux-arm`(Linux dağıtımları Raspberry Pi gibi ARM çalışan)
- Red Hat Enterprise Linux
  - `rhel-x64`(Sürüm 6 yukarıdaki `linux-x64` RHEL için superseded)
  - `rhel.6-x64`(.NET Core 2.0 veya sonraki sürümleri)
- Tizen (.NET Core 2.0 veya sonraki sürümler)
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-linux)

## <a name="macos-rids"></a>macOS IDA'ları

macOS ID'leri eski "OSX" markasını kullanır. Yalnızca ortak değerler listelenir. En son ve tam sürüm için depodaki [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) dosyasına `dotnet/runtime` bakın.

- Taşınabilir (.NET Core 2.0 veya sonraki sürümler)
  - `osx-x64`(Minimum işletim sistemi sürümü macOS 10.12 Sierra' dır)
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

Daha fazla bilgi için [bkz.](install/dependencies.md?pivots=os-macos)

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı T'leri](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
