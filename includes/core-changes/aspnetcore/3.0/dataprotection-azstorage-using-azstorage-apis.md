---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902064"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="22395-101">Veri Koruması: DataProtection.AzureStorage yeni Azure Depolama API'leri kullanır</span><span class="sxs-lookup"><span data-stu-id="22395-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="22395-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>Azure Depolama [kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="22395-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="22395-103">Bu kitaplıklar derlemelerinin, paketlerinin ve ad alanlarının adını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="22395-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="22395-104">Core 3.0ASP.NETdan `Microsoft.AspNetCore.DataProtection.AzureStorage` başlayarak `Microsoft.Azure.Storage.`yeni önceden belirlenmiş API'leri ve paketleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="22395-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="22395-105">Azure Depolama API'leri ile <https://github.com/Azure/azure-storage-net>ilgili sorularınız için .</span><span class="sxs-lookup"><span data-stu-id="22395-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="22395-106">Bu konuda tartışma için [dotnet/aspnetcore#8472'ye](https://github.com/dotnet/aspnetcore/issues/8472)bakın.</span><span class="sxs-lookup"><span data-stu-id="22395-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="22395-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="22395-107">Version introduced</span></span>

<span data-ttu-id="22395-108">3,0</span><span class="sxs-lookup"><span data-stu-id="22395-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="22395-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="22395-109">Old behavior</span></span>

<span data-ttu-id="22395-110">Paket, NuGet `WindowsAzure.Storage` paketine atıfta bulunarak başvuruda bulunarak, bu pakete atıfta bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="22395-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="22395-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="22395-111">New behavior</span></span>

<span data-ttu-id="22395-112">Paket NuGet `Microsoft.Azure.Storage.Blob` paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="22395-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="22395-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="22395-113">Reason for change</span></span>

<span data-ttu-id="22395-114">Bu değişiklik, önerilen Azure Depolama paketlerine geçiş yapılmasına olanak tanır. `Microsoft.AspNetCore.DataProtection.AzureStorage`</span><span class="sxs-lookup"><span data-stu-id="22395-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="22395-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="22395-115">Recommended action</span></span>

<span data-ttu-id="22395-116">Core 3.0'ASP.NET eski Azure Depolama API'lerini kullanmaya devam ederseniz, [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) paketine doğrudan bağımlılık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="22395-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="22395-117">Bu paket, yeni `Microsoft.Azure.Storage` API'lerin yanına yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="22395-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="22395-118">Çoğu durumda, yükseltme yalnızca yeni `using` ad alanlarını kullanmak için deyimleri değiştirmeyi içerir:</span><span class="sxs-lookup"><span data-stu-id="22395-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="22395-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="22395-119">Category</span></span>

<span data-ttu-id="22395-120">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="22395-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="22395-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="22395-121">Affected APIs</span></span>

<span data-ttu-id="22395-122">None</span><span class="sxs-lookup"><span data-stu-id="22395-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
