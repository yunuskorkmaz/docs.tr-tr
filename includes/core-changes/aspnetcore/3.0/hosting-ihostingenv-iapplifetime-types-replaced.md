---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394335"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="1ba35-101">Barındırma: ıhostingenvironment ve ıapplicationlifetime türleri artık kullanılmıyor ve değiştirilmiş olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="1ba35-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="1ba35-102">Var olan `IHostingEnvironment` ve `IApplicationLifetime` türlerini değiştirmek için yeni türler sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="1ba35-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1ba35-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1ba35-103">Version introduced</span></span>

<span data-ttu-id="1ba35-104">3.0</span><span class="sxs-lookup"><span data-stu-id="1ba35-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1ba35-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="1ba35-105">Old behavior</span></span>

<span data-ttu-id="1ba35-106">@No__t-2 ve `Microsoft.AspNetCore.Hosting` ' ten iki farklı `IHostingEnvironment` ve `IApplicationLifetime` türü vardı.</span><span class="sxs-lookup"><span data-stu-id="1ba35-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1ba35-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="1ba35-107">New behavior</span></span>

<span data-ttu-id="1ba35-108">Eski türler kullanım dışı olarak işaretlendi ve yeni türlerle değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="1ba35-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1ba35-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="1ba35-109">Reason for change</span></span>

<span data-ttu-id="1ba35-110">@No__t-0 ASP.NET Core 2,1 ' de tanıtıldığında, `IHostingEnvironment` ve `IApplicationLifetime` gibi bazı türler `Microsoft.AspNetCore.Hosting` ' ten kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="1ba35-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="1ba35-111">Bazı ASP.NET Core 3,0 değişiklikleri, uygulamaların hem `Microsoft.Extensions.Hosting` hem de `Microsoft.AspNetCore.Hosting` ad alanlarını içermesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1ba35-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="1ba35-112">Bu yinelenen türlerin herhangi bir kullanımı, her iki ad alanına de başvuruluyorsa "belirsiz başvuru" derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1ba35-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1ba35-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1ba35-113">Recommended action</span></span>

<span data-ttu-id="1ba35-114">Eski türlerin tüm kullanımları, Yeni tanıtılan türlerle aşağıda gösterildiği gibi değiştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1ba35-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="1ba35-115">**Kullanılmayan türler (uyarı):**</span><span class="sxs-lookup"><span data-stu-id="1ba35-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="1ba35-116">**Yeni türler:**</span><span class="sxs-lookup"><span data-stu-id="1ba35-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="1ba35-117">Yeni `IHostEnvironment` `IsDevelopment` ve `IsProduction` uzantı yöntemleri `Microsoft.Extensions.Hosting` ad alanıdır.</span><span class="sxs-lookup"><span data-stu-id="1ba35-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="1ba35-118">Bu ad alanının projenize eklenmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="1ba35-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="1ba35-119">Kategori</span><span class="sxs-lookup"><span data-stu-id="1ba35-119">Category</span></span>

<span data-ttu-id="1ba35-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1ba35-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ba35-121">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1ba35-121">Affected APIs</span></span>

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
