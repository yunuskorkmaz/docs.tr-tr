---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041665"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="a1155-101">Kimlik: UI statik web varlıkları özelliğini kullanır</span><span class="sxs-lookup"><span data-stu-id="a1155-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="a1155-102">ASP.NET Core 3.0 statik bir web varlıkları özelliği tanıttı ve Kimlik UI bunu benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="a1155-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a1155-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="a1155-103">Change description</span></span>

<span data-ttu-id="a1155-104">Kimlik UI statik web varlıkları özelliği benimseyen bir sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="a1155-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="a1155-105">Çerçeve seçimi, proje dosyanızdaki `IdentityUIFrameworkVersion` özelliği kullanarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a1155-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="a1155-106">Bootstrap 4, Kimlik Arabirimi için varsayılan UI çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="a1155-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="a1155-107">Bootstrap 3 yaşamın sonuna ulaştı ve desteklenen bir sürüme göç düşünmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a1155-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a1155-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="a1155-108">Version introduced</span></span>

<span data-ttu-id="a1155-109">3,0</span><span class="sxs-lookup"><span data-stu-id="a1155-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a1155-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="a1155-110">Old behavior</span></span>

<span data-ttu-id="a1155-111">Kimlik Arabirimi için varsayılan UI çerçevesi **Bootstrap 3**idi.</span><span class="sxs-lookup"><span data-stu-id="a1155-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="a1155-112">UI çerçevesi, 'deki `AddDefaultUI` `Startup.ConfigureServices`yöntem çağrısına bir parametre kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a1155-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a1155-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="a1155-113">New behavior</span></span>

<span data-ttu-id="a1155-114">Kimlik Arabirimi için varsayılan UI çerçevesi **Bootstrap**4'dür.</span><span class="sxs-lookup"><span data-stu-id="a1155-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="a1155-115">U-UI `AddDefaultUI` çerçevesi, yöntem çağrısı yerine proje dosyanızda yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a1155-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a1155-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="a1155-116">Reason for change</span></span>

<span data-ttu-id="a1155-117">Statik web varlıkları özelliğinin benimsenmesi, UI çerçeve yapılandırmasının MSBuild'e taşınmasını gerektiriyordu.</span><span class="sxs-lookup"><span data-stu-id="a1155-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="a1155-118">Hangi çerçeveye yerleştirilemeye karar verebilmek için bir yapı zamanı kararıdır, çalışma zamanı kararı değil.</span><span class="sxs-lookup"><span data-stu-id="a1155-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a1155-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a1155-119">Recommended action</span></span>

<span data-ttu-id="a1155-120">Yeni Bootstrap 4 bileşenlerinin uyumlu olduğundan emin olmak için sitenizin UI'sini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="a1155-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="a1155-121">Gerekirse, Bootstrap `IdentityUIFrameworkVersion` 3'e dönmek için MSBuild özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1155-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="a1155-122">Özelliği proje dosyanızdaki bir `<PropertyGroup>` öğeye ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a1155-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="a1155-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="a1155-123">Category</span></span>

<span data-ttu-id="a1155-124">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="a1155-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a1155-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a1155-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
