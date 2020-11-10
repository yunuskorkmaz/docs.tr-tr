---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440430"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="a7e07-101">Veri koruma: DataProtection. blob 'lar yeni Azure depolama API 'Lerini kullanır</span><span class="sxs-lookup"><span data-stu-id="a7e07-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="a7e07-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs`[Azure depolama kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a7e07-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="a7e07-103">Bu kitaplıklar derlemeleri, paketleri ve ad alanlarını yeniden adlandırdı.</span><span class="sxs-lookup"><span data-stu-id="a7e07-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="a7e07-104">ASP.NET Core 3,0 ' den başlayarak, `Azure.Extensions.AspNetCore.DataProtection.Blobs` Yeni `Azure.Storage.` önekli API 'leri ve paketleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a7e07-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="a7e07-105">Azure depolama API 'Leri hakkında sorularınız için kullanın <https://github.com/Azure/azure-storage-net> .</span><span class="sxs-lookup"><span data-stu-id="a7e07-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="a7e07-106">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="a7e07-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a7e07-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a7e07-107">Version introduced</span></span>

<span data-ttu-id="a7e07-108">3,0</span><span class="sxs-lookup"><span data-stu-id="a7e07-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a7e07-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a7e07-109">Old behavior</span></span>

<span data-ttu-id="a7e07-110">Paket, `WindowsAzure.Storage` NuGet paketine başvurdu.</span><span class="sxs-lookup"><span data-stu-id="a7e07-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="a7e07-111">Paket, `Microsoft.Azure.Storage.Blob` NuGet paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="a7e07-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a7e07-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a7e07-112">New behavior</span></span>

<span data-ttu-id="a7e07-113">Paket, `Azure.Storage.Blob` NuGet paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="a7e07-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a7e07-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a7e07-114">Reason for change</span></span>

<span data-ttu-id="a7e07-115">Bu değişiklik `Azure.Extensions.AspNetCore.DataProtection.Blobs` , önerilen Azure depolama paketlerine geçişe olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a7e07-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a7e07-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a7e07-116">Recommended action</span></span>

<span data-ttu-id="a7e07-117">Hala ASP.NET Core 3,0 ile eski Azure depolama API 'Lerini kullanmanız gerekiyorsa, [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) veya [Microsoft. Azure. Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/)paketine doğrudan bir bağımlılık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a7e07-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="a7e07-118">Bu paket yeni API 'ler ile birlikte yüklenebilir `Azure.Storage` .</span><span class="sxs-lookup"><span data-stu-id="a7e07-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="a7e07-119">Çoğu durumda, yükseltme yalnızca `using` Yeni ad alanlarını kullanmak için deyimlerinin değiştirilmesini içerir:</span><span class="sxs-lookup"><span data-stu-id="a7e07-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="a7e07-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="a7e07-120">Category</span></span>

<span data-ttu-id="a7e07-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a7e07-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a7e07-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a7e07-122">Affected APIs</span></span>

<span data-ttu-id="a7e07-123">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="a7e07-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
