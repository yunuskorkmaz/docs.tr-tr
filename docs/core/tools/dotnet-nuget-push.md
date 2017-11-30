---
title: "DotNet nuget anında iletme komutu - .NET Core CLI"
description: "Dotnet nuget anında iletme komutu sunucuya bir paket gönderir ve onu yayımlar."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: dc4250ab7417c9f19babdf37c556daf7c3bd6a81
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="f2aab-103">DotNet nuget gönderme</span><span class="sxs-lookup"><span data-stu-id="f2aab-103">dotnet nuget push</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="f2aab-104">Ad</span><span class="sxs-lookup"><span data-stu-id="f2aab-104">Name</span></span>

<span data-ttu-id="f2aab-105">`dotnet nuget push`-Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f2aab-105">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f2aab-106">Özet</span><span class="sxs-lookup"><span data-stu-id="f2aab-106">Synopsis</span></span>

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="f2aab-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2aab-107">Description</span></span>

<span data-ttu-id="f2aab-108">`dotnet nuget push` Komutu sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f2aab-108">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="f2aab-109">Anında iletme komutu, sunucu ve sistemin NuGet yapılandırma dosyası veya yapılandırma dosyaları zincirine bulunan kimlik bilgisi ayrıntıları kullanır.</span><span class="sxs-lookup"><span data-stu-id="f2aab-109">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="f2aab-110">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f2aab-110">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="f2aab-111">NuGet'ın varsayılan yapılandırması yükleyerek elde edilir *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS), herhangi bir yükleme *nuget.config*veya *.nuget\nuget.config* sürücüsünün kökünden başlayıp geçerli dizinde.</span><span class="sxs-lookup"><span data-stu-id="f2aab-111">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="f2aab-112">Arguments</span><span class="sxs-lookup"><span data-stu-id="f2aab-112">Arguments</span></span>

`ROOT`

<span data-ttu-id="f2aab-113">Paket ve paket sunucuya göndermek için API anahtarınıza yolunu belirtin.</span><span class="sxs-lookup"><span data-stu-id="f2aab-113">Specify the path to the package and your API key to push the package to the server.</span></span>

## <a name="options"></a><span data-ttu-id="f2aab-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f2aab-114">Options</span></span>

`-h|--help`

<span data-ttu-id="f2aab-115">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f2aab-115">Prints out a short help for the command.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="f2aab-116">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2aab-116">Specifies the server URL.</span></span> <span data-ttu-id="f2aab-117">Bu seçenek sürece gereklidir `DefaultPushSource` yapılandırma değeri NuGet yapılandırma dosyasında ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f2aab-117">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

`--symbol-source <SOURCE>`

<span data-ttu-id="f2aab-118">Sembol sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2aab-118">Specifies the symbol server URL.</span></span>

`-t|--timeout <TIMEOUT>`

<span data-ttu-id="f2aab-119">Saniye cinsinden bir sunucuya gönderilmesi için zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f2aab-119">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f2aab-120">Varsayılan olarak 300 saniye (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="f2aab-120">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f2aab-121">Varsayılan değer belirten 0 (sıfır saniye) uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f2aab-121">Specifying 0 (zero seconds) applies the default value.</span></span>

`-k|--api-key <API_KEY>`

<span data-ttu-id="f2aab-122">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f2aab-122">The API key for the server.</span></span>

`--symbol-api-key <API_KEY>`

<span data-ttu-id="f2aab-123">Simge sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f2aab-123">The API key for the symbol server.</span></span>

`-d|--disable-buffering`

<span data-ttu-id="f2aab-124">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna iletme zaman arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f2aab-124">Disables buffering when pushing to an HTTP(S) server to decrease memory usage.</span></span>

`-n|--no-symbols`

<span data-ttu-id="f2aab-125">Simgeler anında değil (varsa bile).</span><span class="sxs-lookup"><span data-stu-id="f2aab-125">Doesn't push symbols (even if present).</span></span>

`--force-english-output`

<span data-ttu-id="f2aab-126">Günlüğe kaydedilen tüm çıktı İngilizce zorlar.</span><span class="sxs-lookup"><span data-stu-id="f2aab-126">Forces all logged output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="f2aab-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f2aab-127">Examples</span></span>

<span data-ttu-id="f2aab-128">İter *foo.nupkg* bir API anahtarı varsayılan itme kaynağına sağlama:</span><span class="sxs-lookup"><span data-stu-id="f2aab-128">Pushes *foo.nupkg* to the default push source, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

<span data-ttu-id="f2aab-129">Anında iletme *foo.nupkg* özel itme kaynağına `http://customsource`, bir API anahtarı sağlama:</span><span class="sxs-lookup"><span data-stu-id="f2aab-129">Push *foo.nupkg* to the custom push source `http://customsource`, providing an API key:</span></span>

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

<span data-ttu-id="f2aab-130">İter *foo.nupkg* varsayılan itme kaynağına:</span><span class="sxs-lookup"><span data-stu-id="f2aab-130">Pushes *foo.nupkg* to the default push source:</span></span>

`dotnet nuget push foo.nupkg`

<span data-ttu-id="f2aab-131">İter *foo.symbols.nupkg* varsayılan simgeleri kaynağına:</span><span class="sxs-lookup"><span data-stu-id="f2aab-131">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

`dotnet nuget push foo.symbols.nupkg`

<span data-ttu-id="f2aab-132">İter *foo.nupkg* 360 ikinci zaman aşımı varsayılan itme kaynağına belirtme:</span><span class="sxs-lookup"><span data-stu-id="f2aab-132">Pushes *foo.nupkg* to the default push source, specifying a 360 second timeout:</span></span>

`dotnet nuget push foo.nupkg --timeout 360`

<span data-ttu-id="f2aab-133">Tüm iter *.nupkg* varsayılan itme kaynağına geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="f2aab-133">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

`dotnet nuget push *.nupkg`

<span data-ttu-id="f2aab-134">Tüm iter *.nupkg* özel yapılandırma dosyanızı belirten varsayılan itme kaynağına geçerli dizindeki dosyaları *./config/My.Config*:</span><span class="sxs-lookup"><span data-stu-id="f2aab-134">Pushes all *.nupkg* files in the current directory to the default push source, specifying a custom config file *./config/My.Config*:</span></span>

`dotnet nuget push *.nupkg --config-file ./config/My.Config`

<span data-ttu-id="f2aab-135">Tüm itme *.nupkg* en fazla ayrıntı varsayılan itme kaynağıyla geçerli dizindeki dosyaları:</span><span class="sxs-lookup"><span data-stu-id="f2aab-135">Push all *.nupkg* files in the current directory to the default push source with maximum verbosity:</span></span>

`dotnet nuget push *.nupkg --verbosity detailed`
