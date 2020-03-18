---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394335"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="c8e1a-101">Hosting: IHostingEnvironment ve IApplicationLifetime türleri eski işaretlenmiş ve değiştirildi</span><span class="sxs-lookup"><span data-stu-id="c8e1a-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="c8e1a-102">Varolan ve `IHostingEnvironment` `IApplicationLifetime` türleri değiştirmek için yeni türler tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c8e1a-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="c8e1a-103">Version introduced</span></span>

<span data-ttu-id="c8e1a-104">3,0</span><span class="sxs-lookup"><span data-stu-id="c8e1a-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c8e1a-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="c8e1a-105">Old behavior</span></span>

<span data-ttu-id="c8e1a-106">İki farklı `IHostingEnvironment` ve `IApplicationLifetime` türleri `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting`vardı ve .</span><span class="sxs-lookup"><span data-stu-id="c8e1a-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c8e1a-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="c8e1a-107">New behavior</span></span>

<span data-ttu-id="c8e1a-108">Eski türler eski olarak işaretlenmiş ve yeni türlerle değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c8e1a-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c8e1a-109">Reason for change</span></span>

<span data-ttu-id="c8e1a-110">Core `Microsoft.Extensions.Hosting` 2.1ASP.NET de sunulduğunda, bazı `IHostingEnvironment` `IApplicationLifetime` türleri gibi `Microsoft.AspNetCore.Hosting`ve kopyalandı .</span><span class="sxs-lookup"><span data-stu-id="c8e1a-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="c8e1a-111">Bazı ASP.NET Core 3.0 değişiklikleri uygulamaların `Microsoft.Extensions.Hosting` `Microsoft.AspNetCore.Hosting` hem ad alanlarını hem de ad alanlarını içermesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="c8e1a-112">Bu yinelenen türlerin herhangi bir kullanımı, her iki ad alanı başvurulduğunda bir "belirsiz başvuru" derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c8e1a-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c8e1a-113">Recommended action</span></span>

<span data-ttu-id="c8e1a-114">Aşağıdaki gibi yeni tanıtılan türleri ile eski türlerin herhangi bir kullanımları değiştirildi:</span><span class="sxs-lookup"><span data-stu-id="c8e1a-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="c8e1a-115">**Eski türleri (uyarı):**</span><span class="sxs-lookup"><span data-stu-id="c8e1a-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="c8e1a-116">**Yeni türler:**</span><span class="sxs-lookup"><span data-stu-id="c8e1a-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="c8e1a-117">Yeni `IHostEnvironment` `IsDevelopment` ve `IsProduction` uzantı yöntemleri `Microsoft.Extensions.Hosting` ad alanındadır.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="c8e1a-118">Bu ad alanının projenize eklenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c8e1a-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="c8e1a-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="c8e1a-119">Category</span></span>

<span data-ttu-id="c8e1a-120">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="c8e1a-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c8e1a-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c8e1a-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
