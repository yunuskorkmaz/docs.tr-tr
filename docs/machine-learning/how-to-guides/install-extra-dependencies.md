---
title: Ek ML.NET bağımlılıklarını yükler
description: ML.NET paketlerinin bağlı olduğu ancak NuGet paketleriyle birlikte yüklenmeyen tüm yerel kitaplıkları yüklemeyi öğrenin
ms.date: 04/02/2020
author: natke
ms.author: nakersha
ms.custom: how-to
ms.openlocfilehash: 75d29c6bafdce5c9bb104229ddc8d7b847f57e29
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366801"
---
# <a name="install-extra-mlnet-dependencies"></a><span data-ttu-id="60e71-103">Ek ML.NET bağımlılıklarını yükler</span><span class="sxs-lookup"><span data-stu-id="60e71-103">Install extra ML.NET dependencies</span></span>

<span data-ttu-id="60e71-104">Çoğu durumda, tüm işletim sistemlerinde, ML.NET yüklemek uygun NuGet paketine başvurmak kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="60e71-104">In most cases, on all operating systems, installing ML.NET is as simple as referencing the appropriate NuGet package.</span></span>

```dotnetcli
dotnet add package Microsoft.ML
```

<span data-ttu-id="60e71-105">Ancak bazı durumlarda, özellikle yerel bileşenler gerektiğinde ek yükleme gereksinimleri vardır.</span><span class="sxs-lookup"><span data-stu-id="60e71-105">In some cases though, there are additional installation requirements, particularly when native components are required.</span></span> <span data-ttu-id="60e71-106">Bu belgede, bu durumlar için Yükleme gereksinimleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60e71-106">This document describes the installation requirements for those cases.</span></span> <span data-ttu-id="60e71-107">Bölümler, `Microsoft.ML.*` ek bağımlılığı olan belirli bir NuGet paketi tarafından bölünür.</span><span class="sxs-lookup"><span data-stu-id="60e71-107">The sections are broken down by the specific `Microsoft.ML.*` NuGet package that has the additional dependency.</span></span>

## <a name="microsoftmltimeseries-microsoftmlautoml"></a><span data-ttu-id="60e71-108">Microsoft. ML. TimeSeries, Microsoft. ML. oto ml</span><span class="sxs-lookup"><span data-stu-id="60e71-108">Microsoft.ML.TimeSeries, Microsoft.ML.AutoML</span></span>

<span data-ttu-id="60e71-109">Bu paketlerin her ikisi de bağımlılığı olan ' a bağımlıdır `Microsoft.ML.MKL.Redist` `libomp` .</span><span class="sxs-lookup"><span data-stu-id="60e71-109">Both of these packages have a dependency on `Microsoft.ML.MKL.Redist`, which has a dependency on `libomp`.</span></span>

### <a name="windows"></a><span data-ttu-id="60e71-110">Windows</span><span class="sxs-lookup"><span data-stu-id="60e71-110">Windows</span></span>

<span data-ttu-id="60e71-111">Ek yükleme adımı gerekmez.</span><span class="sxs-lookup"><span data-stu-id="60e71-111">No extra installation steps required.</span></span> <span data-ttu-id="60e71-112">Kitaplık, NuGet paketi projeye eklendiğinde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="60e71-112">The library is installed when the NuGet package is added to the project.</span></span>

### <a name="linux"></a><span data-ttu-id="60e71-113">Linux</span><span class="sxs-lookup"><span data-stu-id="60e71-113">Linux</span></span>

1. <span data-ttu-id="60e71-114">Depo için GPG anahtarını yükler</span><span class="sxs-lookup"><span data-stu-id="60e71-114">Install the GPG key for the repository</span></span>

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

2. <span data-ttu-id="60e71-115">MKL için APT deposunu ekleme</span><span class="sxs-lookup"><span data-stu-id="60e71-115">Add the APT Repository for MKL</span></span>

    ```bash
    sudo sh -c 'echo deb https://apt.repos.intel.com/mkl all main > /etc/apt/sources.list.d/intel-mkl.list'
    ```

3. <span data-ttu-id="60e71-116">Güncelleştirme paketleri</span><span class="sxs-lookup"><span data-stu-id="60e71-116">Update packages</span></span>

    ```bash
    sudo apt-get update
    ```

4. <span data-ttu-id="60e71-117">MKL 'yi yükler</span><span class="sxs-lookup"><span data-stu-id="60e71-117">Install MKL</span></span>

    ```bash
    sudo apt-get install <COMPONENT>-<VERSION>.<UPDATE>-<BUILD_NUMBER>
    ```

    <span data-ttu-id="60e71-118">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60e71-118">For example:</span></span>

    ```bash
    sudo apt-get install intel-mkl-64bit-2020.0-088
    ```

    <span data-ttu-id="60e71-119">Konumunu belirleme `libiomp.so`</span><span class="sxs-lookup"><span data-stu-id="60e71-119">Determine the location of `libiomp.so`</span></span>

    ```bash
    find /opt -name "libiomp5.so"
    ```

    <span data-ttu-id="60e71-120">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="60e71-120">For example:</span></span>

    ```output
    /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin/libiomp5.so
    ```

5. <span data-ttu-id="60e71-121">Bu konumu yükleme kitaplığı yoluna ekleyin:</span><span class="sxs-lookup"><span data-stu-id="60e71-121">Add this location to the load library path:</span></span>

    ```bash
    sudo ldconfig /opt/intel/compilers_and_libraries_2020.0.166/linux/compiler/lib/intel64_lin
    ```

### <a name="mac"></a><span data-ttu-id="60e71-122">Mac</span><span class="sxs-lookup"><span data-stu-id="60e71-122">Mac</span></span>

1. <span data-ttu-id="60e71-123">Kitaplığı ile birlikte yükler `Homebrew`</span><span class="sxs-lookup"><span data-stu-id="60e71-123">Install the library with `Homebrew`</span></span>

    ```bash
    brew update && brew install https://raw.githubusercontent.com/Homebrew/homebrew-core/f5b1ac99a7fba27c19cee0bc4f036775c889b359/Formula/libomp.rb && brew link libomp --force
    ```
