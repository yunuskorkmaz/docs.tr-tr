---
title: Linux üzerinde .NET Core önkoşulları
description: Desteklenen Linux sürümleri ve .NET Core bağımlılıklarının geliştirmek, dağıtmak ve .NET Core uygulamaları Linux makinelerinde çalışır.
author: jralexander
ms.author: johalex
ms.date: 08/20/2018
ms.openlocfilehash: d0e5b203dc8e1ec6807f28de7d910c74a2ffe665
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506855"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux üzerinde .NET Core önkoşulları

Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir. Desteklenen Linux dağıtımları/sürümleri ve bağımlılıklarını izleyen iki yolu Linux üzerinde .NET Core uygulamaları geliştirmek için geçerlidir:

* [Sık kullandığınız düzenleyicinizi ile komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK paketini üretim sunucuları/ortamları için gerekli değildir. Yalnızca .NET Core çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir. .NET Core çalışma zamanı ile uygulamaları kendi içinde bir dağıtımının parçası olarak dağıtılan, Framework bağımlı uygulamaları ayrı ayrı dağıtılsa için ancak, dağıtılması gerekir. Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md). Ayrıca bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler için.

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.x tek bir işletim sistemi olarak Linux değerlendirir. Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur.

**NET Core 2.1**

NET Core 2.1 aşağıdaki Linux dağıtımları/sürümleri desteklenir:

* Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` veya `amd64`)
* CentOS 7 - 64-bit (`x86_64` veya `amd64`) 
* Oracle Linux 7 - 64-bit (`x86_64` veya `amd64`) 
* Fedora 28, 27 - 64-bit (`x86_64` veya `amd64`) 
* Debian 9 (64-bit, ARM32), 8,7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)
* Ubuntu 18.04 (64-bit, ARM32), 16.04, 14.04 - 64-bit (`x86_64` veya `amd64`)
* Linux Naneli 18, 17 - 64-bit (`x86_64` veya `amd64`)
* openSUSE 42.3 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri - 64-bit (`x86_64` veya `amd64`)
* Alpine Linux 3.7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)

Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) tam listesi, .NET Core 2.1 desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.

**NET Core 2.0**

NET Core 2.0 üzerinde aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

* Red Hat Enterprise Linux 7, 6
* CentOS 7
* Oracle Linux 7
* Fedora 27
* Debian 9 8,7 veya sonraki sürümleri
* Ubuntu 18.04, 16.04, 14.04
* Linux Naneli 18, 17
* openSUSE 42.3 veya sonraki sürümler
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri

Bkz: [.NET Core 2.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core 2.0 tam listesi desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x aşağıdaki Linux 64-bit üzerinde desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* 27 fedora 28 (.NET Core 1.1)
* Debian 8.2 veya sonraki sürümler
* Ubuntu 18.04 (.NET Core 1.1), 16.04, 14.04
* Linux Mint 17
* openSUSE 42.3 veya sonraki sürümleri (.NET Core 1.1)

Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Aşağıdaki örnekler olacak şekilde tasarlanmıştır. Adları ve tam sürümünü, tercih ettiğiniz Linux dağıtımı biraz değişebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:

* liblttng ust0
* libcurl3
* libssl1.0.0
* libkrb5 3
* zlib1g
* libicu52 (için 14.x)
* libicu55 (için 16.x)
* libicu57 (için 17.x)
* libicu60 (için 18.x)

Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:

* libunwind8
* libuuid1

### <a name="centos-and-fedora"></a>CentOS ve Fedora

CentOS dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:

* ust lttng
* libcurl
* openssl kitaplıkları
* krb5 kitaplıklar
* libicu
* Zlib

Fedora kullanıcılar:, openssl'ın sürümü > = 1.1 compat openssl10'ı yüklemeniz gerekir.

Sürümleri için .NET Core 2.1, daha önce aşağıdaki bağımlılıkları de gereklidir:

* libunwind
* libuuid

Bağımlılıklar hakkında daha fazla bilgi için bkz. [Self-contained Linux uygulamalarını](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>Yerel yükleyicilerden ile .NET Core Bağımlılıkların yüklenmesi

Desteklenen Linux dağıtımları/sürümleri .NET core için yerel yükleyicilerden kullanılabilir. Yerel yükleyicilerden sunucusuna (sudo) yönetici erişimi gerektirir. Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıkları yüklenmesidir. Yerel yükleyiciler, .NET Core SDK'sı sistem genelinde da yükleyin.

Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:

* CentOS/RHEL Ubuntu için apt-get veya yum gibi bir akış tabanlı Paket Yöneticisi'ni kullanarak.
* Paketleri kendileri DEB veya RPM kullanma.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core Yükleyici komut dosyasını yükler betik oluşturma

[Dotnet yükleme betikleri](./tools/dotnet-install-script.md) CLI araç zinciri ve paylaşılan çalışma zamanı'nın bir yönetici olmayan yüklemesini gerçekleştirmek için kullanılır. Betikten indirebileceğiniz [ https://dot.net/v1/dotnet-install.sh ](https://dot.net/v1/dotnet-install.sh).

Şu anda .NET Core 1.1 olan en son "LTS" sürümünü yüklemek için betik Varsayılanları. .NET Core yüklemek için 2.x, aşağıdaki geçiş betiği çalıştırın:

```console
./dotnet-install.sh -c Current
```

Yükleyici bash betiğini Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır. Linux/OS X sistemleri komut ile kullanılabilmesi için bu betiği ayrıca PowerShell anahtarları okur.

## <a name="install-net-core-for-supported-red-hat-enterprise-linux-rhel-versions"></a>Desteklenen Red Hat Enterprise Linux (RHEL) sürümleri için .NET Core yükleyin

Desteklenen bir RHEL sürümlerinde .NET Core yüklemek için:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**.NET core 2.1**

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. En son .NET Core 2.1 için yükleme bilgileri Red Hat Enterprise Linux, bkz: [.NET Core 2.1 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/2.1/html/getting_started_guide/)

**.NET core 2.0**

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. Red Hat Enterprise Linux yükleme bilgileri için en son .NET Core 2.0 için bkz: [.NET Core 2.0 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/) 

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.1**

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2.  Red Hat Enterprise Linux yükleme bilgileri için en son .NET Core 1.1 için bkz: [.NET Core 1.1 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.1/html/getting_started_guide/)
     
**.NET core 1.0**

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2.  Red Hat Enterprise Linux yükleme bilgileri için en son .NET Core 1.0 için bkz: [.NET Core 1.0 Başlarken Kılavuzu](https://access.redhat.com/documentation/en-us/net_core/1.0/html/getting_started_guide/)

Red Hat .NET kanal erişimi kayıt Yardım için bkz: [bölüm 1'de .NET Core 1.1 Başlarken Kılavuzu](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) , Red Hat.

---

## <a name="install-net-core-for-supported-ubuntu-and-linux-mint-distributionsversions-64-bit"></a>Ubuntu ve Linux Naneli dağıtımları/için desteklenen sürümleri (64-bit) .NET Core'u yükleme

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 2.x üzerinde desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core çalışma zamanı 2.0.9  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.9)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.9)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.9)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.9)            |
|.NET core çalışma zamanı 2.0.8  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.8)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.8)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.8)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.8)            |
|.NET core çalışma zamanı 2.0.7  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.7)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.7)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.7)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.7)            |
|.NET core çalışma zamanı 2.0.6  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.6)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.6)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.6)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.6)            |
|.NET core çalışma zamanı 2.0.5  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.0.5)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.0.5)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.0.5)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.0.5)            |
|.NET core SDK'sı 2.1.202    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.202)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.202)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.202)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.202)            |
|.NET core SDK'sı 2.1.201    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.201)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.201)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.201)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.201)            |
|.NET core SDK'sı 2.1.200    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.200)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.200)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.200)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.200)            |
|.NET core SDK'sı 2.1.105    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.105)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.105)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.105)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.105)            |
|.NET core SDK'sı 2.1.103    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.103)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.103)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.103)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.103)            |
|.NET core SDK 2.0.3 sürümünü      |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.3)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.3)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.3)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.3)            |
|.NET core 2.0.0 SDK      |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.0.0)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.0.0)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.0.0)          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.0.0)            |

**.NET core 2.1**

>[!IMPORTANT]
> Visual Studio ile .NET Core 2.1 kullanmak için yapmanız [Visual Studio 2017 15.7 yükleyin ya da daha yeni](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Çalışma zamanları / SDK'ları          |Ubuntu 18.04    |Ubuntu 17.10    |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|-------------------------|----------------|----------------|----------------------------|----------------------------|
|.NET core çalışma zamanı 2.1.2'yi          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.2)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.2)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.2)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.2)            |
|.NET core SDK'sı 2.1.400     |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.400)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.400)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.400)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.400)            |
|.NET core SDK'sı 2.1.302     |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.302)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.302)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.302)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.302)            |
|.NET core çalışma zamanı 2.1.1          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.1)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.1)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.1)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.1)            |
|.NET core SDK'sı 2.1.301     |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.301)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.301)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.301)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.301)            |
|.NET core çalışma zamanı 2.1.0          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/runtime-2.1.0)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/runtime-2.1.0)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/runtime-2.1.0)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/runtime-2.1.0)            |
|.NET core SDK'sı 2.1.300     |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu18-04/sdk-2.1.300)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu17-10/sdk-2.1.300)|[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu16-04/sdk-2.1.300)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/ubuntu14-04/sdk-2.1.300)            |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 1.x üzerinde desteklenen Ubuntu ve Linux Naneli dağıtımları/sürümleri (64 bit) yükleyin:

| Çalışma zamanları / SDK'ları         |Ubuntu 16.04 / Linux Naneli 18|Ubuntu 14.04 / Linux Naneli 17|
|-------------------------|----------------------------|----------------------------|
|.NET core çalışma zamanı 1.1.9  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.1.8  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.1.7  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.1.6  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.1.5  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.1.4  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanlarını 1.0.10 |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanlarını 1.0.9  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanlarını 1.0.8  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.0.7  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.0.5  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core çalışma zamanı 1.0.4  |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.10     |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.9      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.8      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.7      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.5      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.1.4      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.0.4      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-ubuntu-14.04-x64-binaries)            |
|.NET core SDK'sı 1.0.1      |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-16.04-x64-binaries)            |[Bağlantıya yükle](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-ubuntu-14.04-x64-binaries)            |

---

## <a name="install-net-core-for-supported-debian-versions-64-bit"></a>Desteklenen Debian sürümleri (64-bit) için .NET Core yükleyin

.NET Core desteklenen Debian sürümlerinde (64-bit) yüklemek için:

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizinin Linux tar.gz sistemini yükler için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 2.x üzerinde desteklenen Debian sürümleri (64 bit) yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Debian 9       |Debian 8       |
|-------------------------|---------------|---------------|
|.NET core çalışma zamanı 2.0.9  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.9)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.9)   |
|.NET core çalışma zamanı 2.0.8  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.8)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.8)   |
|.NET core çalışma zamanı 2.0.7  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.7)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.7)   |
|.NET core çalışma zamanı 2.0.6  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.6)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.6)   |
|.NET core çalışma zamanı 2.0.5  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.5)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.5)   |
|.NET core çalışma zamanı 2.0.3 sürümünü  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.3)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.3)   |
|.NET core çalışma zamanı 2.0.0  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.0.0)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.0.0)   |
|.NET core SDK'sı 2.1.202    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.202)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.202)   |
|.NET core SDK'sı 2.1.201    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.201)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.201)   |
|.NET core SDK'sı 2.1.200    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.200)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.200)   |
|.NET core SDK'sı 2.1.105    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK'sı 2.1.105    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.105)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.105)   |
|.NET core SDK'sı 2.1.104    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.104)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.104)   |
|.NET core SDK'sı 2.1.103    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.103)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.103)   |
|.NET core SDK'sı 2.1.102    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.102)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.102)   |
|.NET core SDK'sı 2.1.101    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.101)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.101)   |
|.NET core SDK 2.0.3 sürümünü      |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.3)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.3)   |
|.NET core 2.0.0 SDK      |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.0.0)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.0.0)   |

**.NET core 2.1**

>[!IMPORTANT]
> Visual Studio ile .NET Core 2.1 kullanmak için yapmanız [Visual Studio 2017 15.7 yükleyin ya da daha yeni](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Çalışma zamanları / SDK'ları                  |Debian 9       |Debian 8       |
|---------------------------------|---------------|---------------|
|.NET core çalışma zamanı 2.1.2'yi          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.2)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.2)   |
|.NET core SDK'sı 2.1.400        |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.400)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.400)        |
|.NET core SDK'sı 2.1.302        |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.302)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.302)        |
|.NET core çalışma zamanı 2.1.1          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.1)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.1)   |
|.NET core SDK'sı 2.1.301        |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.301)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.301)        |
|.NET core çalışma zamanı 2.1.0          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/runtime-2.1.0)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/runtime-2.1.0)   |
|.NET core SDK'sı 2.1.300        |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian9/sdk-2.1.300)   |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/debian8/sdk-2.1.300)        |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. Yükleme .NET Core 1.x sürümüne Debian 9 veya Debian 8:

* .NET core çalışma zamanı 1.1.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.0-linux-debian-x64-binaries)
* .NET core çalışma zamanlarını 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-debian-x64-binaries)
* .NET core çalışma zamanlarını 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-debian-x64-binaries)
* .NET core çalışma zamanlarını 1.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-debian-x64-binaries)
* .NET core çalışma zamanı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-debian-x64-binaries)
* .NET core SDK'sı 1.1.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-debian-x64-binaries)
* .NET core SDK'sı 1.1.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-debian-x64-binaries)
* .NET core SDK'larını 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-debian-x64-binaries)
* .NET core SDK'sı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-debian-x64-binaries)
* .NET core SDK'sı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-debian-x64-binaries)
* .NET core SDK'sı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-debian-x64-binaries)
* .NET core SDK'sı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-debian-x64-binaries)
* .NET core SDK'sı 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

---

## <a name="install-net-core-for-supported-fedora-versions-64-bit"></a>.NET Core Fedora için desteklenen sürümleri (64-bit) yükleme

.NET Core yüklemek için Fedora sürümleri desteklenir:

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizinin Linux tar.gz sistemini yükler için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 2.x üzerinde Fedora sürümleri (64 bit) desteklenen yükleyin:

**.NET core 2.0**

|Çalışma zamanları / SDK'ları          |Fedora 26 veya üzeri |25 veya önceki fedora |
|-------------------------|-------------------|----------------------|
|.NET core çalışma zamanı 2.0.9  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.9)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.9)           |
|.NET core çalışma zamanı 2.0.8  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.8)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.8)           |
|.NET core çalışma zamanı 2.0.7  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.7)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.7)           |
|.NET core çalışma zamanı 2.0.6  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.6)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.6)           |
|.NET core çalışma zamanı 2.0.5  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.5)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.5)           |
|.NET core çalışma zamanı 2.0.3 sürümünü  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.3)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.3)           |
|.NET core çalışma zamanı 2.0.0  |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/runtime-2.0.0)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/runtime-2.0.0)           |
|.NET core SDK'sı 2.1.200    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.200)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.200)           |
|.NET core SDK'sı 2.1.105    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.105)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.105)           |
|.NET core SDK'sı 2.1.103    |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.1.103)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.1.103)           |
|.NET core SDK 2.0.3 sürümünü      |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora26/sdk-2.0.3)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora25/sdk-2.0.3)           |

**.NET core 2.1**

>[!IMPORTANT]
> Visual Studio ile .NET Core 2.1 kullanmak için yapmanız [Visual Studio 2017 15.7 yükleyin ya da daha yeni](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

|Çalışma zamanları / SDK'ları                  |28 fedora          |Fedora 27             |
|---------------------------------|-------------------|----------------------|
|.NET core çalışma zamanı 2.1.2'yi          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.2)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.2)           |
|.NET core SDK'sı 2.1.400          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.400)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.400)           |
|.NET core SDK'sı 2.1.302          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.302)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.302)           |
|.NET core çalışma zamanı 2.1.1          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.1)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.1)           |
|.NET core SDK'sı 2.1.301          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.301)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.301)           |
|.NET core çalışma zamanı 2.1.0          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/runtime-2.1.0)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/runtime-2.1.0)           |
|.NET core SDK'sı 2.1.300          |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora28/sdk-2.1.300)       |[Bağlantıya yükle](https://www.microsoft.com/net/download/linux-package-manager/fedora27/sdk-2.1.300)           |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 1.x desteklenen Fedora sürümleri (64-bit) yükleyin:

**Fedora 24**

* .NET core çalışma zamanı 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-24-x64-binaries)
* .NET core çalışma zamanı 1.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-24-x64-binaries)
* .NET core SDK'sı 1.1.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-fedora-24-x64-binaries)
* .NET core SDK'larını 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-fedora-24-x64-binaries)
* .NET core SDK'sı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-fedora-24-x64-binaries)
* .NET core SDK'sı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* .NET core SDK'sı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5linux-fedora-24-x64-binaries)
* .NET core SDK'sı 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-debian-x64-binaries)

**Fedora 23**

* .NET core çalışma zamanı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-fedora-23-x64-binaries)
* .NET core çalışma zamanı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-fedora-23-x64-binaries)
* .NET core çalışma zamanı 1.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-fedora-23-x64-binaries)
* .NET core çalışma zamanlarını 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-fedora-23-x64-binaries)
* .NET core çalışma zamanı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-fedora-23-x64-binaries)
* .NET core SDK'sı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4linux-fedora-23-x64-binaries)
* .NET core SDK'sı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* .NET core SDK'sı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.2linux-fedora-23-x64-binaries)
* .NET core SDK'sı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-fedora-23-x64-binaries)
* .NET core SDK'sı 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-fedora-23-x64-binaries)

---

## <a name="install-net-core-for-supported-centos-and-oracle-linux-distributionsversions-64-bit"></a>Desteklenen CentOS ve Oracle Linux için .NET Core yükleyin dağıtımlarını/sürümleri (64-bit)

Yüklemek için .NET Core desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64-bit):

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizinin Linux tar.gz sistemini yükler için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core'u yükleme 2.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64-bit):

**.NET core 2.0**

* .NET core çalışma zamanı 2.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.9)
* .NET core çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.8)
* .NET core çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.7)
* .NET core çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.6)
* .NET core çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.5)
* .NET core çalışma zamanı 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.3)
* .NET core çalışma zamanı 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.0.0)
* .NET core SDK'sı 2.1.202 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.202)
* .NET core SDK'sı 2.1.201 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.201)
* .NET core SDK'sı 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.200)
* .NET core SDK'sı 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.105)
* .NET core SDK'sı 2.1.104 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.104)
* .NET core SDK'sı 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.103)
* .NET core SDK'sı 2.1.102 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.102)
* .NET core SDK 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Visual Studio ile .NET Core 2.1 kullanmak için yapmanız [Visual Studio 2017 15.7 yükleyin ya da daha yeni](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

* .NET core çalışma zamanı 2.1.2'yi [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.2)
* .NET core SDK'sı 2.1.400 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.400)
* .NET core SDK'sı 2.1.302 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.302)
* .NET core çalışma zamanı 2.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.1)
* .NET core SDK'sı 2.1.301 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.301)
* .NET core çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/runtime-2.1.0)
* .NET core SDK'sı 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/centos/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core'u yükleme 1.x desteklenen CentOS ve Oracle Linux dağıtımları/sürümleri (64-bit):

* .NET core çalışma zamanı 1.1.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.9-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.8-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.5-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.4-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.2 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.2-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.1-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.0.12 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.12-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.0.11 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.11-linux-centos-x64-binaries)
* .NET core çalışma zamanlarını 1.0.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.10-linux-centos-x64-binaries)
* .NET core çalışma zamanlarını 1.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.9-linux-centos-x64-binaries)
* .NET core çalışma zamanlarını 1.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.8-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.7-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.5-linux-centos-x64-binaries)
* .NET core çalışma zamanı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.0.4-linux-centos-x64-binaries)
* .NET core SDK'sı 1.1.10 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.10-linux-centos-x64-binaries)
* .NET core SDK'sı 1.1.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.9-linux-centos-x64-binaries)
* .NET core SDK'larını 1.1.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.8-linux-centos-x64-binaries)
* .NET core SDK'sı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-centos-x64-binaries)
* .NET core SDK'sı 1.1.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.5-linux-centos-x64-binaries)
* .NET core SDK'sı 1.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.4-linux-centos-x64-binaries)
* .NET core SDK'sı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-centos-x64-binaries)
* .NET core SDK'sı 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-centos-x64-binaries)

---

## <a name="install-net-core-for-supported-suse-linux-enterprise-server-and-opensuse-distributionsversions-64-bit"></a>SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/için desteklenen sürümleri (64-bit) .NET Core'u yükleme

.NET Core yüklemek için SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64-bit) 2.x için desteklenir:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 2.x üzerinde desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:

**.NET core 2.0**

**SUSE Linux Enterprise Server**

* .NET core çalışma zamanı 2.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.9)
* .NET core çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.8)
* .NET core çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.7)
* .NET core çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.6)
* .NET core çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.5)
* .NET core çalışma zamanı 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.3)
* .NET core çalışma zamanı 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.0.0)
* .NET core SDK'sı 2.1.202 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.202)
* .NET core SDK'sı 2.1.201 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.201)
* .NET core SDK'sı 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.200)
* .NET core SDK'sı 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.105)
* .NET core SDK'sı 2.1.104 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.104)
* .NET core SDK'sı 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.103)
* .NET core SDK'sı 2.1.102 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.102)
* .NET core SDK'sı 2.1.101 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.101)
* .NET core SDK'sı 2.1.100 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.100)
* .NET core SDK'larını 2.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.4)
* .NET core SDK'sı 2.1.2'yi [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.2)
* .NET core SDK 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.0.0)

**openSUSE**

* .NET core çalışma zamanı 2.0.9 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.9)
* .NET core çalışma zamanı 2.0.8 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.8)
* .NET core çalışma zamanı 2.0.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.7)
* .NET core çalışma zamanı 2.0.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.6)
* .NET core çalışma zamanı 2.0.5 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.5)
* .NET core çalışma zamanı 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.3)
* .NET core çalışma zamanı 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.0.0)
* .NET core SDK'sı 2.1.202 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.202)
* .NET core SDK'sı 2.1.201 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.201)
* .NET core SDK'sı 2.1.200 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.200)
* .NET core SDK'sı 2.1.105 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.105)
* .NET core SDK'sı 2.1.103 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.103)
* .NET core SDK'sı 2.1.102 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.102)
* .NET core SDK'sı 2.1.101 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.101)
* .NET core SDK'sı 2.1.100 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.100)
* .NET core SDK'larını 2.1.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.4)
* .NET core SDK'sı 2.1.2'yi [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.2)
* .NET core SDK 2.0.3 sürümünü [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.3)
* .NET core SDK 2.0.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.0.0)
 
**.NET core 2.1**

>[!IMPORTANT]
> Visual Studio ile .NET Core 2.1 kullanmak için yapmanız [Visual Studio 2017 15.7 yükleyin ya da daha yeni](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017).

**SUSE Linux Enterprise Server**

* .NET core çalışma zamanı 2.1.2'yi [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.2)
* .NET core SDK'sı 2.1.400 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.400)
* .NET core SDK'sı 2.1.302 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.302)
* .NET core çalışma zamanı 2.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.1)
* .NET core SDK'sı 2.1.301 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.301)
* .NET core çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/runtime-2.1.0)
* .NET core SDK'sı 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/sles/sdk-2.1.300)

**openSUSE**

* .NET core çalışma zamanı 2.1.2'yi [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.2)
* .NET core SDK'sı 2.1.400 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.400)
* .NET core SDK'sı 2.1.302 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.302)
* .NET core çalışma zamanı 2.1.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.1)
* .NET core SDK'sı 2.1.301 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.301)
* .NET core çalışma zamanı 2.1.0 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/runtime-2.1.0)
* .NET core SDK'sı 2.1.300 [bağlantı yükleyin](https://www.microsoft.com/net/download/linux-package-manager/opensuse/sdk-2.1.300)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

1. Kaldırmak **önceki Önizleme** sisteminizden .NET Core sürümleri.

2. .NET Core 1.x üzerinde desteklenen SUSE Linux Enterprise Server ve OpenSUSE dağıtımları/sürümleri (64 bit) yükleyin:

**SUSE Linux Enterprise Server 13.2**

* .NET core çalışma zamanı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET core çalışma zamanı 1.1.6 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-1.1.6-linux-opensuse-13.2-x64-binaries)
* .NET core SDK'sı 1.1.7 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.1.7-linux-opensuse-13.2-x64-binaries)
* .NET core SDK'sı 1.0.4 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.4-linux-opensuse-13.2-x64-binaries)
* .NET core SDK'sı 1.0.1 [bağlantı yükleyin](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-1.0.1-linux-opensuse-13.2-x64-binaries)

---

## <a name="install-net-core-for-supported-alpine-linux-versions-64-bit"></a>.NET Core Alpine Linux için desteklenen sürümleri (64-bit) yükleme

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizinin Linux tar.gz sistemini yükler için gereklidir.

İndirin ve desteklenen Alpine Linux (64-bit) sürümlerin aşağıdaki bağlantılar için .NET Core 2.1 yükleme yönergelerini izleyin:

* .NET core çalışma zamanı 2.1.2'yi [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.2-linux-x64-alpine-binaries)
* .NET core SDK'sı 2.1.400 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.400-linux-x64-alpine-binaries)
* .NET core SDK'sı 2.1.302 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.302-linux-x64-alpine-binaries)
* .NET core çalışma zamanı 2.1.1 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.1-linux-x64-alpine-binaries)
* .NET core SDK'sı 2.1.301 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.301-linux-x64-alpine-binaries)
* .NET core çalışma zamanı 2.1.0 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-runtime-2.1.0-linux-x64-alpine-binaries)
* .NET core SDK'sı 2.1.300 [indirme bağlantısı](https://www.microsoft.com/net/download/thank-you/dotnet-sdk-2.1.300-linux-x64-alpine-binaries)

> [!IMPORTANT]
> Desteklenen bir Linux dağıtımı/sürümünde .NET Core yüklemesi ile ilgili sorunlar varsa, yüklü, dağıtımları/sürümleri için aşağıdaki konulara bakın:
> * [.NET core 2.1 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1)
> * [.NET core 2.0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0)
> * [.NET core 1.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.1)
> * [.NET core 1.0, bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0)
