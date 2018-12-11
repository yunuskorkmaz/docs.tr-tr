---
title: DotNet nuget Yereller komutu
description: Dotnet nuget Yereller komutu kaldırır veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketler klasörü gibi yerel NuGet kaynakları listeler.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: d0f1c7c2e0b233c214cc48d026c19755fc047bfa
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170762"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="1b3fa-103">DotNet nuget yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="1b3fa-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1b3fa-104">Ad</span><span class="sxs-lookup"><span data-stu-id="1b3fa-104">Name</span></span>

<span data-ttu-id="1b3fa-105">`dotnet nuget locals` -Temizler veya yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1b3fa-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1b3fa-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="1b3fa-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b3fa-107">Description</span></span>

<span data-ttu-id="1b3fa-108">`dotnet nuget locals` Komut temizler veya http istek önbelleği, geçici bir önbellekte ya da makine genelindeki genel paketleri klasörünü yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="1b3fa-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="1b3fa-109">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="1b3fa-110">Liste veya temizlemek için önbellek konumu.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-110">The cache location to list or clear.</span></span> <span data-ttu-id="1b3fa-111">Aşağıdaki değerlerden birini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-111">It accepts one of the following values:</span></span>

  * <span data-ttu-id="1b3fa-112">`all` -Tüm önbellek türleri için belirtilen işlem geçerli olduğunu gösterir: http istek önbelleği, genel paketleri yazma önbelleği ve geçici önbellek.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="1b3fa-113">`http-cache` -Belirtilen işlem yalnızca http isteğini önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="1b3fa-114">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-114">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="1b3fa-115">`global-packages` -Belirtilen işlem yalnızca genel paketleri önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="1b3fa-116">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-116">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="1b3fa-117">`temp` -Belirtilen işlem yalnızca geçici önbelleğe uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="1b3fa-118">Bir önbellek konumlarını etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="1b3fa-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1b3fa-119">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="1b3fa-120">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-120">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="1b3fa-121">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-121">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="1b3fa-122">Açık seçeneği, belirtilen önbellek türü açık bir işlem yürütür.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="1b3fa-123">Önbellek dizin içeriğini silinen yinelemeli olarak var.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="1b3fa-124">Yürütülen kullanıcı/Grup dosyalar için önbellek dizinleri de iznine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="1b3fa-125">Aksi durumda, seçili olmayan dosyaların/klasörlerin belirten bir hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="1b3fa-126">Liste seçeneği, belirtilen önbellek türü konumunu görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1b3fa-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="1b3fa-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1b3fa-127">Examples</span></span>

* <span data-ttu-id="1b3fa-128">Tüm yerel önbellek dizini (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="1b3fa-129">Yerel http önbellek dizin yolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-129">Displays the path for the local http-cache directory:</span></span>

  ```console
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="1b3fa-130">Tüm yerel önbellek dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```console
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="1b3fa-131">Yerel paketler genel önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-131">Clears all files in local global-packages cache directory:</span></span>

  ```console
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="1b3fa-132">Yerel geçici önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="1b3fa-132">Clears all files in local temporary cache directory:</span></span>

  ```console
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="1b3fa-133">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="1b3fa-133">Troubleshooting</span></span>

<span data-ttu-id="1b3fa-134">Kullanırken sık karşılaşılan sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleğini yönetme](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="1b3fa-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>