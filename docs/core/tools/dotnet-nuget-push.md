---
title: DotNet nuget anında iletme komutu
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve belgeyi yayımlar.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 4f0d127d8b9f37b1c381d8981f54035a2fc3b0e5
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169358"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="c2578-103">DotNet nuget anında iletme</span><span class="sxs-lookup"><span data-stu-id="c2578-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c2578-104">Ad</span><span class="sxs-lookup"><span data-stu-id="c2578-104">Name</span></span>

<span data-ttu-id="c2578-105">`dotnet nuget push` -Sunucuya bir paket gönderir ve belgeyi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="c2578-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c2578-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="c2578-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c2578-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c2578-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c2578-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c2578-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="c2578-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c2578-109">Description</span></span>

<span data-ttu-id="c2578-110">`dotnet nuget push` Komutu, yayımlar ve sunucuya bir paket gönderir.</span><span class="sxs-lookup"><span data-stu-id="c2578-110">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="c2578-111">Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c2578-111">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="c2578-112">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="c2578-112">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="c2578-113">NuGet'ın varsayılan yapılandırmayı yükleyerek elde *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), tüm yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.</span><span class="sxs-lookup"><span data-stu-id="c2578-113">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="c2578-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="c2578-114">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="c2578-115">İtilecek paket dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-115">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="c2578-116">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c2578-116">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="c2578-117">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="c2578-117">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="c2578-118">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c2578-118">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="c2578-119">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="c2578-119">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="c2578-120">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c2578-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="c2578-121">Engellemek bir komut verir ve kimlik doğrulaması gibi işlemler için el ile gerçekleştirilen eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="c2578-121">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="c2578-122">Seçeneği bu yana .NET Core 2.2 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2578-122">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="c2578-123">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c2578-123">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="c2578-124">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="c2578-124">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="c2578-125">"API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="c2578-125">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="c2578-126">Seçeneği bu yana .NET Core 2.1 SDK kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c2578-126">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="c2578-127">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-127">Specifies the server URL.</span></span> <span data-ttu-id="c2578-128">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c2578-128">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="c2578-129">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c2578-129">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="c2578-130">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-130">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="c2578-131">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="c2578-132">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="c2578-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="c2578-133">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="c2578-133">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="c2578-134">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="c2578-134">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-d|--disable-buffering`**

  <span data-ttu-id="c2578-135">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c2578-135">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="c2578-136">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="c2578-136">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="c2578-137">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="c2578-137">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="c2578-138">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c2578-138">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="c2578-139">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="c2578-139">Doesn't push symbols (even if present).</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="c2578-140">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-140">Specifies the server URL.</span></span> <span data-ttu-id="c2578-141">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c2578-141">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="c2578-142">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="c2578-142">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="c2578-143">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-143">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="c2578-144">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="c2578-144">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="c2578-145">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="c2578-145">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="c2578-146">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="c2578-146">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="c2578-147">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c2578-147">Examples</span></span>

* <span data-ttu-id="c2578-148">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı için bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="c2578-148">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="c2578-149">Anında iletme *foo.nupkg* özel anında iletme kaynağına `https://customsource`, bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="c2578-149">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="c2578-150">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı:</span><span class="sxs-lookup"><span data-stu-id="c2578-150">Pushes *foo.nupkg* to the default push source:</span></span>

  ```console
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="c2578-151">Gönderim *foo.symbols.nupkg* varsayılan simgeleri kaynağı:</span><span class="sxs-lookup"><span data-stu-id="c2578-151">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="c2578-152">Gönderim *foo.nupkg* varsayılan anında iletme kaynağına 360 saniyelik zaman aşımı belirtme:</span><span class="sxs-lookup"><span data-stu-id="c2578-152">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="c2578-153">Tüm göndermeler *.nupkg* varsayılan anında iletme kaynağına geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="c2578-153">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```console
  dotnet nuget push *.nupkg
  ```