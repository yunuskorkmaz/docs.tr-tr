---
title: DotNet NuGet Kaynak Ekle komutu
description: DotNet NuGet Kaynak Ekle komutu, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.
ms.date: 03/20/2020
ms.openlocfilehash: df31a2eaba997d0e9fe4f4c2666052fd7c7c2f03
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105057"
---
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="7f06c-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="7f06c-103">dotnet nuget add source</span></span>

<span data-ttu-id="7f06c-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="7f06c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7f06c-105">Name</span><span class="sxs-lookup"><span data-stu-id="7f06c-105">Name</span></span>

<span data-ttu-id="7f06c-106">`dotnet nuget add source` -Bir NuGet kaynağı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7f06c-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f06c-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="7f06c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="7f06c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7f06c-108">Description</span></span>

<span data-ttu-id="7f06c-109">`dotnet nuget add source`Komut, NuGet yapılandırma dosyalarınıza yeni bir paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="7f06c-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

> [!WARNING]
> <span data-ttu-id="7f06c-110">Birden çok paket kaynağı eklerken, bir [bağımlılık karışıklık güvenlik açığı](https://aka.ms/pkg-sec-wp)tanıtmamaya dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="7f06c-110">When adding multiple package sources, be careful not to introduce a [dependency confusion vulnerability](https://aka.ms/pkg-sec-wp).</span></span>

## <a name="arguments"></a><span data-ttu-id="7f06c-111">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="7f06c-111">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="7f06c-112">Paket kaynağının yolu.</span><span class="sxs-lookup"><span data-stu-id="7f06c-112">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="7f06c-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7f06c-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="7f06c-114">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="7f06c-114">The NuGet configuration file.</span></span> <span data-ttu-id="7f06c-115">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="7f06c-115">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="7f06c-116">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="7f06c-116">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="7f06c-117">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="7f06c-117">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="7f06c-118">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="7f06c-118">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="7f06c-119">Kimliği doğrulanmış bir kaynağa bağlanırken kullanılacak parola.</span><span class="sxs-lookup"><span data-stu-id="7f06c-119">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="7f06c-120">Parola şifrelemesini devre dışı bırakarak taşınabilir paket kaynak kimlik bilgilerinin depolanmasını mümkün.</span><span class="sxs-lookup"><span data-stu-id="7f06c-120">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="7f06c-121">Kimliği doğrulanmış bir kaynağa bağlanılırken kullanılacak Kullanıcı adı.</span><span class="sxs-lookup"><span data-stu-id="7f06c-121">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="7f06c-122">Bu kaynak için geçerli kimlik doğrulama türlerinin virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="7f06c-122">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="7f06c-123">`basic`Sunucu ntlm veya anlaşma duyurur ise ve şirket içi Azure DevOps Server BIR Pat kullanırken, kimlik bilgilerinizin temel mekanizma kullanılarak gönderilmesi gerekiyorsa, bunu olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7f06c-123">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="7f06c-124">Diğer geçerli değerler,,, ve içerir, `negotiate` `kerberos` `ntlm` `digest` ancak bu değerlerin yararlı olması çok düşüktür.</span><span class="sxs-lookup"><span data-stu-id="7f06c-124">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="7f06c-125">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7f06c-125">Examples</span></span>

- <span data-ttu-id="7f06c-126">`nuget.org`Kaynak olarak ekle:</span><span class="sxs-lookup"><span data-stu-id="7f06c-126">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="7f06c-127">`c:\packages`Yerel kaynak olarak ekle:</span><span class="sxs-lookup"><span data-stu-id="7f06c-127">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="7f06c-128">Kimlik doğrulaması gerektiren bir kaynak ekleyin:</span><span class="sxs-lookup"><span data-stu-id="7f06c-128">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="7f06c-129">Kimlik doğrulaması gerektiren bir kaynak ekleyin (ardından kimlik bilgisi sağlayıcısı 'nı yüklemeye git):</span><span class="sxs-lookup"><span data-stu-id="7f06c-129">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="7f06c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f06c-130">See also</span></span>

- [<span data-ttu-id="7f06c-131">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="7f06c-131">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="7f06c-132">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="7f06c-132">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
