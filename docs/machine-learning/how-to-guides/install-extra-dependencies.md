---
title: Ek ML.NET bağımlılıkları yükleyin
description: ML.NET paketlerinin bağımlı olduğu ancak NuGet paketleriyle yüklü olmayan yerel kitaplıkları nasıl yükleyebilirsiniz öğrenin
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c427439d0950bfea38f1d6d11af84216e0f1965f
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021852"
---
# <a name="install-extra-mlnet-dependencies"></a>Ek ML.NET bağımlılıkları yükleyin

Çoğu durumda, tüm işletim sistemlerinde, ML.NET yüklemek, uygun NuGet paketine başvurmak kadar basittir.

```bash
dotnet add package Microsoft.ML
```

Ancak bazı durumlarda, özellikle yerel bileşenler gerektiğinde ek yükleme gereksinimleri vardır. Bu belge, bu servis talepleri için yükleme gereksinimlerini açıklar. Bölümler, ek bağımlılık `Microsoft.ML.*` olan belirli NuGet paketi tarafından ayrılmıştır.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft.ML.TimeSeries, Microsoft.ML.AutoML

Bu paketlerin her ikisi `Microsoft.ML.MKL.Redist`de bir bağımlılık var `libiomp`, hangi bir bağımlılığı vardır.

### <a name="windows"></a>Windows

Ek yükleme adımları gerekmez. NuGet paketi projeye eklendiğinde kitaplık yüklenir.

### <a name="linux"></a>Linux

1. Depo için GPG tuşunu yükleyin

    ```bash
    sudo bash
    # <type your user password when prompted.  this will put you in a root shell>
    # cd to /tmp where this shell has write permission
    cd /tmp
    # now get the key:
    wget https://apt.repos.intel.com/intel-gpg-keys/GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now install that key
    apt-key add GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    # now remove the public key file exit the root shell
    rm GPG-PUB-KEY-INTEL-SW-PRODUCTS-2019.PUB
    exit
    ```

2. MKL için APT Deposu ekle

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Paketleri güncelleştirin

    ```bash
    sudo apt-get update
    ```

4. MKL'yi yükle

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Örneğin:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Konumu belirleyin`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Örneğin:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Bu konumu yük kitaplığı yoluna ekleyin:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Kitaplığı`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
