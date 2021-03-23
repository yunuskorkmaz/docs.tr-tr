---
title: .NET CLı ile uygulama yayımlama
description: .Net CLı komutlarını kullanarak bir .NET uygulaması yayımlamayı öğrenin.
author: adegeo
ms.author: adegeo
ms.date: 02/05/2021
dev_langs:
- csharp
- vb
ms.openlocfilehash: 65c9c4929d9ed8ab4005677fbcb0a3745ed14190
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104874309"
---
# <a name="publish-net-apps-with-the-net-cli"></a>.Net CLı ile .NET uygulamaları yayımlama

Bu makalede, .NET uygulamanızı komut satırından nasıl yayımlayacağınız gösterilmektedir. .NET, uygulamalarınızı yayımlamanın üç yolunu sağlar. Çerçeveye bağımlı dağıtım, yerel olarak yüklenmiş .NET çalışma zamanını kullanan platformlar arası bir. dll dosyası üretir. Çerçeveye bağımlı yürütülebilir, yerel olarak yüklenmiş .NET çalışma zamanını kullanan platforma özgü bir yürütülebilir dosya oluşturur. Kendi içinde bulunan yürütülebilir bir platforma özgü yürütülebilir dosya oluşturur ve .NET çalışma zamanının yerel bir kopyasını içerir.

Bu yayımlama modlarına genel bakış için bkz. [.NET uygulama dağıtımı](index.md).

CLı kullanımıyla ilgili bazı hızlı yardım mı arıyorsunuz? Aşağıdaki tabloda, uygulamanızı nasıl yayımlayacağınız hakkında bazı örnekler gösterilmektedir. Hedef çerçeveyi `-f <TFM>` parametresiyle veya proje dosyasını düzenleyerek belirtebilirsiniz. Daha fazla bilgi için bkz. [Yayımlama temelleri](#publishing-basics).

| Yayımlama modu                   | SDK Sürümü | Komut                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| [Çerçeveye bağımlı dağıtım](#framework-dependent-deployment) | 2.1         | `dotnet publish -c Release`                                 |
|                                | 3,1         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | 5.0         | `dotnet publish -c Release -p:UseAppHost=false`             |
| [Çerçeveye bağımlı yürütülebilir dosya](#framework-dependent-executable) | 3,1         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
| [Kendi kendine kapsanan dağıtım](#self-contained-deployment)      | 2.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 3,1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained true`  |

\***SDK sürüm 3,1** veya üzeri kullanılırken, temel komut çalıştırılırken çerçeveye bağımlı yürütülebilir dosya varsayılan yayımlama modudur `dotnet publish` .

> [!NOTE]
> `-c Release`Parametre gerekli değil. Uygulamanızın **yayın** yapısını yayımlamak için bir anımsatıcı olarak sunulur.

## <a name="publishing-basics"></a>Yayımlama temelleri

`<TargetFramework>`Uygulamanızı yayımladığınızda proje dosyasının ayarı varsayılan hedef çerçevesini belirtir. Hedef Framework 'ü geçerli bir [hedef çerçeve bilinen adı (tfd)](../../standard/frameworks.md)olarak değiştirebilirsiniz. Örneğin, projeniz kullanıyorsa `<TargetFramework>netcoreapp2.1</TargetFramework>` , .NET Core 2,1 ' i hedefleyen bir ikili oluşturulur. Bu ayarda belirtilen tfd, komut tarafından kullanılan varsayılan hedeftir [`dotnet publish`](../tools/dotnet-publish.md) .

Birden fazla çerçeveyi hedeflemek istiyorsanız, `<TargetFrameworks>` ayarı noktalı virgülle ayırarak birden çok TFı değeri olarak ayarlayabilirsiniz. Uygulamanızı yapılandırdığınızda, her hedef çerçeve için bir derleme oluşturulur. Ancak, uygulamanızı yayımladığınızda, komutunu kullanarak hedef Framework 'ü belirtmeniz gerekir `dotnet publish -f <TFM>` .

Aksi belirtilmedikçe, komutun çıkış dizini [`dotnet publish`](../tools/dotnet-publish.md) olur `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` . Varsayılan **derleme yapılandırma** modu, parametresiyle değiştirilmediği takdirde **hata ayıklaması** olur `-c` . Örneğin, ' a `dotnet publish -c Release -f netcoreapp2.1` yayınlar `./bin/Release/netcoreapp2.1/publish/` .

.NET Core SDK 3,1 veya sonraki bir sürümü kullanıyorsanız, varsayılan yayımlama modu çerçeveye bağlı _yürütülebilir dosyadır_.

.NET Core SDK 2,1 kullanıyorsanız, varsayılan yayımlama modu çerçeveye bağlı _dağıtımdır_.

### <a name="native-dependencies"></a>Yerel bağımlılıklar

Uygulamanızda Yerel bağımlılıklar varsa, farklı bir işletim sisteminde çalışmayabilir. Örneğin, uygulamanız yerel Windows API 'sini kullanıyorsa macOS veya Linux üzerinde çalışmaz. Platforma özgü kod sağlamanız ve her platform için bir yürütülebilir dosya derlemeniz gerekir.

Ayrıca, başvurduğunuz bir kitaplığın yerel bağımlılığı varsa, uygulamanız her platformda çalışmayabilir. Ancak, başvurduğunuz bir NuGet paketi, sizin için gerekli yerel bağımlılıkları işlemek üzere platforma özgü sürümlere sahiptir.

Bir uygulamayı yerel bağımlılıklarla dağıtırken, `dotnet publish -r <RID>` yayımlamak istediğiniz hedef platformu belirtmek için anahtarını kullanmanız gerekebilir. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

Platforma özgü ikililer hakkında daha fazla bilgi, [çerçeveye bağımlı yürütülebilir](#framework-dependent-executable) ve [kendi kendine dahil edilen dağıtım](#self-contained-deployment) bölümlerinde ele alınmıştır.

## <a name="sample-app"></a>Örnek uygulama

Yayımlama komutlarını araştırmak için aşağıdaki uygulamayı kullanabilirsiniz. Uygulama, terminalinizde aşağıdaki komutlar çalıştırılarak oluşturulur:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs` `Program.vb` Konsol şablonu tarafından oluşturulan veya dosyanın aşağıdaki şekilde değiştirilmesi gerekir:

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
Module Program
    Sub Main(args As String())
        Console.WriteLine(Figgle.FiggleFonts.Standard.Render("Hello, World!"))
    End Sub
End Module
```

Uygulamayı çalıştırdığınızda [`dotnet run`](../tools/dotnet-run.md) , () aşağıdaki çıktı görüntülenir:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Çerçeveye bağımlı dağıtım

.NET Core 2,1 SDK CLı için, çerçeveye bağımlı dağıtım (FDD), temel komut için varsayılan moddur `dotnet publish` . Daha yeni SDK 'larda, [çerçeveye bağımlı yürütülebilir dosya](#framework-dependent-executable) varsayılandır.

Uygulamanızı FDD olarak yayımladığınızda, `<PROJECT-NAME>.dll` klasörde bir dosya oluşturulur `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` . Uygulamanızı çalıştırmak için çıkış klasörüne gidin ve `dotnet <PROJECT-NAME>.dll` komutunu kullanın.

Uygulamanız .NET 'in belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Bu hedeflenen .NET çalışma zamanının, uygulamanızın çalıştırıldığı herhangi bir makinede olması gerekir. Örneğin, uygulamanız .NET Core 3,1 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 3,1 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

FDD yayımlamak, uygulamayı çalıştıran sistemde bulunan en son .NET güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

| Yayımlama modu                   | SDK Sürümü | Komut                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| Çerçeveye bağımlı dağıtım | 2.1         | `dotnet publish -c Release`                                 |
|                                | 3,1         | `dotnet publish -c Release -p:UseAppHost=false`             |
|                                | 5.0         | `dotnet publish -c Release -p:UseAppHost=false`             |

## <a name="framework-dependent-executable"></a>Çerçeveye bağımlı yürütülebilir dosya

.NET 5 (ve .NET Core 3,1) SDK CLı için, çerçeveye bağımlı yürütülebilir dosya (FDE), temel komut için varsayılan moddur `dotnet publish` . Geçerli işletim sistemini hedeflemek istediğiniz sürece herhangi bir parametreyi belirtmeniz gerekmez.

Bu modda, platformlar arası uygulamanızı barındırmak için platforma özgü bir yürütülebilir ana bilgisayar oluşturulur. FDD, komut biçiminde bir konak gerektirdiğinden, bu mod FDD ile benzerdir `dotnet` . Ana bilgisayar yürütülebilir dosya adı, platforma göre farklılık gösterir ve şuna benzer bir şey olarak adlandırılır `<PROJECT-FILE>.exe` . Bu yürütülebilir dosyayı çağırmak yerine doğrudan çalıştırabilirsiniz, bu da `dotnet <PROJECT-FILE>.dll` uygulamayı çalıştırmak için yine de kabul edilebilir bir yoldur.

Uygulamanız .NET 'in belirli bir sürümünü hedefleyecek şekilde yapılandırılmıştır. Bu hedeflenen .NET çalışma zamanının, uygulamanızın çalıştırıldığı herhangi bir makinede olması gerekir. Örneğin, uygulamanız .NET Core 3,1 hedefliyorsa, uygulamanızın üzerinde çalıştığı tüm makineler .NET Core 3,1 çalışma zamanının yüklü olması gerekir. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, varsayılan hedef Framework 'ü değiştirmek veya birden fazla çerçeveyi hedeflemek için proje dosyanızı düzenleyebilirsiniz.

Bir FDE yayımlamak, uygulamayı çalıştıran sistemde bulunan en son .NET güvenlik düzeltme ekine otomatik olarak bağlanan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET sürümünü seçme](../versions/selection.md#framework-dependent-apps-roll-forward).

.NET 2,1 için, `dotnet publish` BIR FDE yayımlamak için komutuyla aşağıdaki anahtarları kullanmanız gerekir:

- `-r <RID>` Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained false` Bu anahtar, anahtarın varsayılan davranışını devre dışı bırakır, bu, `-r` kendinden bağımsız bir dağıtım (SCD) oluşturmaktır. Bu anahtar bir FDE oluşturur.

| Yayımlama modu                   | SDK Sürümü | Komut                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| Çerçeveye bağımlı yürütülebilir dosya | 3,1         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained false`<br>`dotnet publish -c Release` |

Anahtarı her kullandığınızda `-r` , çıkış klasörü yolu şu şekilde değişir: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

[Örnek uygulamayı](#sample-app)kullanıyorsanız, öğesini çalıştırın `dotnet publish -f net5.0 -r win10-x64 --self-contained false` . Bu komut aşağıdaki yürütülebiliri oluşturur: `./bin/Debug/net5.0/win10-x64/publish/apptest1.exe`

> [!NOTE]
> **Genelleştirme sabit modunu** etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).

## <a name="self-contained-deployment"></a>Kendi kendine kapsanan dağıtım

Kendi kendine içerilen bir dağıtımı yayımladığınızda (SCD), .NET SDK, platforma özgü bir yürütülebilir dosya oluşturur. Bir SCD yayımlamak, uygulamanızı çalıştırmak için gerekli tüm .NET dosyalarını içerir, ancak bu, [.net 'in yerel bağımlılıklarını](https://github.com/dotnet/core/blob/main/Documentation/prereqs.md)içermez. Uygulamanın çalışması için önce bu bağımlılıkların sistemde mevcut olması gerekir.

Bir SCD yayımlandığında, en son kullanılabilir .NET güvenlik düzeltme ekine geri dönerek bir uygulama oluşturulur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanılacak .NET sürümünü seçme](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

`dotnet publish`BIR SCD yayımlamak için komutuyla aşağıdaki anahtarları kullanmanız gerekir:

- `-r <RID>` Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için bkz. [Runtime Identifier (RID) Catalog](../rid-catalog.md).

- `--self-contained true` Bu anahtar, .NET Core SDK çalıştırılabilir bir SCD oluşturmasını söyler.

| Yayımlama modu                   | SDK Sürümü | Komut                                                     |
|--------------------------------|-------------|-------------------------------------------------------------|
| Kendi kendine kapsanan dağıtım      | 2.1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 3,1         | `dotnet publish -c Release -r <RID> --self-contained true`  |
|                                | 5.0         | `dotnet publish -c Release -r <RID> --self-contained true`  |

> [!NOTE]
> **Genelleştirme sabit modunu** etkinleştirerek, dağıtımınızın toplam boyutunu azaltabilirsiniz. Bu mod, genel olarak kullanmayan ve [sabit kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)biçimlendirme kurallarını, büyük/küçük harf kurallarını ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için yararlıdır. **Genelleştirme sabit modu** ve nasıl etkinleştirileceği hakkında daha fazla bilgi için bkz. [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/main/docs/design/features/globalization-invariant-mode.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uygulama dağıtımına genel bakış](index.md)
- [.NET çalışma zamanı tanımlayıcısı (RID) kataloğu](../rid-catalog.md)
