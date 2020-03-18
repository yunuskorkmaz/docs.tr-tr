---
title: .NET Core SDK ve çalışma zamanı bağımlılıkları - .NET Core
description: .NET Core SDK'yı ve Windows, Linux ve macOS'ta çalışma süresini yüklemek için işletim sistemi ve CPU mimarisi ön koşulları ayrıntılarıyla anlatılmaktadır.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157822"
---
# <a name="net-core-dependencies-and-requirements"></a>.NET Temel bağımlılıklar ve gereksinimler

Bu makalede, işletim sistemleri ve CPU mimarisi .NET Core tarafından desteklenen ayrıntılar.

## <a name="supported-operating-systems"></a>Desteklenen işletim sistemleri

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Çekirdek 3.1](#tab/netcore31)

Aşağıdaki Windows sürümleri .NET Core 3.1 ile desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimarileri   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1+, 8.1                    | x64, x86        |
| Windows 10 İstemci             | Sürüm 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803+                  | x64, ARM32      |

.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

Aşağıdaki Windows sürümleri .NET Core 3.0 ile desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimarileri   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1+, 8.1                    | x64, x86        |
| Windows 10 İstemci             | Sürüm 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Sunucu                   | Sürüm 1803+                  | x64, ARM32      |

.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

Aşağıdaki Windows sürümleri .NET Core 2.2 ile desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimarileri   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1+, 8.1                    | x64, x86        |
| Windows 10 İstemci             | Sürüm 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803+                   | x64, ARM32      |

.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Aşağıdaki Windows sürümleri .NET Core 2.1 ile desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                            | Sürüm                        | Mimarileri   |
| ----------------------------- | ------------------------------ | --------------- |
| Windows İstemcisi                | 7 SP1+, 8.1                    | x64, x86        |
| Windows 10 İstemci             | Sürüm 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Sunucu                   | Sürüm 1803+                  | x64,            |

.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Sunucu 2008 R2

.NET SDK'yı veya çalışma süresini aşağıdaki Windows sürümlerine yüklüyorsanız ek bağımlılıklar gereklidir:

- Windows 7 SP1
- Windows Vista SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Aşağıdakileri yükleyin:

- [Microsoft Visual C++ 2015 Yeniden Dağıtılabilir Güncelleştirme 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Aşağıdaki hatalardan biriyle karşılaşırsanız yukarıdaki gereksinimler de gereklidir:

> *Api-ms-win-crt-runtime-l1-1-0.dll* bilgisayarınızdan eksik olduğu için program başlatılamaz. Bu sorunu gidermek için programı yeniden yüklemeyi deneyin.
>
> \-veya -
>
> Kütüphane *hostfxr.dll* bulundu, ancak *C\\\<yükleme: \\path_to_app>hostfxr.dll* başarısız oldu.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Çekirdek 3.1](#tab/netcore31)

.NET Core 3.1, Linux'u tek bir işletim sistemi olarak ele alıyor. Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.

.NET Core 3.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                             | Sürüm               | Mimarileri    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16,04+                | x64, ARM32, ARM64 |
| Linux Darphane                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Kurumsal Linux (SLES)   | 12 SP2+               | x64 |
| Alp Linux                   | 3.10+                 | x64, ARM64 |

.NET Core 3.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md)bkz.

ARM64'e .NET Core 3.1'in nasıl yüklenir (çekirdek 4.14+) nasıl yüklenirhakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.

> [!IMPORTANT]
> ARM64 desteği Linux çekirdeği 4.14 veya daha yüksek gerektirir. Bazı linux dağıtımları bu gereksinimi karşılarken, diğerleri bunu karşılamaz. Örneğin, Ubuntu 18.04 desteklenir, ancak Ubuntu 16.04 desteklenmez.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0, Linux'u tek bir işletim sistemi olarak ele alıyor. Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.

.NET Core 3.0 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                             | Sürüm               | Mimarileri    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16,04+                | x64, ARM32, ARM64 |
| Linux Darphane                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Kurumsal Linux (SLES)   | 12 SP2+               | x64 |
| Alp Linux                   | 3.8+                  | x64, ARM64 |

.NET Core 3.0 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)bkz.

ARM64'e .NET Core 3.0 nasıl yüklenir hakkında daha fazla bilgi için Linux [ARM64'te .NET Core 3.0](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213)yükleme'ye bakın.

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2, Linux'u tek bir işletim sistemi olarak ele alıyor. Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.

.NET Core 2.2 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                             |  Sürüm                |  Mimarileri   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64, ARM32 |
| Linux Darphane                     |  17, 18                 | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Kurumsal Linux (SLES)   |  12 SP2+                | x64 |
| Alp Linux                   |  3.8+                   | x64 |

.NET Core 2.2 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)bkz.

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1, Linux'u tek bir işletim sistemi olarak ele alıyor. Desteklenen Linux dağıtımları için tek bir Linux yapısı (yonga mimarisi başına) vardır.

.NET Core 2.1 aşağıdaki Linux dağıtımlarında/sürümlerinde desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| İşletim Sistemi                             |  Sürüm                |  Mimarileri   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29+                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux Darphane                     |  17+                    | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Kurumsal Linux (SLES)   |  12 SP2+                | x64 |
| Alp Linux                   |  3.8+                   | x64 |

.NET Core 2.1 destekli işletim sistemleri, dağıtımlar ve yaşam döngüsü ilkesi hakkında daha fazla bilgi [için](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)bkz.

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Linux dağıtımınıza bağlı olarak, ek bağımlılıklar yüklemeniz gerekebilir.

> [!IMPORTANT]
> Tam sürümleri ve adları tercih Linux dağıtımı biraz değişebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağılımları, aşağıdaki kitaplıkların yüklenmesini gerektirir:

- liblttng-ust0
- libcurl3 (14.x ve 16.x için)
- libcurl4 (18.x için)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (14.x için)
- libicu55 (16.x için)
- libicu57 (17.x için)
- libicu60 (18.x için)

*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:

- libgdiplus (sürüm 6.0.1 veya sonrası)

> [!WARNING]
> Ubuntu çoğu sürümleri libgdiplus önceki bir sürümünü içerir. Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS ve Fedora

CentOS dağıtımları için aşağıdaki kitaplıklar yüklenir:

- lttng-ust
- libcurl
- openssl-libs
- krb5-libs
- libicu
- Zlib

Fedora kullanıcıları: OpenSSL sürümünüz = 1.1'i >**ise, compat-openssl10**yüklemeniz gerekir.

.NET Core 2.0 için aşağıdaki bağımlılıklar da gereklidir:

- libunwind
- libuuid

Bağımlılıklar hakkında daha fazla bilgi için, [bağımsız Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md)bakın.

*System.Drawing.Common* derlemesini kullanan .NET Core uygulamaları için aşağıdaki bağımlılık da gerekir:

- libgdiplus (sürüm 6.0.1 veya sonrası)

> [!WARNING]
> CentOS ve Fedora'nın çoğu sürümü nde libgdiplus'ın önceki bir sürümü yer almaktadır. Mono deposunu sisteminize ekleyerek libgdiplus'ın yeni bir sürümünü yükleyebilirsiniz. Daha fazla bilgi için bkz. <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

.NET Core aşağıdaki macOS sürümlerinde desteklenir:

> [!NOTE]
> Bir `+` sembol minimum sürümü temsil eder.

| .NET Çekirdek Sürümü | macOS                 | Mimarileri |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Yüksek Sierra (10.13+)  | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3,0               | Yüksek Sierra (10.13+)  | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2,2               | Sierra (10.12+)       | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | x64 | [Daha fazla bilgi](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

MacOS Catalina (sürüm 10.15) ile başlayarak, Geliştirici Kimliği ile dağıtılan 1 Haziran 2019 tarihinden sonra üretilen tüm yazılımların noter tasdikli olması gerekir. Bu gereksinim .NET Core çalışma zamanı, .NET Core SDK ve .NET Core ile oluşturulan yazılımlar için geçerlidir.

.NET Core (hem çalışma süresi hem de SDK) 3.1, 3.0 ve 2.1 sürümlerinin yükleyicileri 18 Şubat 2020'den beri noter olarak noterolarak verilmiştir. Önceki sürümler noter onaylı değildir. Noter onaylı olmayan bir uygulama çalıştırıyorsanız, aşağıdaki resme benzer bir hata görürsünüz:

![macOS Catalina noterizasyon uyarısı](media/dependencies/macos-notarized-pkg-warning.png)

Zorunlu noterizasyonun .NET Core 'u (ve .NET Core uygulamalarını) nasıl etkilediği hakkında daha fazla bilgi için [bkz.](macos-notarization-issues.md)

## <a name="libgdiplus"></a>libgdiplus

*.System.Drawing.Common* assembly kullanan NET Core uygulamaları libgdiplus'ın yüklenmesini gerektirir.

Libgdiplus elde etmek için kolay bir yolu macOS için [Homebrew ("brew")](https://brew.sh/) paket yöneticisi kullanarak. *Brew*yükledikten sonra, terminal (komut) komut u komutu aşağıdaki komutları çalıştırarak libgdiplus yükleyin:

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Sonraki adımlar

- Uygulamaları geliştirmek ve çalıştırmak için [.NET Core SDK'yı](sdk.md) (çalışma süresini içerir) yükleyin.
- Başkalarının oluşturduğu uygulamaları çalıştırmak için [.NET Core çalışma süresini](runtime.md)yükleyin.
