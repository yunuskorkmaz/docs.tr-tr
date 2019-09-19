---
title: DotNet NuGet Push komutu
description: DotNet NuGet Push komutu, bir paketi sunucuya gönderir ve yayınlar.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 3299f79ec62aebdcdbef38f1e8b09a2dc5529ec4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117498"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="f0e56-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="f0e56-103">dotnet nuget push</span></span>

<span data-ttu-id="f0e56-104">**Bu konu şu şekilde geçerlidir: ✓** .NET Core 1. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f0e56-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f0e56-105">Ad</span><span class="sxs-lookup"><span data-stu-id="f0e56-105">Name</span></span>

<span data-ttu-id="f0e56-106">`dotnet nuget push`-Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="f0e56-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f0e56-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="f0e56-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f0e56-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0e56-108">Description</span></span>

<span data-ttu-id="f0e56-109">Komut `dotnet nuget push` , bir paketi sunucuya gönderir ve yayınlar.</span><span class="sxs-lookup"><span data-stu-id="f0e56-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="f0e56-110">Push komutu, sistemin NuGet yapılandırma dosyasında veya yapılandırma dosyaları zincirinde bulunan sunucu ve kimlik bilgisi ayrıntılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0e56-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="f0e56-111">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f0e56-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="f0e56-112">NuGet 'in varsayılan yapılandırması, *%AppData%\NuGet\NuGet.config* (Windows) veya *$Home/PST local/share* (Linux/MacOS) yükleyerek elde edilir ve bundan sonra herhangi bir *NuGet. config* veya *. nuget\nuget.exe* yüklenir geçerli dizinde sürücü ve bitiş.</span><span class="sxs-lookup"><span data-stu-id="f0e56-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="f0e56-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="f0e56-113">Arguments</span></span>

* **`ROOT`**

  <span data-ttu-id="f0e56-114">Gönderilecek paketin dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="f0e56-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f0e56-115">Options</span></span>

* **`-d|--disable-buffering`**

  <span data-ttu-id="f0e56-116">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderilirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="f0e56-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

* **`--force-english-output`**

  <span data-ttu-id="f0e56-117">Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="f0e56-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

<span data-ttu-id="f0e56-118">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="f0e56-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="f0e56-119">Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="f0e56-120">.NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f0e56-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="f0e56-121">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f0e56-121">The API key for the server.</span></span>

* **`-n|--no-symbols`**

  <span data-ttu-id="f0e56-122">Sembol (varsa bile) almaz.</span><span class="sxs-lookup"><span data-stu-id="f0e56-122">Doesn't push symbols (even if present).</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="f0e56-123">Kaynak URL 'ye "API/v2/Package" eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="f0e56-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="f0e56-124">.NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="f0e56-124">Option available since .NET Core 2.1 SDK.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="f0e56-125">Sunucu URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-125">Specifies the server URL.</span></span> <span data-ttu-id="f0e56-126">Bu seçenek, NuGet yapılandırma `DefaultPushSource` dosyasında yapılandırma değeri ayarlanmadığı takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

* **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="f0e56-127">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="f0e56-127">The API key for the symbol server.</span></span>

* **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="f0e56-128">Sembol sunucusu URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-128">Specifies the symbol server URL.</span></span>

* **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="f0e56-129">Bir sunucuya saniye cinsinden gönderme zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f0e56-129">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="f0e56-130">Varsayılan değer 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="f0e56-130">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="f0e56-131">0 (sıfır saniye) belirtilmesi varsayılan değeri uygular.</span><span class="sxs-lookup"><span data-stu-id="f0e56-131">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="f0e56-132">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f0e56-132">Examples</span></span>

* <span data-ttu-id="f0e56-133">*Foo. nupkg* 'yi varsayılan itme kaynağına iter, bir API anahtarı belirtin:</span><span class="sxs-lookup"><span data-stu-id="f0e56-133">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* <span data-ttu-id="f0e56-134">Bir API anahtarı belirterek, özel itme kaynağına `https://customsource` *foo. nupkg* gönderin:</span><span class="sxs-lookup"><span data-stu-id="f0e56-134">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* <span data-ttu-id="f0e56-135">*Foo. nupkg* 'yi varsayılan gönderim kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="f0e56-135">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* <span data-ttu-id="f0e56-136">*Foo. Symbols. nupkg* 'yi varsayılan semboller kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="f0e56-136">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* <span data-ttu-id="f0e56-137">*Foo. nupkg* 'yi varsayılan gönderim kaynağına iter, 360 saniyelik bir zaman aşımı belirterek:</span><span class="sxs-lookup"><span data-stu-id="f0e56-137">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* <span data-ttu-id="f0e56-138">Geçerli dizindeki tüm *. nupkg* dosyalarını varsayılan gönderim kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="f0e56-138">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > <span data-ttu-id="f0e56-139">Bu komut işe yaramazsa, bunun nedeni SDK 'nın eski sürümlerinde var olan bir hata olabilir (.NET Core 2,1 SDK ve önceki sürümleri).</span><span class="sxs-lookup"><span data-stu-id="f0e56-139">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="f0e56-140">Bunu onarmak için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="f0e56-140">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>
