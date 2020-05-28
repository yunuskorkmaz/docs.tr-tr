---
title: Ek ML.NET bağımlılıklarını yükler
description: ML.NET paketlerinin bağlı olduğu ancak NuGet paketleriyle birlikte yüklenmeyen tüm yerel kitaplıkları yüklemeyi öğrenin
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: c744b42b4b95681de7b0cbeaef338cc890708fd8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008436"
---
# <a name="install-extra-mlnet-dependencies"></a>Ek ML.NET bağımlılıklarını yükler

Çoğu durumda, tüm işletim sistemlerinde, ML.NET yüklemek uygun NuGet paketine başvurmak kadar basittir.

```dotnetcli
dotnet add package Microsoft.ML
```

Ancak bazı durumlarda, özellikle yerel bileşenler gerektiğinde ek yükleme gereksinimleri vardır. Bu belgede, bu durumlar için Yükleme gereksinimleri açıklanmaktadır. Bölümler, `Microsoft.ML.*` ek bağımlılığı olan belirli bir NuGet paketi tarafından bölünür.

## <a name="microsoftmltimeseries-microsoftmlautoml"></a>Microsoft. ML. TimeSeries, Microsoft. ML. oto ml

Bu paketlerin her ikisi de bağımlılığı olan ' a bağımlıdır `Microsoft.ML.MKL.Redist` `libiomp` .

### <a name="windows"></a>Windows

Ek yükleme adımı gerekmez. Kitaplık, NuGet paketi projeye eklendiğinde yüklenir.

### <a name="linux"></a>Linux

1. Depo için GPG anahtarını yükler

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

2. MKL için APT deposunu ekleme

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. Güncelleştirme paketleri

    ```bash
    sudo apt-get update
    ```

4. MKL 'yi yükler

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    Örneğin:

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    Konumunu belirleme`libiomp.so`

    ```bash
    find /opt -name "libiomp5.so"
    ```

    Örneğin:

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. Bu konumu yükleme kitaplığı yoluna ekleyin:

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a>Mac

1. Kitaplığı ile birlikte yükler`Homebrew`

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
