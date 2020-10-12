---
title: DotNet NuGet Verify komutu
description: DotNet NuGet Verify komutu imzalı bir paketi doğrular.
author: kartheekp-ms
ms.date: 10/08/2020
ms.openlocfilehash: 6cb368e2b6c203f3774b4450c0831c5d6b2dc0e8
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957169"
---
# <a name="dotnet-nuget-verify"></a><span data-ttu-id="8286d-103">DotNet NuGet doğrulaması</span><span class="sxs-lookup"><span data-stu-id="8286d-103">dotnet nuget verify</span></span>

<span data-ttu-id="8286d-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET 5.0.100-RC. 2. x SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="8286d-104">**This article applies to:** ✔️ .NET 5.0.100-rc.2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8286d-105">Name</span><span class="sxs-lookup"><span data-stu-id="8286d-105">Name</span></span>

<span data-ttu-id="8286d-106">`dotnet nuget verify` -İmzalı bir NuGet paketini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8286d-106">`dotnet nuget verify` - Verifies a signed NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8286d-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="8286d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget verify [<package-path(s)>]
    [--all]
    [--certificate-fingerprint <FINGERPRINT>]
    [-v|--verbosity <LEVEL>]

dotnet nuget verify -h|--help
```

## <a name="description"></a><span data-ttu-id="8286d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8286d-108">Description</span></span>

<span data-ttu-id="8286d-109">`dotnet nuget verify`Komut imzalı bir NuGet paketini doğrular.</span><span class="sxs-lookup"><span data-stu-id="8286d-109">The `dotnet nuget verify` command verifies a signed NuGet package.</span></span>

## <a name="arguments"></a><span data-ttu-id="8286d-110">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="8286d-110">Arguments</span></span>

- **`package-path(s)`**

  <span data-ttu-id="8286d-111">Doğrulanacak paket (ler) in dosya yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8286d-111">Specifies the file path to the package(s) to be verified.</span></span> <span data-ttu-id="8286d-112">Birden çok paketi doğrulamak için birden çok konum bağımsız değişkeni geçirilebilir.</span><span class="sxs-lookup"><span data-stu-id="8286d-112">Multiple position arguments can be passed in to verify multiple packages.</span></span>

## <a name="options"></a><span data-ttu-id="8286d-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8286d-113">Options</span></span>

- **`--all`**

  <span data-ttu-id="8286d-114">Tüm doğrulamaları, paketler üzerinde gerçekleştirilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="8286d-114">Specifies that all verifications possible should be performed on the package(s).</span></span> <span data-ttu-id="8286d-115">Varsayılan olarak, yalnızca `signatures` doğrulanır.</span><span class="sxs-lookup"><span data-stu-id="8286d-115">By default, only `signatures` are verified.</span></span>

> [!NOTE]
> <span data-ttu-id="8286d-116">Bu komut şu anda yalnızca `signature` doğrulamayı desteklemektedir.</span><span class="sxs-lookup"><span data-stu-id="8286d-116">This command currently supports only `signature` verification.</span></span>

- **`--certificate-fingerprint <FINGERPRINT>`**

  <span data-ttu-id="8286d-117">İmzalayan sertifikasının belirtilen `SHA256` parmak izlerinden biriyle eşleştiğini doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="8286d-117">Verify that the signer certificate matches with one of the specified `SHA256` fingerprints.</span></span> <span data-ttu-id="8286d-118">Birden çok parmak izi sağlamak için bu seçeneğin birden çok kez sağlanması sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8286d-118">This option can be supplied multiple times to provide multiple fingerprints.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="8286d-119">MSBuild ayrıntı düzeyi düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8286d-119">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="8286d-120">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="8286d-120">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8286d-121">Varsayılan değer: `normal`.</span><span class="sxs-lookup"><span data-stu-id="8286d-121">The default is `normal`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="8286d-122">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="8286d-122">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="8286d-123">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8286d-123">Examples</span></span>

- <span data-ttu-id="8286d-124">*Foo. nupkg*'yi doğrula:</span><span class="sxs-lookup"><span data-stu-id="8286d-124">Verify *foo.nupkg*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg
  ```

- <span data-ttu-id="8286d-125">Belirtilen dizindeki birden çok NuGet paketini ( *foo. nupkg* ) ve *tüm. nupkg dosyalarını*doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="8286d-125">Verify multiple NuGet packages - *foo.nupkg* and *all .nupkg files in the directory specified*:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg c:\mydir\*.nupkg
  ```

- <span data-ttu-id="8286d-126">Belirtilen sertifika parmak iziyle *foo. nupkg* imzasını eşleştirenleri doğrula:</span><span class="sxs-lookup"><span data-stu-id="8286d-126">Verify *foo.nupkg* signature matches with the specified certificate fingerprint:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039
  ```

- <span data-ttu-id="8286d-127">*Foo. nupkg* imzasını belirtilen sertifika parmak izlerinden biriyle eşleştirirken doğrulayın:</span><span class="sxs-lookup"><span data-stu-id="8286d-127">Verify *foo.nupkg* signature matches with one of the specified certificate fingerprints:</span></span>

  ```dotnetcli
  dotnet nuget verify foo.nupkg --certificate-fingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 --certificate-fingerprint EC10992GG5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E027
  ```
