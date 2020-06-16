---
title: .NET Core ve Linux dağıtımlarını yükler
description: Linux 'ta .NET Core 'u yüklemeyi destekleyen Linux dağıtımları hakkında bilgi edinin.
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: fbb057825395d4e024f99e1abbd1a6e65ba1dce7
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768359"
---
# <a name="install-net-core-on-linux"></a>Linux 'ta .NET Core 'u yükler

.NET Core, farklı linux dağıtımlarıyla kullanılabilir. Çoğu Linux platformu ve dağıtımı, her yıl önemli bir sürüme sahiptir ve çoğu .NET Core 'u yüklemek için kullanılan bir paket yöneticisi sağlar. Bu makalede, şu anda desteklenen ve hangi paket yöneticisinin kullanıldığı açıklanmaktadır.

Bu makalenin geri kalanı, .NET Core 'un desteklediği her bir ana Linux dağıtımının bir dökümdedir. [.NET Core 'un sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya Linux dağıtımı yaşam sonuna ulaşıncaya kadar tüm .NET Core sürümleri desteklenmeye devam eder.

En iyi uyumluluk için uzun süreli bir sürüm (LTS) sürümü seçin.

## <a name="unsupported-releases"></a>Desteklenmeyen yayınlar

Aşağıdaki .NET Core sürümleri ❌ artık desteklenmemektedir. Bunlara yönelik İndirilenler hala yayımlandı olarak kalmaya devam eder:

- 3.0
- 2,2
- 2.0

Bu desteklenmeyen sürümler aşağıdaki bölümlerde ayrıntılandırılmıştır ve bu sürümü yüklemeye çalışırsanız mesafmeniz farklılık gösterebilir.

## <a name="alpine"></a>Alpine

Alp için yükleyiciler yok. [Install betiğini](linux-alpine.md#scripted-install) kullanmanız veya [el ile Install](linux-alpine.md#manual-install) yönergelerini izlemeniz gerekir.

Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve ' de desteklendiği alp sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşana](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [alçam sürümü yaşam sonuna ulaştığında](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases)desteklenene kadar desteklenmeye devam eder.

- ✔️, alp veya .NET Core sürümünün hala desteklendiğini gösterir.
- A ❌ , alp veya .NET Core sürümünün bu Alu sürümünde desteklenmediğini belirtir.
- Hem alp hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Alpine                      | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3,12](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [3,11](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [3,10](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [3,9](linux-alpine.md)   | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[3,8](linux-alpine.md)   | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |

Daha fazla bilgi için bkz. [alp 'de .NET Core 'U yüklemeye](linux-alpine.md).

## <a name="centos"></a>CentOS

CentOS 7, Paket Yöneticisi olarak Yılayı kullanır ve CentOS 8 DNF 'yi kullanır.

Aşağıdaki tabloda, hem CentOS 7 hem de CentOS 8 ' de şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya CentOS sürümü artık desteklenene kadar desteklenmeye devam eder.

| CentOS                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Daha fazla bilgi için bkz. [CentOS 'a .NET Core 'U yüklemeyin](linux-centos.md).

## <a name="debian"></a>Debian

Dekim, bir paket yöneticisi olarak APT (Gelişmiş paket aracı) kullanır.

Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve üzerinde desteklendikleri kaldırıcı sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core 'un sürümü destek sonuna ulaşıncaya](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [detem 'ın kullanım ömrü sona](https://wiki.debian.org/DebianReleases)erecek kadar desteklenmeye devam eder.

- ✔️, debir veya .NET Core sürümünün hala desteklendiğini gösterir.
- A ❌ , debir veya .NET Core sürümünün bu Dey sürümünde desteklenmediğini belirtir.
- Her iki sürüm de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Debian                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |

## <a name="fedora"></a>Fedora

Fedora, Paket Yöneticisi olarak DNF 'yi kullanır.

Aşağıdaki tabloda, şu anda desteklenen .NET Core sürümlerinin ve desteklenen Fedora sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core 'un sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya [Fedora sürümü yaşam sonuna](https://fedoraproject.org/wiki/End_of_life)ulaşana kadar desteklenmeye devam eder.

- ✔️, Fedora veya .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Fedora veya .NET Core sürümünün bu Fedora sürümünde desteklenmediğini belirtir.
- Hem Fedora hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Fedora                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[30](linux-fedora.md#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Önizleme |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Önizleme |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |

Daha fazla bilgi için bkz. [Fedora 'da .NET Core 'U kurma](linux-fedora.md).

## <a name="opensuse"></a>openSUSE

openSUSE paket yöneticisi olarak zypper kullanır.

Aşağıdaki tabloda, openSUSE 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core 'un sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya openSUSE 'un sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, openSUSE veya .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ , openSUSE veya .NET Core sürümünün bu openSUSE sürümünde desteklenmediğini belirtir.
- Hem openSUSE hem de .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| openSUSE                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) paket yöneticisi olarak yıum (RHEL 7) ve DNF (RHEL 8) kullanır.

Aşağıdaki tabloda, hem RHEL 7 hem de RHEL 8 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core sürümü destek sonuna](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya RHEL sürümüne ulaşıncaya kadar desteklenmeye devam eder.

- ✔️, RHEL veya .NET Core sürümünün hala desteklendiğini gösterir.
- A ❌ , RHEL veya .NET Core sürümünün bu RHEL sürümünde desteklenmediğini belirtir.
- Hem RHEL hem de bir .NET Core sürümü ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="sles"></a>SLES

SLES, Paket Yöneticisi olarak zypper kullanır.

Aşağıdaki tabloda, hem SLES 12 SP2 hem de SLES 15 üzerinde şu anda desteklenen .NET Core sürümlerinin bir listesi verilmiştir. Bu sürümler, [.NET Core sürümü destek sonu](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) veya SLES sürümü artık desteklenene kadar desteklenmeye devam eder.

- ✔️, SLES veya .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ , SLES veya .NET Core sürümünün bu SLES sürümünde desteklenmediğini belirtir.
- SLES ve .NET Core sürümlerinin her ikisi de ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| SLES                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [12 SP2](linux-sles.md#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

## <a name="ubuntu"></a>Ubuntu

Ubuntu bir paket yöneticisi olarak APT (Gelişmiş paket aracı) kullanır.

Aşağıdaki tablo Ubuntu ve .NET Core 'un destek durumunu temsil eder.

- ✔️, Ubuntu veya .NET Core sürümünün hala desteklendiğini gösterir.
- Bir ❌ , Ubuntu veya .NET Core sürümünün bu Ubuntu sürümünde desteklenmediğini belirtir.
- Ubuntu ve .NET Core sürümlerinin her ikisi de ✔️ olduğunda, bu işletim sistemi ve .NET birleşimi desteklenir.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 Preview (yalnızca el ile yüklenir) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ✔️ [19,10](linux-ubuntu.md#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[19,04](linux-ubuntu.md#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌5,0 Önizleme |
| ❌[18,10](linux-ubuntu.md#1810-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |
| ✔️ [18,04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |
| ❌[17,10](linux-ubuntu.md#1710-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |
| ❌[17,04](linux-ubuntu.md#1704-)       | ✔️ 2,1        | ❌3,1        | ❌5,0 Önizleme |
| ❌[16,10](linux-ubuntu.md#1610-)       | ❌2,1        | ❌3,1        | ❌5,0 Önizleme |
| ✔️ [16,04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 Preview |

Daha fazla bilgi için bkz. [Ubuntu 'da .NET Core 'U kurma](linux-ubuntu.md).
