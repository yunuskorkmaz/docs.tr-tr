---
title: DotNet NuGet Yereller komutu
description: DotNet NuGet Yereller komutu http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: cb5747636aa9d04f1ef6a6ff9309ba29c0630dd6
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087402"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="92d9d-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="92d9d-103">dotnet nuget locals</span></span>

<span data-ttu-id="92d9d-104">**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="92d9d-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="92d9d-105">Name</span><span class="sxs-lookup"><span data-stu-id="92d9d-105">Name</span></span>

<span data-ttu-id="92d9d-106">`dotnet nuget locals`-yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="92d9d-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92d9d-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="92d9d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="92d9d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92d9d-108">Description</span></span>

<span data-ttu-id="92d9d-109">`dotnet nuget locals` komutu, http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasöründeki yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="92d9d-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="92d9d-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="92d9d-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="92d9d-111">Listelemek veya temizlemek için önbellek konumu.</span><span class="sxs-lookup"><span data-stu-id="92d9d-111">The cache location to list or clear.</span></span> <span data-ttu-id="92d9d-112">Aşağıdaki değerlerden birini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="92d9d-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="92d9d-113">`all`-belirtilen işlemin tüm önbellek türlerine uygulandığını gösterir: http-istek önbelleği, genel paketler önbelleği ve geçici önbellek.</span><span class="sxs-lookup"><span data-stu-id="92d9d-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="92d9d-114">`http-cache`-belirtilen işlemin yalnızca http istek önbelleğine uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92d9d-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="92d9d-115">Diğer önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="92d9d-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="92d9d-116">`global-packages`-belirtilen işlemin yalnızca genel paketler önbelleğine uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="92d9d-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="92d9d-117">Diğer önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="92d9d-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="92d9d-118">`temp`-belirtilen işlemin yalnızca geçici önbelleğe uygulandığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="92d9d-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="92d9d-119">Diğer önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="92d9d-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="92d9d-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="92d9d-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="92d9d-121">Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="92d9d-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="92d9d-122">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="92d9d-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="92d9d-123">Clear seçeneği, belirtilen önbellek türü üzerinde açık bir işlem yürütür.</span><span class="sxs-lookup"><span data-stu-id="92d9d-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="92d9d-124">Önbellek dizinlerinin içeriği yinelemeli olarak silinir.</span><span class="sxs-lookup"><span data-stu-id="92d9d-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="92d9d-125">Yürütülen Kullanıcı/Grup, önbellek dizinlerindeki dosyalar üzerinde izne sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="92d9d-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="92d9d-126">Aksi takdirde, temizlenmeyen dosyaları/klasörleri gösteren bir hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="92d9d-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="92d9d-127">Liste seçeneği, belirtilen önbellek türünün konumunu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="92d9d-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="92d9d-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="92d9d-128">Examples</span></span>

* <span data-ttu-id="92d9d-129">Tüm yerel önbellek dizinlerinin (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="92d9d-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

* <span data-ttu-id="92d9d-130">Yerel http önbelleği dizininin yolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="92d9d-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

* <span data-ttu-id="92d9d-131">Tüm yerel önbellek dizinlerindeki tüm dosyaları temizler (http-önbellek dizini, genel paketler önbellek dizini ve geçici önbellek dizini):</span><span class="sxs-lookup"><span data-stu-id="92d9d-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

* <span data-ttu-id="92d9d-132">Yerel genel paketler önbellek dizinindeki tüm dosyaları temizler:</span><span class="sxs-lookup"><span data-stu-id="92d9d-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

* <span data-ttu-id="92d9d-133">Yerel geçici önbellek dizinindeki tüm dosyaları temizler:</span><span class="sxs-lookup"><span data-stu-id="92d9d-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="92d9d-134">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="92d9d-134">Troubleshooting</span></span>

<span data-ttu-id="92d9d-135">`dotnet nuget locals` komutunu kullanırken yaygın sorunlar ve hatalar hakkında bilgi için bkz. [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="92d9d-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
