---
title: Kaynaktan .NET Core derleme
description: .NET Core ve .NET Core CLI kaynak kodundan oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 2623c5d21121b71960d174301c35bdd0d7f8558a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43468804"
---
# <a name="build-net-core-from-source"></a>Kaynaktan .NET Core derleme

.NET Core, kaynak koddan oluşturma imkanı birden çok yolla önemlidir: .NET Core numaralı bağlantı noktasına yeni platformlara kolaylaştırır, katkı sağlar ve düzeltmeleri ürüne ve .NET özel sürümlerini oluşturulmasını sağlar.
Bu makalede, derleme ve kendi .NET Core sürümlerini dağıtmak isteyen geliştiriciler için konusunda rehberlik sağlar.

## <a name="build-the-clr-from-source"></a>CLR kaynağından alınan derleme

.NET CoreCLR için kaynak kodu bulunabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/) github deposu.

Derleme şu anda üzerinde aşağıdaki ön koşullara bağlıdır:

* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* bir C++ derleyicisi.

Bu Önkoşullar yükledikten sonra derleme betiğinin çağırarak CLR oluşturabilirsiniz (`build.cmd` Windows, şirket veya `build.sh` Linux ve macOS) temel [dotnet/coreclr](https://github.com/dotnet/coreclr/) depo.

İşletim sistemi (OS) bağlı olarak farklı bileşenler yükleniyor. Belirli işletim sisteminiz için derleme yönergelere bakın:

* [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

İşletim sistemi (için X64 üzerinde yerleşik yalnızca ARM,) arasında çapraz derleme yok.  
Bu platformu oluşturmak için belirli platform olması gerekir.  

İki ana derleme sahip `buildTypes`:

* Hata ayıklama (varsayılan) - en az iyileştirmeleri ve ek çalışma zamanı denetimleri ile çalışma zamanı derleme (bildirimler). Bu iyileştirme düzeyini düşüş ve ek denetimler çalışma zamanı yürütme yavaş ancak hata ayıklama için değerlidir. Geliştirme ve test ortamları için Önerilen ayar budur.
* Yayın - çalışma zamanı tam iyileştirmeler ve ek çalışma zamanı denetimleri olmadan derler. Bu çok daha hızlı çalıştırma performans verir ancak oluşturmak biraz uzun sürebilir ve hata ayıklaması zor olabilir. Geçirmek `release` yapı betiği bunu seçmek için yapı türü.

Ayrıca, varsayılan yapı yalnızca çalışma zamanı yürütülebilir dosyalar oluşturur, ancak ayrıca tüm testleri oluşturur.
Videonuz testleri, önemli miktarda değişikliklerle denemek istiyorsanız, gerekli olmayan zaman ayırdığınız vardır.
Ekleyerek, test derlemeleri atlayabilirsiniz `skiptests` yapı komut dosyası bağımsız değişkeni aşağıdaki örnekte ister (Değiştir `.\build` ile `./build.sh` Unix makinelerinde):

```bat
    .\build skiptests
```

Önceki örnekte gösterilen nasıl oluşturulacağını `Debug` geliştirme zamanı denetimleri olan bir özellik (onaylar) etkin ve iyileştirmeleri devre dışı. Derleme sürümü (tam hız) türü için aşağıdakileri yapın:

```bat
    .\build release skiptests
```

Daha fazla yapı seçeneklerini derleme ile kullanarak bulabilirsiniz? ya da-niteleyicisi yardımcı olun.

### <a name="using-your-build"></a>Yapınızı kullanma

Altında oluşturulan dosyalarının tüm yapı yerleştirir `bin` deponun temel dizin.
Var olan bir *bin\Log* (en derleme başarısız olduğunda yararlıdır) derleme sırasında oluşturulan günlük dosyalarını içeren dizin.
Gerçek çıkış yerleştirilen bir *bin\Product\[platform]. [ CPU mimarisi]. [türü build]*  gibi dizin *bin\Product\Windows_NT.x64.Release*.

Derleme 'raw' çıkışı bazen yararlı olsa da, normalde yalnızca yerleştirilir NuGet paketlerini ilgilendiğiniz `.nuget\pkg` önceki çıktı dizininin alt.

Yeni, çalışma zamanı kullanmak için iki temel teknik vardır:

 1. **Bir uygulama oluşturmak için dotnet.exe ve NuGet kullanma**.
    Bkz: [kullanarak yapı](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) kullanarak, yeni bir çalışma zamanı kullanan bir program oluşturma yönergeleri için NuGet oluşturdunuz ve 'dotnet' komut satırı arabirimi (CLI) paketleri. Bu, yeni bir çalışma zamanı kullanmak büyük olasılıkla beklenen şekilde çalışma zamanı olmayan geliştiriciler bir tekniktir.

 2. **Corerun.exe paketlenmemiş DLL'leri kullanmanın bir uygulamayı çalıştırmak için kullanmak**.
    Bu depo, NuGet üzerinde hiçbir bağımlılık almaz corerun.exe adlı basit bir konak da tanımlar.
    El ile araya toplamak zorunda ve gerçekten kullandığınız gerekli DLL'lerin nereden ana bilgisayara bildirmek gerekir.
    Bu teknik, tüm testler tarafından kullanılan [dotnet/coreclr](https://github.com/dotnet/coreclr) deponun ve ön birim testi gibi hızlı yerel 'düzenleme-derleme-hata ayıklama' döngüsü için kullanışlıdır.
    Bkz: [CoreRun.exe ile .NET Core uygulamaları çalıştırma](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) bu yöntemi kullanma hakkında bilgi.

## <a name="build-the-cli-from-source"></a>Kaynak CLI'dan oluşturun

.NET Core CLI için kaynak kodu bulunabilir [dotnet/CLI](https://github.com/dotnet/cli/) github deposu.

.NET Core CLI'yı oluşturmak için makinenizde aşağıdaki ihtiyacınız vardır.

* Windows ve Linux için:
  * YOL üzerindeki Git
* macOS:
  * YOL üzerindeki Git
  * Xcode
  * Openssl

Derleme için çalıştırmanız `build.cmd` Windows, şirket veya `build.sh` Linux ve Macos'ta kök. Testleri yürütmek istemiyorsanız çalıştırma `build.cmd /t:Compile` veya `./build.sh /t:Compile`. MacOS Sierra CLI'daki oluşturmak için çalıştırarak DOTNET_RUNTIME_ID ortam değişkenini ayarlamanız gerekir `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Yapınızı kullanma

Kullanım `dotnet` gelen yürütülebilir *yapıtları / {os}-{arch} / stage2* yeni oluşturulan CLI'yı denemek için. Derleme çağrılırken çıktısını kullanmak istiyorsanız `dotnet` de ekleyebilirsiniz geçerli konsolundan *yapıtları / {os}-{arch} / stage2* yolu.

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core ortak dil çalışma zamanı (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [.NET core CLI Geliştirici Kılavuzu](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [.NET Core dağıtımı paketleme](./distribution-packaging.md)
