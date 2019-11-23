---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393938"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="e6a05-101">Veri koruma: DataProtection. AzureStorage yeni Azure depolama API 'Lerini kullanır</span><span class="sxs-lookup"><span data-stu-id="e6a05-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="e6a05-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>, [Azure depolama kitaplıklarına](https://github.com/Azure/azure-storage-net)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e6a05-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="e6a05-103">Bu kitaplıklar derlemeleri, paketleri ve ad alanlarını yeniden adlandırdı.</span><span class="sxs-lookup"><span data-stu-id="e6a05-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="e6a05-104">ASP.NET Core 3,0 ' den başlayarak, `Microsoft.AspNetCore.DataProtection.AzureStorage` yeni `Microsoft.Azure.Storage.`ön eki olan API 'Leri ve paketleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="e6a05-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="e6a05-105">Azure depolama API 'Leri hakkında sorularınız için <https://github.com/Azure/azure-storage-net>kullanın.</span><span class="sxs-lookup"><span data-stu-id="e6a05-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="e6a05-106">Bu sorunla ilgili tartışmak için bkz. [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="e6a05-106">For discussion on this issue, see [aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e6a05-107">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e6a05-107">Version introduced</span></span>

<span data-ttu-id="e6a05-108">3,0</span><span class="sxs-lookup"><span data-stu-id="e6a05-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e6a05-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e6a05-109">Old behavior</span></span>

<span data-ttu-id="e6a05-110">Paket, `WindowsAzure.Storage` NuGet paketine başvurdu.</span><span class="sxs-lookup"><span data-stu-id="e6a05-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e6a05-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e6a05-111">New behavior</span></span>

<span data-ttu-id="e6a05-112">Paket, `Microsoft.Azure.Storage.Blob` NuGet paketine başvurur.</span><span class="sxs-lookup"><span data-stu-id="e6a05-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e6a05-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e6a05-113">Reason for change</span></span>

<span data-ttu-id="e6a05-114">Bu değişiklik, `Microsoft.AspNetCore.DataProtection.AzureStorage` önerilen Azure depolama paketlerine geçiş yapmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e6a05-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e6a05-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e6a05-115">Recommended action</span></span>

<span data-ttu-id="e6a05-116">Hala ASP.NET Core 3,0 ile eski Azure depolama API 'Lerini kullanmanız gerekiyorsa, [windowsazure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) paketine doğrudan bir bağımlılık ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6a05-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="e6a05-117">Bu paket, yeni `Microsoft.Azure.Storage` API 'Leri ile birlikte yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="e6a05-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="e6a05-118">Çoğu durumda, yükseltme yalnızca `using` deyimlerinin yeni ad alanlarını kullanacak şekilde değiştirilmesini içerir:</span><span class="sxs-lookup"><span data-stu-id="e6a05-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="e6a05-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="e6a05-119">Category</span></span>

<span data-ttu-id="e6a05-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e6a05-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e6a05-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e6a05-121">Affected APIs</span></span>

<span data-ttu-id="e6a05-122">Yok.</span><span class="sxs-lookup"><span data-stu-id="e6a05-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
