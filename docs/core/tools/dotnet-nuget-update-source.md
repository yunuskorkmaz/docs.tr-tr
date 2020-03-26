---
title: dotnet nuget güncelleme kaynak komutu
description: Dotnet nuget güncelleştirme kaynak komutu, NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148549"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="629b5-103">dotnet nuget güncelleme kaynağı</span><span class="sxs-lookup"><span data-stu-id="629b5-103">dotnet nuget update source</span></span>

<span data-ttu-id="629b5-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="629b5-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="629b5-105">Adı</span><span class="sxs-lookup"><span data-stu-id="629b5-105">Name</span></span>

<span data-ttu-id="629b5-106">`dotnet nuget update source`- Bir NuGet kaynağını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="629b5-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="629b5-107">Özet</span><span class="sxs-lookup"><span data-stu-id="629b5-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="629b5-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="629b5-108">Description</span></span>

<span data-ttu-id="629b5-109">Komut, `dotnet nuget update source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="629b5-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="629b5-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="629b5-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="629b5-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="629b5-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="629b5-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="629b5-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="629b5-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="629b5-113">The NuGet configuration file.</span></span> <span data-ttu-id="629b5-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="629b5-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="629b5-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="629b5-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="629b5-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="629b5-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password`**

  <span data-ttu-id="629b5-117">Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak parola.</span><span class="sxs-lookup"><span data-stu-id="629b5-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source`**

  <span data-ttu-id="629b5-118">Paket kaynağına giden yol.</span><span class="sxs-lookup"><span data-stu-id="629b5-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="629b5-119">Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynağı kimlik bilgilerini depolamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="629b5-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="629b5-120">Kimlik doğrulaması yapılan bir kaynağa bağlanırken kullanılacak kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="629b5-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="629b5-121">Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="629b5-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="629b5-122">Sunucu ntlm veya Negotiate'in reklamını yaparsa ve kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, örneğin şirket içi Azure DevOps Server'a sahip bir PAT kullanırken bunu `basic` ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="629b5-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="629b5-123">Diğer geçerli `negotiate`değerler `kerberos` `ntlm`, `digest`, , ve , içerir, ancak bu değerlerin yararlı olması olası değildir.</span><span class="sxs-lookup"><span data-stu-id="629b5-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="629b5-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="629b5-124">Examples</span></span>

- <span data-ttu-id="629b5-125">Adı olan bir `mySource`kaynağı güncelleştirin:</span><span class="sxs-lookup"><span data-stu-id="629b5-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="629b5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="629b5-126">See also</span></span>

- [<span data-ttu-id="629b5-127">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="629b5-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="629b5-128">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="629b5-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
