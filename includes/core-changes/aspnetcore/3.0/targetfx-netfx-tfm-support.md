---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937272"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="d3fea-101">Hedef çerçeve: .NET Framework desteği düştü</span><span class="sxs-lookup"><span data-stu-id="d3fea-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="d3fea-102">ASP.NET Core 3.0 ile başlayan .NET Framework desteklenmeyen bir hedef çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="d3fea-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d3fea-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="d3fea-103">Change description</span></span>

<span data-ttu-id="d3fea-104">.NET Framework 4.8 ,.NET Framework'ün son ana sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="d3fea-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="d3fea-105">Yeni ASP.NET Core uygulamaları .NET Core üzerine kurulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d3fea-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="d3fea-106">.NET Core 3.0 sürümünden başlayarak, ASP.NET Core 3.0'ı .NET Core'un bir parçası olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3fea-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="d3fea-107">.NET Framework ile ASP.NET Core kullanan müşteriler [2.1 LTS sürümü](https://www.microsoft.com/net/download/dotnet-core/2.1)kullanarak tam destekli bir şekilde devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3fea-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="d3fea-108">2.1 için destek ve hizmet en az 21 Ağustos 2021 tarihine kadar devam etmektedir.</span><span class="sxs-lookup"><span data-stu-id="d3fea-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="d3fea-109">Bu tarih, [.NET Destek İlkesi](https://www.microsoft.com/net/platform/support-policy)uyarınca LTS sürümünin beyanı tarihinden üç yıl sonradır.</span><span class="sxs-lookup"><span data-stu-id="d3fea-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="d3fea-110">**.NET Framework'deki** ASP.NET Core 2.1 paketlerinin desteği, [diğer paket tabanlı ASP.NET çerçeveleri için servis politikasına](https://dotnet.microsoft.com/platform/support/policy/aspnet)benzer şekilde süresiz olarak uzayacaktır.</span><span class="sxs-lookup"><span data-stu-id="d3fea-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="d3fea-111">.NET Framework'den .NET Core'a taşıma hakkında daha fazla bilgi [için](~/docs/core/porting/index.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="d3fea-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="d3fea-112">`Microsoft.Extensions`paketleri (günlük, bağımlılık enjeksiyonu ve yapılandırma gibi) ve Entity Framework Core etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d3fea-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="d3fea-113">.NET Standard'ı desteklemeye devam edeceklerdir.</span><span class="sxs-lookup"><span data-stu-id="d3fea-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="d3fea-114">Bu değişikliğin motivasyonu hakkında daha fazla bilgi için [orijinal blog gönderisi](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="d3fea-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3fea-115">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="d3fea-115">Version introduced</span></span>

<span data-ttu-id="d3fea-116">3,0</span><span class="sxs-lookup"><span data-stu-id="d3fea-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d3fea-117">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="d3fea-117">Old behavior</span></span>

<span data-ttu-id="d3fea-118">ASP.NET Core uygulamaları .NET Core veya .NET Framework üzerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3fea-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d3fea-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="d3fea-119">New behavior</span></span>

<span data-ttu-id="d3fea-120">ASP.NET Core uygulamaları yalnızca .NET Core'da çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d3fea-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3fea-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d3fea-121">Recommended action</span></span>

<span data-ttu-id="d3fea-122">Aşağıdaki eylemlerden birini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="d3fea-122">Take one of the following actions:</span></span>

- <span data-ttu-id="d3fea-123">Uygulamanızı Core 2.1ASP.NET de tutun.</span><span class="sxs-lookup"><span data-stu-id="d3fea-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="d3fea-124">Uygulamanızı ve bağımlılıklarınızı .NET Core'a geçirin.</span><span class="sxs-lookup"><span data-stu-id="d3fea-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="d3fea-125">Kategori</span><span class="sxs-lookup"><span data-stu-id="d3fea-125">Category</span></span>

<span data-ttu-id="d3fea-126">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="d3fea-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3fea-127">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d3fea-127">Affected APIs</span></span>

<span data-ttu-id="d3fea-128">None</span><span class="sxs-lookup"><span data-stu-id="d3fea-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
