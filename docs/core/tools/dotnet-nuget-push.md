---
title: DotNet nuget anında iletme komutu - .NET Core CLI
description: Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve onu yayımlar.
author: karann-msft
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: c835b1b9d44b9ed12dc0ea4568414a83c926ae4f
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696500"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="f96c5-103">DotNet nuget gönderme</span><span class="sxs-lookup"><span data-stu-id="f96c5-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f96c5-104">Ad</span><span class="sxs-lookup"><span data-stu-id="f96c5-104">Name</span></span>

<span data-ttu-id="f96c5-105">`dotnet nuget push` -Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f96c5-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f96c5-106">Özet</span><span class="sxs-lookup"><span data-stu-id="f96c5-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f96c5-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f96c5-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f96c5-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="f96c5-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f96c5-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f96c5-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="f96c5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f96c5-110">Description</span></span>

<span data-ttu-id="f96c5-111">`dotnet nuget push` Komutu sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f96c5-111">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="f96c5-112">Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-112">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="f96c5-113">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f96c5-113">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="f96c5-114">NuGet'ın varsayılan yapılandırması yükleyerek elde edilir *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), herhangi bir yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.</span><span class="sxs-lookup"><span data-stu-id="f96c5-114">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="f96c5-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="f96c5-115">Arguments</span></span>

`ROOT`

<span data-ttu-id="f96c5-116">Edilmesini paketin dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-116">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="f96c5-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f96c5-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="f96c5-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="f96c5-118">.NET Core 2.1</span></span>](#tab/netcore21)

`-d|--disable-buffering`

<span data-ttu-id="f96c5-119">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="f96c5-120">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="f96c5-120">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="f96c5-121">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-121">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="f96c5-122">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-122">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="f96c5-123">Simgeler anında değil (varsa bile).</span><span class="sxs-lookup"><span data-stu-id="f96c5-123">Doesn't push symbols (even if present).</span></span>

`--no-service-endpoint`

<span data-ttu-id="f96c5-124">"V2/api/paketler" kaynak URL'sini append değil.</span><span class="sxs-lookup"><span data-stu-id="f96c5-124">Doesn't append "api/v2/packages" to the source URL.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="f96c5-125">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-125">Specifies the server URL.</span></span> <span data-ttu-id="f96c5-126">Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="f96c5-127">Simge sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-127">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="f96c5-128">Sembol sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-128">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="f96c5-129">Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f96c5-130">Varsayılan olarak 300 saniye (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="f96c5-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f96c5-131">Varsayılan değer belirten 0 (sıfır saniye) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-131">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="f96c5-132">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="f96c5-132">.NET Core 2.0</span></span>](#tab/netcore20)

`-d|--disable-buffering`

<span data-ttu-id="f96c5-133">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-133">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="f96c5-134">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="f96c5-134">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="f96c5-135">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-135">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="f96c5-136">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-136">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="f96c5-137">Simgeler anında değil (varsa bile).</span><span class="sxs-lookup"><span data-stu-id="f96c5-137">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="f96c5-138">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-138">Specifies the server URL.</span></span> <span data-ttu-id="f96c5-139">Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-139">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="f96c5-140">Simge sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-140">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="f96c5-141">Sembol sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-141">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="f96c5-142">Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-142">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f96c5-143">Varsayılan olarak 300 saniye (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="f96c5-143">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f96c5-144">Varsayılan değer belirten 0 (sıfır saniye) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-144">Specifying 0 (zero seconds) applies the default value.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="f96c5-145">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="f96c5-145">.NET Core 1.x</span></span>](#tab/netcore1x)

`-d|--disable-buffering`

<span data-ttu-id="f96c5-146">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-146">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

`--force-english-output`

<span data-ttu-id="f96c5-147">Bir sabit, İngilizce tabanlı kültürü kullanarak çalıştırmak için uygulamayı zorlar.</span><span class="sxs-lookup"><span data-stu-id="f96c5-147">Forces the application to run using an invariant, English-based culture.</span></span>

`-h|--help`

<span data-ttu-id="f96c5-148">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-148">Prints out a short help for the command.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="f96c5-149">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-149">The API key for the server.</span></span>

`-n|--no-symbols`

<span data-ttu-id="f96c5-150">Simgeler anında değil (varsa bile).</span><span class="sxs-lookup"><span data-stu-id="f96c5-150">Doesn't push symbols (even if present).</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="f96c5-151">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-151">Specifies the server URL.</span></span> <span data-ttu-id="f96c5-152">Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-152">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`-sk|--symbol-api-key <API_KEY>`

<span data-ttu-id="f96c5-153">Simge sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f96c5-153">The API key for the symbol server.</span></span>

`-ss|--symbol-source <SOURCE>`

<span data-ttu-id="f96c5-154">Sembol sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-154">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="f96c5-155">Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f96c5-155">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f96c5-156">Varsayılan olarak 300 saniye (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="f96c5-156">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f96c5-157">Varsayılan değer belirten 0 (sıfır saniye) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f96c5-157">Specifying 0 (zero seconds) applies the default value.</span></span>

---

## <a name="examples"></a><span data-ttu-id="f96c5-158">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f96c5-158">Examples</span></span>

<span data-ttu-id="f96c5-159">İter *foo.nupkg* varsayılan itme kaynağına bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="f96c5-159">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="f96c5-160">Anında iletme *foo.nupkg* özel itme kaynağına `http://customsource`, bir API anahtarı belirtme:</span><span class="sxs-lookup"><span data-stu-id="f96c5-160">Push *foo.nupkg* to the custom push source `http://customsource`, specifying an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="f96c5-161">İter *foo.nupkg* varsayılan itme kaynağına:</span><span class="sxs-lookup"><span data-stu-id="f96c5-161">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="f96c5-162">İter *foo.symbols.nupkg* varsayılan simgeleri kaynağına:</span><span class="sxs-lookup"><span data-stu-id="f96c5-162">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="f96c5-163">İter *foo.nupkg* 360 saniyelik zaman aşımı varsayılan itme kaynağına belirtme:</span><span class="sxs-lookup"><span data-stu-id="f96c5-163">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="f96c5-164">Tüm iter *.nupkg* varsayılan itme kaynağına geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="f96c5-164">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="f96c5-165">Tüm iter *.nupkg* özel yapılandırma dosyanızı belirten varsayılan itme kaynağına geçerli dizindeki dosyaları *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="f96c5-165">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
