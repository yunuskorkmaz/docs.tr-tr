---
ms.openlocfilehash: 8bcd9987cb061233c8476b9c083a224fc0e25440
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539512"
---
### <a name="authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete"></a><span data-ttu-id="dd301-101">Kimlik doğrulaması: AzureAD. UI ve AzureADB2C. UI API 'Leri ve kullanım dışı olarak işaretlenen paketler</span><span class="sxs-lookup"><span data-stu-id="dd301-101">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>

<span data-ttu-id="dd301-102">ASP.NET Core 2,1 ' de, Azure Active Directory (Azure AD) ve Azure Active Directory B2C (Azure AD B2C) kimlik doğrulaması ile tümleştirme [Microsoft. aspnetcore. Authentication. AzureAD. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) ve [Microsoft. Aspnetcore. Authentication. AzureADB2C. UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) paketleri tarafından sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd301-102">In ASP.NET Core 2.1, integration with Azure Active Directory (Azure AD) and Azure Active Directory B2C (Azure AD B2C) authentication is provided by the [Microsoft.AspNetCore.Authentication.AzureAD.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureAD.UI) and [Microsoft.AspNetCore.Authentication.AzureADB2C.UI](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.AzureADB2C.UI) packages.</span></span> <span data-ttu-id="dd301-103">Bu paketler tarafından sunulan işlevsellik, Azure AD v 1.0 uç noktasını temel alır.</span><span class="sxs-lookup"><span data-stu-id="dd301-103">The functionality provided by these packages is based on the Azure AD v1.0 endpoint.</span></span>

<span data-ttu-id="dd301-104">ASP.NET Core 5,0 ve üzeri sürümlerde, Azure AD ve Azure AD B2C kimlik doğrulamasıyla tümleştirme [Microsoft. Identity. Web](https://www.nuget.org/packages/Microsoft.Identity.Web) paketi tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="dd301-104">In ASP.NET Core 5.0 and later, integration with Azure AD and Azure AD B2C authentication is provided by the [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) package.</span></span> <span data-ttu-id="dd301-105">Bu paket, daha önce Azure AD v 2.0 uç noktası olarak bilinen Microsoft Identity platformunu temel alır.</span><span class="sxs-lookup"><span data-stu-id="dd301-105">This package is based on the Microsoft Identity Platform, which is formerly known as the Azure AD v2.0 endpoint.</span></span> <span data-ttu-id="dd301-106">Sonuç olarak, `Microsoft.AspNetCore.Authentication.AzureAD.UI` ve paketlerdeki eski API 'ler `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd301-106">Consequently, the old APIs in the `Microsoft.AspNetCore.Authentication.AzureAD.UI` and `Microsoft.AspNetCore.Authentication.AzureADB2C.UI` packages were deprecated.</span></span>

<span data-ttu-id="dd301-107">Tartışma için bkz. GitHub sorunu [DotNet/aspnetcore # 25807](https://github.com/dotnet/aspnetcore/issues/25807).</span><span class="sxs-lookup"><span data-stu-id="dd301-107">For discussion, see GitHub issue [dotnet/aspnetcore#25807](https://github.com/dotnet/aspnetcore/issues/25807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd301-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="dd301-108">Version introduced</span></span>

<span data-ttu-id="dd301-109">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="dd301-109">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dd301-110">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="dd301-110">Old behavior</span></span>

<span data-ttu-id="dd301-111">API 'Ler eski olarak işaretlenmedi.</span><span class="sxs-lookup"><span data-stu-id="dd301-111">The APIs weren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dd301-112">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="dd301-112">New behavior</span></span>

<span data-ttu-id="dd301-113">API 'Ler eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="dd301-113">The APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dd301-114">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="dd301-114">Reason for change</span></span>

<span data-ttu-id="dd301-115">Azure AD ve Azure AD B2C kimlik doğrulaması işlevselliği tarafından sağlanmış olan Microsoft kimlik doğrulama kitaplığı (MSAL) API 'Lerine geçirildi `Microsoft.Identity.Web` .</span><span class="sxs-lookup"><span data-stu-id="dd301-115">The Azure AD and Azure AD B2C authentication functionality was migrated to Microsoft Authentication Library (MSAL) APIs that are provided by `Microsoft.Identity.Web`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd301-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="dd301-116">Recommended action</span></span>

<span data-ttu-id="dd301-117">`Microsoft.Identity.Web` [Web uygulamaları](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) ve [Web API 'leri](https://github.com/azuread/microsoft-identity-web/wiki/web-apis)için API kılavuzunu izleyin.</span><span class="sxs-lookup"><span data-stu-id="dd301-117">Follow the `Microsoft.Identity.Web` API guidance for [web apps](https://github.com/azuread/microsoft-identity-web/wiki/web-apps) and [web APIs](https://github.com/azuread/microsoft-identity-web/wiki/web-apis).</span></span>

#### <a name="category"></a><span data-ttu-id="dd301-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="dd301-118">Category</span></span>

<span data-ttu-id="dd301-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd301-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd301-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="dd301-120">Affected APIs</span></span>

* [<span data-ttu-id="dd301-121">Microsoft. AspNetCore. Authentication. AzureADAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="dd301-121">Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="dd301-122">Microsoft. AspNetCore. Authentication. AzureAD. UI. AzureADDefaults</span><span class="sxs-lookup"><span data-stu-id="dd301-122">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureaddefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="dd301-123">Microsoft. aspnetcore. Authentication. azuread. UI. azureadoçen</span><span class="sxs-lookup"><span data-stu-id="dd301-123">Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azuread.ui.azureadoptions?view=aspnetcore-3.0)
* [<span data-ttu-id="dd301-124">Microsoft. AspNetCore. Authentication. AzureADB2CAuthenticationBuilderExtensions</span><span class="sxs-lookup"><span data-stu-id="dd301-124">Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2cauthenticationbuilderextensions?view=aspnetcore-3.0)
* [<span data-ttu-id="dd301-125">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2CDefaults</span><span class="sxs-lookup"><span data-stu-id="dd301-125">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2cdefaults?view=aspnetcore-3.0)
* [<span data-ttu-id="dd301-126">Microsoft. AspNetCore. Authentication. AzureADB2C. UI. AzureADB2COptions</span><span class="sxs-lookup"><span data-stu-id="dd301-126">Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions</span></span>](/dotnet/api/microsoft.aspnetcore.authentication.azureadb2c.ui.azureadb2coptions?view=aspnetcore-3.0)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Authentication.AzureADAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureAD.UI.AzureADOptions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2CAuthenticationBuilderExtensions`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2CDefaults`
- `T:Microsoft.AspNetCore.Authentication.AzureADB2C.UI.AzureADB2COptions`

-->
