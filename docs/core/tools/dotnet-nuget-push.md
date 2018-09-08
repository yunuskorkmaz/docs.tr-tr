---
title: DotNet nuget anında iletme komutu - .NET Core CLI
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve belgeyi yayımlar.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186469"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="6c66b-103">DotNet nuget anında iletme</span><span class="sxs-lookup"><span data-stu-id="6c66b-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6c66b-104">Ad</span><span class="sxs-lookup"><span data-stu-id="6c66b-104">Name</span></span>

<span data-ttu-id="6c66b-105">`dotnet nuget push` -Sunucuya bir paket gönderir ve belgeyi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6c66b-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6c66b-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="6c66b-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c66b-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c66b-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c66b-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c66b-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c66b-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c66b-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="6c66b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6c66b-110">Description</span></span>

<span data-ttu-id="6c66b-111">`dotnet nuget push` Komutu, yayımlar ve sunucuya bir paket gönderir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="6c66b-112">Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="6c66b-113">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="6c66b-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="6c66b-114">NuGet'ın varsayılan yapılandırmayı yükleyerek elde *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), tüm yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.</span><span class="sxs-lookup"><span data-stu-id="6c66b-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="6c66b-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c66b-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="6c66b-116">İtilecek paket dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="6c66b-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6c66b-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6c66b-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6c66b-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="6c66b-119">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="6c66b-120">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c66b-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="6c66b-121">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="6c66b-122">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="6c66b-123">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="6c66b-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="6c66b-124">"API/v2/paket" kaynak URL'ye değil.</span><span class="sxs-lookup"><span data-stu-id="6c66b-124">Doesn't append "api/v2/package" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="6c66b-125">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-125">Specifies the server URL.</span></span> <span data-ttu-id="6c66b-126">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="6c66b-127">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="6c66b-128">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="6c66b-129">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="6c66b-130">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="6c66b-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="6c66b-131">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="6c66b-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6c66b-132">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6c66b-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="6c66b-133">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="6c66b-134">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c66b-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="6c66b-135">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="6c66b-136">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="6c66b-137">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="6c66b-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="6c66b-138">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-138">Specifies the server URL.</span></span> <span data-ttu-id="6c66b-139">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="6c66b-140">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="6c66b-141">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="6c66b-142">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="6c66b-143">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="6c66b-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="6c66b-144">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="6c66b-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6c66b-145">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6c66b-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="6c66b-146">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="6c66b-147">Uygulamayı bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için zorlar.</span><span class="sxs-lookup"><span data-stu-id="6c66b-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="6c66b-148">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="6c66b-149">Sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="6c66b-150">Semboller gönderin değil (hatta varsa).</span><span class="sxs-lookup"><span data-stu-id="6c66b-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="6c66b-151">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-151">Specifies the server URL.</span></span> <span data-ttu-id="6c66b-152">Sürece bu seçenek gereklidir `DefaultPushSource` yapılandırma değeri, NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="6c66b-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="6c66b-153">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="6c66b-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="6c66b-154">Sembol sunucusu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="6c66b-155">Saniyeler içinde bir sunucuya göndermek için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6c66b-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="6c66b-156">Varsayılan olarak 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="6c66b-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="6c66b-157">Varsayılan değer belirten 0 (sıfır saniye cinsinden) uygular.</span><span class="sxs-lookup"><span data-stu-id="6c66b-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="6c66b-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6c66b-158">Examples</span></span>

<span data-ttu-id="6c66b-159">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı için bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="6c66b-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="6c66b-160">Anında iletme *foo.nupkg* özel anında iletme kaynağına `http://customsource`, bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="6c66b-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="6c66b-161">Gönderim *foo.nupkg* varsayılan anında iletme kaynağı:</span><span class="sxs-lookup"><span data-stu-id="6c66b-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="6c66b-162">Gönderim *foo.symbols.nupkg* varsayılan simgeleri kaynağı:</span><span class="sxs-lookup"><span data-stu-id="6c66b-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="6c66b-163">Gönderim *foo.nupkg* varsayılan anında iletme kaynağına 360 saniyelik zaman aşımı belirtme:</span><span class="sxs-lookup"><span data-stu-id="6c66b-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="6c66b-164">Tüm göndermeler *.nupkg* varsayılan anında iletme kaynağına geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="6c66b-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`
