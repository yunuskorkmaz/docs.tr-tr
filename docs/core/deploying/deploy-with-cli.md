---
title: Yayımlama .NET Core CLI ile uygulamaları
description: .NET Core SDK komut satırı arabirimi (CLI) araçları ile .NET Core uygulaması yayımlama hakkında bilgi alın.
author: thraka
ms.author: adegeo
ms.date: 01/16/2019
dev_langs:
- csharp
- vb
ms.custom: seodec18
ms.openlocfilehash: c71ab84cfd97e65f5e30bd5e1ff651f8e0c2d700
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132086"
---
# <a name="publish-net-core-apps-with-the-cli"></a>Yayımlama .NET Core CLI ile uygulamaları

Bu makalede, komut satırından .NET Core uygulamanızı nasıl yayımlayabilirsiniz gösterilmektedir. .NET core, uygulamalarınızı yayımlamak için üç yol sunar. Framework bağımlı dağıtım, yerel olarak yüklü .NET Core çalışma zamanı kullanan bir platformlar arası .dll dosyası oluşturur. Framework bağımlı yürütülebilir dosyayı yerel olarak yüklü .NET Core çalışma zamanı kullanan bir platforma özgü çalıştırılabilir dosyası oluşturur. Kendi içinde yürütülebilir, platforma özgü çalıştırılabilir dosyası oluşturur ve .NET Core çalışma zamanı yerel bir kopyasını içerir.

Bu yayımlama modu genel bakış için bkz. [.NET Core uygulaması dağıtımını](index.md).

Hızlı Yardım için CLI'yı kullanarak istiyorsunuz? Aşağıdaki tablo bazı örnekler nasıl uygulama yayımlanacağı gösterilmektedir. Hedef çerçeve ile belirttiğiniz `-f <TFM>` parametresi ya da proje dosyasını düzenleyerek. Daha fazla bilgi için [temelleri yayımlama](#publishing-basics).

| Yayımlama modu | SDK sürümü | Komut |
| ------------ | ----------- | ------- |
| Framework bağımlı dağıtım | 2.x | `dotnet publish -c Release` |
| Framework bağımlı yürütülebilir dosya | 2.2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Kendi içinde dağıtım      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2.2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3.0 | `dotnet publish -c Release -r <RID> --self-contained true` |

> [!IMPORTANT]
> \*SDK'sı sürüm 3.0 kullanırken, framework bağımlı yürütülebilir varsayılan yayımlama modu temel çalıştırırken budur `dotnet publish` komutu. Bu yalnızca projelerine hedefleyen yöneliktir **.NET Core 2.1** veya **.NET Core 3.0**.

## <a name="publishing-basics"></a>Yayımlama temelleri

`<TargetFramework>` Ayar proje dosyasının, uygulamanızı yayımladığınızda, varsayılan hedef Framework'ü belirtir. Hedef çerçeve için herhangi bir geçerli değiştirebilirsiniz [hedef çerçeve adı (TFM)](../../standard/frameworks.md). Örneğin, projeniz kullanıyorsa `<TargetFramework>netcoreapp2.2</TargetFramework>`, .NET Core 2.2 hedefleyen bir ikili oluşturulur. Bu ayarda belirttiğiniz TFM tarafından kullanılan varsayılan hedef olduğunu [ `dotnet publish` ](../tools/dotnet-publish.md) komutu.

Birden fazla framework hedeflemek istiyorsanız, ayarlayabileceğiniz `<TargetFrameworks>` birden fazla noktalı virgülle ayrılmış TFM değer ayarlanamadı. İle altyapılarından birini yayımlayabilirsiniz `dotnet publish -f <TFM>` komutu. Örneğin, `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` çalıştırıp `dotnet publish -f netcoreapp2.1`, .NET Core 2.1'i hedefleyen bir ikili oluşturulur.

Sürece ayarlanmış Aksi takdirde çıktı dizinine [ `dotnet publish` ](../tools/dotnet-publish.md) komutu `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`. Varsayılan **derleme Yapılandırması** modu **hata ayıklama** ile değiştirmediyse `-c` parametresi. Örneğin, `dotnet publish -c Release -f netcoreapp2.1` yayımlar `myfolder/bin/Release/netcoreapp2.1/publish/`.

.NET Core SDK 3.0 kullanıyorsanız, varsayılan mod uygulamaları .NET Core sürümlerini hedefleyen 2.1 veya 2.2 3.0 framework bağımlı yürütülebilir dosya olduğu için yayımlayın.

.NET Core SDK 2.1 kullanırsanız, varsayılan modu .NET Core sürümlerini hedefleyen 2.1 2.2 framework bağımlı dağıtım olan uygulamalar için yayımlayın.

### <a name="native-dependencies"></a>Yerel bağımlılıkları

Uygulamanızı yerel bağımlılıkları varsa, farklı bir işletim sisteminde çalışmayabilir. Örneğin, uygulamanız yerel Windows API kullanıyorsa, macOS veya Linux üzerinde çalışmaz. Platforma özgü kod sağlar ve her platform için bir yürütülebilir dosya derlemek gerekir.

Göz önünde bulundurun, başvurulan kitaplık yerel bağımlılığı varsa, ayrıca, uygulamanızı her platformda çalışabilir. Ancak, sizin için gerekli yerel bağımlılıkları işlemek için platforma özgü sürümlerinde, başvuran bir NuGet paketi eklenmiştir mümkündür.

Yerel bağımlılıkları olan bir uygulamayı dağıtırken kullanmanız gerekebilir `dotnet publish -r <RID>` geçme için yayımlamak istediğiniz hedef platform belirtin. Çalışma zamanı tanımlayıcılarının bir listesi için bkz. [çalışma zamanı tanımlayıcı (RID) katalog](../rid-catalog.md).

Platforma özgü ikili dosyaları hakkında daha fazla bilgi ele alınmıştır [Framework bağımlı yürütülebilir](#framework-dependent-executable) ve [müstakil dağıtım](#self-contained-deployment) bölümler.

## <a name="sample-app"></a>Örnek uygulama

Aşağıdaki uygulama yayımlama komutları keşfetmek için kullanabilirsiniz. Uygulama, terminalde aşağıdaki komutları çalıştırarak oluşturulur:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

`Program.cs` Veya `Program.vb` konsol şablon tarafından oluşturulan dosya şu şekilde değiştirilmesi gerekir:

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

Uygulamayı çalıştırdığınızda ([`dotnet run`](../tools/dotnet-run.md)), aşağıdaki çıktıyı görüntülenir:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Framework bağımlı dağıtım

.NET Core SDK 2.x CLI, framework bağımlı dağıtım (FDD) olan temel için varsayılan modu `dotnet publish` komutu.

Uygulamanızla bir FDD yayımladığınızda bir `<PROJECT-NAME>.dll` dosyasının oluşturulduğunu `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` klasör. Uygulamanızı çalıştırmak için çıkış klasörüne gidin ve kullanmak `dotnet <PROJECT-NAME>.dll` komutu.

Uygulamanızı .NET Core belirli bir sürümünü hedefleyecek şekilde yapılandırılır. .NET Core çalışma zamanı, uygulamanızı çalıştırmak için istediğiniz makinede olması gereken hedef. Örneğin, uygulamanız .NET Core 2.2 hedefliyorsa, uygulamanızın üzerinde çalışacağı herhangi bir makineye yüklü olan .NET Core 2.2 çalışma zamanı olması gerekir. Bölümünde belirtildiği [temelleri yayımlama](#publishing-basics) bölümünde, varsayılan hedef Framework'ü değiştirmek veya birden fazla Framework'ü hedefleyen için proje dosyanızı düzenleyebilirsiniz.

Bir FDD yayımlama bir uygulama, otomatik olarak yapar İleri en son .NET Core güvenlik düzeltme eki uygulama çalışır sistemde kullanılabilir oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanmak için .NET Core sürümü](../versions/selection.md#framework-dependent-apps-roll-forward).

## <a name="framework-dependent-executable"></a>Framework bağımlı yürütülebilir dosya

.NET Core SDK'sı 3.x CLI, framework bağımlı yürütülebilir dosyası (FDE) varsayılan modu temel `dotnet publish` komutu. Geçerli işletim sistemi hedeflemek istediğiniz sürece herhangi bir parametre belirtmeniz gerekmez.

Bu modda, platforma özgü yürütülebilir bir konak, platformlar arası uygulamanızı barındırmak için oluşturulur. FDD şeklinde bir ana bilgisayar gerektirdiğinden bu mod için FDD benzer `dotnet` komutu. Konak yürütülebilir dosya adı platforma göre değişiklik gösterir ve aşağıdakine benzer adlı `<PROJECT-FILE>.exe`. Doğrudan çağırmak yerine bu yürütülebilir dosyayı çalıştırarak `dotnet <PROJECT-FILE>.dll` olduğu yine de uygulamayı çalıştırmak için kabul edilebilir bir şekilde.

Uygulamanızı .NET Core belirli bir sürümünü hedefleyecek şekilde yapılandırılır. .NET Core çalışma zamanı, uygulamanızı çalıştırmak için istediğiniz makinede olması gereken hedef. Örneğin, uygulamanız .NET Core 2.2 hedefliyorsa, uygulamanızın üzerinde çalışacağı herhangi bir makineye yüklü olan .NET Core 2.2 çalışma zamanı olması gerekir. Bölümünde belirtildiği [temelleri yayımlama](#publishing-basics) bölümünde, varsayılan hedef Framework'ü değiştirmek veya birden fazla Framework'ü hedefleyen için proje dosyanızı düzenleyebilirsiniz.

Bir FDE yayımlama bir uygulama, otomatik olarak yapar İleri en son .NET Core güvenlik düzeltme eki uygulama çalışır sistemde kullanılabilir oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanmak için .NET Core sürümü](../versions/selection.md#framework-dependent-apps-roll-forward).

Gerekir (.NET Core hariç geçerli platform hedeflediğinizde 3.x) ile aşağıdaki anahtarları kullanarak `dotnet publish` bir FDE yayımlamak için komutu:

- `-r <RID>`
  Bu anahtar, hedef platform belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının bir listesi için bkz. [çalışma zamanı tanımlayıcı (RID) katalog](../rid-catalog.md).

- `--self-contained false` Bu anahtar, yürütülebilir bir FDE olarak oluşturmak için .NET Core SDK'sı söyler.

Herhangi bir zamanda kullandığınız `-r` anahtarı, çıkış klasörü yolu değişir: `./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

Kullanırsanız [örnek uygulamayı](#sample-app)çalıştırın `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`. Bu komut aşağıdaki oluşturur çalıştırılabilir: `./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> Etkinleştirerek dağıtımınızın toplam boyutunu azaltabilirsiniz **Genelleştirme sabit modu**. Bu mod, genel olarak duyarlı değildir ve biçimlendirme kuralları, büyük/küçük harf kuralları ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için kullanılabilir [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture). Hakkında daha fazla bilgi için **Genelleştirme sabit modu** ve etkinleştirmek için bkz [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Kendi içinde dağıtım

Kendi içinde bir dağıtım (SCD) yayımladığınızda, .NET Core SDK'sını bir platforma özgü yürütülebilir dosya oluşturur. Bir SCD yayımlama, uygulamanızı çalıştırmak için gerekli tüm .NET Core dosyaları içerir, ancak bunu içermez [yerel .NET Core bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md). Bu bağımlılıklar, uygulama çalışmadan önce sistemde bulunmalıdır.

Bir SCD yayımlama, en son kullanılabilir .NET Core güvenlik düzeltme eki sarma olmayan bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için bkz. [kullanmak için .NET Core sürümü](../versions/selection.md#self-contained-deployments-include-the-selected-runtime).

Aşağıdaki anahtarlar ile kullanmalısınız `dotnet publish` bir SCD yayımlamak için komutu:

- `-r <RID>`
  Bu anahtar, hedef platform belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının bir listesi için bkz. [çalışma zamanı tanımlayıcı (RID) katalog](../rid-catalog.md).

- `--self-contained true` Bu anahtar, yürütülebilir bir SCD olarak oluşturmak için .NET Core SDK'sı söyler.

> [!NOTE]
> Etkinleştirerek dağıtımınızın toplam boyutunu azaltabilirsiniz **Genelleştirme sabit modu**. Bu mod, genel olarak duyarlı değildir ve biçimlendirme kuralları, büyük/küçük harf kuralları ve dize karşılaştırma ve sıralama düzenini kullanabilen uygulamalar için kullanılabilir [sabit kültür](xref:System.Globalization.CultureInfo.InvariantCulture). Hakkında daha fazla bilgi için **Genelleştirme sabit modu** ve etkinleştirmek için bkz [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET core uygulama dağıtımına genel bakış](index.md)
- [.NET core çalışma zamanı tanımlayıcı (RID) Kataloğu](../rid-catalog.md)
