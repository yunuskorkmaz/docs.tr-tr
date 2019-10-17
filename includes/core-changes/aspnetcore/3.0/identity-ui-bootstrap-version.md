---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393891"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="e139c-101">Kimlik: UI 'nin varsayılan önyükleme sürümü değişti</span><span class="sxs-lookup"><span data-stu-id="e139c-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="e139c-102">ASP.NET Core 3,0 ' den başlayarak, kimlik Kullanıcı arabirimi varsayılan önyükleme sürüm 4 ' ü kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="e139c-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e139c-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="e139c-103">Version introduced</span></span>

<span data-ttu-id="e139c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="e139c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e139c-105">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="e139c-105">Old behavior</span></span>

<span data-ttu-id="e139c-106">@No__t-0 Yöntem çağrısı, `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);` ile aynı idi</span><span class="sxs-lookup"><span data-stu-id="e139c-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e139c-107">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="e139c-107">New behavior</span></span>

<span data-ttu-id="e139c-108">@No__t-0 Yöntem çağrısı, `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);` ile aynı</span><span class="sxs-lookup"><span data-stu-id="e139c-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e139c-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="e139c-109">Reason for change</span></span>

<span data-ttu-id="e139c-110">Bootstrap 4 ASP.NET Core 3,0 zaman dilimi sırasında yayınlandı.</span><span class="sxs-lookup"><span data-stu-id="e139c-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e139c-111">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="e139c-111">Recommended action</span></span>

<span data-ttu-id="e139c-112">Varsayılan kimlik Kullanıcı arabirimini kullanırsanız ve bunu aşağıdaki örnekte gösterildiği gibi `Startup.ConfigureServices` ' a eklediyseniz, bu değişiklikten etkilenmiş olursunuz:</span><span class="sxs-lookup"><span data-stu-id="e139c-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="e139c-113">Aşağıdaki eylemlerden birini yapın:</span><span class="sxs-lookup"><span data-stu-id="e139c-113">Take one of the following actions:</span></span>

- <span data-ttu-id="e139c-114">Uygulamanızı [geçiş kılavuzunu](https://getbootstrap.com/docs/4.0/migration)kullanarak önyükleme 4 ' ü kullanacak şekilde geçirin.</span><span class="sxs-lookup"><span data-stu-id="e139c-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="e139c-115">Bootstrap 3 ' ün kullanımını zorlamak için `Startup.ConfigureServices` güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="e139c-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="e139c-116">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e139c-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="e139c-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="e139c-117">Category</span></span>

<span data-ttu-id="e139c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e139c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e139c-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="e139c-119">Affected APIs</span></span>

<span data-ttu-id="e139c-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="e139c-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
