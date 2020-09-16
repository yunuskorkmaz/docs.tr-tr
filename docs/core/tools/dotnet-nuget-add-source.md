---
title: DotNet NuGet Kaynak Ekle komutu
description: DotNet NuGet Kaynak Ekle komutu, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: b847d987de2d88cb3452d32d1bc84232a1e20b6e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537979"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="f1547-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="f1547-103">dotnet nuget add source</span></span>

<span data-ttu-id="f1547-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f1547-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f1547-105">Name</span><span class="sxs-lookup"><span data-stu-id="f1547-105">Name</span></span>

<span data-ttu-id="f1547-106">`dotnet nuget add source` -Bir NuGet kaynağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f1547-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f1547-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="f1547-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="f1547-108">Description</span><span class="sxs-lookup"><span data-stu-id="f1547-108">Description</span></span>

<span data-ttu-id="f1547-109">`dotnet nuget add source`Komut, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="f1547-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="f1547-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="f1547-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="f1547-111">Paket kaynağının yolu.</span><span class="sxs-lookup"><span data-stu-id="f1547-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="f1547-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f1547-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f1547-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="f1547-113">The NuGet configuration file.</span></span> <span data-ttu-id="f1547-114">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1547-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="f1547-115">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="f1547-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="f1547-116">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="f1547-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="f1547-117">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="f1547-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="f1547-118">Kimliği doğrulanmış bir kaynağa bağlanırken kullanılacak parola.</span><span class="sxs-lookup"><span data-stu-id="f1547-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="f1547-119">Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynak kimlik bilgilerinin depolanmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="f1547-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="f1547-120">Kimliği doğrulanmış bir kaynağa bağlanılırken kullanılacak Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="f1547-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="f1547-121">Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="f1547-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="f1547-122">`basic`Sunucu ntlm veya anlaşma duyurur ise ve şirket içi Azure DevOps Server BIR Pat kullanırken, kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, bunu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f1547-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="f1547-123">Diğer geçerli değerler,,, ve içerir, `negotiate` `kerberos` `ntlm` `digest` ancak bu değerlerin yararlı olması çok düşüktür.</span><span class="sxs-lookup"><span data-stu-id="f1547-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="f1547-124">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f1547-124">Examples</span></span>

- <span data-ttu-id="f1547-125">`nuget.org`Kaynak olarak ekle:</span><span class="sxs-lookup"><span data-stu-id="f1547-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="f1547-126">`c:\packages`Yerel kaynak olarak ekle:</span><span class="sxs-lookup"><span data-stu-id="f1547-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="f1547-127">Kimlik doğrulaması gerektiren bir kaynak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f1547-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="f1547-128">Kimlik doğrulaması gerektiren bir kaynak ekleyin (ardından kimlik bilgisi sağlayıcısı 'nı yüklemeye git):</span><span class="sxs-lookup"><span data-stu-id="f1547-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="f1547-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1547-129">See also</span></span>

- [<span data-ttu-id="f1547-130">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="f1547-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="f1547-131">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="f1547-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
