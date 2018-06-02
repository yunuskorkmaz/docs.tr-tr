---
title: DotNet nuget Yereller komutu - .NET Core CLI
description: Dotnet nuget Yereller komutu temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 799acb92d6ab7439e15c23c9f0b7b572c966adda
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696877"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="63184-103">DotNet nuget yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="63184-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="63184-104">Ad</span><span class="sxs-lookup"><span data-stu-id="63184-104">Name</span></span>

<span data-ttu-id="63184-105">`dotnet nuget locals` -Temizler veya yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="63184-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="63184-106">Özet</span><span class="sxs-lookup"><span data-stu-id="63184-106">Synopsis</span></span>

```
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="63184-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63184-107">Description</span></span>

<span data-ttu-id="63184-108">`dotnet nuget locals` Komutu temizler veya http isteği önbelleği, geçici önbelleği ya da makine genelinde genel paketler klasörü yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="63184-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="63184-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="63184-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="63184-110">Liste veya temizlemek için önbellek konumu.</span><span class="sxs-lookup"><span data-stu-id="63184-110">The cache location to list or clear.</span></span> <span data-ttu-id="63184-111">Aşağıdaki değerlerden birini kabul eder:</span><span class="sxs-lookup"><span data-stu-id="63184-111">It accepts one of the following values:</span></span>

* <span data-ttu-id="63184-112">`all` -Belirtilen işlem için tüm önbellek türleri uygulandığını gösterir: http isteği önbellek, genel paketleri önbellek ve geçici önbelleği.</span><span class="sxs-lookup"><span data-stu-id="63184-112">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="63184-113">`http-cache` -Belirtilen işlem yalnızca http isteği önbelleği uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63184-113">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="63184-114">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="63184-114">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="63184-115">`global-packages` -Belirtilen işlem yalnızca genel paketleri önbelleği uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63184-115">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="63184-116">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="63184-116">The other cache locations aren't affected.</span></span>
* <span data-ttu-id="63184-117">`temp` -Belirtilen işlem yalnızca geçici önbelleğine uygulandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63184-117">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="63184-118">Bir önbellek konumları etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="63184-118">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="63184-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="63184-119">Options</span></span>

`--force-english-output`

<span data-ttu-id="63184-120">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="63184-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="63184-121">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="63184-121">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="63184-122">Temizle seçeneği belirtilen önbellek türündeki clear işlemini yürütür.</span><span class="sxs-lookup"><span data-stu-id="63184-122">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="63184-123">Önbellek dizin içeriğini silinen yinelemeli olarak var.</span><span class="sxs-lookup"><span data-stu-id="63184-123">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="63184-124">Yürütülen kullanıcı/grup, önbellek dizinlerdeki dosyalara izni olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="63184-124">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="63184-125">Aksi durumda, temizlenmiş doğru dosyaların/klasörlerin belirten bir hata görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="63184-125">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

`-l|--list`

<span data-ttu-id="63184-126">Liste seçeneği, belirtilen önbellek türü konumu göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="63184-126">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="63184-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="63184-127">Examples</span></span>

<span data-ttu-id="63184-128">Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) yollarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="63184-128">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="63184-129">Yerel http önbellek dizin yolunu görüntüler:</span><span class="sxs-lookup"><span data-stu-id="63184-129">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="63184-130">Tüm yerel önbelleği dizinleri (http-önbellek dizini, paketleri genel önbellek dizini ve geçici önbellek dizini) tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="63184-130">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="63184-131">Yerel paketler genel önbellek dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="63184-131">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="63184-132">Yerel geçici önbelleği dizindeki tüm dosyaları siler:</span><span class="sxs-lookup"><span data-stu-id="63184-132">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="63184-133">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="63184-133">Troubleshooting</span></span>

<span data-ttu-id="63184-134">Kullanırken yaygın sorunlar ve hatalar hakkında bilgi için `dotnet nuget locals` komutu, bkz: [NuGet önbelleği yönetme](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="63184-134">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>