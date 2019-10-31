---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198595"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="a8d3a-101">MVC: ön derleme aracı kullanım dışı</span><span class="sxs-lookup"><span data-stu-id="a8d3a-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="a8d3a-102">ASP.NET Core 1,1 ' de, Razor dosyalarının ( *. cshtml* dosyaları) yayımlama zamanı derlemesi için destek eklemek üzere `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC ön derleme aracı) paketi sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="a8d3a-103">ASP.NET Core 2,1 ' de, [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) , ön derleme aracının özelliklerini genişletmek üzere sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="a8d3a-104">Razor SDK, Razor dosyalarının derleme ve yayımlama zamanı derlemesi için destek eklendi.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="a8d3a-105">SDK, uygulama başlatma zamanında geliştirirken derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="a8d3a-106">Razor SDK varsayılan olarak açık olur ve kullanmaya başlamak için herhangi bir hareket gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="a8d3a-107">ASP.NET Core 3,0 ' de, ASP.NET Core 1,1-Era MVC prederlemesini kaldırma aracı kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="a8d3a-108">Önceki paket sürümleri, düzeltme eki sürümünde önemli hata ve güvenlik düzeltmeleri almaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8d3a-109">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a8d3a-109">Version introduced</span></span>

<span data-ttu-id="a8d3a-110">3.0</span><span class="sxs-lookup"><span data-stu-id="a8d3a-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a8d3a-111">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a8d3a-111">Old behavior</span></span>

<span data-ttu-id="a8d3a-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi, MVC Razor görünümlerini önceden derlemek için kullanıldı.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a8d3a-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a8d3a-113">New behavior</span></span>

<span data-ttu-id="a8d3a-114">Razor SDK, bu işlevselliği yerel olarak destekler.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="a8d3a-115">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` paketi artık güncelleştirilmedi.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a8d3a-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a8d3a-116">Reason for change</span></span>

<span data-ttu-id="a8d3a-117">Razor SDK daha fazla işlevsellik sağlar ve derleme zamanında *. cshtml* dosyalarının doğruluğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="a8d3a-118">SDK Ayrıca uygulama başlatma süresini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8d3a-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a8d3a-119">Recommended action</span></span>

<span data-ttu-id="a8d3a-120">ASP.NET Core 2,1 veya sonraki bir sürümü kullananlar için, [Razor SDK 'sında](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0)ön derleme için yerel desteği kullanmak üzere güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="a8d3a-121">Hatalar veya eksik özellikler Razor SDK 'ya geçişi engelliyorsa, [ASPNET/AspNetCore](https://github.com/aspnet/AspNetCore/issues)yolunda bir sorun açın.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="a8d3a-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="a8d3a-122">Category</span></span>

<span data-ttu-id="a8d3a-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8d3a-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8d3a-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a8d3a-124">Affected APIs</span></span>

<span data-ttu-id="a8d3a-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="a8d3a-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
