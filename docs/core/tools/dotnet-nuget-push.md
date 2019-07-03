---
title: DotNet nuget anında iletme komutu
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve belgeyi yayımlar.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4d5efa94c6a4494158aea447be98256d2a307cd6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539138"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="5199f-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="5199f-103">dotnet nuget push</span></span>

<span data-ttu-id="5199f-104">**Bu konu için geçerlidir: ✓** .NET Core SDK'sı 1.x ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="5199f-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5199f-105">Ad</span><span class="sxs-lookup"><span data-stu-id="5199f-105">Name</span></span>

<span data-ttu-id="5199f-106">`dotnet nuget push` -Sunucuya bir paket gönderir ve belgeyi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="5199f-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5199f-107">Synopsis</span><span class="sxs-lookup"><span data-stu-id="5199f-107">Synopsis</span></span>

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5199f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5199f-108">Description</span></span>

<span data-ttu-id="5199f-109">`dotnet nuget push` Komutu, yayımlar ve sunucuya bir paket gönderir.</span><span class="sxs-lookup"><span data-stu-id="5199f-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="5199f-110">Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5199f-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="5199f-111">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5199f-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="5199f-112">NuGet'ın varsayılan yapılandırmayı yükleyerek elde *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), tüm yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.</span><span class="sxs-lookup"><span data-stu-id="5199f-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="5199f-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="5199f-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="5199f-114">İtilecek paket dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5199f-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="5199f-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5199f-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="5199f-116">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5199f-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="5199f-117">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="5199f-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="5199f-118">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5199f-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="5199f-119">Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5199f-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="5199f-120">Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5199f-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="5199f-121">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="5199f-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="5199f-122">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="5199f-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="5199f-123">"API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="5199f-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="5199f-124">Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5199f-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="5199f-125">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5199f-125">Specifies the server URL.</span></span> <span data-ttu-id="5199f-126">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5199f-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="5199f-127">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="5199f-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="5199f-128">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5199f-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="5199f-129">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5199f-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="5199f-130">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="5199f-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="5199f-131">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="5199f-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="5199f-132">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5199f-132">Examples</span></span>

* <span data-ttu-id="5199f-133">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı için bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="5199f-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="5199f-134">Anında iletme *foo.nupkg* özel anında iletme kaynağına `https://customsource`, bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="5199f-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="5199f-135">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı:</span><span class="sxs-lookup"><span data-stu-id="5199f-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="5199f-136">Gönderim *foo.symbols.nupkg* varsayılan simgeleri kaynağı:</span><span class="sxs-lookup"><span data-stu-id="5199f-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="5199f-137">Gönderim *foo.nupkg* varsayılan anında iletme kaynağına 360 saniyelik zaman aşımı belirtme:</span><span class="sxs-lookup"><span data-stu-id="5199f-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="5199f-138">Tüm göndermeler *.nupkg* varsayılan anında iletme kaynağına geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="5199f-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="5199f-139">Bu komut işe yaramazsa, (.NET Core 2.1 SDK ve önceki sürümler) SDK'ın eski sürümlerinde var olan bir hata nedeniyle olabilir.</span><span class="sxs-lookup"><span data-stu-id="5199f-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="5199f-140">Bu sorunu gidermek için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın: `dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="5199f-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
