---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları-.NET Core
description: Windows, Linux ve macOS 'ta .NET Core SDK ve çalışma zamanı yüklemek için işletim sistemi ve CPU mimarisi ön koşullarını ayrıntılı olarak izleyin.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a535048fc8756b55068098ad61fdc37fc8c1f04e
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837005"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Core bağımlılıkları ve gereksinimleri

Bu makalede .NET Core tarafından desteklenen işletim sistemleri ve CPU mimarisinin ayrıntıları verilir.

## <a name="supported-operating-systems"></a>Supported operating systems

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31tabnetcore31"></a>[.NET Core 3,1](#tab/netcore31)

Aşağıdaki Windows sürümleri .NET Core 3,1 ile desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemci                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64, ARM32      |

.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Aşağıdaki Windows sürümleri .NET Core 3,0 ile desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemci                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64, ARM32      |

.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

Aşağıdaki Windows sürümleri .NET Core 2,2 ile desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemci                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                   | x64, ARM32      |

.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

Aşağıdaki Windows sürümleri .NET Core 2,1 ile desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimariler   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemci                | 7 SP1 +, 8,1                    | x64, x86        |
| Windows 10 Istemcisi             | Sürüm 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 SP1 +                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803 +                  | x64            |

.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7/Vista/8,1/Server 2008 R2

Aşağıdaki Windows sürümlerine .NET SDK veya çalışma zamanı yüklüyorsanız ek bağımlılıklar gereklidir:

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Aşağıdakileri yükleyin:

- [Microsoft Visual C++ 2015 yeniden dağıtılabilir güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:

> *API-MS-Win-CRT-Runtime-L1-1 -0. dll* dosyası bilgisayarınızda bulunmadığı için program başlatılamıyor. Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.
>
> \- veya -
>
> *Hostfxr. dll* kitaplığı bulundu, ancak *C:\\\<path_to_app >\\hostfxr. dll* ' den yükleniyor.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31tabnetcore31"></a>[.NET Core 3,1](#tab/netcore31)

.NET Core 3,1, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

.NET Core 3,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                             | Sürüm               | Mimariler    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | X64 |
| CentOS                         | 7 +                    | X64 |
| Oracle Linux                   | 7 +                    | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux Mint                     | 18 +                   | X64 |
| openSUSE                       | 15 +                   | X64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | X64 |
| Alp Linux                   | 3.10 +                 | x64, ARM64 |

.NET Core 3,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

.NET Core 3,1 ' i ARM64 üzerinde yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> ARM64 desteği Linux Kernel 4,14 veya üstünü gerektirir. Bazı Linux dağıtımları, diğerleri bu gereksinimi karşılar. Örneğin, Ubuntu 18,04 desteklenir, ancak Ubuntu 16,04 değildir.

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3,0, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

.NET Core 3,0, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                             | Sürüm               | Mimariler    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | X64 |
| CentOS                         | 7 +                    | X64 |
| Oracle Linux                   | 7 +                    | X64 |
| Fedora                         | 29 +                   | X64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Linux Mint                     | 18 +                   | X64 |
| openSUSE                       | 15 +                   | X64 |
| SUSE Enterprise Linux (SLES)   | 12 SP2 +               | X64 |
| Alp Linux                   | 3.8 +                  | x64, ARM64 |

.NET Core 3,0 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 3,0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22tabnetcore22"></a>[.NET Core 2,2](#tab/netcore22)

.NET Core 2,2, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

.NET Core 2,2, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                             |  Sürüm                |  Mimariler   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | X64 |
| CentOS                         |  7                      | X64 |
| Oracle Linux                   |  7                      | X64 |
| Fedora                         |  29, 30                 | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10, 19,04    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | X64 |
| openSUSE                       |  15 +                    | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | X64 |
| Alp Linux                   |  3.8 +                   | X64 |

.NET Core 2,2 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

.NET Core 2,1, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır.

.NET Core 2,1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| İşletim Sistemi                             |  Sürüm                |  Mimariler   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | X64 |
| CentOS                         |  7 +                     | X64 |
| Oracle Linux                   |  7 +                     | X64 |
| Fedora                         |  29 +                    | X64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04, 19,10    | x64, ARM32 |
| Linux Mint                     |  17 +                    | X64 |
| openSUSE                       |  15 +                    | X64 |
| SUSE Enterprise Linux (SLES)   |  12 SP2 +                | X64 |
| Alp Linux                   |  3.8 +                   | X64 |

.NET Core 2,1 desteklenen işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi için bkz. [.net core 2,1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Linux dağıtımına bağlı olarak ek bağımlılıklar yüklemeniz gerekebilir.

> [!IMPORTANT]
> Tam sürümler ve adlar, tercih ettiğiniz Linux dağıtımında biraz farklılık gösterebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları aşağıdaki kitaplıkların yüklenmesini gerektirir:

- liblttng-ust0
- libcurl3 (14. x ve 16. x için)
- libcurl4 (18. x için)
- libssl 1.0.0
- libkrb5-3
- zlib1g
- libicu52 (14. x için)
- libicu55 (16. x için)
- libicu57 (17. x için)
- libicu60 (18. x için)

*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız vardır:

- libgdiplus (sürüm 6.0.1 veya üzeri)

> [!WARNING]
> Ubuntu 'ın çoğu sürümü libgdiplus 'in önceki bir sürümünü içerir. En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS ve Fedora

CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:

- lttng-ust
- libkıvrık
- OpenSSL-libs
- krb5-libs
- libıu
- zlib

Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 Ise, **COMPAT-openssl10**yüklemeniz gerekir.

.NET Core 2,0 için aşağıdaki bağımlılıklar da gereklidir:

- librüzgar
- libuuid

Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

*System. Drawing. Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılığa de ihtiyacınız olacaktır:

- libgdiplus (sürüm 6.0.1 veya üzeri)

> [!WARNING]
> CentOS ve Fedora sürümlerinin çoğu, libgdiplus 'in önceki bir sürümünü içerir. En son bir libgdiplus sürümünü sisteminize mono deposunu ekleyerek yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

.NET Core aşağıdaki macOS sürümleriyle desteklenir:

> [!NOTE]
> `+` sembol en düşük sürümü temsil eder.

| .NET Core sürümü | macOS                 | Mimariler |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | High Sierra (10.13 +)  | X64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | High Sierra (10.13 +)  | X64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | X64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | X64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

## <a name="libgdiplus"></a>libgdiplus

*System. Drawing. Common* derlemesini kullanan .NET Core Uygulamaları, libgdiplus 'in yüklenmesini gerektirir.

Libgdiplus almanın kolay bir yolu, macOS için [homebrew ("Brew")](https://brew.sh/) paket yöneticisini kullanmaktır. *Brew*yükledikten sonra, bir Terminal (komut) isteminde aşağıdaki komutları yürüterek libgdiplus yükleme yapın:

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Sonraki adımlar

- Uygulama geliştirmek ve çalıştırmak için, [.NET Core SDK](sdk.md) (çalışma zamanını içerir).
- Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma zamanı](runtime.md)'nı yüklersiniz.
