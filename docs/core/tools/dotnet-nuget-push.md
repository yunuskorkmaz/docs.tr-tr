---
title: dotnet nuget push komutu
description: Dotnet nuget push komutu bir paketi sunucuya iter ve yayımlar.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503666"
---
# <a name="dotnet-nuget-push"></a><span data-ttu-id="e47f4-103">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="e47f4-103">dotnet nuget push</span></span>

<span data-ttu-id="e47f4-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.x SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="e47f4-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e47f4-105">Adı</span><span class="sxs-lookup"><span data-stu-id="e47f4-105">Name</span></span>

<span data-ttu-id="e47f4-106">`dotnet nuget push`- Bir paketi sunucuya iter ve yayınlar.</span><span class="sxs-lookup"><span data-stu-id="e47f4-106">`dotnet nuget push` - Pushes a package to the server and publishes it.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e47f4-107">Özet</span><span class="sxs-lookup"><span data-stu-id="e47f4-107">Synopsis</span></span>

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a><span data-ttu-id="e47f4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e47f4-108">Description</span></span>

<span data-ttu-id="e47f4-109">Komut `dotnet nuget push` bir paketi sunucuya iter ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="e47f4-109">The `dotnet nuget push` command pushes a package to the server and publishes it.</span></span> <span data-ttu-id="e47f4-110">Push komutu, sistemin NuGet config dosyasında veya config dosyaları zincirinde bulunan sunucu ve kimlik bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e47f4-110">The push command uses server and credential details found in the system's NuGet config file or chain of config files.</span></span> <span data-ttu-id="e47f4-111">Config dosyaları hakkında daha fazla bilgi için [NuGet Davranışını Yapılandırma'ya](/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="e47f4-111">For more information on config files, see [Configuring NuGet Behavior](/nuget/consume-packages/configuring-nuget-behavior).</span></span> <span data-ttu-id="e47f4-112">NuGet'in varsayılan yapılandırması *%AppData%\NuGet\NuGet.config* (Windows) veya *$HOME/.local/share* (Linux/macOS) yüklenerek elde edilir, ardından sürücü kökünden başlayıp geçerli dizinde biten herhangi bir *nuget.config* veya *.nuget\nuget.config* yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-112">NuGet's default configuration is obtained by loading *%AppData%\NuGet\NuGet.config* (Windows) or *$HOME/.local/share* (Linux/macOS), then loading any *nuget.config* or *.nuget\nuget.config* starting from the root of drive and ending in the current directory.</span></span>

## <a name="arguments"></a><span data-ttu-id="e47f4-113">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="e47f4-113">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="e47f4-114">Itilecek pakete dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-114">Specifies the file path to the package to be pushed.</span></span>

## <a name="options"></a><span data-ttu-id="e47f4-115">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e47f4-115">Options</span></span>

- **`-d|--disable-buffering`**

  <span data-ttu-id="e47f4-116">Bellek kullanımını azaltmak için bir HTTP(S) sunucusuna bastırırken arabelleği devre dışı düşürür.</span><span class="sxs-lookup"><span data-stu-id="e47f4-116">Disables buffering when pushing to an HTTP(S) server to reduce memory usage.</span></span>

- **`--force-english-output`**

  <span data-ttu-id="e47f4-117">Uygulamayı değişmez, İngilizce tabanlı bir kültür kullanarak çalıştırmaya zorlar.</span><span class="sxs-lookup"><span data-stu-id="e47f4-117">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e47f4-118">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="e47f4-118">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="e47f4-119">Komutun engellenmesine izin verir ve kimlik doğrulama gibi işlemler için el ile eylem gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="e47f4-120">Seçenek .NET Core 2.2 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e47f4-120">Option available since .NET Core 2.2 SDK.</span></span>

- **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="e47f4-121">Sunucu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e47f4-121">The API key for the server.</span></span>

- **`-n|--no-symbols`**

  <span data-ttu-id="e47f4-122">Sembolleri itmiyor (mevcut olsa bile).</span><span class="sxs-lookup"><span data-stu-id="e47f4-122">Doesn't push symbols (even if present).</span></span>

- **`--no-service-endpoint`**

  <span data-ttu-id="e47f4-123">Kaynak URL'ye "api/v2/package" eklenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-123">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="e47f4-124">Seçenek .NET Core 2.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e47f4-124">Option available since .NET Core 2.1 SDK.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="e47f4-125">Sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-125">Specifies the server URL.</span></span> <span data-ttu-id="e47f4-126">Config değeri `DefaultPushSource` NuGet config dosyasında ayarlılmadığı sürece bu seçenek gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-126">This option is required unless `DefaultPushSource` config value is set in the NuGet config file.</span></span>

- **`--skip-duplicate`**

  <span data-ttu-id="e47f4-127">Bir HTTP(S) sunucusuna birden çok paket iterken, herhangi bir 409 Çakışma yanıtını bir uyarı olarak ele alır, böylece itme devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-127">When pushing multiple packages to an HTTP(S) server, treats any 409 Conflict response as a warning so that the push can continue.</span></span> <span data-ttu-id="e47f4-128">.NET Core 3.1 SDK'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e47f4-128">Available since .NET Core 3.1 SDK.</span></span>

- **`-sk|--symbol-api-key <API_KEY>`**

  <span data-ttu-id="e47f4-129">Sembol sunucusu için API anahtarı.</span><span class="sxs-lookup"><span data-stu-id="e47f4-129">The API key for the symbol server.</span></span>

- **`-ss|--symbol-source <SOURCE>`**

  <span data-ttu-id="e47f4-130">Sembol sunucu URL'sini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-130">Specifies the symbol server URL.</span></span>

- **`-t|--timeout <TIMEOUT>`**

  <span data-ttu-id="e47f4-131">Bir sunucuya saniyeler içinde itmek için zaman anına göre belirtir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-131">Specifies the timeout for pushing to a server in seconds.</span></span> <span data-ttu-id="e47f4-132">Varsayılan olarak 300 saniye (5 dakika) olarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="e47f4-132">Defaults to 300 seconds (5 minutes).</span></span> <span data-ttu-id="e47f4-133">0 (sıfır saniye) belirtmek varsayılan değeri uygular.</span><span class="sxs-lookup"><span data-stu-id="e47f4-133">Specifying 0 (zero seconds) applies the default value.</span></span>

## <a name="examples"></a><span data-ttu-id="e47f4-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e47f4-134">Examples</span></span>

- <span data-ttu-id="e47f4-135">*Foo.nupkg'ı* varsayılan itme kaynağına iter ve bir API anahtarı belirtir:</span><span class="sxs-lookup"><span data-stu-id="e47f4-135">Pushes *foo.nupkg* to the default push source, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- <span data-ttu-id="e47f4-136">*Foo.nupkg'ı* resmi NuGet sunucusuna itin ve bir API anahtarı belirtin:</span><span class="sxs-lookup"><span data-stu-id="e47f4-136">Push *foo.nupkg* to the official NuGet server, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * <span data-ttu-id="e47f4-137">*Foo.nupkg'ı* özel push `https://customsource`kaynağına itin, API tuşu belirterek:</span><span class="sxs-lookup"><span data-stu-id="e47f4-137">Push *foo.nupkg* to the custom push source `https://customsource`, specifying an API key:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- <span data-ttu-id="e47f4-138">*Foo.nupkg'ı* varsayılan itme kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="e47f4-138">Pushes *foo.nupkg* to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- <span data-ttu-id="e47f4-139">*Foo.symbols.nupkg'ı* varsayılan semboller kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="e47f4-139">Pushes *foo.symbols.nupkg* to the default symbols source:</span></span>

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- <span data-ttu-id="e47f4-140">*Foo.nupkg'ı* varsayılan itme kaynağına iter ve 360 saniyelik bir zaman ayarı belirtir:</span><span class="sxs-lookup"><span data-stu-id="e47f4-140">Pushes *foo.nupkg* to the default push source, specifying a 360-second timeout:</span></span>

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- <span data-ttu-id="e47f4-141">Geçerli dizindeki tüm *.nupkg* dosyalarını varsayılan itme kaynağına iter:</span><span class="sxs-lookup"><span data-stu-id="e47f4-141">Pushes all *.nupkg* files in the current directory to the default push source:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > <span data-ttu-id="e47f4-142">Bu komut işe yaramazsa, SDK'nın (.NET Core 2.1 SDK ve önceki sürümlerinde) eski sürümlerinde bulunan bir hatadan kaynaklanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e47f4-142">If this command doesn't work, it might be due to a bug that existed in older versions of the SDK (.NET Core 2.1 SDK and earlier versions).</span></span>
  > <span data-ttu-id="e47f4-143">Bunu düzeltmek için SDK sürümünüzü yükseltin veya bunun yerine aşağıdaki komutu çalıştırın:`dotnet nuget push **/*.nupkg`</span><span class="sxs-lookup"><span data-stu-id="e47f4-143">To fix this, upgrade your SDK version or run the following command instead: `dotnet nuget push **/*.nupkg`</span></span>

- <span data-ttu-id="e47f4-144">409 Çakışma yanıtı bir HTTP(S) sunucusu tarafından döndürülse bile tüm *.nupkg* dosyalarını iter:</span><span class="sxs-lookup"><span data-stu-id="e47f4-144">Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:</span></span>

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
