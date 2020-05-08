---
title: DotNet NuGet Push komutu
description: DotNet NuGet Push komutu, bir paketi sunucuya gönderir ve yayınlar.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 1e7831de4c041591b3602e405418f89f1d1d27d1
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895465"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="9f1e3-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="9f1e3-103">dotnet nuget push</span></span>

<span data-ttu-id="9f1e3-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="9f1e3-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9f1e3-105">Name</span><span class="sxs-lookup"><span data-stu-id="9f1e3-105">Name</span></span>

<span data-ttu-id="9f1e3-106">`dotnet nuget push`-Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9f1e3-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="9f1e3-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a><span data-ttu-id="9f1e3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f1e3-108">Description</span></span>

<span data-ttu-id="9f1e3-109">Komut `dotnet nuget push` , bir paketi sunucuya gönderir ve yayınlar.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="9f1e3-110">Push komutu, sistemin NuGet yapılandırma dosyasında veya yapılandırma dosyaları zincirinde bulunan sunucu ve kimlik bilgisi ayrıntılarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="9f1e3-111">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [NuGet davranışını yapılandırma](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="9f1e3-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="9f1e3-112">NuGet 'in varsayılan yapılandırması, *%AppData%\NuGet\NuGet.config* (Windows) veya *$Home/PST local/share* (Linux/MacOS) yükleyerek elde edilir ve sürücü kökünden başlayıp geçerli dizinde sona ermek üzere herhangi bir *NuGet. config* veya *. nuget\nuget.exe* .</span><span class="sxs-lookup"><span data-stu-id="9f1e3-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

<span data-ttu-id="9f1e3-113">Komut, var olan bir paketi iter.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-113">The command pushes an existing package.</span></span> <span data-ttu-id="9f1e3-114">Paket oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-114">It doesn't create a package.</span></span> <span data-ttu-id="9f1e3-115">Bir paket oluşturmak için kullanın [`dotnet pack`](dotnet-pack.md).</span><span class="sxs-lookup"><span data-stu-id="9f1e3-115">To create a package, use [`dotnet pack`](dotnet-pack.md).</span></span>

## <a name="arguments"></a><span data-ttu-id="9f1e3-116">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="9f1e3-116">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="9f1e3-117">Gönderilecek paketin dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-117">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="9f1e3-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9f1e3-118">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="9f1e3-119">Bellek kullanımını azaltmak için bir HTTP (S) sunucusuna gönderilirken arabelleğe almayı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-119">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="9f1e3-120">Uygulamayı, sabit, Ingilizce tabanlı bir kültür kullanılarak çalışmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-120">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9f1e3-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="9f1e3-122">Komutun, kimlik doğrulaması gibi işlemler için el ile eylem yapmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-122">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="9f1e3-123">.NET Core 2,2 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-123">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="9f1e3-124">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-124">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="9f1e3-125">Sembol (varsa bile) almaz.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-125">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="9f1e3-126">Kaynak URL 'ye "API/v2/Package" eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-126">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="9f1e3-127">.NET Core 2,1 SDK 'dan beri kullanılabilir seçeneği.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-127">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="9f1e3-128">Sunucu URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-128">Specifies the server URL.</span></span> <span data-ttu-id="9f1e3-129">Bu seçenek, NuGet yapılandırma `DefaultPushSource` dosyasında yapılandırma değeri ayarlanmadığı takdirde gereklidir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-129">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="9f1e3-130">Bir HTTP (S) sunucusuna birden çok paket gönderdiğinizde, gönderim devam edebilmesi için 409 çakışma yanıtını uyarı olarak değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-130">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="9f1e3-131">.NET Core 3,1 SDK 'dan beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-131">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="9f1e3-132">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-132">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="9f1e3-133">Sembol sunucusu URL 'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-133">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="9f1e3-134">Bir sunucuya saniye cinsinden gönderme zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-134">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="9f1e3-135">Varsayılan değer 300 saniyedir (5 dakika).</span><span class="sxs-lookup"><span data-stu-id="9f1e3-135">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="9f1e3-136">0 (sıfır saniye) belirtilmesi varsayılan değeri uygular.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-136">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="9f1e3-137">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9f1e3-137">Examples</span></span>

- <span data-ttu-id="9f1e3-138">Bir API anahtarı belirterek, varsayılan gönderim kaynağına *foo. nupkg* gönderin:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-138">Push *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="9f1e3-139">Bir API anahtarı belirterek, resmi NuGet sunucusuna *foo. nupkg* gönderin:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-139">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="9f1e3-140">Bir API anahtarı belirterek, özel itme kaynağına `https://customsource` *foo. nupkg* gönderin:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-140">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="9f1e3-141">*Foo. nupkg* 'yi varsayılan gönderim kaynağına gönder:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-141">Push *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="9f1e3-142">Varsayılan semboller kaynağına *foo. Symbols. nupkg* gönder:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-142">Push *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="9f1e3-143">Varsayılan itme kaynağına *foo. nupkg* göndererek 360 saniyelik bir zaman aşımı belirtin:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-143">Push *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="9f1e3-144">Geçerli dizindeki tüm *. nupkg* dosyalarını varsayılan gönderim kaynağına gönder:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-144">Push all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="9f1e3-145">Bu komut işe yaramazsa, bunun nedeni SDK 'nın eski sürümlerinde var olan bir hata olabilir (.NET Core 2,1 SDK ve önceki sürümleri).</span><span class="sxs-lookup"><span data-stu-id="9f1e3-145">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="9f1e3-146">Bunu onarmak için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="9f1e3-146">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="9f1e3-147">Bir HTTP (S) sunucusu tarafından 409 çakışma yanıtı döndürülse bile tüm *. nupkg* dosyalarını gönderin:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-147">Push all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```

- <span data-ttu-id="9f1e3-148">Geçerli dizindeki tüm *. nupkg* dosyalarını yerel akış dizinine gönder:</span><span class="sxs-lookup"><span data-stu-id="9f1e3-148">Push all *.nupkg* files in the current directory to a local feed directory:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg -s c:\mydir
  ```

  <span data-ttu-id="9f1e3-149">Bu komut, paketleri hiyerarşik bir klasör yapısında depolamaz, bu da performansı iyileştirmek için önerilir.</span><span class="sxs-lookup"><span data-stu-id="9f1e3-149">This command doesn't store packages in a hierarchical folder structure, which is recommended to optimize performance.</span></span> <span data-ttu-id="9f1e3-150">Daha fazla bilgi için bkz. [Yerel akışlar](/nuget/hosting-packages/local-feeds).</span><span class="sxs-lookup"><span data-stu-id="9f1e3-150">For more information, see [Local feeds](/nuget/hosting-packages/local-feeds).</span></span>  
