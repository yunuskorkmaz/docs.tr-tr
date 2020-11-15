---
title: DotNet depo komutu
description: "' DotNet Store ' komutu, belirtilen derlemeleri çalışma zamanı paket deposunda depolar."
ms.date: 02/14/2020
ms.openlocfilehash: 8efb11c6bf648bc7787d5627e02b180abb8a0afd
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634343"
---
# <a name="dotnet-store"></a><span data-ttu-id="fa5fa-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="fa5fa-103">dotnet store</span></span>

<span data-ttu-id="fa5fa-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="fa5fa-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fa5fa-105">Name</span><span class="sxs-lookup"><span data-stu-id="fa5fa-105">Name</span></span>

<span data-ttu-id="fa5fa-106">`dotnet store` -Belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="fa5fa-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="fa5fa-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest <PATH_TO_MANIFEST_FILE>
    -f|--framework <FRAMEWORK_VERSION> -r|--runtime <RUNTIME_IDENTIFIER>
    [--framework-version <FRAMEWORK_VERSION>] [--output <OUTPUT_DIRECTORY>]
    [--skip-optimization] [--skip-symbols] [-v|--verbosity <LEVEL>]
    [--working-dir <WORKING_DIRECTORY>]

dotnet store -h|--help
```

## <a name="description"></a><span data-ttu-id="fa5fa-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fa5fa-108">Description</span></span>

<span data-ttu-id="fa5fa-109">`dotnet store` belirtilen derlemeleri [çalışma zamanı paket deposunda](../deploying/runtime-store.md)depolar.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="fa5fa-110">Varsayılan olarak, derlemeler hedef çalışma zamanına ve çerçeveye en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="fa5fa-111">Daha fazla bilgi için bkz. [çalışma zamanı paket deposu](../deploying/runtime-store.md) konusu.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="fa5fa-112">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="fa5fa-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="fa5fa-113">[Hedef çerçeveyi](../../standard/frameworks.md)belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="fa5fa-114">Hedef çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="fa5fa-115">*Paket deposu bildirim dosyası* , depolanacak paketlerin listesini IÇEREN bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="fa5fa-116">Bildirim dosyasının biçimi, SDK stili proje biçimiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="fa5fa-117">Bu nedenle, istenen paketlere başvuruda bulunan bir proje dosyası, `-m|--manifest` derlemeleri çalışma zamanı paket deposunda depolama seçeneğiyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="fa5fa-118">Birden çok bildirim dosyası belirtmek için, her bir dosyanın seçeneğini ve yolunu tekrarlayın.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="fa5fa-119">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="fa5fa-120">Hedeflenecek [çalışma zamanı tanımlayıcısı](../rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="fa5fa-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="fa5fa-121">İsteğe bağlı seçenekler</span><span class="sxs-lookup"><span data-stu-id="fa5fa-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="fa5fa-122">.NET SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-122">Specifies the .NET SDK version.</span></span> <span data-ttu-id="fa5fa-123">Bu seçenek, seçeneği tarafından belirtilen çerçevenin ötesinde belirli bir çerçeve sürümü seçmenizi sağlar `-f|--framework` .</span><span class="sxs-lookup"><span data-stu-id="fa5fa-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fa5fa-124">Yardım bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="fa5fa-125">Çalışma zamanı paket deposunun yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="fa5fa-126">Belirtilmemişse, varsayılan olarak Kullanıcı profili .NET yükleme dizininin *Depo* alt dizini olur.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="fa5fa-127">İyileştirme aşamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="fa5fa-128">Sembol oluşturmayı atlar.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-128">Skips symbol generation.</span></span> <span data-ttu-id="fa5fa-129">Şu anda yalnızca Windows ve Linux üzerinde semboller oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fa5fa-130">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fa5fa-131">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="fa5fa-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="fa5fa-132">Komut tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-132">The working directory used by the command.</span></span> <span data-ttu-id="fa5fa-133">Belirtilmemişse, geçerli dizinin *obj* alt dizinini kullanır.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="fa5fa-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fa5fa-134">Examples</span></span>

- <span data-ttu-id="fa5fa-135">.NET Core 2.0.0 için *Packages. csproj* proje dosyasında belirtilen paketleri depolayın:</span><span class="sxs-lookup"><span data-stu-id="fa5fa-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="fa5fa-136">*Packages. csproj* içinde belirtilen paketleri iyileştirme olmadan depola:</span><span class="sxs-lookup"><span data-stu-id="fa5fa-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="fa5fa-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa5fa-137">See also</span></span>

- [<span data-ttu-id="fa5fa-138">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="fa5fa-138">Runtime package store</span></span>](../deploying/runtime-store.md)
