---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393891"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="56478-101">Kimlik: UI Varsayılan Bootstrap sürümü değiştirildi</span><span class="sxs-lookup"><span data-stu-id="56478-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="56478-102">Core 3.0ASP.NETdan başlayarak, Identity UI varsayılan olarak Bootstrap'ın sürüm 4'ü kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="56478-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56478-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="56478-103">Version introduced</span></span>

<span data-ttu-id="56478-104">3,0</span><span class="sxs-lookup"><span data-stu-id="56478-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="56478-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="56478-105">Old behavior</span></span>

<span data-ttu-id="56478-106">Yöntem `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` çağrısı aynıydı`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="56478-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="56478-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="56478-107">New behavior</span></span>

<span data-ttu-id="56478-108">Yöntem `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` çağrısı aynıdır`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="56478-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="56478-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="56478-109">Reason for change</span></span>

<span data-ttu-id="56478-110">Bootstrap 4 Core 3.0 ASP.NET zaman dilimi sırasında piyasaya sürüldü.</span><span class="sxs-lookup"><span data-stu-id="56478-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56478-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56478-111">Recommended action</span></span>

<span data-ttu-id="56478-112">Varsayılan Kimlik UI'sini kullanırsanız ve aşağıdaki örnekte gösterildiği `Startup.ConfigureServices` gibi eklediyseniz, bu değişiklikten etkilenirsiniz:</span><span class="sxs-lookup"><span data-stu-id="56478-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="56478-113">Aşağıdaki eylemlerden birini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="56478-113">Take one of the following actions:</span></span>

- <span data-ttu-id="56478-114">[Geçiş kılavuzunu](https://getbootstrap.com/docs/4.0/migration)kullanarak Bootstrap 4'u kullanmak için uygulamanızı geçirin.</span><span class="sxs-lookup"><span data-stu-id="56478-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="56478-115">Bootstrap 3 kullanımını zorlamak için güncelleştirin. `Startup.ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="56478-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="56478-116">Örnek:</span><span class="sxs-lookup"><span data-stu-id="56478-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="56478-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="56478-117">Category</span></span>

<span data-ttu-id="56478-118">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="56478-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56478-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56478-119">Affected APIs</span></span>

<span data-ttu-id="56478-120">None</span><span class="sxs-lookup"><span data-stu-id="56478-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
