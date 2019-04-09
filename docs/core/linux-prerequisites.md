---
title: Linux üzerinde .NET Core önkoşulları
description: Desteklenen Linux sürümleri ve .NET Core bağımlılıklarının geliştirmek, dağıtmak ve .NET Core uygulamaları Linux makinelerinde çalışır.
author: thraka
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: 29256259c66b909ad65691230bd652f38583184e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084919"
---
# <a name="prerequisites-for-net-core-on-linux"></a>Linux üzerinde .NET Core önkoşulları

Bu makalede, Linux üzerinde .NET Core uygulamaları geliştirmek için ihtiyaç duyulan bağımlılıkları gösterir. Desteklenen Linux dağıtımları/sürümleri ve bağımlılıklarını izleyen iki yolu Linux üzerinde .NET Core uygulamaları geliştirmek için geçerlidir:

* [Sık kullandığınız düzenleyicinizi ile komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

> [!NOTE]
> .NET Core SDK paketini üretim sunucuları/ortamları için gerekli değildir. Yalnızca .NET Core çalışma zamanı paketi üretim ortamlarına dağıtılan uygulamalar için gereklidir. .NET Core çalışma zamanı ile uygulamaları kendi içinde bir dağıtımının parçası olarak dağıtılan, Framework bağımlı uygulamaları ayrı ayrı dağıtılsa için ancak, dağıtılması gerekir. Framework bağımlı ve kendi başına dağıtım türleri hakkında daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](./deploying/index.md). Ayrıca bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md) belirli yönergeler için.

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

# [<a name="net-core-2x"></a>.NET core 2.x](#tab/netcore2x)

.NET core 2.x tek bir işletim sistemi olarak Linux değerlendirir. Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur. 

Daha fazla bilgi ve indirme bağlantıları [.NET Core 2.2 indirir](https://www.microsoft.com/net/download/dotnet-core/2.2) veya [.NET Core 2.1 yükler](https://www.microsoft.com/net/download/dotnet-core/2.1).

.NET core 2.x, aşağıdaki Linux dağıtımları/sürümleri desteklenir:

* Red Hat Enterprise Linux 7, 6 - 64-bit (`x86_64` veya `amd64`)
* CentOS 7 - 64-bit (`x86_64` veya `amd64`) 
* Oracle Linux 7 - 64-bit (`x86_64` veya `amd64`) 
* Fedora 28, 27 - 64-bit (`x86_64` veya `amd64`) 
* Debian 9 (64 bit `arm32`), 8,7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)
* Ubuntu 18.04 (64 bit `arm32`), 16.04, 14.04 - 64-bit (`x86_64` veya `amd64`)
* Linux Naneli 18, 17 - 64-bit (`x86_64` veya `amd64`)
* openSUSE 42.3 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)
* SUSE Enterprise Linux (SLES) 12 Service Pack 2 veya üzeri - 64-bit (`x86_64` veya `amd64`)
* Alpine Linux 3.7 veya sonraki sürümler - 64-bit (`x86_64` veya `amd64`)

Bkz: [.NET Core 2.1 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) ve [.NET Core 2.2 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) tam listesi, .NET Core 2.1 ve .NET Core 2.2 dışı işletim sistemleri, dağıtımlar ve sürümleri, desteklenen işletim sistemi sürümleri ve yaşam döngüsü İlkesi bağlantılarını destekler.

# [<a name="net-core-1x"></a>.NET core 1.x](#tab/netcore1x)

Daha fazla bilgi ve indirme bağlantıları [.NET Core 1.1 indirir](https://www.microsoft.com/net/download/dotnet-core/1.1) veya [.NET Core 1.0 indirir](https://www.microsoft.com/net/download/dotnet-core/1.0).

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

# [<a name="net-core-30-preview-1"></a>.NET core 3.0 Önizleme 1](#tab/netcore30)

.NET core 3.0 Önizleme 1, tek bir işletim sistemi Linux değerlendirir. Tek bir Linux yapı (yonga Mimarisi) başına desteklenen Linux dağıtımları için yoktur. 

Daha fazla bilgi ve indirme bağlantıları [.NET Core 3.0 indirir](https://dotnet.microsoft.com/download/dotnet-core/3.0).

.NET core 3.0 Önizleme 1, aşağıdaki Linux dağıtımları/sürümleri desteklenir. 

İşletim Sistemi                            | Sürüm               | Mimarileri  
------------------------------|-----------------------|----------------
Red Hat Enterprise Linux      | 6                     | X64
Red Hat Enterprise Linux<br>CentOS<br>Oracle Linux  | 7                     | X64
Fedora                        | 28                    | X64
Debian                        | 9                     | x64, ARM32\*, ARM64\*
Ubuntu                        | 16.04+, 18.04+        | x64, ARM32\*, ARM64\*
Linux Naneli                    | 18                    | X64
openSUSE                      | 42.3+                 | X64
SUSE Enterprise Linux (SLES)  | 12 SP2+               | X64
Alpine Linux                  | 3.8+                  | x64, ARM64

\* ARM32 ve ARM64 desteği 9 Debian ve Ubuntu 16.04 başlatır. Bu dağıtım paketlerini önceki sürümlerinde, ARM yongalarında desteklenmez.

Bkz: [.NET Core 3.0 desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) tam listesi .NET Core 3.0, desteklenen işletim sistemleri, dağıtımlar ve sürümler, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantılar dışında.

ARM64'te .NET Core 3.0 yükleme hakkında daha fazla bilgi için bkz. [Linux ARM64 üzerinde .NET Core 3.0 yükleme](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Aşağıdaki örnekler olacak şekilde tasarlanmıştır. Adları ve tam sürümünü, tercih ettiğiniz Linux dağıtımı biraz değişebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları, aşağıdaki kitaplıkların yüklü gerektirir:

* liblttng ust0
* libcurl3 (için 14.x ve 16.x)
* libcurl4 (için 18.x)
* libssl1.0.0
* libkrb5-3
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
* openssl-libs
* krb5 kitaplıklar
* libicu
* zlib

Fedora kullanıcılar: Varsa, openssl'ın sürümü > = 1.1 compat openssl10'ı yüklemeniz gerekir.

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

Şu anda .NET Core 1.1 olan en son "LTS" sürümünü yüklemek için betik Varsayılanları. .NET Core 2.1 yüklemek için aşağıdaki geçiş betiği çalıştırın:

```console
./dotnet-install.sh -c Current
```

Yükleyici bash betiğini Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır. Linux/OS X sistemleri komut ile kullanılabilmesi için bu betiği ayrıca PowerShell anahtarları okur.

## <a name="troubleshoot"></a>Sorun giderme

Desteklenen bir Linux dağıtımı/sürümünde .NET Core yüklemesi ile ilgili sorunlar varsa, yüklü, dağıtımları/sürümleri için aşağıdaki konulara bakın:

* [.NET core bilinen sorunları 3.0](https://github.com/dotnet/core/tree/master/release-notes/3.0)
* [.NET core bilinen sorunları 2.2](https://github.com/dotnet/core/tree/master/release-notes/2.2)
* [.NET core 2.1 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.1)
* [.NET core 1.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.1)
* [.NET core 1.0, bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0)
