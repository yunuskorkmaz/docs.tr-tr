---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041665"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="5794b-101">Kimlik: UI statik Web varlıkları özelliğini kullanır</span><span class="sxs-lookup"><span data-stu-id="5794b-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="5794b-102">ASP.NET Core 3,0, statik bir Web varlıkları özelliği sunmuştur ve kimlik Kullanıcı arabirimi benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="5794b-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5794b-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="5794b-103">Change description</span></span>

<span data-ttu-id="5794b-104">Statik Web varlıkları özelliğini benimseme kimlik UI 'sinin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="5794b-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="5794b-105">Çerçeve seçimi, proje dosyanızdaki `IdentityUIFrameworkVersion` özelliği kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5794b-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="5794b-106">Bootstrap 4, kimlik Kullanıcı arabirimi için varsayılan UI çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="5794b-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="5794b-107">Bootstrap 3 yaşam sonuna ulaştı ve desteklenen bir sürüme geçirmeyi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5794b-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5794b-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="5794b-108">Version introduced</span></span>

<span data-ttu-id="5794b-109">3.0</span><span class="sxs-lookup"><span data-stu-id="5794b-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5794b-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="5794b-110">Old behavior</span></span>

<span data-ttu-id="5794b-111">Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 3**idi.</span><span class="sxs-lookup"><span data-stu-id="5794b-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="5794b-112">UI çerçevesi, `Startup.ConfigureServices``AddDefaultUI` yöntemi çağrısına bir parametre kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5794b-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="5794b-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="5794b-113">New behavior</span></span>

<span data-ttu-id="5794b-114">Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 4**' dir.</span><span class="sxs-lookup"><span data-stu-id="5794b-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="5794b-115">Kullanıcı arabirimi çerçevesi, `AddDefaultUI` yöntemi çağrısı yerine proje dosyanızda yapılandırılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5794b-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="5794b-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="5794b-116">Reason for change</span></span>

<span data-ttu-id="5794b-117">UI çerçevesi yapılandırmasının MSBuild 'e taşınması için statik Web varlıkları özelliğini benimseme özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5794b-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="5794b-118">Hangi çerçevenin katıştırılması, çalışma zamanı kararı değil, derleme zamanı karardır.</span><span class="sxs-lookup"><span data-stu-id="5794b-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5794b-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="5794b-119">Recommended action</span></span>

<span data-ttu-id="5794b-120">Yeni önyükleme 4 bileşenlerinin uyumlu olduğundan emin olmak için site Kullanıcı arabirimini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="5794b-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="5794b-121">Gerekirse, önyükleme 3 ' e dönmek için `IdentityUIFrameworkVersion` MSBuild özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5794b-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="5794b-122">Özelliği proje dosyanızdaki bir `<PropertyGroup>` öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="5794b-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="5794b-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="5794b-123">Category</span></span>

<span data-ttu-id="5794b-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5794b-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5794b-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="5794b-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
