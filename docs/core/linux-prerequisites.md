---
title: ".NET Core Linux önkoşulları"
description: "Desteklenen Linux sürümleri ve geliştirmek, dağıtmak ve Linux makinelerde .NET Core uygulamaları çalıştırmak için .NET Core bağımlılıkları."
keywords: .NET, .NET core, Linux, debian, ubuntu, RHEL, centOS,
author: jralexander
ms.author: johalex
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload: dotnetcore
ms.openlocfilehash: 1a698516ae2aea9242fe929cd213e9dac0b1119d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="prerequisites-for-net-core-on-linux"></a>.NET Core Linux önkoşulları

Bu makalede Linux'ta .NET Core uygulamaları geliştirmek için gerekli bağımlılıkların gösterilmektedir. Desteklenen Linux dağıtımları/sürümleri ve izleyin bağımlılıkları Linux'ta .NET Core uygulama geliştirme iki yolu için geçerlidir:

* [Tercih ettiğiniz Düzenleyicisi ile komut satırı](tutorials/using-with-xplat-cli.md)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="supported-linux-versions"></a>Desteklenen Linux sürümleri

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET core 2.0 tek bir işletim sistemi Linux değerlendirir. Bir tek desteklenen Linux distro'lar Linux yapı (her yonga Mimarisi) yoktur.

NET çekirdek 2.x, aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

 * Red Hat Enterprise Linux 7
 * CentOS 7
 * Oracle Linux 7
 * Fedora 25, Fedora 26
 * Debian 8,7 veya sonraki sürümleri 
 * Ubuntu 17.04, Ubuntu 16.04, Ubuntu 14.04
 * Linux Naneli 18, Linux Naneli 17
 * openSUSE 42,2 veya sonraki sürümler
 * SUSE Enterprise Linux (SLES) 12 SP2 veya sonraki sürümler

Bkz: [.NET Core 2.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) .NET Core tam listesi için 2.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

.NET core 1.x aşağıdaki Linux 64-bit desteklenir (`x86_64` veya `amd64`) dağıtımları/sürümleri:

* Red Hat Enterprise Linux 7
* CentOS 7
* Oracle Linux 7
* Fedora 24
* Debian 8.2 veya sonraki sürümler
* Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10\*
 * Ubuntu 16.10 .NET Core 1.1 en son düzeltme eki sürümü tarafından desteklenen
* Linux Mint 17
* openSUSE 42,1 veya sonraki sürümleri (.NET Core 1.1)

Bkz: [.NET Core 1.x desteklenen işletim sistemi sürümleri](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) .NET Core tam listesi için 1.x desteklenen işletim sistemleri, destek işletim sistemi sürümleri ve yaşam döngüsü ilkesi bağlantıları dışında.

---

## <a name="linux-distribution-dependencies"></a>Linux dağıtım bağımlılıkları

Aşağıdaki örnekler olacak şekilde tasarlanmıştır. Tam sürümünü ve adları, seçim Linux dağıtımını biraz değişebilir.

### <a name="ubuntu"></a>Ubuntu

Ubuntu dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:

* libunwind8
* liblttng ust0
* libcurl3
* libssl1.0.0
* libuuid1
* libkrb5
* zlib1g
* libicu52 (için 14.X)
* libicu55 (için 16.X)
* libicu57 (için 17.X)

### <a name="centos"></a>CentOS

CentOS dağıtımları yüklü aşağıdaki kitaplıkları gerektirir:

* libunwind
* lttng hakkınızın
* libcurl
* openssl kitaplıklar
* libuuid
* krb5 kitaplıklar
* libicu
* Zlib

Bağımlılıklar hakkında daha fazla bilgi için bkz: [Self-contained Linux uygulamaları](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

## <a name="installing-net-core-dependencies-with-the-native-installers"></a>.NET Core bağımlılıkları ile yerel yükleyicileri yükleme

Desteklenen Linux dağıtımları/sürümleri .NET core yerel yükleyicileri için kullanılabilir. Yerel yükleyicileri sunucusuna yönetici (sudo) erişim gerektirir. Yerel bir yükleyici kullanmanın avantajı tüm .NET Core yerel bağımlılıklarını yüklenmesidir. Yerel yükleyicileri ayrıca .NET Core SDK sistem genelinde yükleyin.

Linux üzerinde iki yükleyici paketi seçeneğiniz vardır:

* Get apt Ubuntu için veya yum gibi bir akış tabanlı Paket Yöneticisi CentOS/RHEL için kullanma.
* Paketleri kendileri DEB veya RPM kullanma.

### <a name="scripting-installs-with-the-net-core-installer-script"></a>.NET Core Yükleyici komut dosyasıyla yükler komut dosyası oluşturma

`dotnet-install` Komut dosyaları, CLI zincirinin ve paylaşılan çalışma zamanı yönetici olmayan yüklemesini gerçekleştirmek için kullanılır. Komut dosyasını indirebilirsiniz: https://dot.net/v1/dotnet-install.sh

Yükleyici bash betik Otomasyon senaryoları ve yönetici olmayan yüklemeleri kullanılır. Linux/OS X sistemleri komut ile kullanılabilmesi için bu komut dosyası ayrıca PowerShell anahtarları okur.

> [!IMPORTANT]
> Komut dosyasını çalıştırmadan önce gerekli yükleme [bağımlılıkları](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

## <a name="install-net-core-for-red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7 .NET Core yükleyin

.NET Core üzerinde RHEL 7 yüklemek için:

1. RHEL 7 abonelik altında kullanılabilir Red Hat .NET kanal etkinleştirin.
    * Red Hat Enterprise 7 Server için kullanın:
    
         ```bash
         subscription-manager repos --enable=rhel-7-server-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 için iş istasyonu, kullanın:
    
        ```bash
        subscription-manager repos --enable=rhel-7-workstation-dotnet-rpms
         ```
    
    * Red Hat Enterprise 7 HPC işlem düğümü için kullanın:
    
        ```bash
        subscription-manager repos --enable=rhel-7-hpc-node-dotnet-rpms
        ```

2. Scl aracını yükleyin.

    ```bash
    yum install scl-utils
    ```
    
3. .NET Core yükleyin

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

.NET Core 2.0 yükleme SDK ve çalışma zamanı:

   ```bash
   yum install rh-dotnet20
   ```

.NET Core 2.0 SDK/Runtime ortamınız için etkinleştir:

   ```bash
   scl enable rh-dotnet20 bash
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**.NET core 1.1**

.NET Core 1.1 yüklemek SDK ve çalışma zamanı:

   ```bash
   yum install rh-dotnetcore11
   ```

.NET Core 1.1 SDK ve çalışma zamanı, ortamınız için etkinleştir:

   ```bash
   scl enable rh-dotnetcore11 bash
   ```

**.NET core 1.0**

.NET yüklemek çekirdek 1.0 SDK ve çalışma zamanı:

   ```bash
   yum install rh-dotnetcore10
   ```

.NET Core 1.0 SDK ve çalışma zamanı, ortamınız için etkinleştir:

   ```bash
   scl enable rh-dotnetcore10 bash
   ```

---
4. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

     ```bash
     dotnet --version
     ```

Red Hat .NET kanal erişim kayıt Yardım için bkz: [.NET Core 1.1 Başlarken Kılavuzu, bölüm 1](https://access.redhat.com/documentation/en/net-core/1.1/paged/getting-started-guide/) Red Hat hızında.

## <a name="install-net-core-for-ubuntu-1404-ubuntu-1604-ubuntu-1610--linux-mint-17-linux-mint-18-64-bit"></a>.NET Core Ubuntu 14.04, Ubuntu 16.04, Ubuntu 16.10 ve Linux Naneli 17, Linux Naneli 18 (64 bit) için yükleme

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

2. Microsoft Product anahtarı güvenilir olarak kaydedin.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```

3. Akış istediğiniz sürümü konak paketini ayarlayın.

   **Ubuntu 17.04**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-zesty-prod zesty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 16.04 / Linux Naneli 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

   **Ubuntu 14.04 / Linux Naneli 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-trusty-prod trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-get update
   ```

4. .NET Core yükleyin.

   ```bash
   sudo apt-get install dotnet-sdk-2.0.0
   ```

4. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

2. Akış istediğiniz sürümü konak paketini ayarlayın.

   **Ubuntu 16.10**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ yakkety main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

  **Ubuntu 16.04 / Linux Naneli 18**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```
    
   **Ubuntu 14.04 / Linux Naneli 17**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'
   sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys B02C46DF417A0893
   sudo apt-get update
   ```

3. .NET yüklemek Ubuntu ya da Linux Naneli 1.x Çekirdek:

   ```bash
   sudo apt-get install dotnet-dev-1.0.4
   ```

4. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

---

 ## <a name="install-net-core-for-debian-8-or-debian-9-64-bit"></a>.NET Core Debian 8 veya Debian 9 (64 bit) için yükleme

.NET Core Debian 8 veya Debian 9 (64 bit) yüklemek için:

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

2. Sistem bileşenlerini yükleyin.

   ```bash
   sudo apt-get update
   sudo apt-get install curl libunwind8 gettext apt-transport-https
   ```
   
3. Güvenilen Microsoft Product anahtarını kaydedin.

   ```bash
   curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
   sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg
   ```
   
4. Microsoft Product akışı kaydedin.

   **Debian 9 (Esnetme)**

   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
   **Debian 8 (Jessie)**
   
   ```bash
   sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/dotnetdev.list'
   ```
   
5. .NET Core SDK yükleyin.

   ```bash
   sudo apt-get update
   sudo apt-get install dotnet-sdk-2.0.0
   ```

6. DotNet YOLUNU ekleyin.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```
   
7. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```   
  

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

2. Önkoşullar alın.

   ```bash
   sudo apt-get install curl libunwind8 gettext
   ```

3. .NET Core SDK ikili dosyaları (tarball) indirin.

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848826
   ```

4. .NET Core SDK ikili dosyaları ayıklayın.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

6. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

---

## <a name="install-net-core-for-fedora-24-fedora-25-or-fedora-26-64-bit"></a>.NET Core Fedora 24, Fedora 25 veya Fedora 26 (64 bit) için yükleme

.NET Core yüklemek için Fedora 26 veya Fedora 25 veya .NET Core 2.x 1.x Fedora 24 üzerinde:

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**Fedora 26 veya Fedora 25**

2. Microsoft imza anahtarı kaydedin.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Dotnet ürün akışı ekleyin.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. .NET Core SDK yükleyin.

   ```bash
   sudo dnf update
   sudo dnf install libunwind libicu
   sudo dnf install dotnet-sdk-2.0.0
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Fedora 24**

2. Önkoşullar alın.

   ```bash
   sudo dnf install libunwind libicu
   ```

3. .NET Core SDK ikili (tarball) indirin.

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848833
   ```

4. .NET Core SDK ikili dosyaları ayıklayın.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-centos-71-64-bit--oracle-linux-71-64-bit"></a>.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yükleme

.NET Core CentOS 7.1 (64 bit) ve Oracle Linux 7.1 (64 bit) için yüklemek için:

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

2. Microsoft imza anahtarı kaydedin.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Microsoft Product akışı ekleyin.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo'
   ```

4. .NET Core SDK yükleyin.

   ```bash
   sudo yum update
   sudo yum install libunwind libicu
   sudo yum install dotnet-sdk-2.0.0
   ```

5. DotNet YOLUNUZU ekleme

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

2. Önkoşullar alın.

   ```bash
   sudo yum install libunwind libicu
   ```
   
3. .NET Core SDK ikili (tarball) indirin.

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848821
   ```

4. .NET Core SDK ikili dosyaları ayıklayın.

   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```

---

6. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

## <a name="install-net-core-for-suse-linux-enterprise-server-64-bit"></a>.NET Core SUSE Linux Enterprise Server (64 bit) için yükleme

.NET Core yüklemek için 2.x için SUSE Linux Enterprise Server (SLES) 12 SP2 (64 bit):

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

2. Dotnet ürün akışı ekleyin.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ```

3. .NET Core SDK yükleyin.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

4. DotNet YOLUNU ekleyin.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

5. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```
   
## <a name="install-net-core-for-opensuse-64-bit"></a>.NET Core (64 bit) openSUSE için yükleyin

.NET Core yüklemek için openSUSE veya .NET Core 2.x 1.x openSUSE (64 bit) için:

1. Herhangi bir kaldırma **önceki Önizleme** sisteminizi .NET Core sürümlerinden.

> [!NOTE]
> Bir kullanıcı tarafından denetlenen dizin sistemi tar.gz yükler Linux için gereklidir.

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

2. Microsoft imza anahtarı kaydedin.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

3. Dotnet ürün akışı ekleyin.

   ```bash
   sudo sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl=https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/zypp/repos.d/dotnetdev.repo'
   ``` 

4. .NET Core SDK yükleyin.

   ```bash
   sudo zypper update
   sudo zypper install libunwind libicu
   sudo zypper install dotnet-sdk-2.0.0
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   export PATH=$PATH:$HOME/dotnet
   ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

2. Önkoşullar alın.

   ```bash
   sudo zypper install libunwind libicu
   ```

3. .NET Core SDK ikili (tarball) indirin.

   ```bash
   curl -sSL -o dotnet.tar.gz https://go.microsoft.com/fwlink/?linkid=848824
   ```

4. .NET Core SDK ikili dosyaları ayıklayın.
   
   ```bash
   sudo mkdir -p /opt/dotnet && sudo tar zxf dotnet.tar.gz -C /opt/dotnet
   ```

5. DotNet YOLUNU ekleyin.

   ```bash
   sudo ln -s /opt/dotnet/dotnet /usr/local/bin
   ```
   
---

6. Çalıştırma `dotnet --version` başarılı yükleme kanıtlamak için komutu.

   ```bash
   dotnet --version
   ```

> [!IMPORTANT]
> Desteklenen bir Linux dağıtım/sürümünde .NET Core 2.x yükleme sorunları varsa başvurun [2.0 bilinen sorunlar](https://github.com/dotnet/core/tree/master/release-notes/2.0) yüklü dağıtımları/sürümü için konu. 
>
> Desteklenen bir Linux dağıtım/sürümünde .NET Core 1.x yükleme sorunları varsa başvurun [1.0.0 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) ve [1.0.1 bilinen sorunlar](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) yüklü dağıtımları konuları / sürümleri.
