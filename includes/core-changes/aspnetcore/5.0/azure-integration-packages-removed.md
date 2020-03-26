---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291661"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="58ce7-101">Azure: Microsoft tarafından önceden belirlenmiş Azure tümleştirme paketleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="58ce7-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="58ce7-102">ASP.NET `Microsoft.*` Core ve Azure SDK'ları arasında tümleştirme sağlayan aşağıdaki paketler ASP.NET Core 5.0'a dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="58ce7-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="58ce7-103">[Azure Key Vault'u](/azure/key-vault/) [Yapılandırma sistemine](/aspnet/core/fundamentals/configuration/)entegre eden [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/).</span><span class="sxs-lookup"><span data-stu-id="58ce7-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="58ce7-104">Azure Key Vault'u [ASP.NET Çekirdek Veri Koruma sistemine](/aspnet/core/security/data-protection/introduction)entegre eden [Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/).</span><span class="sxs-lookup"><span data-stu-id="58ce7-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="58ce7-105">[Azure Blob Depolama'yı](/azure/storage/blobs/) ASP.NET Çekirdek Veri Koruma sistemine entegre eden [Microsoft.AspNetCore.DataProtection.AzureStorage.](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/)</span><span class="sxs-lookup"><span data-stu-id="58ce7-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="58ce7-106">Bu konuda tartışma için [dotnet/aspnetcore#19570'e](https://github.com/dotnet/aspnetcore/issues/19570)bakın.</span><span class="sxs-lookup"><span data-stu-id="58ce7-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="58ce7-107">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="58ce7-107">Version introduced</span></span>

<span data-ttu-id="58ce7-108">5.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="58ce7-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="58ce7-109">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="58ce7-109">Old behavior</span></span>

<span data-ttu-id="58ce7-110">Paketler `Microsoft.*` Azure hizmetlerini Yapılandırma ve Veri Koruma API'leriyle bütünleştirdi.</span><span class="sxs-lookup"><span data-stu-id="58ce7-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="58ce7-111">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="58ce7-111">New behavior</span></span>

<span data-ttu-id="58ce7-112">Yeni `Azure.*` paketler Azure hizmetlerini Yapılandırma ve Veri Koruma API'leriyle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="58ce7-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="58ce7-113">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="58ce7-113">Reason for change</span></span>

<span data-ttu-id="58ce7-114">Değişiklik yapıldı çünkü `Microsoft.*` paketler:</span><span class="sxs-lookup"><span data-stu-id="58ce7-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="58ce7-115">Azure SDK'nın eski sürümlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="58ce7-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="58ce7-116">Azure SDK'nın yeni sürümlerinde kesme değişiklikleri içerdiğinden basit güncelleştirmeler mümkün değildi.</span><span class="sxs-lookup"><span data-stu-id="58ce7-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="58ce7-117">.NET Core yayın programına bağlı.</span><span class="sxs-lookup"><span data-stu-id="58ce7-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="58ce7-118">Paketlerin sahipliğini Azure SDK ekibine aktarmak, Azure SDK güncelleştirildikçe paket güncelleştirmelerine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="58ce7-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="58ce7-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="58ce7-119">Recommended action</span></span>

<span data-ttu-id="58ce7-120">core 2.1 veya daha sonraki ASP.NET `Microsoft.*` projelerde, eskiyi yeni `Azure.*` paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="58ce7-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="58ce7-121">Eski</span><span class="sxs-lookup"><span data-stu-id="58ce7-121">Old</span></span> | <span data-ttu-id="58ce7-122">Yeni</span><span class="sxs-lookup"><span data-stu-id="58ce7-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="58ce7-123">Azure.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="58ce7-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="58ce7-124">Azure.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="58ce7-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="58ce7-125">Azure.Extensions.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="58ce7-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="58ce7-126">Yeni paketler, Azure SDK'nın değişiklikleri kesmeyi içeren yeni bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="58ce7-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="58ce7-127">Genel kullanım desenleri değişmedi.</span><span class="sxs-lookup"><span data-stu-id="58ce7-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="58ce7-128">Bazı aşırı yüklemeler ve seçenekler, temel Azure SDK API'lerinde ki değişikliklere uyum sağlamak için farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="58ce7-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="58ce7-129">Eski paketler:</span><span class="sxs-lookup"><span data-stu-id="58ce7-129">The old packages will:</span></span>

* <span data-ttu-id="58ce7-130">.NET Core 2.1 ve 3.1 ömrü boyunca ASP.NET Core ekibi tarafından desteklenebilir.</span><span class="sxs-lookup"><span data-stu-id="58ce7-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="58ce7-131">.NET 5'e dahil edilmeyin.</span><span class="sxs-lookup"><span data-stu-id="58ce7-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="58ce7-132">Projenizi .NET 5'e yükseltirken, `Azure.*` desteği korumak için paketlere geçiş yap.</span><span class="sxs-lookup"><span data-stu-id="58ce7-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="58ce7-133">Kategori</span><span class="sxs-lookup"><span data-stu-id="58ce7-133">Category</span></span>

<span data-ttu-id="58ce7-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="58ce7-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58ce7-135">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="58ce7-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
