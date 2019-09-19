---
title: Linux üzerinde .NET Core önkoşulları
description: Linux makinelerde .NET Core uygulamaları geliştirmek, dağıtmak ve çalıştırmak için desteklenen Linux sürümleri ve .NET Core bağımlılıkları.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 31c53b2cc0fe576e56685f4a5561258136fd2541
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116588"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux üzerinde .NET Core önkoşulları

Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için gereken bağımlılıklar gösterilmektedir. Desteklenen Linux dağıtımları/sürümleri ve aşağıdaki bağımlılıklar, Linux üzerinde .NET Core uygulamaları geliştirmenin iki yolu için geçerlidir:

* [En sevdiğiniz düzenleyicinizle komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK paketi üretim sunucuları/ortamları için gerekli değildir. Üretim ortamlarına dağıtılan uygulamalar için yalnızca .NET Core çalışma zamanı paketi gereklidir. .NET Core çalışma zamanı, uygulamalar ile birlikte bulunan bir dağıtımın parçası olarak dağıtılır, ancak çerçeveye bağımlı dağıtılan uygulamalar için ayrı olarak dağıtılmalıdır. Çerçeveye bağımlı ve kendi kendine içerilen dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md). Ayrıca, belirli yönergeler için [kendi Içindeki Linux uygulamalarına](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) bakın.

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

.NET Core 2. x, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır. 

İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 2,2 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.2) veya [.NET Core 2,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/2.1).

.NET Core 2. x, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir:

* Red Hat Enterprise Linux 7, 6-64-bit (`x86_64` veya `amd64`)
* CentOS 7-64-bit (`x86_64` veya `amd64`) 
* Oracle Linux 7-64 bit (`x86_64` veya) `amd64` 
* Fedora 28, 27-64-bit (`x86_64` veya `amd64`) 
* 9 (64-bit, `arm32`), 8,7 veya sonraki sürümler-64-bit (`x86_64` veya `amd64`)
* Ubuntu 18,04 (64-bit, `arm32`), 16,04, 14,04-64-bit (`x86_64` veya `amd64`)
* Linux Mint 18, 17-64-bit (`x86_64` veya `amd64`)
* openSUSE 42,3 veya sonraki sürümleri-64-bit (`x86_64` veya `amd64`)
* Suse Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri-64-bit (`x86_64` veya `amd64`)
* Alp Linux 3,7 veya sonraki sürümleri-64-bit (`x86_64` veya `amd64`)

.NET Core 2,1 ve .NET Core 2,2 tarafından desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin tamamı, destek SISTEMI sürümleri ve yaşam döngüsü ilkesi için [.net core 2,1 desteklenen](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) işletim sistemi sürümleri ve [.NET Core 2,2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) ' ne bakın Köprü.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

İndirme bağlantıları ve daha fazla bilgi için bkz. [.net core 1,1 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.1) veya [.NET Core 1,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/1.0).

.NET Core 1. x, aşağıdaki Linux 64-bit (`x86_64` veya `amd64`) dağıtımları/sürümlerinde desteklenir:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 28 (.NET Core 1,1), 27
* 8,2 veya sonraki sürümlerini kaldırma
* Ubuntu 18,04 (.NET Core 1,1), 16,04, 14,04
* Linux Mint 17
* openSUSE 42,3 veya sonraki sürümleri (.NET Core 1,1)

.NET Core 1. x desteklenen işletim sistemlerinin tüm listesi için bkz. .NET Core [1.](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) x tarafından desteklenen işletim sistemleri, destek sistemi sürümlerinin dışında ve yaşam döngüsü ilkesi bağlantıları.

# <a name="net-core-30-preview-1tabnetcore30"></a>[.NET Core 3,0 Preview 1](#tab/netcore30)

.NET Core 3,0 Preview 1, Linux 'u tek bir işletim sistemi olarak değerlendirir. Desteklenen Linux dağıtımları için tek bir Linux derlemesi (yonga mimarisi başına) vardır. 

İndirme bağlantıları ve daha fazla bilgi için bkz. [.NET Core 3,0 İndirmeleri](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET Core 3,0 Preview 1, aşağıdaki Linux dağıtımları/sürümlerinde desteklenir. 

OS                            | Sürüm               | Mimarileri  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04 +, 18.04 +        | x64, ARM32\*, ARM64\*
Linux Mint                    | 18                    | X64
openSUSE                      | 42.3 +                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2 +               | X64
Alp Linux                  | 3.8 +                  | x64, ARM64

\*ARM32 ve ARM64 desteği, de, 9 ve Ubuntu 16,04 ile başlar. Bu detrolar 'ın önceki sürümleri ARM yongalarında desteklenmez.

.NET Core 3,0 desteklenen işletim sistemlerinin, dağıtımların ve sürümlerin, destek SISTEMI sürümlerinden ve yaşam döngüsü ilke bağlantılarının tüm listesi için bkz. [.net core 3,0 desteklenen IŞLETIM sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .

ARM64 üzerinde .NET Core 3,0 yükleme hakkında daha fazla bilgi için bkz. [LINUX ARM64 üzerinde .net core 3,0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

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

### <a name="centos-and-fedora"></a>CentOS ve Fedora

CentOS dağıtımları için aşağıdaki kitaplıkların yüklü olması gerekir:

* lttng-ust
* libkıvrık
* OpenSSL-libs
* krb5-libs
* libıu
* zlib

Fedora kullanıcıları: OpenSSL sürümünüz > = 1,1 ise, COMPAT-openssl10 ' ı yüklemeniz gerekir.

.NET Core 2,1 öncesi sürümler için aşağıdaki bağımlılıklar da gereklidir:

* librüzgar
* libuuid

Bağımlılıklar hakkında daha fazla bilgi için bkz. [kendi Içindeki Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Yerel yükleyicilerle .NET Core bağımlılıklarını yükleme

.NET Core yerel yükleyicileri desteklenen Linux dağıtımları/sürümleri için kullanılabilir. Yerel yükleyiciler sunucuya yönetici (sudo) erişimi gerektirir. Yerel bir yükleyiciyi kullanmanın avantajı, tüm .NET Core yerel bağımlılıklarının yüklü olması. Yerel yükleyiciler Ayrıca sistem genelinde .NET Core SDK de yükler.

Linux 'ta iki yükleyici paketi seçeneği vardır:

* Bir akış tabanlı Paket Yöneticisi, Ubuntu için apt-get veya CentOS/RHEL için de rivı kullanma.
* Paketlerin kendisini, DEB veya RPM 'yi kullanma.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core yükleyici betiği ile betik yüklemeleri

[DotNet-install betikleri](./tools/dotnet-install-script.md) , CLI araç zinciri ve paylaşılan çalışma zamanının yönetici olmayan bir yüklemesini gerçekleştirmek için kullanılır. Betiği konumundan <https://dot.net/v1/dotnet-install.sh>indirebilirsiniz.

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
