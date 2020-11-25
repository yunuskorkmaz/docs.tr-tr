---
title: 'Son değişiklik: Azure: Microsoft-önekli Azure tümleştirme paketleri kaldırıldı'
description: "ASP.NET Core 5,0 ' deki Son değişiklik hakkında bilgi edinin: Microsoft-önekli Azure tümleştirme paketleri kaldırıldı"
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b9f685b8c9fdcd73044f78840f2732809a0de710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761665"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="d3638-103">Azure: Microsoft 'un ön eki olan Azure tümleştirme paketleri kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="d3638-103">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="d3638-104">`Microsoft.*`ASP.NET Core ve Azure SDK 'ları arasında tümleştirme sağlayan aşağıdaki paketler, ASP.NET Core 5,0 ' ye dahil değildir:</span><span class="sxs-lookup"><span data-stu-id="d3638-104">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="d3638-105">[Microsoft.Extensions.Configurlama. ](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/) [Yapılandırma sistemine](/aspnet/core/fundamentals/configuration/) [Azure Key Vault](/azure/key-vault/) tümleştiren AzureKeyVault.</span><span class="sxs-lookup"><span data-stu-id="d3638-105">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="d3638-106">Azure Key Vault [ASP.NET Core veri koruma sistemine](/aspnet/core/security/data-protection/introduction)tümleştiren [Microsoft. Aspnetcore. DataProtection. AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/).</span><span class="sxs-lookup"><span data-stu-id="d3638-106">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="d3638-107">[Azure Blob depolamayı](/azure/storage/blobs/) ASP.NET Core veri koruma sistemine tümleştiren [Microsoft. Aspnetcore. DataProtection. azurestorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/).</span><span class="sxs-lookup"><span data-stu-id="d3638-107">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="d3638-108">Bu sorunla ilgili tartışmak için bkz. [DotNet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="d3638-108">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="d3638-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d3638-109">Version introduced</span></span>

<span data-ttu-id="d3638-110">5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="d3638-110">5.0 Preview 1</span></span>

## <a name="old-behavior"></a><span data-ttu-id="d3638-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d3638-111">Old behavior</span></span>

<span data-ttu-id="d3638-112">, `Microsoft.*` Yapılandırma ve veri koruma API 'leri ile tümleştirilmiş Azure hizmetlerini paketler.</span><span class="sxs-lookup"><span data-stu-id="d3638-112">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="d3638-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d3638-113">New behavior</span></span>

<span data-ttu-id="d3638-114">Yeni `Azure.*` paketler, Azure hizmetlerini yapılandırma ve veri koruma API 'leriyle tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="d3638-114">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d3638-115">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d3638-115">Reason for change</span></span>

<span data-ttu-id="d3638-116">Bu değişiklik, paketler şu şekilde yapılmıştır `Microsoft.*` :</span><span class="sxs-lookup"><span data-stu-id="d3638-116">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="d3638-117">Azure SDK 'sının güncel olmayan sürümlerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="d3638-117">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="d3638-118">Azure SDK 'sının yeni sürümleri büyük değişiklikler yaptığından basit güncelleştirmeler yapılamıyor.</span><span class="sxs-lookup"><span data-stu-id="d3638-118">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="d3638-119">.NET Core sürüm çizelgesine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d3638-119">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="d3638-120">Paketlerin sahipliğini Azure SDK ekibine aktarmak, Azure SDK güncelleştirildiğinde paket güncelleştirmelerinin yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3638-120">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d3638-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d3638-121">Recommended action</span></span>

<span data-ttu-id="d3638-122">ASP.NET Core 2,1 veya üzeri projelerde eskisini `Microsoft.*` Yeni `Azure.*` paketlerle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="d3638-122">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="d3638-123">Eskisi</span><span class="sxs-lookup"><span data-stu-id="d3638-123">Old</span></span> | <span data-ttu-id="d3638-124">Yeni</span><span class="sxs-lookup"><span data-stu-id="d3638-124">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="d3638-125">Azure. Extensions. AspNetCore. DataProtection. Keys</span><span class="sxs-lookup"><span data-stu-id="d3638-125">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="d3638-126">Azure. Extensions. AspNetCore. DataProtection. blob 'Lar</span><span class="sxs-lookup"><span data-stu-id="d3638-126">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="d3638-127">Azure.Extensions.AspNetCore.Configurlama. Kaynaklanır</span><span class="sxs-lookup"><span data-stu-id="d3638-127">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="d3638-128">Yeni paketler Azure SDK 'sının son değişiklikleri içeren yeni bir sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="d3638-128">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="d3638-129">Genel kullanım desenleri değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="d3638-129">The general usage patterns are unchanged.</span></span> <span data-ttu-id="d3638-130">Bazı aşırı yüklemeler ve seçenekler, temel alınan Azure SDK API 'Lerinde değişikliklere uyum sağlamak için farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="d3638-130">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="d3638-131">Eski paketler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d3638-131">The old packages will:</span></span>

* <span data-ttu-id="d3638-132">.NET Core 2,1 ve 3,1 ' nin kullanım ömrü boyunca ASP.NET Core ekibi tarafından desteklenmelidir.</span><span class="sxs-lookup"><span data-stu-id="d3638-132">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="d3638-133">.NET 5 ' te bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="d3638-133">Not be included in .NET 5.</span></span>

<span data-ttu-id="d3638-134">Projenizi .NET 5 ' e yükseltirken, `Azure.*` destek sağlamak için paketlere geçiş yapın.</span><span class="sxs-lookup"><span data-stu-id="d3638-134">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d3638-135">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d3638-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
