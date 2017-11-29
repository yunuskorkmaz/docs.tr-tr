---
title: ".NET Core SDK'yı ve araçları sürekli tümleştirme (CI içinde) kullanma"
description: ".NET Core SDK ve araçlarını derleme sunucusundaki kullanımı hakkında bilgi."
keywords: ".NET, .NET core, sürekli tümleştirme, CI, yapı, otomasyon, Travis CI, AppVeyor, Visual Studio Team Services, vsts"
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 0d6e1e34-277c-4aaf-9880-3ebf81023857
ms.openlocfilehash: 596bc689e423082dcae0c79801e9f796b398391e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>.NET Core SDK'yı ve araçları sürekli tümleştirme (CI içinde) kullanma

## <a name="overview"></a>Genel Bakış

Bu belge, bir derleme sunucuda .NET Core SDK ve araçlarını kullanma özetlenmektedir. .NET Core araç takımı works hem etkileşimli olarak, burada bir geliştirici komutları komut istemine komut isteminde ve otomatik olarak bir sürekli tümleştirme (CI) sunucusu burada türleri bir yapı komut dosyasını çalıştırır. Komutları, seçenekleri, girişleri ve çıkışları aynıdır ve sağladığınız yalnızca araçları ve uygulamanızı oluşturmak için bir sistem edinmenin yolunu noktalardır. Bu belge CI için aracı alım senaryoları tasarım ve yapı komut dosyalarınızı yapısı hakkında öneriler odaklanır.

## <a name="installation-options-for-ci-build-servers"></a>CI için yükleme seçeneklerini sunucuları derleme

### <a name="using-the-native-installers"></a>Yerel yükleyicileri kullanma

Yerel yükleyicileri macOS, Linux ve Windows için kullanılabilir. Yükleyicileri yapı sunucuya yönetici (sudo) erişimi gerektirir. Yerel bir yükleyici kullanmanın avantajı tüm araçları çalıştırmak gerekli yerel bağımlılıkları yükler ' dir. Yerel yükleyicileri da SDK'ın bir sistem genelinde yüklemesini sağlar.

macOS kullanıcıları PKG yükleyicileri kullanmalıdır. Linux üzerinde get apt Ubuntu için veya CentOS, yum gibi bir akış tabanlı Paket Yöneticisi veya paketleri kendileri DEB veya RPM kullanarak seçeneği yoktur. Windows üzerinde MSI yükleyicisi kullanın.

En son kararlı ikili dosyaları bulunan [.NET Core ile çalışmaya başlama](https://aka.ms/dotnetcoregs). En son (ve büyük olasılıkla kararsız) yayın öncesi araçları kullanmak isterseniz, verilen bağlantıları kullanın [dotnet/CLI GitHub deposunu](https://github.com/dotnet/cli#installers-and-binaries). Linux dağıtımları için `tar.gz` arşivler (olarak da bilinen `tarballs`) kullanılabilir; .NET Core yüklemek için yükleme komut dosyaları arşivler içinde kullanın.

### <a name="using-the-installer-script"></a>Yükleyici komut dosyası kullanma

Yükleyici komut dosyası kullanarak derleme sunucunuz ve araçları alma kolay Otomasyon yönetimsel olmayan yükleme sağlar. Komut dosyası araçları yükleme ve onu bir varsayılan veya kullanım için belirtilen konum ayıklayın ilgilenir. Bir sürümünü yüklemek istediğiniz araçları ve tüm SDK veya yalnızca paylaşılan çalışma yüklemek isteyip istemediğinizi de belirtebilirsiniz.

Yükleyicisi betiği fetch ve SDK istenen sürümü yüklemek için yapı başlangıcında çalıştırmak için otomatik hale getirilmiştir. *İstediğiniz sürümü* oluşturmak için seçtiğiniz sürüm SDK'sının projelerinizi gerektir değil. Komut dosyası, sunucu üzerindeki yerel bir dizinde SDK'sını yükleyin, araçları yüklü konumundan çalıştırın ve sonra temizleme (veya CI hizmeti sağlayan temizleme) derleme sonrası sağlar. Bu derleme işlemi kapsülleme ve bütün yalıtım sağlar. Yükleme komut dosyası başvurusu bulunan [dotnet yükleme](dotnet-install-script.md) konu.

> [!NOTE]
> Yükleyici komut dosyası kullanırken, yerel bağımlılıkları otomatik olarak yüklü değildir. İşletim sisteminin bunları yoksa yerel bağımlılıkları yüklemeniz gerekir. Önkoşullar listesine bakın [.NET Core Yerel Önkoşullar](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) konu.

## <a name="ci-setup-examples"></a>CI Kurulum örnekleri

Bu bölümde, çeşitli yazılım açıklamasını hizmet (SaaS) CI çözümleri olarak birlikte PowerShell veya bash bir betik kullanarak el ile kuruluma açıklanmaktadır. Kapsanan SaaS CI çözümleri [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Visual Studio Team Services yapı](https://www.visualstudio.com/docs/build/overview).

### <a name="manual-setup"></a>El ile Kurulum

Her SaaS hizmet oluşturma ve derleme sürecinde yapılandırma kendi yöntemlerine sahiptir. Listelenenden farklı SaaS çözümü veya önceden paketlenmiş destek ötesinde özelleştirme gerektiren kullanıyorsanız, en az bazı el ile yapılandırma gerçekleştirmelidir.

Genel olarak, el ile kuruluma Araçlar (veya Araçları'nın en son gecelik derlemeleri) sürümünü edinin ve derleme betiğinizin çalıştırmak gerektirir. Bir PowerShell veya bash derleme süreci özetlenmektedir bir proje dosyasını kullanmanız veya .NET Core komutları düzenlemek için komut dosyası kullanabilirsiniz. [Orchestration bölüm](#orchestrating-the-build) Bu seçenekler hakkında daha fazla ayrıntı sağlar.

CI yapı Sunucusu Kurulumu el ile gerçekleştiren bir komut dosyası oluşturduktan sonra geliştirme makinenizde yerel olarak test etmek için kodunuzu oluşturmak için kullanın. Komut dosyası da yerel olarak çalıştığı onaylandıktan sonra CI yapı sunucunuza dağıtın. Görece basit bir PowerShell komut dosyası, .NET Core SDK edinme ve bir Windows yapı sunucuya yüklemek gösterilmiştir:

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the 
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the 
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it 
#   does, it's removed. This is not strictly required, but it's a 
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the 
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the 
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the 
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

Yapı işleminizin betik sonunda için uygulama sağlar. Komut dosyası araçları edinir ve yapı işleminizin yürütür. UNIX makineler için aşağıdaki bash betiği PowerShell Betiği benzer bir şekilde açıklanan eylemleri gerçekleştirir:

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a>Travis CI

Yapılandırabileceğiniz [Travis CI](https://travis-ci.org/) .NET Core SDK'sını kullanarak yüklemek için `csharp` dil ve `dotnet` anahtarı. Resmi Travis CI belgeleri bakın [bir C#, F # veya Visual Basic proje oluşturma](https://docs.travis-ci.com/user/languages/csharp/) daha fazla bilgi için. Not Travis CI bilgilere erişme gibi topluluk tarafından tutulan `language: csharp` dil tanımlayıcısını F # ve Mono dahil olmak üzere tüm .NET dilleri için çalışır.

Travis CI hem macOS (OS X 10.11 sürümünü, OS X 10,12) çalıştıran ve Linux (Ubuntu 14.04) işleri bir *matris yapı*çalışma zamanı ortamı ve uygulamanız için derleme birleşimleri karşılamak üzere özel durumlar/içermeler bileşimini burada belirtin. Bkz: [. travis.yml örnek](https://github.com/dotnet/docs/blob/master/.travis.yml) dosya ve [yapı özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) daha fazla bilgi için Travis CI belgeleri içinde. MSBuild tabanlı araçlar LTS (1.0.x) ve geçerli (1.1.x) çalışma zamanları pakete dahil; SDK yükleyerek oluşturmak için gereken her şeyi aldığınız şekilde.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) .NET Core 1.0.1 yükler SDK ile `Visual Studio 2017` çalışan görüntüsünü oluşturabilirsiniz. .NET Core SDK farklı sürümlerini diğer yapı görüntülerle kullanılabilir; bkz: [appveyor.yml örnek](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [yapı çalışan görüntüleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) konusunda daha fazla bilgi için AppVeyor belgeleri.

.NET Core SDK ikili dosyaları indirilir ve yükleme komut dosyası kullanarak bir alt dizinde sıkıştırması açılmış ve ardından eklenmiş `PATH` ortam değişkeni. .NET Core SDK birden çok sürümü ile tümleştirme testleri çalıştırmak için bir yapı matris ekleyin:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a>Visual Studio Team Services (VSTS)

Visual Studio Team Services (Bu yaklaşımlardan birini kullanarak .NET Core projeler derlemek için VSTS) yapılandırın:

1. Komut dosyasını çalıştırmak [el ile kuruluma adım](#manual-setup) , komutları kullanarak.
1. .NET Core araçları kullanmak üzere yapılandırılmış birkaç VSTS yerleşik yapı görevlerin oluşan bir yapı oluşturun.

Her iki çözüm de geçerlidir. El ile Kurulum betiği kullanarak, bunları derleme bir parçası olarak indirmek bu yana, aldığınız araçları sürümünü denetler. Yapı oluşturmanız gereken bir komut dosyasından çalıştırın. Bu konuda, yalnızca el ile seçeneği ele alınmaktadır. Derleme görevleri VSTS ile bir yapı oluşturma hakkında daha fazla bilgi için VSTS ziyaret [sürekli tümleştirme ve dağıtım](https://www.visualstudio.com/docs/build/overview) konu.

VSTS içinde el ile Kurulum komut dosyası kullanmak için yeni bir derleme tanımı oluşturun ve derleme adımı için çalıştırılacak komut dosyasını belirtin. Bu, VSTS kullanıcı arabirimi kullanılarak gerçekleştirilir:

1. Yeni bir derleme tanımı oluşturarak başlayın. Ne tür bir yapı istediğiniz oluşturmak için seçin tanımlamak için bir seçenek sağlar ekran ulaştıktan sonra **boş** seçeneği.

   ![Boş bir yapıyı seçme](./media/using-ci-with-cli/screen1.png)

1. Yapı depo yapılandırdıktan sonra derleme tanımları yönlendirilirsiniz. Seçin **Ekle derleme adımı**:

   ![Bir derleme adımı ekleme](./media/using-ci-with-cli/screen2.png)

1. İle sunulan **görev katalog**. Katalog derlemede kullanma görevleri içerir. Bir komut dosyası sahip olduğundan, seçin **Ekle** için düğmesini **PowerShell: bir PowerShell betiğini çalıştırmak**.

   ![Bir PowerShell komut dosyası adımı ekleme](./media/using-ci-with-cli/screen3.png)

1. Derleme adımı yapılandırın. Komut dosyası oluşturmakta olduğunuz depodan ekleyin:

   ![Çalıştırılacak PowerShell komut dosyası belirtme](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a>Yapı yönetme

Bu belge çoğunu açıklar .NET Core araçları edinin ve düzenlemek hakkında bilgi sağlamadan çeşitli CI Hizmetleri Yapılandırma veya *gerçekten yapı*, .NET Core kodunuzla. Yapı sürecini yapılandırma konusunda seçenekler burada genel hatlarıyla ele birçok faktöre bağlıdır. Belge kümeleri içinde sağlanan örnekleri ve kaynakları keşfetme [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [VSTS](https://www.visualstudio.com/docs/build/overview) derlemeleriniz her yönetme hakkında daha fazla bilgi teknoloji.

.NET Core Araçları'nı kullanarak .NET Core kod derleme işlemi yapılandırılması ele iki genel yaklaşım kullanarak doğrudan MSBuild veya .NET Core komut satırı komutlarını kullanarak. Almanız gereken hangi yaklaşımın karmaşıklığı rahatlık düzeyinizi yaklaşımlar ve dengelemeler ile belirlenir. MSBuild hedefleri ve görevleri de yapı işleminizin express olanağı sağlar, ancak MSBuild proje dosyası sözdizimi öğrenme eklenen karmaşıklığını ile gelir. .NET Core komut satırı araçlarını kullanarak belki de daha basit olmakla birlikte, bir komut dosyası dili gibi orchestration mantığı yazmanızı gerektirir `bash` veya PowerShell.

## <a name="see-also"></a>Ayrıca bkz.

[Ubuntu alma adımları](https://www.microsoft.com/net/core#linuxubuntu)   
