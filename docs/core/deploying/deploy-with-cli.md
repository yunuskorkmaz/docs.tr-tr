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
ms.openlocfilehash: c8b4c60eb4ea09c8b10bd0b2fffc803d0a5fb6e0
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834290"
---
# <a name="publish-net-core-apps-with-the-cli"></a>CLı ile .NET Core uygulamaları yayımlayın

Bu makalede, .NET Core uygulamanızı komut satırından nasıl yayımlayacağınız gösterilmektedir. .NET Core, uygulamalarınızı yayımlamanın üç yolunu sağlar. Çerçeveye bağımlı dağıtım, yerel olarak yüklenmiş .NET Core çalışma zamanını kullanan platformlar arası bir. dll dosyası üretir. Çerçeveye bağımlı yürütülebilir, yerel olarak yüklenmiş .NET Core çalışma zamanını kullanan platforma özgü bir yürütülebilir dosya oluşturur. Kendi içinde bulunan yürütülebilir bir platforma özgü yürütülebilir dosya oluşturur ve .NET Core çalışma zamanının yerel bir kopyasını içerir.

Bu yayımlama modlarına genel bakış için bkz. [.NET Core uygulama dağıtımı](index.md).

CLı kullanımıyla ilgili bazı hızlı yardım mı arıyorsunuz? Aşağıdaki tabloda, uygulamanızı nasıl yayımlayacağınız hakkında bazı örnekler gösterilmektedir. Hedef Framework 'ü `-f <TFM>` parametresiyle veya proje dosyasını düzenleyerek belirtebilirsiniz. Daha fazla bilgi için bkz. [Yayımlama temelleri](#publishing-basics).

| Yayımlama modu | SDK sürümü | Komut |
| ------------ | ----------- | ------- |
| Çerçeveye bağımlı dağıtım | 2.x | `dotnet publish -c Release` |
| Çerçeveye bağımlı yürütülebilir dosya | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 * | `dotnet publish -c Release` |
| Kendi kendine kapsanan dağıtım      | 2,1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\* SDK sürüm 3,0 kullanılırken, temel `dotnet publish` komutu çalıştırılırken çerçeveye bağlı yürütülebilir dosya varsayılan yayımlama modudur. Bu, yalnızca proje **.net core 2,1** veya **.NET Core 3,0**' i hedefliyorsa geçerlidir.

## <a name="publishing-basics"></a>Yayımlama temelleri

Proje dosyasının `<TargetFramework>` ayarı, uygulamanızı yayımladığınızda varsayılan hedef çerçevesini belirtir. Hedef Framework 'ü geçerli bir [hedef çerçeve bilinen adı (tfd)](../../standard/frameworks.md)olarak değiştirebilirsiniz. Örneğin, projeniz `<TargetFramework>netcoreapp2.2</TargetFramework>` kullanıyorsa, .NET Core 2,2 ' i hedefleyen bir ikili oluşturulur. Bu ayarda belirtilen tfd, [`dotnet publish`](../tools/dotnet-publish.md) komutu tarafından kullanılan varsayılan hedeftir.

Birden fazla çerçeveyi hedeflemek istiyorsanız, `<TargetFrameworks>` ayarını noktalı virgülle ayırarak birden fazla TFı değeri olarak ayarlayabilirsiniz. @No__t-0 komutuyla çerçevelerden birini yayımlayabilirsiniz. Örneğin, `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` ' a sahipseniz ve `dotnet publish -f netcoreapp2.1` ' i çalıştırırsanız, .NET Core 2,1 ' i hedefleyen bir ikili oluşturulur.

Aksi belirtilmedikçe, [`dotnet publish`](../tools/dotnet-publish.md) komutunun çıkış dizini `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` ' dir. @No__t-2 parametresiyle değiştirilmediği takdirde varsayılan **derleme yapılandırma** modu **hata ayıklaması** olur. Örneğin, `dotnet publish -c Release -f netcoreapp2.1` `myfolder/bin/Release/netcoreapp2.1/publish/` ' e yayınlar.

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

Konsol şablonu tarafından oluşturulan `Program.cs` veya `Program.vb` dosyasının aşağıdaki şekilde değiştirilmesi gerekir:

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

Uygulamayı çalıştırdığınızda ([`dotnet run`](../tools/dotnet-run.md)) aşağıdaki çıktı görüntülenir:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Çerçeveye bağımlı dağıtım

.NET Core SDK 2. x CLı için, çerçeveye bağımlı dağıtım (FDD), temel `dotnet publish` komutu için varsayılan moddur.

Uygulamanızı FDD olarak yayımladığınızda, `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` klasöründe bir `<PROJECT-NAME>.dll` dosyası oluşturulur. Uygulamanızı çalıştırmak için çıkış klasörüne gidin ve `dotnet <PROJECT-NAME>.dll` komutunu kullanın.

Uygulamanız .NET Core 'un belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Uygulamanızı çalıştırmak istediğiniz makinede bu hedeflenen .NET Core çalışma zamanının olması gerekir. Örneğin, uygulamanız .NET Core 2,2 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 2,2 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

FDD yayımlama, uygulamayı çalıştıran sistemde kullanılabilir olan en son .NET Core güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Çerçeveye bağımlı yürütülebilir dosya

.NET Core SDK 3. x CLı için, çerçeveye bağımlı yürütülebilir dosya (FDE), temel `dotnet publish` komutu için varsayılan moddur. Geçerli işletim sistemini hedeflemek istediğiniz sürece herhangi bir parametreyi belirtmeniz gerekmez.

Bu modda, platformlar arası uygulamanızı barındırmak için platforma özgü bir yürütülebilir ana bilgisayar oluşturulur. FDD, `dotnet` komutu biçiminde bir konak gerektirdiğinden, bu mod FDD ile benzerdir. Ana bilgisayar yürütülebilir dosya adı her platform için farklılık gösterir ve `<PROJECT-FILE>.exe` ' a benzer bir şey olarak adlandırılır. Bu yürütülebilir dosyayı, uygulamayı çalıştırmak için yine de kabul edilebilir `dotnet <PROJECT-FILE>.dll` çağırmak yerine doğrudan çalıştırabilirsiniz.

Uygulamanız .NET Core 'un belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Uygulamanızı çalıştırmak istediğiniz makinede bu hedeflenen .NET Core çalışma zamanının olması gerekir. Örneğin, uygulamanız .NET Core 2,2 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 2,2 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

Bir FDE yayımlamak, uygulamayı çalıştıran sistemde kullanılabilir en son .NET Core güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

(Geçerli platformu hedeflediğinizde .NET Core 3. x hariç) yapmanız gerekir. bir FDE yayımlamak için aşağıdaki anahtarları `dotnet publish` komutuyla kullanın:

- `-r <RID>` Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained false` Bu anahtar, .NET Core SDK olarak yürütülebilir bir FDE oluşturmasını söyler.

@No__t-0 anahtarını her kullandığınızda, çıkış klasörü yolu şu şekilde değişir: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

[Örnek uygulamayı](#sample-app)kullanıyorsanız, `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false` ' i çalıştırın. Bu komut şu yürütülebiliri oluşturur: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> **Genelleştirme sabit modunu**etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Kendi kendine kapsanan dağıtım

Kendi içinde bir dağıtımı yayımladığınızda (SCD), .NET Core SDK platforma özgü bir yürütülebilir dosya oluşturur. Bir SCD yayımlamak, uygulamanızı çalıştırmak için gerekli tüm .NET Core dosyalarını içerir [, ancak .NET Core 'un yerel bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)içermez. Uygulamanın çalışması için önce bu bağımlılıkların sistemde mevcut olması gerekir.

Bir SCD yayımlandığında, en son kullanılabilir .NET Core güvenlik düzeltme ekine iletmeyen bir uygulama oluşturulur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET Core sürümünü seçme](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Bir SCD yayımlamak için aşağıdaki anahtarları `dotnet publish` komutuyla kullanmanız gerekir:

- `-r <RID>` Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained true` Bu anahtar, .NET Core SDK olarak yürütülebilir bir SCD oluşturmasını söyler.

> [!NOTE]
> **Genelleştirme sabit modunu**etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımına genel bakış](index.md)
- [.NET Core çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
