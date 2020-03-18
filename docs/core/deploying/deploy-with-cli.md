---
title: .NET Core CLI ile uygulama yayınlama
description: .NET Core CLI komutlarını kullanarak bir .NET Core uygulaması yayınlamayı öğrenin.
author: thraka
ms.author: adegeo
ms.date: 12/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: f4c2a4ccf551c53e4aa4e125cb5720d6f1cc9601
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399072"
---
# <a name="publish-net-core-apps-with-the-net-core-cli"></a>.NET Core CLI ile .NET Core uygulamalarını yayımla

Bu makalede, .NET Core uygulamanızı komut satırından nasıl yayımlayacağınızı gösterin. .NET Core, uygulamalarınızı yayınlamak için üç yol sağlar. Çerçeveye bağımlı dağıtım, yerel olarak yüklenen .NET Core çalışma süresini kullanan bir çapraz platform .dll dosyası üretir. Çerçeveye bağımlı yürütülebilir, yerel olarak yüklenen .NET Core çalışma süresini kullanan platforma özgü bir yürütülebilir üretir. Bağımsız yürütülebilir, platforma özgü bir çalıştırılabilir üretir ve .NET Core çalışma zamanının yerel bir kopyasını içerir.

Bu yayımlama modlarına genel bir bakış için [bkz.](index.md)

CLI kullanarak bazı hızlı yardım mı arıyorsunuz? Aşağıdaki tabloda uygulamanızın nasıl yayımlandırılabildiğini gösteren bazı örnekler gösterilmektedir. `-f <TFM>` Parametre ile veya proje dosyasını düzenleyerek hedef çerçeveyi belirtebilirsiniz. Daha fazla bilgi için [yayımlama temellerine](#publishing-basics)bakın.

| Yayımlama Modu | SDK Sürümü | Komut |
| ------------ | ----------- | ------- |
| Çerçeveye bağımlı dağıtım | 2.x | `dotnet publish -c Release` |
| Çerçeveye bağımlı yürütülebilir | 2,2 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3,0 | `dotnet publish -c Release -r <RID> --self-contained false` |
|                                | 3.0* | `dotnet publish -c Release` |
| Bağımsız dağıtım      | 2.1 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 2,2 | `dotnet publish -c Release -r <RID> --self-contained true` |
|                                | 3,0 | `dotnet publish -c Release -r <RID> --self-contained true` |

\*SDK sürüm 3.0 kullanırken, çerçeveye bağımlı yürütülebilir temel `dotnet publish` komutu çalıştırırken varsayılan yayımlama modudur. Bu yalnızca proje **.NET Core 2.1 veya .NET Core 3.0'ı** hedefaldığında geçerlidir. **.NET Core 3.0**

## <a name="publishing-basics"></a>Yayımlama temelleri

Proje `<TargetFramework>` dosyasının ayarı, uygulamanızı yayımladığınızda varsayılan hedef çerçeveyi belirtir. Hedef çerçeveyi geçerli bir Hedef Çerçeve Takma Adıyla [(TFM)](../../standard/frameworks.md)değiştirebilirsiniz. Örneğin, projeniz kullanıyorsa `<TargetFramework>netcoreapp2.2</TargetFramework>`,.NET Core 2.2'yi hedefleyen bir ikili oluşturulur. Bu ayarda belirtilen TFM [`dotnet publish`](../tools/dotnet-publish.md) komutu tarafından kullanılan varsayılan hedeftir.

Birden fazla çerçeve hedeflemek istiyorsanız, `<TargetFrameworks>` ayarı bir yarı nokta nokta ile ayrılmış birden fazla TFM değerine ayarlayabilirsiniz. `dotnet publish -f <TFM>` Komutla çerçevelerden birini yayımlayabilirsiniz. Örneğin, .NET `<TargetFrameworks>netcoreapp2.1;netcoreapp2.2</TargetFrameworks>` Core `dotnet publish -f netcoreapp2.1`2.1'i hedefleyen bir ikili oluşturduysanız ve çalıştırın.

Aksi ayarlmadıkça, komutun [`dotnet publish`](../tools/dotnet-publish.md) çıktı `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/`dizini . Varsayılan **BUILD-CONFIGURATION** modu `-c` parametre ile değiştirilmediği sürece **Hata Ayıklama'dır.** Örneğin, `dotnet publish -c Release -f netcoreapp2.1` '' `myfolder/bin/Release/netcoreapp2.1/publish/`için yayımlar.

.NET Core SDK 3.0 veya sonraki sürümlerini kullanıyorsanız, .NET Core sürümleri 2.1, 2.2, 3.0 veya daha sonraki bir sürümü hedefleyen uygulamalar için varsayılan yayımlama modu çerçeveye bağlı yürütülebilir.

.NET Core SDK 2.1 kullanıyorsanız, .NET Core sürümleri 2.1 ve 2.2'yi hedefleyen uygulamalar için varsayılan yayımlama modu çerçeveye bağımlı dağıtımdır.

### <a name="native-dependencies"></a>Yerel bağımlılıklar

Uygulamanızın yerel bağımlılıkları varsa, farklı bir işletim sisteminde çalışmayabilir. Örneğin, uygulamanız yerel Windows API'sını kullanıyorsa, macOS veya Linux'ta çalışmaz. Platforma özgü kod sağlamanız ve her platform için bir yürütülebilir derlemeniz gerekir.

Ayrıca, başvurur ettiğiniz bir kitaplığın yerel bir bağımlılığı varsa, uygulamanızın her platformda çalışmayabileceğini de göz önünde bulundurun. Ancak, başvurduğunuz bir NuGet paketinin sizin için gerekli yerel bağımlılıkları işlemek için platforma özgü sürümler eklenmiş olması mümkündür.

Yerel bağımlılıkları olan bir uygulamayı dağıtırken, yayımlamak istediğiniz hedef platformu belirtmek için `dotnet publish -r <RID>` anahtarı kullanmanız gerekebilir. Çalışma zamanı tanımlayıcılarının listesi için [Runtime Tanımlayıcı (RID) kataloğuna](../rid-catalog.md)bakın.

Platforma özgü ikililer hakkında daha fazla [bilgi, Framework'e bağlı yürütülebilir](#framework-dependent-executable) ve [bağımsız dağıtım](#self-contained-deployment) bölümlerinde yer almaktadır.

## <a name="sample-app"></a>Örnek uygulama

Yayımlama komutlarını keşfetmek için aşağıdaki uygulamayı kullanabilirsiniz. Uygulama, terminalinizde aşağıdaki komutları çalıştırarak oluşturulur:

```dotnetcli
mkdir apptest1
cd apptest1
dotnet new console
dotnet add package Figgle
```

Konsol `Program.cs` `Program.vb` şablonu tarafından oluşturulan veya dosyanın aşağıdakiyle değiştirilmesi gerekir:

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

Uygulamayı çalıştırdığınızda[`dotnet run`](../tools/dotnet-run.md)( ), aşağıdaki çıktı görüntülenir:

```terminal
  _   _      _ _         __        __         _     _ _
 | | | | ___| | | ___    \ \      / /__  _ __| | __| | |
 | |_| |/ _ \ | |/ _ \    \ \ /\ / / _ \| '__| |/ _` | |
 |  _  |  __/ | | (_) |    \ V  V / (_) | |  | | (_| |_|
 |_| |_|\___|_|_|\___( )    \_/\_/ \___/|_|  |_|\__,_(_)
                     |/
```

## <a name="framework-dependent-deployment"></a>Çerçeveye bağımlı dağıtım

.NET Core SDK 2.x CLI için, çerçeveye bağımlı dağıtım (FDD) temel `dotnet publish` komutiçin varsayılan moddur.

Uygulamanızı FDD olarak `<PROJECT-NAME>.dll` `./bin/<BUILD-CONFIGURATION>/<TFM>/publish/` yayımladığınızda, klasörde bir dosya oluşturulur. Uygulamanızı çalıştırmak için çıktı klasörüne gidin `dotnet <PROJECT-NAME>.dll` ve komutu kullanın.

Uygulamanız .NET Core'un belirli bir sürümünü hedef almak üzere yapılandırılmıştır. Hedeflenen .NET Core çalışma süresi, uygulamanızın çalıştığı herhangi bir makinede olması gerekir. Örneğin, uygulamanız .NET Core 2.2'yi hedefliyorsa, uygulamanızın çalıştığı herhangi bir makinede .NET Core 2.2 çalışma zamanı yüklü olmalıdır. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, proje dosyanızı varsayılan hedef çerçeveyi değiştirmek veya birden fazla çerçeveyi hedeflemek için değiştirebilirsiniz.

FDD yayımlamak, uygulamayı çalıştıran sistemde bulunan en son .NET Core güvenlik yamasına otomatik olarak ileten bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için [kullanmak üzere .NET Core sürümünü seçin'e](../versions/selection.md#framework-dependent-apps-roll-forward)bakın.

## <a name="framework-dependent-executable"></a>Çerçeveye bağımlı yürütülebilir

.NET Core SDK 3.x CLI için, çerçeveye bağımlı yürütülebilir (FDE) temel `dotnet publish` komutiçin varsayılan moddur. Geçerli işletim sistemini hedeflemek istediğiniz sürece başka parametreler belirtmeniz gerekmez.

Bu modda, platforma özel bir çalıştırılabilir ana bilgisayar, çapraz platform uygulamanızı barındırmak için oluşturulur. FDD `dotnet` komut şeklinde bir ana bilgisayar gerektirdiğinden, bu mod FDD'ye benzer. Ana bilgisayar adedi çalıştırılabilir dosya adı platforma `<PROJECT-FILE>.exe`göre değişir ve ''ye benzer bir şey olarak adlandırılır. Uygulamayı çalıştırmak için hala kabul `dotnet <PROJECT-FILE>.dll`edilebilir bir yol olan bu çalıştırılabilir i arama yerine doğrudan çalıştırılabilir çalıştırabilirsiniz.

Uygulamanız .NET Core'un belirli bir sürümünü hedef almak üzere yapılandırılmıştır. Hedeflenen .NET Core çalışma süresi, uygulamanızın çalıştığı herhangi bir makinede olması gerekir. Örneğin, uygulamanız .NET Core 2.2'yi hedefliyorsa, uygulamanızın çalıştığı herhangi bir makinede .NET Core 2.2 çalışma zamanı yüklü olmalıdır. [Yayımlama temelleri](#publishing-basics) bölümünde belirtildiği gibi, proje dosyanızı varsayılan hedef çerçeveyi değiştirmek veya birden fazla çerçeveyi hedeflemek için değiştirebilirsiniz.

FDE yayımlamak, uygulamayı çalıştıran sistemde bulunan en son .NET Core güvenlik yamasına otomatik olarak ileten bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için [kullanmak üzere .NET Core sürümünü seçin'e](../versions/selection.md#framework-dependent-apps-roll-forward)bakın.

.NET Core 2.2 ve daha önce için, bir `dotnet publish` FDE yayınlamak için aşağıdaki anahtarları komutu ile kullanmanız gerekir:

- `-r <RID>`Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için [Runtime Tanımlayıcı (RID) kataloğuna](../rid-catalog.md)bakın.

- `--self-contained false`Bu anahtar .NET Core SDK'ya FDE olarak çalıştırılabilir bir işlem oluşturmasını söyler.

Anahtarı her kullandığınızda, `-r` çıktı klasörü yolu aşağıdakilere dönüşür:`./bin/<BUILD-CONFIGURATION>/<TFM>/<RID>/publish/`

[Örnek uygulamayı](#sample-app)kullanıyorsanız , `dotnet publish -f netcoreapp2.2 -r win10-x64 --self-contained false`çalıştırın. Bu komut aşağıdaki yürütülebilir oluşturur:`./bin/Debug/netcoreapp2.2/win10-x64/publish/apptest1.exe`

> [!NOTE]
> **Globalization değişmez modunu**etkinleştirerek dağıtımınızın toplam boyutunu küçültebilirsiniz. Bu mod, genel olarak farkında olmayan ve biçimlendirme kurallarını, kasa kurallarını ve [değişken kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)dize karşılaştırma ve sıralama sırasını kullanabilen uygulamalar için yararlıdır. Küreselleşme değişmez **modu** ve nasıl etkinleştirilir hakkında daha fazla bilgi için [bkz.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)

## <a name="self-contained-deployment"></a>Bağımsız dağıtım

Bağımsız bir dağıtım (SCD) yayımladığınızda, .NET Core SDK platforma özgü bir yürütülebilir oluşturur. Bir SCD yayımlama, uygulamanızı çalıştırmak için gereken tüm .NET Core dosyalarını içerir, ancak [.NET Core'un yerel bağımlılıklarını](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)içermez. Bu bağımlılıklar uygulama çalıştırmadan önce sistemde bulunmalıdır.

SCD yayımlamak, kullanılabilir en son .NET Core güvenlik yamasına ilerlemeyen bir uygulama oluşturur. Derleme zamanında sürüm bağlama hakkında daha fazla bilgi için [kullanmak üzere .NET Core sürümünü seçin'e](../versions/selection.md#self-contained-deployments-include-the-selected-runtime)bakın.

Bir SCD yayınlamak için `dotnet publish` aşağıdaki anahtarları komutla kullanmanız gerekir:

- `-r <RID>`Bu anahtar, hedef platformu belirtmek için bir tanımlayıcı (RID) kullanır. Çalışma zamanı tanımlayıcılarının listesi için [Runtime Tanımlayıcı (RID) kataloğuna](../rid-catalog.md)bakın.

- `--self-contained true`Bu anahtar ,NET Core SDK'ya SCD olarak çalıştırılabilir bir işlem oluşturmasını söyler.

> [!NOTE]
> **Globalization değişmez modunu**etkinleştirerek dağıtımınızın toplam boyutunu küçültebilirsiniz. Bu mod, genel olarak farkında olmayan ve biçimlendirme kurallarını, kasa kurallarını ve [değişken kültürün](xref:System.Globalization.CultureInfo.InvariantCulture)dize karşılaştırma ve sıralama sırasını kullanabilen uygulamalar için yararlıdır. Küreselleşme değişmez **modu** ve nasıl etkinleştirilir hakkında daha fazla bilgi için [bkz.](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek Uygulama Dağıtım Genel Bakış](index.md)
- [.NET Core Runtime Tanımlayıcı (RID) kataloğu](../rid-catalog.md)
