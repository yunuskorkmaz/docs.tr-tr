---
title: DotNet nuget Yereller komutu
description: Dotnet nuget Yereller komutu kaldırır veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketler klasörü gibi yerel NuGet kaynakları listeler.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 6436bbaee7ae50f4b225c32b2245c737b0d359c3
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539263"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="fc1bf-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="fc1bf-103">dotnet nuget locals</span></span>

<span data-ttu-id="fc1bf-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="fc1bf-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="fc1bf-105">Ad</span><span class="sxs-lookup"><span data-stu-id="fc1bf-105">Name</span></span>

<span data-ttu-id="fc1bf-106">`dotnet nuget locals` -Temizler veya yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fc1bf-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="fc1bf-107">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="fc1bf-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc1bf-108">Description</span></span>

<span data-ttu-id="fc1bf-109">`dotnet nuget locals` Komut temizler veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketleri klasörünü yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="fc1bf-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="fc1bf-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="fc1bf-111">Liste veya temizlemek için önbellek konumu.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-111">The cache location to list or clear.</span></span> <span data-ttu-id="fc1bf-112">Aşağıdaki değerlerden birini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="fc1bf-113">`all` -Tüm önbellek türleri için belirtilen işlem geçerli olduğunu gösterir: http istek önbelleği, genel paketleri yazma önbelleği ve geçici önbellek.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="fc1bf-114">`http-cache` -Belirtilen işlem yalnızca http isteğini önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="fc1bf-115">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="fc1bf-116">`global-packages` -Belirtilen işlem yalnızca genel paketleri önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="fc1bf-117">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="fc1bf-118">`temp` -Belirtilen işlem yalnızca geçici önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="fc1bf-119">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="fc1bf-120">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="fc1bf-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="fc1bf-121">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="fc1bf-122">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="fc1bf-123">Açık seçeneği, belirtilen önbellek türü açık bir işlem yürütür.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="fc1bf-124">Önbellek dizin içeriğini silinen yinelemeli olarak var.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="fc1bf-125">Yürütülen kullanıcı/Grup dosyalar için önbellek dizinleri de iznine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="fc1bf-126">Aksi durumda, seçili olmayan dosyaların/klasörlerin belirten bir hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="fc1bf-127">Liste seçeneği, belirtilen önbellek türü konumunu görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc1bf-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="fc1bf-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fc1bf-128">Examples</span></span>

* <span data-ttu-id="fc1bf-129">Tüm yerel önbellek dizini (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="fc1bf-130">Yerel http önbellek dizin yolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-130">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="fc1bf-131">Tüm yerel önbellek dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="fc1bf-132">Yerel paketler genel önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-132">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="fc1bf-133">Yerel geçici önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="fc1bf-133">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="fc1bf-134">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="fc1bf-134">Troubleshooting</span></span>

<span data-ttu-id="fc1bf-135">Kullanırken sık karşılaşılan sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="fc1bf-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
