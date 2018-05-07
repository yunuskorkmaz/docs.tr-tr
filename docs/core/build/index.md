---
title: .NET Core kaynağından derleme
description: .NET Core ve kaynak kodu .NET Core CLI oluşturmayı öğrenin.
author: bleroy
ms.author: mairaw
ms.date: 06/28/2017
ms.openlocfilehash: 55a35223a4bc11156e056cceb7f86365c4906222
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="build-net-core-from-source"></a>.NET Core kaynağından derleme

.NET Core kendi kaynak kodundan oluşturma yeteneği birden çok yolla önemlidir: .NET Core numaralı bağlantı noktasına yeni platformlar için kolaylaştırır, katkı sağlar ve düzeltmeleri ürüne ve .NET özel sürümlerinin oluşturulmasını sağlar.
Bu makalede oluşturmak ve kendi sürümlerini .NET Core dağıtmak isteyen geliştiriciler için yönergeler sağlar.

## <a name="build-the-clr-from-source"></a>Kaynağından CLR derleme

.NET CoreCLR için kaynak kodunu bulunabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/) github'daki.

Yapı şu anda üzerinde aşağıdaki önkoşullar bağlıdır:
* [Git](https://git-scm.com/)
* [CMake](https://cmake.org/)
* [Python](https://www.python.org/)
* C++ derleyicisi.

Yükledikten sonra bu Önkoşullar yüklendi, derleme betiğindeki çağırarak CLR oluşturabilirsiniz (`build.cmd` , Windows'da veya `build.sh` Linux ve macOS) temeline [dotnet/coreclr](https://github.com/dotnet/coreclr/) deposu.

Bileşenlerini yükleme (OS) işletim sistemine bağlı olarak farklılık gösterir. Belirli işletim sisteminizi yapı yönergelerine bakın:

 * [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
 * [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
 * [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
 * [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md) 
 * [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

İşletim sistemi (X64 üzerinde yerleşik yalnızca ARM için) arasında çapraz yapı yoktur.  
Bu platform oluşturmak için belirli platformda olması gerekir.  

İki ana derleme sahip `buildTypes`:

 * Hata ayıklama (varsayılan) - en az en iyi duruma getirme ve ek çalışma zamanı denetimleri ile çalışma zamanı derler (onaylar). Bu en iyi duruma getirme düzeyini düşüş ve ek denetimler çalışma zamanı yürütme yavaş ancak hata ayıklama için değerlidir. Geliştirme ve test ortamları için Önerilen ayar budur.
 * Yayın - ek çalışma zamanı denetimleri olmadan tam iyileştirmeler ile çalışma zamanı derler. Bu kadar daha hızlı çalışma süresi performans sunacak ancak oluşturmak biraz uzun sürebilir ve hata ayıklama zor olabilir. Geçirmek `release` yapı bu seçmek için komut dosyası derleme türü.

Ayrıca, varsayılan olarak yapı yalnızca çalışma zamanı yürütülebilir dosyaları oluşturur, ancak aynı zamanda tüm testleri oluşturur.
Önemli miktarda yalnızca değişikliklerle denemek istiyorsanız, gerekli olmayan zaman ayırdığınız oldukça birkaç testleri vardır.
Ekleyerek testleri derlemeleri atlayabilirsiniz `skiptests` yapı komut bağımsız değişkeni aşağıdaki örnekteki gibi (Değiştir `.\build` ile `./build.sh` UNIX makinelerde):

```bat
    .\build skiptests 
```

Önceki örnekte gösterilen nasıl oluşturulacağını `Debug` geliştirme zamanı denetimleri sahip özellik (onaylar) etkin ve en iyi duruma getirme devre dışı. Yayın (tam hız) özellik oluşturmak için aşağıdakileri yapın:

```bat 
    .\build release skiptests
```

Daha fazla yapı seçenekleri ile yapı kullanarak bulabilirsiniz? ya da-niteleyici yardımcı olun.   

### <a name="using-your-build"></a>Yapınızı kullanma

Yapı tüm altında oluşturulan dosyaları yerleştirir `bin` depo tabanında dizin.
Var olan bir *bin\Log* (en yapı başarısız olduğunda yararlı) derleme sırasında oluşturulan günlük dosyalarını içeren dizini.
Gerçek çıkış yerleştirilen bir *bin\Product\[platform]. [ CPU mimarisi]. [türü yapı]*  gibi dizin *bin\Product\Windows_NT.x64.Release*.

Derleme 'ham' çıktısı bazen yararlı olsa da, normalde yalnızca yerleştirilir NuGet paketlerini ilgilendiğiniz `.nuget\pkg` önceki çıkış dizininin alt.

Yeni, çalışma zamanı kullanmak için iki temel teknikler şunlardır:

 1. **Dotnet.exe ve kullanma NuGet bir uygulama oluşturmak için**.
    Bkz: [kullanarak bilgisayarınızı yapı](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) kullanarak, yeni çalışma zamanı kullanan bir program oluşturma yönergeleri için NuGet, yeni oluşturduğunuz ve 'dotnet' komut satırı arabirimi (CLI) paketleri. Beklenen şekilde çalışma zamanı olmayan geliştiriciler, yeni çalışma zamanı kullanmak büyük olasılıkla bu tekniğidir.    

 2. **Corerun.exe paketlenmemiş taleplere DLL'leri kullanarak bir uygulamayı çalıştırmak için kullandığınız**.
    Bu depo, ayrıca herhangi bir bağımlılığı NuGet üzerinde almaz corerun.exe adlı basit bir ana bilgisayar tanımlar.
    Ana bilgisayar gerçekten gerekli DLL'leri alınacağı bildirmeniz gerekir ve el ile araya toplamak zorunda.
    Bu teknik tüm testler tarafından kullanılan [dotnet/coreclr](https://github.com/dotnet/coreclr) depodaki ve ön birim testi gibi hızlı yerel 'düzenleme-derleme-debug' döngü için kullanışlıdır.
    Bkz: [yürütme .NET Core uygulamalarla CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) Bu teknik kullanımıyla ilgili ayrıntılar için.

## <a name="build-the-cli-from-source"></a>CLI kaynağından derleme

.NET Core CLI için kaynak kodunu bulunabilir [dotnet/CLI](https://github.com/dotnet/cli/) github'daki.

.NET Core CLI oluşturmak için aşağıdaki makinenize yüklü gerekir.

* Windows ve Linux:
    - YOL üzerindeki Git
* macOS:
    - YOL üzerindeki Git
    - Xcode
    - Openssl

Derleme için çalıştırın `build.cmd` , Windows'da veya `build.sh` Linux ve kök macOS. Testler yürütmek istemiyorsanız, çalıştırmak `build.cmd /t:Compile` veya `./build.sh /t:Compile`. MacOS Sierra CLI oluşturmak için DOTNET_RUNTIME_ID ortam değişkeni çalıştırarak ayarlamanız gerektiğini `export DOTNET_RUNTIME_ID=osx.10.11-x64`.

### <a name="using-your-build"></a>Yapınızı kullanma

Kullanım `dotnet` gelen yürütülebilir *yapıları / {os}-{arch} / stage2* yeni oluşturulan CLI denemek için. Çağrılırken, çıktı yapı kullanmak istiyorsanız, `dotnet` geçerli konsolundan de ekleyebilirsiniz *yapıları / {os}-{arch} / stage2* yolu.

## <a name="see-also"></a>Ayrıca bkz.

* [.NET core ortak dil çalışma zamanı (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
* [.NET core CLI Geliştirici Kılavuzu](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [.NET Core dağıtımı paketleme](./distribution-packaging.md)
