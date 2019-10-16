---
title: Linux üzerinde .NET Core önkoşulları
description: Linux makinelerde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen Linux sürümleri ve .NET Core bağımlılıkları.
author: leecow
ms.author: leecow
ms.date: 10/11/2019
ms.openlocfilehash: bb9049059de9d8208fc92234b28acdfb3d7f0cb3
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318334"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux üzerinde .NET Core önkoşulları

Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için gereken bağımlılıklar gösterilmektedir. Desteklenen Linux dağıtımları/sürümleri ve aşağıdaki bağımlılıklar, Linux üzerinde .NET Core uygulamaları geliştirmenin iki yolu için geçerlidir:

* [En sevdiğiniz düzenleyicinizle komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK paketi üretim sunucuları/ortamları için gerekli değildir. Üretim ortamlarına dağıtılan uygulamalar için yalnızca .NET Core çalışma zamanı paketi gereklidir. .NET Core çalışma zamanı, uygulamalar ile birlikte bulunan bir dağıtımın parçası olarak dağıtılır, ancak çerçeveye bağımlı dağıtılan uygulamalar için ayrı olarak dağıtılmalıdır. Çerçeveye bağımlı ve kendi kendine içerilen dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md). Ayrıca, belirli yönergeler için [kendi Içindeki Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) bakın.

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır. 

İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir):

> [!NOTE]
> @No__t-0 simgesi en düşük sürümü temsil eder.

| ATAYAMADı                             | Version               | Mimarileri    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6 +, 7                 | X64 |
| Oracle Linux                   | 7                     | X64 |
| CentOS                         | 7                     | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux Mint                     | 18 +                   | X64 |
| openSUSE                       | 15 +                   | X64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | X64 |
| Alp Linux                   | 3.8 +                  | x64, ARM64 |

.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2).

.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

> [!NOTE]
> @No__t-0 simgesi en düşük sürümü temsil eder.

| ATAYAMADı                             |  Version                |  Mimarileri   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  15 +                    | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | X64 |
| Alp Linux                   |  3.7 +                   | X64 |

.NET Core 2,2 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,2 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) .

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).

.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

| ATAYAMADı                             |  Version                |  Mimarileri   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | X64 |
| Oracle Linux                   |  7                      | X64 |
| CentOS                         |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  42.3 +                  | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | X64 |
| Alp Linux                   |  3.7 +                   | X64 |

.NET Core 2,1 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 2,1 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) .

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Aşağıdakiler örnek olarak verilmiştir. Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları aşağıdaki kitaplıkların yüklü olmasını gerektirir:

* liblttng-ust0
* libcurl3 (14. x ve 16. x için)
* libcurl4 (18. x için)
* libssl 1.0.0
* libkrb5-3
* zlib1g
* libicu52 (14. x için)
* libicu55 (16. x için)
* libicu57 (17. x için)
* libicu60 (18. x için)

.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:

* libunwind8
* libuuid1

*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:

* libgdiplus (sürüm 6.0.1 veya üzeri)

> [!NOTE]
> Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir. En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS ve Fedora

CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:

* lttng-ust
* libkıvrık
* OpenSSL-libs
* krb5-libs
* libıu
* zlib

Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, COMPAT-openssl10 yüklemeniz gerekir.

.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:

* librüzgar
* libuuid

Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:

* libgdiplus (sürüm 6.0.1 veya üzeri)

> [!NOTE]
> CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir. En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Yerel yükleyicilerle .NET Core bağımlılıklarını yükleme

.NET Core yerel yükleyicileri desteklenen Linux dağıtımları/sürümleri için kullanılabilir. Yerel yükleyiciler sunucuya yönetici (sudo) erişimi gerektirir. Yerel bir yükleyiciyi kullanmanın avantajı, tüm .NET Core yerel bağımlılıklarının yüklü olması. Yerel yükleyiciler Ayrıca sistem genelinde .NET Core SDK de yükler.

Linux 'ta iki yükleyici paketi seçeneği vardır:

* Bir akış tabanlı Paket Yöneticisi, Ubuntu için apt-get veya CentOS/RHEL için de rivı kullanma.
* Paketlerin kendisini, DEB veya RPM 'yi kullanma.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core yükleyici betiği ile betik yüklemeleri

[DotNet-install betikleri](./tools/dotnet-install-script.md) , CLI araç zinciri ve paylaşılan çalışma zamanının yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır. Betiği <https://dot.net/v1/dotnet-install.sh> ' dan indirebilirsiniz.

Komut dosyası, şu anda .NET Core 1,1 olan en son "LTS" sürümünü yüklemek için varsayılan değerdir. .NET Core 2,1 yüklemek için betiği aşağıdaki anahtarla çalıştırın:

```bash
./dotnet-install.sh -c Current
```

Yükleyici Bash betiği, Otomasyon senaryolarında ve yönetici olmayan yüklemelerde kullanılır. Bu betik Ayrıca PowerShell anahtarlarını okur, bu nedenle Linux/OS X sistemlerinde komut dosyasıyla kullanılabilirler.

## <a name="troubleshoot"></a>Sorun giderme

Desteklenen bir Linux dağıtımında/sürümünde .NET Core yüklemesiyle ilgili sorunlar yaşıyorsanız, yüklü dağıtımlarınız/sürümleriniz için aşağıdaki konulara bakın:

* [.NET Core 3,0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [.NET Core 2,2 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [.NET Core 2,1 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [.NET Core 1,1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [.NET Core 1,0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0)
