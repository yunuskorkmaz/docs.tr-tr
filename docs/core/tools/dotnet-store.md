---
title: DotNet depo komutu
description: "' DotNet Store ' komutu, belirtilen derlemeleri çalışma zamanı paket deposunda depolar."
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503583"
---
# <a name="dotnet-store"></a><span data-ttu-id="5306a-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="5306a-103">dotnet store</span></span>

<span data-ttu-id="5306a-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5306a-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5306a-105">Adı</span><span class="sxs-lookup"><span data-stu-id="5306a-105">Name</span></span>

<span data-ttu-id="5306a-106">`dotnet store`-belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="5306a-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="5306a-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5306a-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="5306a-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5306a-108">Description</span></span>

<span data-ttu-id="5306a-109">`dotnet store`, belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="5306a-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="5306a-110">Varsayılan olarak, derlemeler hedef çalışma zamanına ve çerçeveye en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="5306a-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="5306a-111">Daha fazla bilgi için bkz. [çalışma zamanı paket deposu](../deploying/runtime-store.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="5306a-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="5306a-112">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="5306a-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5306a-113">[Hedef çerçeveyi](../../standard/frameworks.md)belirtir.</span><span class="sxs-lookup"><span data-stu-id="5306a-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5306a-114">Hedef çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5306a-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="5306a-115">*Paket deposu bildirim dosyası* , depolanacak paketlerin listesini IÇEREN bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="5306a-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="5306a-116">Bildirim dosyasının biçimi, SDK stili proje biçimiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="5306a-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="5306a-117">Bu nedenle, istenen paketlere başvuran bir proje dosyası, derlemeleri çalışma zamanı paket deposunda depolamak için `-m|--manifest` seçeneği ile birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5306a-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="5306a-118">Birden çok bildirim dosyası belirtmek için, her bir dosyanın seçeneğini ve yolunu tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="5306a-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="5306a-119">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="5306a-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5306a-120">Hedeflenecek [çalışma zamanı tanımlayıcısı](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="5306a-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="5306a-121">İsteğe bağlı seçenekler</span><span class="sxs-lookup"><span data-stu-id="5306a-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="5306a-122">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="5306a-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="5306a-123">Bu seçenek, `-f|--framework` seçeneği tarafından belirtilen çerçevenin ötesinde belirli bir çerçeve sürümü seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5306a-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5306a-124">Yardım bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5306a-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5306a-125">Çalışma zamanı paket deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5306a-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="5306a-126">Belirtilmemişse, varsayılan olarak Kullanıcı profili .NET Core yükleme dizininin *Depo* alt dizini olur.</span><span class="sxs-lookup"><span data-stu-id="5306a-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="5306a-127">İyileştirme aşamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="5306a-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="5306a-128">Sembol oluşturmayı atlar.</span><span class="sxs-lookup"><span data-stu-id="5306a-128">Skips symbol generation.</span></span> <span data-ttu-id="5306a-129">Şu anda yalnızca Windows ve Linux üzerinde semboller oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5306a-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5306a-130">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5306a-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5306a-131">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5306a-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="5306a-132">Komut tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="5306a-132">The working directory used by the command.</span></span> <span data-ttu-id="5306a-133">Belirtilmemişse, geçerli dizinin *obj* alt dizinini kullanır.</span><span class="sxs-lookup"><span data-stu-id="5306a-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="5306a-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5306a-134">Examples</span></span>

- <span data-ttu-id="5306a-135">.NET Core 2.0.0 için *Packages. csproj* proje dosyasında belirtilen paketleri depolayın:</span><span class="sxs-lookup"><span data-stu-id="5306a-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="5306a-136">*Packages. csproj* içinde belirtilen paketleri iyileştirme olmadan depola:</span><span class="sxs-lookup"><span data-stu-id="5306a-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="5306a-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5306a-137">See also</span></span>

- [<span data-ttu-id="5306a-138">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="5306a-138">Runtime package store</span></span>](../deploying/runtime-store.md)
