---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394002"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="3aa94-101">Kimlik: SignInManager Oluşturucusu yeni parametreyi kabul ediyor</span><span class="sxs-lookup"><span data-stu-id="3aa94-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="3aa94-102">ASP.NET Core 3,0 ' den başlayarak `SignInManager` oluşturucusuna yeni bir `IUserConfirmation<TUser>` parametresi eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3aa94-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="3aa94-103">Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="3aa94-103">For more information, see [aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3aa94-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3aa94-104">Version introduced</span></span>

<span data-ttu-id="3aa94-105">3,0</span><span class="sxs-lookup"><span data-stu-id="3aa94-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3aa94-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3aa94-106">Reason for change</span></span>

<span data-ttu-id="3aa94-107">Değişiklik için mosyon, kimlik içinde yeni e-posta/onay akışları için destek eklemektir.</span><span class="sxs-lookup"><span data-stu-id="3aa94-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3aa94-108">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3aa94-108">Recommended action</span></span>

<span data-ttu-id="3aa94-109">`SignInManager`el ile oluşturuyorsanız, bir `IUserConfirmation` uygulamasını sağlayın veya bir bağımlılık ekleme işleminden bir tane alın.</span><span class="sxs-lookup"><span data-stu-id="3aa94-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="3aa94-110">Kategori</span><span class="sxs-lookup"><span data-stu-id="3aa94-110">Category</span></span>

<span data-ttu-id="3aa94-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3aa94-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3aa94-112">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3aa94-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
