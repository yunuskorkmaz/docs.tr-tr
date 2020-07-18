---
title: .NET Core SDK ve araçlarla sürekli tümleştirme (CI)
description: .NET Core SDK ve araçlarını sürekli tümleştirme ile yapı sunucusunda nasıl kullanacağınızı öğrenin.
ms.date: 05/18/2017
ms.openlocfilehash: ddccb477bc112157a155e2217e04c329e7ab51c5
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415997"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a>Sürekli tümleştirme (CI) içinde .NET Core SDK ve araçları kullanma

Bu belge, yapı sunucusunda .NET Core SDK ve araçlarını kullanarak özetlenmektedir. .NET Core araç takımı hem etkileşimli olarak hem de bir geliştirici komut isteminde komutlar yazdığında ve sürekli tümleştirme (CI) sunucusunun bir yapı betiğini çalıştırdığı otomatik olarak çalışır. Komutlar, Seçenekler, girişler ve çıktılar aynıdır ve sağladığınız tek şey, uygulamayı derlemek için araç ve bir sistem elde etmenin bir yoludur. Bu belge, derleme betiklerinizi tasarlamaya ve oluşturmaya yönelik önerilere sahip CI için araç alımı senaryolarına odaklanır.

## <a name="installation-options-for-ci-build-servers"></a>CI derleme sunucuları için yükleme seçenekleri

### <a name="using-the-native-installers"></a>Yerel yükleyicileri kullanma

Yerel yükleyiciler macOS, Linux ve Windows için kullanılabilir. Yükleyiciler, derleme sunucusuna yönetici (sudo) erişimi gerektirir. Yerel bir yükleyiciyi kullanmanın avantajı, araçları çalıştırmak için gerekli tüm yerel bağımlılıkların yüklenidir. Yerel yükleyiciler Ayrıca SDK 'nın sistem genelinde bir yüklemesini de sağlar.

macOS kullanıcıları paket yükleyicilerini kullanmalıdır. Linux 'ta, bir akış tabanlı Paket Yöneticisi (örneğin, Ubuntu veya CentOS için apt-get) veya paketlerin kendilerini, DEB veya RPM 'yi kullanmayı tercih eden bir seçim vardır. Windows 'ta, MSI yükleyicisini kullanın.

En son kararlı ikili dosyalar [.net indirmelerinde](https://dotnet.microsoft.com/download)bulunur. En son (ve kararsız) yayın öncesi araçları kullanmak istiyorsanız, [DotNet/Core-SDK GitHub deposunda](https://github.com/dotnet/core-sdk#installers-and-binaries)sunulan bağlantıları kullanın. Linux dağıtımları için `tar.gz` Arşivler (olarak da bilinir `tarballs` ) kullanılabilir; .NET Core yüklemek için arşivlerdeki yükleme betikleri kullanın.

### <a name="using-the-installer-script"></a>Yükleyici betiğini kullanma

Yükleyici betiğinin kullanılması, yapı sunucunuzda yönetimsel olmayan yüklemeye ve araçları almak için kolay otomatikleştirilmesine izin verir. Betik, araçları indirme ve varsayılan veya belirtilen bir konuma çıkarma işlemini gerçekleştirir. Ayrıca, yüklemek istediğiniz bir araç sürümünü ve tüm SDK 'Yı mı yoksa yalnızca paylaşılan çalışma zamanını mı yüklemek istediğinizi de belirtebilirsiniz.

Yükleyici betiği, SDK 'nın istenen sürümünü getirmek ve yüklemek üzere Yapı başlangıcında çalışmak için otomatikleştirilir. *İstediğiniz sürüm* , projelerinizin derlemek için IHTIYAç duyduğu SDK 'nın herhangi bir sürümüdür. Komut dosyası, SDK 'Yı sunucudaki yerel bir dizine yüklemenize, yüklü konumdan araçları çalıştırmanıza ve sonra da derlemeyi (ya da CI hizmeti temizlemeye izin verir) derlemeden sonra temizleyebilir. Bu, tüm derleme sürecinizi kapsülleme ve yalıtıma sağlar. Yükleme betiği başvurusu [DotNet yükleme](dotnet-install-script.md) makalesinde bulunur.

> [!NOTE]
> **Azure DevOps Services**
>
> Yükleyici betiği kullanılırken, yerel bağımlılıklar otomatik olarak yüklenmez. İşletim sisteminde yoksa yerel bağımlılıkları yüklemelisiniz. Daha fazla bilgi için bkz. [.NET Core Dependencies ve gereksinimleri](../install/windows.md#dependencies).

## <a name="ci-setup-examples"></a>CI kurulum örnekleri

Bu bölümde, bir PowerShell veya bash betiği kullanılarak el ile yapılan bir kurulum ve hizmet olarak yazılım (SaaS) CI çözümlerinin bir açıklaması açıklanmaktadır. Kapsanan SaaS CI çözümleri, [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).

### <a name="manual-setup"></a>El ile kurulum

Her SaaS hizmeti bir yapı işlemi oluşturmak ve yapılandırmak için kendi yöntemlerine sahiptir. Listelenenlerden farklı SaaS çözümü kullanıyorsanız veya önceden paketlenmiş desteğin ötesinde özelleştirme yapmayı düşünüyorsanız, en az bir el ile yapılandırma gerçekleştirmeniz gerekir.

Genel olarak, el ile kurulum, araçların bir sürümünü (veya araçların en son gecelik sürümlerini) almanızı ve derleme betiğinizi çalıştırmanızı gerektirir. .NET Core komutlarını düzenlemek veya yapı sürecini özetleyen bir proje dosyası kullanmak için bir PowerShell veya bash betiği kullanabilirsiniz. [Orchestration bölümü](#orchestrating-the-build) , bu seçenekler hakkında daha fazla ayrıntı sağlar.

El ile CI derleme sunucusu kurulumu gerçekleştiren bir komut dosyası oluşturduktan sonra, test amacıyla kodunuzu yerel olarak derlemek için geliştirme makinenizde kullanın. Betiğin yerel olarak çalıştığını onaylayıp CI Build sunucunuza dağıtın. Görece basit bir PowerShell betiği, .NET Core SDK nasıl alınacağını ve bir Windows Build Server 'a nasıl yükleneceğini göstermektedir:

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

Betik sonunda derleme işleminiz için uygulama sağlarsınız. Komut dosyası araçları alır ve yapı işleminizi yürütür. UNIX makineler için aşağıdaki Bash betiği, PowerShell komut dosyasında açıklanan eylemleri benzer bir şekilde gerçekleştirir:

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

Dili ve anahtarı kullanarak .NET Core SDK yüklemek için [Travis CI](https://travis-ci.org/) 'yi yapılandırabilirsiniz `csharp` `dotnet` . Daha fazla bilgi için bkz. [C#, F # veya Visual Basic projesi oluşturma](https://docs.travis-ci.com/user/languages/csharp/)üzerindeki resmi TRAVIS CI belgeleri. Topluluk tarafından korunan `language: csharp` Dil tanımlayıcısının F # ve mono dahil tüm .NET dilleri için kullandığı Travis CI bilgilerine eriştiğinizde dikkat edin.

Travis CI hem macOS hem de Linux işlerini, uygulamanızın yapı kombinasyonlarını kapsayacak çalışma zamanı, ortam ve dışlamaları/eklemeleri belirlediğiniz bir *derleme matrisi*içinde çalıştırır. Daha fazla bilgi için bkz. Travis CI belgelerindeki [derlemeyi özelleştirme](https://docs.travis-ci.com/user/customizing-the-build) makalesi. MSBuild tabanlı araçlar, paketteki LTS (1.0. x) ve geçerli (1.1. x) çalışma zamanlarını içerir; Bu nedenle SDK 'yı yükleyerek, oluşturmanız gereken her şeyi alırsınız.

### <a name="appveyor"></a>AppVeyor

[AppVeyor](https://www.appveyor.com/) , derleme Worker görüntüsüyle .NET Core 1.0.1 SDK 'sını yüklüyor `Visual Studio 2017` . .NET Core SDK farklı sürümlerine sahip diğer derleme görüntüleri mevcuttur. Daha fazla bilgi için AppVeyor docs içindeki [AppVeyor. yıml örneğine](https://github.com/dotnet/docs/blob/master/appveyor.yml) ve [Build Worker Images](https://www.appveyor.com/docs/build-environment/#build-worker-images) makalesine bakın.

.NET Core SDK ikilileri, Install betiği kullanılarak bir alt dizinde indirilir ve sıkıştırılırsınız ve ardından `PATH` ortam değişkenine eklenir. .NET Core SDK birden çok sürümüyle tümleştirme testlerini çalıştırmak için bir derleme matrisi ekleyin:

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a>Azure DevOps Services

Aşağıdaki yaklaşımlardan birini kullanarak .NET Core projeleri oluşturmak için Azure DevOps Services yapılandırın:

1. Komutlarınızı kullanarak [el ile kurulum adımından](#manual-setup) betiği çalıştırın.
1. .NET Core araçları kullanmak üzere yapılandırılmış çeşitli Azure DevOps Services yerleşik oluşturma görevlerinden oluşan bir yapı oluşturun.

Her iki çözüm de geçerlidir. El ile kurulum betiği kullanarak, bunları yapılandırmanın bir parçası olarak indirdiklerinden, aldığınız araçların sürümünü kontrol edersiniz. Derleme, oluşturmanız gereken bir betikten çalıştırılır. Bu makale yalnızca el ile seçeneği içerir. Azure DevOps Services yapı görevleriyle derleme oluşturma hakkında daha fazla bilgi için [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) belgelerine bakın.

Azure DevOps Services içinde el ile kurulum betiği kullanmak için yeni bir derleme tanımı oluşturun ve derleme adımı için çalıştırılacak betiği belirtin. Bu, Azure DevOps Services kullanıcı arabirimi kullanılarak gerçekleştirilir:

1. Yeni bir derleme tanımı oluşturarak başlayın. Oluşturmak istediğiniz bir yapı türünü tanımlama seçeneği sunan ekrana ulaştığınızda **boş** seçeneğini belirleyin.

   ![Boş bir derleme tanımı seçme](./media/using-ci-with-cli/select-empty-build-definition.png)

1. Derlemeyi derlemek için yapılandırdıktan sonra, derleme tanımlarına yönlendirilirsiniz. **Yapı Ekle adımını**seçin:

   ![Derleme adımı ekleme](./media/using-ci-with-cli/add-build-step.png)

1. **Görev kataloğu**ile karşılaşırsınız. Katalog, derlemede kullandığınız görevleri içerir. Bir betiğinizin olduğundan, PowerShell için **Ekle** düğmesini seçin **: PowerShell betiği çalıştırın**.

   ![PowerShell betiği ekleme adımı](./media/using-ci-with-cli/add-powershell-script.png)

1. Yapı adımını yapılandırın. Oluşturmakta olduğunuz depodan betiği ekleyin:

   ![Çalıştırılacak PowerShell betiğini belirtme](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a>Derlemeyi düzenleme

Bu belgenin çoğunda, .NET Core ile kodunuzu *düzenleme veya yapılandırma*hakkında bilgi sağlamadan .NET Core araçlarının nasıl elde edileceğini ve çeşitli CI hizmetlerinin nasıl yapılandırılacağı açıklanmaktadır. Yapı işlemini nasıl yapılandıracağınıza ilişkin seçimler burada genel bir şekilde ele alınmayan birçok etkene bağlıdır. Her teknolojiyle derlemelerinizi düzenleme hakkında daha fazla bilgi için, [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)ve [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index)belge kümelerinde sağlanan kaynakları ve örnekleri inceleyin.

.NET Core araçları kullanılarak .NET Core kodu için derleme işlemini yapılandırırken uygulamanız gereken iki genel yaklaşım doğrudan MSBuild 'i veya .NET Core komut satırı komutlarını kullanmaktır. Uygulamanız gereken yaklaşım, yaklaşımlar ve yüksek düzeyde karmaşıklığa sahip olan rahatlık düzeyinize göre belirlenir. MSBuild, derleme işleminizi görev ve hedef olarak ifade etme olanağı sağlar, ancak öğrenme MSBuild proje dosyası sözdiziminin ek karmaşıklığı ile birlikte gelir. .NET Core komut satırı araçlarının kullanılması belki de basittir, ancak düzenleme mantığını veya PowerShell gibi bir komut dosyası dilinde yazmanızı gerektirir `bash` .

## <a name="see-also"></a>Ayrıca bkz.

- [.NET İndirmeleri-Linux](https://dotnet.microsoft.com/download?initial-os=linux)
