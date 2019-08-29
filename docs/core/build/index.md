---
title: Kaynaktan .NET Core derleme
description: Kaynak koddan .NET Core ve .NET Core CLI oluşturmayı öğrenin.
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105394"
---
# <a name="build-net-core-from-source"></a>Kaynaktan .NET Core derleme

Kaynak kodundan .NET Core oluşturma özelliği, birden çok şekilde önemlidir: .NET Core 'u yeni platformlar için bağlantı noktasını daha kolay hale getirir, ürüne katkı ve düzeltmeler sağlar ve .NET 'in özel sürümlerinin oluşturulmasına olanak tanır.
Bu makale, kendi .NET Core sürümlerini derlemek ve dağıtmak isteyen geliştiricilere kılavuzluk sağlar.

## <a name="build-the-clr-from-source"></a>Kaynaktan CLR oluşturma

.NET CoreCLR 'ın kaynak kodu GitHub 'daki [DotNet/CoreCLR](https://github.com/dotnet/coreclr/) deposunda bulunabilir.

Yapı şu anda aşağıdaki önkoşullara bağımlıdır:

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- C++ derleyici.

Bu önkoşulları yükledikten sonra,`build.cmd` [DotNet/CoreCLR](https://github.com/dotnet/coreclr/) deposunun tabanında derleme betiğini (Windows veya `build.sh` Linux ve MacOS 'ta) çağırarak clr 'yi oluşturabilirsiniz.

Bileşenleri yüklemek, işletim sistemine (OS) göre farklılık gösterir. Belirli işletim sistemi için derleme yönergelerine bakın:

- [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

İşletim sistemi genelinde çapraz oluşturma yoktur (yalnızca x64 üzerinde oluşturulan ARM için).  
Bu platformu oluşturmak için belirli bir platformda olmanız gerekir.  

Derleme iki ana `buildTypes`öğesine sahiptir:

- Hata ayıklama (varsayılan)-çalışma zamanını en az iyileştirmeler ve ek çalışma zamanı denetimleri (onaylar) ile derler. En iyi duruma getirme düzeyi ve ek denetimler, çalışma zamanı yürütmesinin yavaşlamasına karşın hata ayıklama için değerlidir. Bu, geliştirme ve test ortamları için önerilen ayardır.
- Release-çalışma zamanını, ek çalışma zamanı denetimleri olmadan tam iyileştirmelere göre derler. Bu çok daha hızlı çalışma süresi performansına sahiptir, ancak oluşturulması biraz daha uzun sürebilir ve hata ayıklaması zor olabilir. Bu `release` derleme türünü seçmek için derleme betiğine iletin.

Buna ek olarak, yapı varsayılan olarak yalnızca çalışma zamanı yürütülebilir dosyalarını oluşturur, ancak tüm testleri de oluşturur.
Az sayıda test vardır ve yalnızca değişikliklerle denemeler yapmak istiyorsanız gerekli olmayan önemli miktarda zaman elde edersiniz.
Aşağıdaki örnekte olduğu gibi derleme betiğine `skiptests` bağımsız değişkeni ekleyerek test yapılarını atlayabilirsiniz (UNIX makinelerinde ile `./build.sh` değiştirin `.\build` ):

```bat
    .\build skiptests
```

Önceki örnekte, geliştirme zamanı denetimleri (onaylar `Debug` ) etkin ve iyileştirmeler devre dışı olan Flavor 'nin nasıl oluşturulacağı gösterildi. Yayın (tam hız) türü oluşturmak için aşağıdakileri yapın:

```bat
    .\build release skiptests
```

-? Kullanarak derleme ile daha fazla derleme seçeneği bulabilirsiniz. veya-help niteleyicisi.

### <a name="using-your-build"></a>Yapınızı kullanma

Yapı, oluşturulan tüm dosyalarını deponun tabanında `bin` dizin altında koyar.
Derleme sırasında oluşturulan günlük dosyalarını içeren bir *bin\log* dizini vardır (en çok derleme başarısız olduğunda yararlıdır).
Gerçek çıktı bir *bin\product\[platformuna yerleştirildi]. [ CPU mimarisi]. [derleme türü]* Dizin, örneğin *bin\Product\Windows_NT.x64.Release*.

Derleme ' Ham ' çıkışı bazen yararlı olsa da, normalde yalnızca önceki çıkış dizininin `.nuget\pkg` alt dizinine yerleştirilmiş olan NuGet paketlerini ilgileniyorsunuz.

Yeni çalışma zamanını kullanmanın iki temel tekniği vardır:

 1. **Bir uygulama oluşturmak için DotNet. exe ve NuGet kullanın**.
    Yeni oluşturduğunuz NuGet paketlerini ve ' DotNet ' komut satırı arabirimini (CLı) kullanarak yeni çalışma zamanı kullanan bir program oluşturma yönergeleri için [yapınızı kullanma](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) konusuna bakın. Bu teknik, çalışma zamanı olmayan geliştiricilerin yeni çalışma zamanını tüketmesi olasılığını tahmin eden bir yöntemdir.

 2. **Paket olmayan dll 'leri kullanarak bir uygulamayı çalıştırmak için corerun. exe**' yi kullanın.
    Bu depo Ayrıca, NuGet üzerinde hiçbir bağımlılığı olmayan corerun. exe adlı basit bir ana bilgisayarı tanımlar.
    Ana bilgisayara gerçekten kullandığınız gerekli dll 'Leri nereden alınacağını ve bunları birlikte el ile toplamanız gerektiğini söylemeniz gerekir.
    Bu teknik, [DotNet/CoreCLR](https://github.com/dotnet/coreclr) deposunda bulunan tüm testler tarafından kullanılır ve hızlı yerel ' düzenleme-derleme-hata ayıklama ' döngüsü için, ön birim testi gibi yararlıdır.
    Bu tekniği kullanma hakkında ayrıntılı bilgi için bkz. [CoreRun. exe ile .NET Core uygulamaları yürütme](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) .

## <a name="build-the-cli-from-source"></a>Kaynaktan CLı oluştur

.NET Core CLI kaynak kodu GitHub 'daki [DotNet/CLI](https://github.com/dotnet/cli/) deposunda bulunabilir.

.NET Core CLI derlemek için makinenizde aşağıdakilerin yüklü olması gerekir.

- Windows & Linux:
  - YOLDAKI git
- MacOS
  - YOLDAKI git
  - Xcode
  - Openssl

Kök veya `build.cmd` `build.sh` Linux ve MacOS üzerinde derlemek, çalıştırmak için. Testleri yürütmek istemiyorsanız, veya `build.cmd -t:Compile` `./build.sh -t:Compile`çalıştırın. MacOS Sierra CLı 'yi oluşturmak için, DOTNET_RUNTIME_ID ortam değişkenini çalıştırarak `export DOTNET_RUNTIME_ID=osx.10.11-x64`ayarlamanız gerekir.

### <a name="using-your-build"></a>Yapınızı kullanma

Yeni oluşturulan CLI 'yı denemek için *yapıtlar/{OS}-{Arch}/STAGE2* içindeki yürütülebilirdosyayıkullanın.`dotnet` Yapı çıkışını geçerli konsolundan çağırırken `dotnet` kullanmak istiyorsanız, yolu */{OS}-{Arch}/STAGE2* da yola ekleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core ortak dil çalışma zamanı (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
- [.NET Core CLI geliştirici kılavuzu](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [.NET Core dağıtımı paketleme](./distribution-packaging.md)
