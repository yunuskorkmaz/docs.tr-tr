---
title: dotnet mağaza komutu
description: "'dotnet mağazası' komutu belirtilen derlemeleri çalışma zamanı paket deposunda depolar."
ms.date: 02/14/2020
ms.openlocfilehash: da1d132b2b873ff55ec104b5bb092d0194889bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503583"
---
# <a name="dotnet-store"></a><span data-ttu-id="e9d8e-103">dotnet store</span><span class="sxs-lookup"><span data-stu-id="e9d8e-103">dotnet store</span></span>

<span data-ttu-id="e9d8e-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="e9d8e-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e9d8e-105">Adı</span><span class="sxs-lookup"><span data-stu-id="e9d8e-105">Name</span></span>

<span data-ttu-id="e9d8e-106">`dotnet store`- Belirtilen montajları [çalışma zamanı paket deposunda](../deploying/runtime-store.md)saklar.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-106">`dotnet store` - Stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span>

## <a name="synopsis"></a><span data-ttu-id="e9d8e-107">Özet</span><span class="sxs-lookup"><span data-stu-id="e9d8e-107">Synopsis</span></span>

```dotnetcli
dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]
```

## <a name="description"></a><span data-ttu-id="e9d8e-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e9d8e-108">Description</span></span>

<span data-ttu-id="e9d8e-109">`dotnet store`belirtilen montajları çalışma [zamanı paket deposunda](../deploying/runtime-store.md)saklar.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-109">`dotnet store` stores the specified assemblies in the [runtime package store](../deploying/runtime-store.md).</span></span> <span data-ttu-id="e9d8e-110">Varsayılan olarak, derlemeler hedef çalışma süresi ve çerçeve için en iyi duruma getirilir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-110">By default, assemblies are optimized for the target runtime and framework.</span></span> <span data-ttu-id="e9d8e-111">Daha fazla bilgi için [çalışma zamanı paket deposu](../deploying/runtime-store.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-111">For more information, see the [runtime package store](../deploying/runtime-store.md) topic.</span></span>

## <a name="required-options"></a><span data-ttu-id="e9d8e-112">Gerekli seçenekler</span><span class="sxs-lookup"><span data-stu-id="e9d8e-112">Required options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="e9d8e-113">[Hedef çerçeveyi](../../standard/frameworks.md)belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-113">Specifies the [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e9d8e-114">Hedef çerçeve proje dosyasında belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-114">The target framework has to be specified in the project file.</span></span>

- **`-m|--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="e9d8e-115">*Paket deposu bildirimi dosyası,* depoya çıkacak paketlerin listesini içeren bir XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-115">The *package store manifest file* is an XML file that contains the list of packages to store.</span></span> <span data-ttu-id="e9d8e-116">Bildirim dosyasının biçimi SDK tarzı proje biçimiyle uyumludur.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-116">The format of the manifest file is compatible with the SDK-style project format.</span></span> <span data-ttu-id="e9d8e-117">Bu nedenle, istenilen paketlere başvuran bir proje `-m|--manifest` dosyası, derlemeleri çalışma zamanı paket deposunda depolama seçeneğiyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-117">So, a project file that references the desired packages can be used with the `-m|--manifest` option to store assemblies in the runtime package store.</span></span> <span data-ttu-id="e9d8e-118">Birden çok bildirim dosyası belirtmek için, her dosya için seçeneği ve yolu yineleyin.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-118">To specify multiple manifest files, repeat the option and path for each file.</span></span> <span data-ttu-id="e9d8e-119">Örneğin: `--manifest packages1.csproj --manifest packages2.csproj`.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-119">For example: `--manifest packages1.csproj --manifest packages2.csproj`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="e9d8e-120">Hedef için [çalışma zamanı tanımlayıcısı.](../rid-catalog.md)</span><span class="sxs-lookup"><span data-stu-id="e9d8e-120">The [runtime identifier](../rid-catalog.md) to target.</span></span>

## <a name="optional-options"></a><span data-ttu-id="e9d8e-121">İsteğe bağlı seçenekler</span><span class="sxs-lookup"><span data-stu-id="e9d8e-121">Optional options</span></span>

- **`--framework-version <FRAMEWORK_VERSION>`**

  <span data-ttu-id="e9d8e-122">.NET Core SDK sürümünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-122">Specifies the .NET Core SDK version.</span></span> <span data-ttu-id="e9d8e-123">Bu seçenek, `-f|--framework` seçenek tarafından belirtilen çerçevenin ötesinde belirli bir çerçeve sürümü seçmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-123">This option enables you to select a specific framework version beyond the framework specified by the `-f|--framework` option.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e9d8e-124">Yardım bilgilerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-124">Shows help information.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="e9d8e-125">Çalışma zamanı paket deposuna giden yolu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-125">Specifies the path to the runtime package store.</span></span> <span data-ttu-id="e9d8e-126">Belirtilmemişse, kullanıcı profili .NET Core yükleme dizininin *mağaza* alt dizini varsayılan olarak.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-126">If not specified, it defaults to the *store* subdirectory of the user profile .NET Core installation directory.</span></span>

- **`--skip-optimization`**

  <span data-ttu-id="e9d8e-127">Optimizasyon aşamasını atlar.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-127">Skips the optimization phase.</span></span>

- **`--skip-symbols`**

  <span data-ttu-id="e9d8e-128">Sembol neslini atlar.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-128">Skips symbol generation.</span></span> <span data-ttu-id="e9d8e-129">Şu anda yalnızca Windows ve Linux'ta semboller oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-129">Currently, you can only generate symbols on Windows and Linux.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="e9d8e-130">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e9d8e-131">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="e9d8e-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`-w|--working-dir <WORKING_DIRECTORY>`**

  <span data-ttu-id="e9d8e-132">Komut tarafından kullanılan çalışma dizini.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-132">The working directory used by the command.</span></span> <span data-ttu-id="e9d8e-133">Belirtilmemişse, geçerli dizinin *obj* alt dizini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-133">If not specified, it uses the *obj* subdirectory of the current directory.</span></span>

## <a name="examples"></a><span data-ttu-id="e9d8e-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e9d8e-134">Examples</span></span>

- <span data-ttu-id="e9d8e-135">.NET Core 2.0.0 için *packages.csproj* proje dosyasında belirtilen paketleri saklayın:</span><span class="sxs-lookup"><span data-stu-id="e9d8e-135">Store the packages specified in the *packages.csproj* project file for .NET Core 2.0.0:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --framework-version 2.0.0
  ```

- <span data-ttu-id="e9d8e-136">*Paketlerde* belirtilen paketleri en iyi duruma kaynaklanmadan saklayın:</span><span class="sxs-lookup"><span data-stu-id="e9d8e-136">Store the packages specified in the *packages.csproj* without optimization:</span></span>

  ```dotnetcli
  dotnet store --manifest packages.csproj --skip-optimization
  ```

## <a name="see-also"></a><span data-ttu-id="e9d8e-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9d8e-137">See also</span></span>

- [<span data-ttu-id="e9d8e-138">Çalışma zamanı paket deposu</span><span class="sxs-lookup"><span data-stu-id="e9d8e-138">Runtime package store</span></span>](../deploying/runtime-store.md)
