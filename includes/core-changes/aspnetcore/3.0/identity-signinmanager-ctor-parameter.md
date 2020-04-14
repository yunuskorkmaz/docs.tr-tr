---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275504"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="fdf36-101">Kimlik: SignInManager constructor yeni parametre kabul eder</span><span class="sxs-lookup"><span data-stu-id="fdf36-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="fdf36-102">Core 3.0 ile ASP.NET `IUserConfirmation<TUser>` ile `SignInManager` başlayan, yeni bir parametre oluşturucuya eklendi.</span><span class="sxs-lookup"><span data-stu-id="fdf36-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="fdf36-103">Daha fazla bilgi için [dotnet/aspnetcore#8356'ya](https://github.com/dotnet/aspnetcore/issues/8356)bakın.</span><span class="sxs-lookup"><span data-stu-id="fdf36-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fdf36-104">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="fdf36-104">Version introduced</span></span>

<span data-ttu-id="fdf36-105">3,0</span><span class="sxs-lookup"><span data-stu-id="fdf36-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fdf36-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="fdf36-106">Reason for change</span></span>

<span data-ttu-id="fdf36-107">Değişiklik için motivasyon kimlik yeni e-posta / onay akışları için destek eklemek oldu.</span><span class="sxs-lookup"><span data-stu-id="fdf36-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fdf36-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="fdf36-108">Recommended action</span></span>

<span data-ttu-id="fdf36-109">El ile bir `SignInManager`inşa, bir `IUserConfirmation` uygulama sağlamak veya sağlamak için bağımlılık enjeksiyon bir kapmak.</span><span class="sxs-lookup"><span data-stu-id="fdf36-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="fdf36-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="fdf36-110">Category</span></span>

<span data-ttu-id="fdf36-111">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="fdf36-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fdf36-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="fdf36-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
