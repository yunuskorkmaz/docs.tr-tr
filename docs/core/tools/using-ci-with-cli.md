---
title: .NET Core SDK ve araçları ile Sürekli Entegrasyon (CI)
description: .NET Core SDK'yı ve araçlarını yapı sunucusunda sürekli tümleştirme ile nasıl kullanacağınızı öğrenin.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451044"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Sürekli Entegrasyonda .NET Core SDK ve araçları kullanma (CI)

Bu belge, .NET Core SDK ve araçlarını bir yapı sunucusunda kullanarak özetliyor. .NET Core araç kümesi hem etkileşimli olarak çalışır, burada bir geliştirici komut isteminde komut ları yazar ve otomatik olarak, sürekli tümleştirme (CI) sunucusu bir yapı komut dosyası çalıştırAr. Komutlar, seçenekler, girişler ve çıktılar aynıdır ve sağladığınız tek şey, aracı ve uygulamanızı oluşturmak için bir sistem edinmenin bir yoludur. Bu belge, yapı komut dosyalarınızı nasıl tasarlayıp yapılandırılabildiğini anlatan önerileriçeren CI için araç edinme senaryolarına odaklanır.

## <a name="installation-options-for-ci-build-servers"></a>CI yapı sunucuları için yükleme seçenekleri

### <a name="using-the-native-installers"></a>Yerel yükleyicileri kullanma

MacOS, Linux ve Windows için yerel yükleyiciler kullanılabilir. Yükleyiciler yapı sunucusuna yönetici (sudo) erişimi gerektirir. Yerel bir yükleyici kullanmanın avantajı, takım çalışması için gereken tüm yerel bağımlılıkları yüklemesidir. Yerel yükleyiciler de SDK bir sistem çapında yükleme sağlar.

macOS kullanıcıları PKG yükleyicilerini kullanmalıdır. Linux'ta, Ubuntu için apt-get veya CentOS için yum gibi bir özet akışı tabanlı paket yöneticisi veya paketlerin kendileri, DEB veya RPM'yi kullanma seçeneği vardır. Windows'da MSI yükleyicisini kullanın.

En son kararlı ikililer [.NET indirme bulunur.](https://dotnet.microsoft.com/download) En son (ve potansiyel olarak kararsız) ön sürüm aracını kullanmak istiyorsanız, [dotnet/core-sdk GitHub deposunda](https://github.com/dotnet/core-sdk#installers-and-binaries)sağlanan bağlantıları kullanın. Linux dağıtımları `tar.gz` için arşivler `tarballs`(diğer adıyla da bilinir) mevcuttur; .NET Core'u yüklemek için arşivdeki yükleme komut dosyalarını kullanın.

### <a name="using-the-installer-script"></a>Yükleyici komut dosyasını kullanma

Yükleyici komut dosyasının kullanılması, yapı sunucunuzda yönetim dışı yükleme ve takım oluşturma yı elde etmek için kolay otomasyon sağlar. Komut dosyası, aracı indirmeyi ve kullanmak üzere varsayılan veya belirtilen bir konuma çıkarmayı halleder. Ayrıca, yüklemek istediğiniz aracın bir sürümünü ve tüm SDK'yı mı yoksa yalnızca paylaşılan çalışma süresini mi yüklemek istediğinizi de belirtebilirsiniz.

Yükleyici komut dosyası, SDK'nın istenen sürümünü almak ve yüklemek için yapının başında çalışmak üzere otomatikleştirilir. *İstenilen sürüm,* projelerinizin oluşturması gereken SDK'nın ne reisiyse odur. Komut dosyası, SDK'yı sunucudaki yerel bir dizine yüklemenize, yüklenen konumdan araçları çalıştırmanıza ve yapıdan sonra temizlemenize (veya CI hizmetinin temizlenmesine izin vermenize) olanak tanır. Bu, tüm yapı işleminize kapsülleme ve yalıtım sağlar. Yükleme komut dosyası başvurusu [dotnet yükleme](dotnet-install-script.md) makalesinde bulunur.

> [!NOTE]
> **Azure DevOps Services**
>
> Yükleyici komut dosyasını kullanırken, yerel bağımlılıklar otomatik olarak yüklenmiyor. İşletim sistemi bunlara sahip değilse, yerel bağımlılıkları yüklemeniz gerekir. Daha fazla bilgi için [bkz.](../install/dependencies.md)

## <a name="ci-setup-examples"></a>CI kurulum örnekleri

Bu bölümde, powershell veya bash komut dosyası kullanılarak yapılan el ile kurulum ve hizmet (SaaS) CI çözümleri olarak çeşitli yazılımların tanımı açıklanmaktadır. SaaS CI çözümleri kaplı [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), ve [Azure Boru Hatları](https://docs.microsoft.com/azure/devops/pipelines/index)vardır.

### <a name="manual-setup"></a>Manuel kurulum

Her SaaS hizmetinin bir yapı işlemi oluşturmak ve yapılandırmak için kendi yöntemleri vardır. Listelenenlerden farklı SaaS çözümü kullanıyorsanız veya önceden paketlenmiş desteğin ötesinde özelleştirme gerektiriyorsanız, en azından bazı el ile yapılandırma gerçekleştirmeniz gerekir.

Genel olarak, el ile kurulum, araçların (veya araçların en son gece yapılarını) bir sürümünü edinmenizi ve yapı komut dosyanızı çalıştırmanızı gerektirir. .NET Core komutlarını düzenlemek için powershell veya bash komut dosyası kullanabilir veya yapı işlemini özetleyen bir proje dosyası kullanabilirsiniz. [Orkestrasyon bölümü](#orchestrating-the-build) bu seçenekler hakkında daha fazla ayrıntı sağlar.

Manuel CI build sunucu kurulumu gerçekleştiren bir komut dosyası oluşturduktan sonra, kodunuzu test amacıyla yerel olarak oluşturmak için geliştirme makinenizde kullanın. Komut dosyasının yerel olarak iyi çalıştığını doğruladıktan sonra, komut dosyasını CI yapı sunucunuza dağıtın. Nispeten basit bir PowerShell komut dosyası ,NET Core SDK'nın nasıl elde edilip Windows build sunucusuna yükleyin:

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

Komut dosyasının sonunda yapı işleminiz için uygulama sağlarsınız. Komut dosyası araçları edinir ve sonra yapı işleminizi yürütür. UNIX makineleri için aşağıdaki bash komut dosyası PowerShell komut dosyasında açıklanan eylemleri benzer bir şekilde gerçekleştirir:

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

[Travis CI'yi](https://travis-ci.org/) `csharp` dili ve `dotnet` anahtarı kullanarak .NET Core SDK'yı yükecek şekilde yapılandırabilirsiniz. Daha fazla bilgi için, [C#, F#veya Visual Basic Project oluşturma](https://docs.travis-ci.com/user/languages/csharp/)yla ilgili resmi Travis CI dokümanlarına bakın. Topluluk tarafından korunan `language: csharp` dil tanımlayıcısının F#ve Mono dahil olmak üzere tüm .NET dilleri için çalıştığını Travis CI bilgilerine erişirken not edin.

Travis CI, uygulamanız için yapı kombinasyonlarınızı kapsayacak şekilde çalışma süresi, ortam ve dışlamaların/dahil etmelerin bir birleşimini belirttiğiniz bir *yapı matrisinde*hem macOS hem de Linux işlerini çalıştırır. Daha fazla bilgi için Travis CI belgelerinde Yapı makalesini [özelleştirmeye](https://docs.travis-ci.com/user/customizing-the-build) bakın. MSBuild tabanlı araçlar, paketteki LTS (1.0.x) ve Geçerli (1.1.x) çalışma sürelerini içerir; böylece SDK yükleyerek, oluşturmak için gereken her şeyi alırsınız.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) `Visual Studio 2017` yapı işçisi görüntüsü ile .NET Core 1.0.1 SDK yükler. .NET Core SDK'nın farklı sürümlerine sahip diğer yapı görüntüleri mevcuttur. Daha fazla bilgi için [appveyor.yml örneğine](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve AppVeyor dokümanlarında yapı [işçisi resimleri](https://www.appveyor.com/docs/build-environment/#build-worker-images) makalesine bakın.

.NET Core SDK ikilileri yük komut dosyası kullanılarak bir alt dizinde indirilir ve fermuarsız olarak çıkarılır ve ortam değişkenine `PATH` eklenir. .NET Core SDK'nın birden çok sürümüyle tümleştirme testleri çalıştırmak için bir yapı matrisi ekleyin:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Azure DevOps Hizmetlerini bu yaklaşımlardan birini kullanarak .NET Core projeleri oluşturmak için yapılandırın:

1. Komutlarınızı kullanarak komut dosyasını [el ile kurulum adımından](#manual-setup) çalıştırın.
1. .NET Core araçlarını kullanacak şekilde yapılandırılan birkaç Azure DevOps Hizmeti yerleşik yapı görevlerinden oluşan bir yapı oluşturun.

Her iki çözüm de geçerlidir. El ile kurulum komut dosyası kullanarak, bunları yapının bir parçası olarak karşıdan yüklediğiniz için aldığınız araçların sürümünü denetlersiniz. Yapı, oluşturmanız gereken bir komut dosyasından çalıştırılır. Bu makale yalnızca el ile seçeneğini kapsar. Azure DevOps Hizmetleri ile oluşturma görevleri oluşturma hakkında daha fazla bilgi için [Azure Ardışık Hatları](https://docs.microsoft.com/azure/devops/pipelines/index) belgelerine bakın.

Azure DevOps Hizmetleri'nde el ile kurulum komut dosyası kullanmak için yeni bir yapı tanımı oluşturun ve yapı adımı için çalışacak komut dosyasını belirtin. Bu, Azure DevOps Hizmetleri kullanıcı arabirimi kullanılarak gerçekleştirilir:

1. Yeni bir yapı tanımı oluşturarak başlayın. Oluşturmak istediğiniz yapı türünü tanımlama seçeneği sunan ekrana ulaştığınızda **Boşver** seçeneğini seçin.

   ![Boş yapı tanımı seçme](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Depoyu oluşturmak üzere yapılandırdıktan sonra yapı tanımlarına yönlendirilirsiniz. **Yapı adımEkle'yi**seçin :

   ![Yapı adımı ekleme](./media/using-ci-with-cli/add-build-step.png)

1. **Size Görev kataloğu**sunuluyor. Katalog, yapıda kullandığınız görevleri içerir. Bir komut dosyanız olduğundan, PowerShell için **Ekle** düğmesini **seçin: PowerShell komut dosyası çalıştırın.**

   ![PowerShell komut dosyası adımı ekleme](./media/using-ci-with-cli/add-powershell-script.png)

1. Yapı adımını yapılandırın. Oluşturmakta olduğunuz depodan komut dosyasını ekleyin:

   ![Çalışacak PowerShell komut dosyasını belirtme](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Yapıyı düzenleme

Bu belgenin çoğu ,NET Core araçlarını nasıl edineceklerini ve kodunuzu .NET Core ile nasıl düzenleyecekleriniz veya *gerçekte nasıl oluşturabileceğiniz*hakkında bilgi vermeden çeşitli CI hizmetlerini nasıl yapılandırabileceğinizi açıklar. Yapı sürecinin nasıl yapılandırılabildiği konusundaki seçimler, burada genel bir şekilde ele alınabilen birçok etkene bağlıdır. Yapılarınızı her teknolojiyle düzenleme hakkında daha fazla bilgi için Travis [CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)dokümantasyon kümelerinde sağlanan kaynakları ve örnekleri keşfedin.

.NET Core araçlarını kullanarak .NET Core kodunun yapılandırılmasında aldığınız iki genel yaklaşım, MSBuild'i doğrudan veya .NET Core komut satırı komutlarını kullanmakta. Hangi yaklaşımı almanız gerektiği, karmaşıklıktaki yaklaşımlar ve dengelerle konfor seviyenize göre belirlenir. MSBuild, yapı işleminizi görev ve hedef olarak ifade etme olanağı sağlar, ancak MSBuild proje dosya sözdizimini öğrenmenin ek karmaşıklığıyla birlikte gelir. .NET Core komut satırı araçlarını kullanmak belki daha kolaydır, ancak powershell gibi `bash` bir komut dosyası dilinde düzenleme mantığı yazmanızı gerektirir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET indirme - Linux](https://dotnet.microsoft.com/download?initial-os=linux)
