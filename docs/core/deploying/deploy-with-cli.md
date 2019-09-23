---
title: CLı ile .NET Core uygulamaları yayımlayın
description: .NET Core SDK komut satırı arabirimi (CLı) araçlarıyla .NET Core uygulaması yayımlamayı öğrenin.
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: 00064b774145e7267fe26b31ef3bba4d5271a5c3
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181512"
---
# <a name="publish-net-core-apps-with-the-cli"></a>CLı ile .NET Core uygulamaları yayımlayın

Bu makalede, .NET Core uygulamanızı komut satırından nasıl yayımlayacağınız gösterilmektedir. .NET Core, uygulamalarınızı yayımlamanın üç yolunu sağlar. Çerçeveye bağımlı dağıtım, yerel olarak yüklenmiş .NET Core çalışma zamanını kullanan platformlar arası bir. dll dosyası üretir. Çerçeveye bağımlı yürütülebilir, yerel olarak yüklenmiş .NET Core çalışma zamanını kullanan platforma özgü bir yürütülebilir dosya oluşturur. Kendi içinde bulunan yürütülebilir bir platforma özgü yürütülebilir dosya oluşturur ve .NET Core çalışma zamanının yerel bir kopyasını içerir.

Bu yayımlama modlarına genel bakış için bkz. [.NET Core uygulama dağıtımı](index.md).

CLı kullanımıyla ilgili bazı hızlı yardım mı arıyorsunuz? Aşağıdaki tabloda, uygulamanızı nasıl yayımlayacağınız hakkında bazı örnekler gösterilmektedir. Hedef çerçeveyi `-f <TFM>` parametresiyle veya proje dosyasını düzenleyerek belirtebilirsiniz. Daha fazla bilgi için bkz. [Yayımlama temelleri](#publishing-basics).

| Yayımlama modu | SDK sürümü | Komut |
| ------------ | ----------- | ------- |
| Framework bağımlı dağıtım | 2.x | `dotnet publish -c Release` |
| Çerçeveye bağımlı yürütülebilir dosya | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Kendi içinde dağıtım      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*SDK sürüm 3,0 kullanılırken, temel `dotnet publish` komut çalıştırılırken çerçeveye bağlı yürütülebilir dosya varsayılan yayımlama modudur. Bu, yalnızca proje **.net core 2,1** veya **.NET Core 3,0**' i hedefliyorsa geçerlidir.

## <a name="publishing-basics"></a>Yayımlama temelleri

Uygulamanızı yayımladığınızda proje dosyasının ayarıvarsayılanhedefçerçevesinibelirtir.`<TargetFramework>` Hedef Framework 'ü geçerli bir [hedef çerçeve bilinen adı (tfd)](../../standard/frameworks.md)olarak değiştirebilirsiniz. Örneğin, projeniz kullanıyorsa `<TargetFramework>netcoreapp2.2</TargetFramework>`, .NET Core 2,2 ' i hedefleyen bir ikili oluşturulur. Bu ayarda belirtilen tfd, [`dotnet publish`](../tools/dotnet-publish.md) komut tarafından kullanılan varsayılan hedeftir.

Birden fazla çerçeveyi hedeflemek istiyorsanız, `<TargetFrameworks>` ayarı noktalı virgülle ayırarak birden fazla TFI değeri olarak ayarlayabilirsiniz. `dotnet publish -f <TFM>` Komutuyla bir çerçeve yayımlayabilirsiniz. Örneğin, `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` ve çalıştırırsanız `dotnet publish -f netcoreapp2.1`, .NET Core 2,1 ' i hedefleyen bir ikili oluşturulur.

Aksi belirtilmedikçe, [`dotnet publish`](../tools/dotnet-publish.md) komutun çıkış dizini olur `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Varsayılan **derleme yapılandırma** modu, `-c` parametresiyle değiştirilmediği takdirde **hata ayıklaması** olur. Örneğin, ' `dotnet publish -c Release -f netcoreapp2.1` a `myfolder/bin/Release/netcoreapp2.1/publish/`yayınlar.

.NET Core SDK 3,0 kullanırsanız, .NET Core sürümlerini 2,1, 2,2 veya 3,0 ' i hedefleyen uygulamalar için varsayılan yayımlama modu, çerçeveye bağlı yürütülebilir dosyadır.

.NET Core SDK 2,1 kullanırsanız, .NET Core sürümleri 2,1 ' i hedefleyen uygulamalar için varsayılan yayımlama modu, 2,2 çerçeveye bağımlı dağıtımdır.

### <a name="native-dependencies"></a>Yerel bağımlılıklar

Uygulamanızda Yerel bağımlılıklar varsa, farklı bir işletim sisteminde çalışmayabilir. Örneğin, uygulamanız yerel Windows API 'sini kullanıyorsa macOS veya Linux üzerinde çalışmaz. Platforma özgü kod sağlamanız ve her platform için bir yürütülebilir dosya derlemeniz gerekir.

Ayrıca, başvurduğunuz bir kitaplığın yerel bağımlılığı varsa, uygulamanız her platformda çalışmayabilir. Ancak, başvurduğunuz bir NuGet paketi, sizin için gerekli yerel bağımlılıkları işlemek üzere platforma özgü sürümlere sahiptir.

Bir uygulamayı yerel bağımlılıklarla dağıtırken, yayımlamak istediğiniz hedef platformu belirtmek için `dotnet publish -r <RID>` anahtarını kullanmanız gerekebilir. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

Platforma özgü ikililer hakkında daha fazla bilgi, [çerçeveye bağımlı yürütülebilir](#framework-dependent-executable) ve [kendi kendine dahil edilen dağıtım](#self-contained-deployment) bölümlerinde ele alınmıştır.

## <a name="sample-app"></a>Örnek uygulama

Yayımlama komutlarını araştırmak için aşağıdaki uygulamayı kullanabilirsiniz. Uygulama, terminalinizde aşağıdaki komutlar çalıştırılarak oluşturulur:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Konsol şablonu `Program.vb` tarafından oluşturulan veyadosyanınaşağıdakişekildedeğiştirilmesigerekir:`Program.cs`

```csharp
using System;

namespace apptest1
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"));
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Uygulamayı çalıştırdığınızda, ([`dotnet run`](../tools/dotnet-run.md)) aşağıdaki çıktı görüntülenir:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Framework bağımlı dağıtım

.NET Core SDK 2. x CLI için, çerçeveye bağımlı dağıtım (FDD), temel `dotnet publish` komut için varsayılan moddur.

Uygulamanızı FDD olarak yayımladığınızda, `<PROJECT-NAME>.dll` `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` klasörde bir dosya oluşturulur. Uygulamanızı çalıştırmak için çıkış klasörüne gidin ve `dotnet <PROJECT-NAME>.dll` komutunu kullanın.

Uygulamanız .NET Core 'un belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Uygulamanızı çalıştırmak istediğiniz makinede bu hedeflenen .NET Core çalışma zamanının olması gerekir. Örneğin, uygulamanız .NET Core 2,2 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 2,2 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

FDD yayımlama, uygulamayı çalıştıran sistemde kullanılabilir olan en son .NET Core güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Çerçeveye bağımlı yürütülebilir dosya

.NET Core SDK 3. x CLI için, çerçeveye bağımlı yürütülebilir dosya (FDE), temel `dotnet publish` komut için varsayılan moddur. Geçerli işletim sistemini hedeflemek istediğiniz sürece herhangi bir parametreyi belirtmeniz gerekmez.

Bu modda, platformlar arası uygulamanızı barındırmak için platforma özgü bir yürütülebilir ana bilgisayar oluşturulur. FDD, `dotnet` komut biçiminde bir konak gerektirdiğinden, bu mod FDD ile benzerdir. Ana bilgisayar yürütülebilir dosya adı, platforma göre farklılık gösterir ve şuna benzer bir `<PROJECT-FILE>.exe`şey olarak adlandırılır. Bu yürütülebiliri çağırmak `dotnet <PROJECT-FILE>.dll` yerine, uygulamayı çalıştırmak için yine de kabul edilebilir bir yol değil doğrudan çalıştırabilirsiniz.

Uygulamanız .NET Core 'un belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Uygulamanızı çalıştırmak istediğiniz makinede bu hedeflenen .NET Core çalışma zamanının olması gerekir. Örneğin, uygulamanız .NET Core 2,2 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 2,2 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

Bir FDE yayımlamak, uygulamayı çalıştıran sistemde kullanılabilir en son .NET Core güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

(Geçerli platformu hedeflediğinizde .NET Core 3. x hariç) yapmanız gerekir. bir FDE yayımlamak için aşağıdaki anahtarları `dotnet publish` kullanın:

- `-r <RID>`Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained false`Bu anahtar, .NET Core SDK çalıştırılabilir bir FDE oluşturmasını söyler.

`-r` Anahtarı her kullandığınızda, çıkış klasörü yolu şu şekilde değişir:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

[Örnek uygulamayı](#sample-app)kullanıyorsanız, öğesini çalıştırın `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Bu komut aşağıdaki yürütülebiliri oluşturur:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> **Genelleştirme sabit modunu**etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Kendi içinde dağıtım

Kendi içinde bir dağıtımı yayımladığınızda (SCD), .NET Core SDK platforma özgü bir yürütülebilir dosya oluşturur. Bir SCD yayımlamak, uygulamanızı çalıştırmak için gerekli tüm .NET Core dosyalarını içerir [, ancak .NET Core 'un yerel bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)içermez. Uygulamanın çalışması için önce bu bağımlılıkların sistemde mevcut olması gerekir.

Bir SCD yayımlandığında, en son kullanılabilir .NET Core güvenlik düzeltme ekine iletmeyen bir uygulama oluşturulur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Bir SCD yayımlamak için `dotnet publish` komutuyla aşağıdaki anahtarları kullanmanız gerekir:

- `-r <RID>`Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained true`Bu anahtar, .NET Core SDK çalıştırılabilir bir SCD oluşturmasını söyler.

> [!NOTE]
> **Genelleştirme sabit modunu**etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımına genel bakış](index.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
