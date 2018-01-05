---
title: DotNet nuget Yereller komutu - .NET Core CLI
description: "Dotnet nuget Yereller komutu temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9c8df8e457a9883b86abd0505c0c682d849bc7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="19fdd-103">DotNet nuget yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="19fdd-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="19fdd-104">Ad</span><span class="sxs-lookup"><span data-stu-id="19fdd-104">Name</span></span>

<span data-ttu-id="19fdd-105">`dotnet nuget locals`-Temizler veya yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="19fdd-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="19fdd-106">Özet</span><span class="sxs-lookup"><span data-stu-id="19fdd-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="19fdd-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19fdd-107">Description</span></span>

<span data-ttu-id="19fdd-108">`dotnet nuget locals` Komutu temizler veya http isteği önbelleği, geçici önbelleği ya da makine genelinde genel paketler klasörü yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="19fdd-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="19fdd-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="19fdd-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="19fdd-110">Aşağıdaki değerlerden biri:</span><span class="sxs-lookup"><span data-stu-id="19fdd-110">One of the following values:</span></span>

* <span data-ttu-id="19fdd-111">`all`-Belirtilen işlem için tüm önbellek türleri uygulandığını gösterir: http isteği önbellek, genel paketleri önbellek ve geçici önbelleği.</span><span class="sxs-lookup"><span data-stu-id="19fdd-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="19fdd-112">`http-cache`-Belirtilen işlem yalnızca http isteği önbelleği uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19fdd-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="19fdd-113">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="19fdd-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="19fdd-114">`global-packages`-Belirtilen işlem yalnızca genel paketleri önbelleği uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19fdd-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="19fdd-115">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="19fdd-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="19fdd-116">`temp`-Belirtilen işlem yalnızca geçici önbelleğine uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="19fdd-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="19fdd-117">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="19fdd-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="19fdd-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="19fdd-118">Options</span></span>

`-h|--help`

<span data-ttu-id="19fdd-119">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="19fdd-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="19fdd-120">Temizle seçeneği belirtilen önbellek türü üzerinde NET bir işlemi gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="19fdd-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="19fdd-121">Önbellek dizin içeriğini silinen yinelemeli olarak var.</span><span class="sxs-lookup"><span data-stu-id="19fdd-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="19fdd-122">Yürütülen kullanıcı/grup, önbellek dizinlerdeki dosyalara izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="19fdd-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="19fdd-123">Aksi durumda, dosyaların/klasörlerin hangi değil silinmesinden belirten bir hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="19fdd-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="19fdd-124">Liste seçeneği, belirtilen önbellek türü konumu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="19fdd-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="19fdd-125">Zorlar komut satırı, İngilizce çıktı.</span><span class="sxs-lookup"><span data-stu-id="19fdd-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="19fdd-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="19fdd-126">Examples</span></span>

<span data-ttu-id="19fdd-127">Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="19fdd-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="19fdd-128">Yerel http önbellek dizin yolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="19fdd-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="19fdd-129">Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="19fdd-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="19fdd-130">Yerel paketler genel önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="19fdd-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="19fdd-131">Yerel geçici önbelleği dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="19fdd-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="19fdd-132">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="19fdd-132">Troubleshooting</span></span>

<span data-ttu-id="19fdd-133">Kullanırken yaygın sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleği yönetme](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="19fdd-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>