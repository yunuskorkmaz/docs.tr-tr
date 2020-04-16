---
title: dotnet nuget kaynak komutu eklemek
description: Dotnet nuget add kaynak komutu NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463595"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="c6b58-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="c6b58-103">dotnet nuget add source</span></span>

<span data-ttu-id="c6b58-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="c6b58-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c6b58-105">Adı</span><span class="sxs-lookup"><span data-stu-id="c6b58-105">Name</span></span>

<span data-ttu-id="c6b58-106">`dotnet nuget add source`- NuGet kaynağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c6b58-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c6b58-107">Özet</span><span class="sxs-lookup"><span data-stu-id="c6b58-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="c6b58-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6b58-108">Description</span></span>

<span data-ttu-id="c6b58-109">Komut, `dotnet nuget add source` NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="c6b58-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="c6b58-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="c6b58-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="c6b58-111">Paket kaynağına giden yol.</span><span class="sxs-lookup"><span data-stu-id="c6b58-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="c6b58-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c6b58-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="c6b58-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="c6b58-113">The NuGet configuration file.</span></span> <span data-ttu-id="c6b58-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6b58-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="c6b58-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c6b58-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="c6b58-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="c6b58-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="c6b58-117">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="c6b58-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="c6b58-118">Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.</span><span class="sxs-lookup"><span data-stu-id="c6b58-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="c6b58-119">Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6b58-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="c6b58-120">Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="c6b58-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="c6b58-121">Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="c6b58-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="c6b58-122">Sunucu ntlm veya Negotiate'in reklamını yaparsa ve kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, örneğin şirket içi Azure DevOps Server'a sahip bir PAT kullanırken bunu `basic` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c6b58-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="c6b58-123">Diğer geçerli `negotiate`değerler `kerberos` `ntlm`, `digest`, , ve , içerir, ancak bu değerlerin yararlı olması olası değildir.</span><span class="sxs-lookup"><span data-stu-id="c6b58-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="c6b58-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="c6b58-124">Examples</span></span>

- <span data-ttu-id="c6b58-125">Kaynak `nuget.org` olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b58-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="c6b58-126">Yerel `c:\packages` kaynak olarak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b58-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="c6b58-127">Kimlik doğrulaması gereken bir kaynak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b58-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="c6b58-128">Kimlik doğrulaması gereken bir kaynak ekleyin (ardından kimlik bilgisi sağlayıcısını yükleyin:</span><span class="sxs-lookup"><span data-stu-id="c6b58-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="c6b58-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6b58-129">See also</span></span>

- [<span data-ttu-id="c6b58-130">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="c6b58-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="c6b58-131">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="c6b58-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
