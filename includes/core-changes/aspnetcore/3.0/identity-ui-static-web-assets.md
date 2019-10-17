---
ms.openlocfilehash: 8d7942ef6c36c01a9ae7ae2a9739f26dfcda5813
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394139"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="b2de6-101">Kimlik: UI statik Web varlıkları özelliğini kullanır</span><span class="sxs-lookup"><span data-stu-id="b2de6-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="b2de6-102">ASP.NET Core 3,0, statik bir Web varlıkları özelliği sunmuştur ve kimlik Kullanıcı arabirimi benimsemiştir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b2de6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="b2de6-103">Change description</span></span>

<span data-ttu-id="b2de6-104">Statik Web varlıkları özelliğini benimseme kimlik UI 'sinin sonucu olarak:</span><span class="sxs-lookup"><span data-stu-id="b2de6-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="b2de6-105">Çerçeve seçimi, proje dosyanızdaki `IdentityUIFrameworkVersion` özelliği kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="b2de6-106">Bootstrap 4, kimlik Kullanıcı arabirimi için varsayılan UI çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="b2de6-107">Bootstrap 3 yaşam sonuna ulaştı ve desteklenen bir sürüme geçirmeyi göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2de6-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="b2de6-108">Version introduced</span></span>

<span data-ttu-id="b2de6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="b2de6-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b2de6-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="b2de6-110">Old behavior</span></span>

<span data-ttu-id="b2de6-111">Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 3**idi.</span><span class="sxs-lookup"><span data-stu-id="b2de6-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="b2de6-112">UI çerçevesi, `Startup.ConfigureServices` ' deki `AddIdentityUI` yöntem çağrısına bir parametre kullanılarak yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-112">The UI framework could be configured using a parameter to the `AddIdentityUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b2de6-113">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="b2de6-113">New behavior</span></span>

<span data-ttu-id="b2de6-114">Kimlik Kullanıcı arabirimi için varsayılan UI çerçevesi **önyükleme 4**' dir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="b2de6-115">Kullanıcı arabirimi çerçevesinin, `AddIdentityUI` Yöntem çağrısında değil, proje dosyanızda yapılandırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-115">The UI framework must be configured in your project file, instead of in the `AddIdentityUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b2de6-116">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="b2de6-116">Reason for change</span></span>

<span data-ttu-id="b2de6-117">UI çerçevesi yapılandırmasının MSBuild 'e taşınması için statik Web varlıkları özelliğini benimseme özelliği gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b2de6-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="b2de6-118">Hangi çerçevenin katıştırılması, çalışma zamanı kararı değil, derleme zamanı karardır.</span><span class="sxs-lookup"><span data-stu-id="b2de6-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2de6-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="b2de6-119">Recommended action</span></span>

<span data-ttu-id="b2de6-120">Yeni önyükleme 4 bileşenlerinin uyumlu olduğundan emin olmak için site Kullanıcı arabirimini gözden geçirin.</span><span class="sxs-lookup"><span data-stu-id="b2de6-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="b2de6-121">Gerekirse, önyükleme 3 ' e dönmek için `IdentityUIFrameworkVersion` MSBuild özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2de6-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="b2de6-122">Özelliği proje dosyanızdaki bir `<PropertyGroup>` öğesine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b2de6-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="b2de6-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="b2de6-123">Category</span></span>

<span data-ttu-id="b2de6-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2de6-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2de6-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b2de6-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)`

-->
