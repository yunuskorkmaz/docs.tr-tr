---
title: Linux dağıtımlarına .NET yükler
description: Linux 'ta .NET yükleme desteği olan Linux dağıtımları hakkında bilgi edinin.
author: adegeo
ms.author: adegeo
ms.date: 01/06/2021
ms.openlocfilehash: 2b79bccf747d37c368b61eb17d3472d75bd665b3
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104873724"
---
# <a name="install-net-on-linux"></a>Linux 'ta .NET 'i yükler

> [!div class="op_single_selector"]
>
> - [Windows’ta yükleme](windows.md)
> - [macOS’ta yükleme](macos.md)
> - [Linux'ta yükleme](linux.md)

.NET, farklı linux dağıtımlarıyla kullanılabilir. Çoğu Linux platformu ve dağıtımı, her yıl önemli bir sürüme sahiptir ve çoğu .NET yüklemek için kullanılan bir paket yöneticisi sağlar. Bu makalede, şu anda desteklenen ve hangi paket yöneticisinin kullanıldığı açıklanmaktadır.

Bu makalenin geri kalanı, .NET tarafından desteklenen her ana Linux dağıtımının bir dökümdedir. [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya Linux dağıtımı yaşam sonuna ulaşıncaya kadar tüm .NET sürümleri desteklenmeye devam eder.

En iyi uyumluluk için uzun süreli bir sürüm (LTS) sürümü seçin.

## <a name="unsupported-releases"></a>Desteklenmeyen yayınlar

Aşağıdaki .NET sürümleri ❌ artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

Bu desteklenmeyen sürümler aşağıdaki bölümlerde ayrıntılandırılmıştır ve bu sürümü yüklemeye çalışırsanız mesafmeniz farklılık gösterebilir.

## <a name="manual-installation"></a>El ile yükleme

Linux 'ta .NET yüklemek için bir paket yöneticisi kullanmak istemiyorsanız, .NET 'i aşağıdaki yollarla yükleyebilirsiniz:

- [Yaslama paketi](linux-snap.md)
- [_İnstall-DotNet.sh_ ile betikleştirilmiş install](linux-scripted-manual.md#scripted-install)
- [El ile ikili ayıklama](linux-scripted-manual.md#manual-install)

El ile yükleme yaptığınızda eksik olabilecek gerekli bağımlılıklar hakkında daha fazla bilgi için uygun dağıtım sayfasını kontrol ettiğinizden emin olun.

## <a name="alpine"></a>Alpine

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.

- ✔️, alp veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , alp veya .NET sürümünün bu alp sürümünde desteklenmediğini belirtir.
- Hem alp hem de bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Alpine                      | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3,13](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [3,12](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [3,11](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [3,10](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[3,9](linux-alpine.md)   | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌ [3.8](linux-alpine.md)   | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |

Daha fazla bilgi için bkz. [alp 'de .net 'ı Install](linux-alpine.md).

## <a name="centos"></a>CentOS

CentOS 7, Paket Yöneticisi olarak Yılayı kullanır ve CentOS 8 DNF 'yi kullanır.

Aşağıdaki tabloda, hem CentOS 7 hem de CentOS 8 ' de şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya CentOS sürümü artık desteklenene kadar desteklenmeye devam eder.

| CentOS                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Daha fazla bilgi için bkz. [CentOS 'ta .net 'ı Install](linux-centos.md).

## <a name="debian"></a>Debian

Dekim, bir paket yöneticisi olarak APT (Gelişmiş paket aracı) kullanır.

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve üzerinde desteklendikleri kaldırıcı sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [detem 'un yaşam sonuna](https://wiki.debian.org/DebianReleases)ulaştığı sürece desteklenene kadar desteklenmeye devam eder.

- ✔️, deni veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , debir veya .NET sürümünün bu Dey sürümünde desteklenmediğini belirtir.
- Her iki sürümü de ve bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Debian                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Daha fazla bilgi için bkz. [de, .net yüklemesi](linux-debian.md).

## <a name="fedora"></a>Fedora

Fedora, Paket Yöneticisi olarak DNF 'yi kullanır.

Aşağıdaki tabloda, şu anda desteklenen .NET sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ya da [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.

- ✔️, Fedora veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Fedora veya .NET sürümünün bu Fedora sürümünde desteklenmediğini belirtir.
- Hem Fedora hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Fedora                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [33](linux-fedora.md#install-net-50) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [32](linux-fedora.md#install-net-50) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[31](linux-fedora.md#install-on-older-distributions) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[30](linux-fedora.md#install-on-older-distributions) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[29](linux-fedora.md#install-on-older-distributions) | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[28](linux-fedora.md#install-on-older-distributions) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[27](linux-fedora.md#install-on-older-distributions) | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |

Daha fazla bilgi için bkz. [Fedora 'da .net 'ı kurma](linux-fedora.md).

## <a name="opensuse"></a>openSUSE

openSUSE paket yöneticisi olarak zypper kullanır.

Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE sürümü artık desteklenene kadar desteklenmeye devam eder.

| openSUSE                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Daha fazla bilgi için bkz. [openSUSE 'e .net 'ı yükler](linux-opensuse.md).

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) paket yöneticisi olarak yıum (RHEL 7) ve DNF (RHEL 8) kullanır.

Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, RHEL veya .NET sürümünün hala desteklendiğini gösterir.
- A ❌ , RHEL veya .NET sürümünün bu RHEL sürümünde desteklenmediğini belirtir.
- Hem RHEL hem de .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| RHEL                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [7](linux-rhel.md#rhel-7--net-50) | ✔️ 2,1        | ✔️ [3,1](linux-rhel.md#rhel-7--net-core-31)        | ✔️ [5,0](linux-rhel.md#rhel-7--net-50) |

Daha fazla bilgi için bkz. [RHEL 'de .net 'ı yükler](linux-rhel.md).

## <a name="sles"></a>SLES

SLES, Paket Yöneticisi olarak zypper kullanır.

Aşağıdaki tabloda, hem SLES 12 SP2 hem de SLES 15 üzerinde desteklenen .NET sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya SLES sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, SLES veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , SLES veya .NET sürümünün bu SLES sürümünde desteklenmediğini belirtir.
- Her iki SLES sürümü ve bir .NET sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| SLES                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Daha fazla bilgi için bkz. [SLES 'de .net 'ı yükler](linux-sles.md).

## <a name="ubuntu"></a>Ubuntu

Ubuntu bir paket yöneticisi olarak APT (Gelişmiş paket aracı) kullanır.

Aşağıdaki tablo Ubuntu ve .NET Destek durumunu temsil eder.

- ✔️, Ubuntu veya .NET sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Ubuntu veya .NET sürümünün bu Ubuntu sürümünde desteklenmediğini belirtir.
- Ubuntu ve .NET sürümünün her ikisi de ✔️ sahip olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3.1 | .NET 5.0 |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,10](linux-ubuntu.md#2010-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ✔️ [20,04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[19,10](linux-ubuntu.md#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[19,04](linux-ubuntu.md#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌ 5,0 |
| ❌[18,10](linux-ubuntu.md#1810-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ✔️ [18,04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |
| ❌[17,10](linux-ubuntu.md#1710-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[17,04](linux-ubuntu.md#1704-)       | ✔️ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ❌[16,10](linux-ubuntu.md#1610-)       | ❌ 2,1        | ❌ 3,1        | ❌ 5,0 |
| ✔️ [16,04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 |

Daha fazla bilgi için bkz. [Ubuntu 'da .net 'ı kurma](linux-ubuntu.md).

## <a name="next-steps"></a>Sonraki adımlar

- [.Net 'in zaten yüklü olup olmadığını denetleme](how-to-detect-installed-versions.md?pivots=os-linux).
- [Öğretici: Visual Studio Code yeni bir uygulama oluşturun](../tutorials/with-visual-studio-code.md).
- [Öğretici: bir .NET uygulamasını Kapsayıize](../docker/build-container.md)edin.
