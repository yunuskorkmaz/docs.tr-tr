---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901823"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="e256d-101">Kimlik: SignInManager constructor yeni parametre kabul eder</span><span class="sxs-lookup"><span data-stu-id="e256d-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="e256d-102">Core 3.0 ile ASP.NET `IUserConfirmation<TUser>` ile `SignInManager` başlayan, yeni bir parametre oluşturucuya eklendi.</span><span class="sxs-lookup"><span data-stu-id="e256d-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="e256d-103">Daha fazla bilgi için [dotnet/aspnetcore#8356'ya](https://github.com/dotnet/aspnetcore/issues/8356)bakın.</span><span class="sxs-lookup"><span data-stu-id="e256d-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e256d-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="e256d-104">Version introduced</span></span>

<span data-ttu-id="e256d-105">3,0</span><span class="sxs-lookup"><span data-stu-id="e256d-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e256d-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e256d-106">Reason for change</span></span>

<span data-ttu-id="e256d-107">Değişiklik için motivasyon kimlik yeni e-posta / onay akışları için destek eklemek oldu.</span><span class="sxs-lookup"><span data-stu-id="e256d-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e256d-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e256d-108">Recommended action</span></span>

<span data-ttu-id="e256d-109">El ile bir `SignInManager`inşa, bir `IUserConfirmation` uygulama sağlamak veya sağlamak için bağımlılık enjeksiyon bir kapmak.</span><span class="sxs-lookup"><span data-stu-id="e256d-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="e256d-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="e256d-110">Category</span></span>

<span data-ttu-id="e256d-111">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="e256d-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e256d-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e256d-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
