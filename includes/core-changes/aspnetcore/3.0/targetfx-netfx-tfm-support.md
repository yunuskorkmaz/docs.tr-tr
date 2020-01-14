---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937272"
---
### <a name="target-framework-net-framework-support-dropped"></a><span data-ttu-id="ef0c6-101">Hedef Framework: .NET Framework desteği bırakıldı</span><span class="sxs-lookup"><span data-stu-id="ef0c6-101">Target framework: .NET Framework support dropped</span></span>

<span data-ttu-id="ef0c6-102">ASP.NET Core 3,0 ' den başlayarak, .NET Framework desteklenmeyen bir hedef çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-102">Starting with ASP.NET Core 3.0, .NET Framework is an unsupported target framework.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ef0c6-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ef0c6-103">Change description</span></span>

<span data-ttu-id="ef0c6-104">.NET Framework 4,8, .NET Framework son ana sürümüdür.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-104">.NET Framework 4.8 is the last major version of .NET Framework.</span></span> <span data-ttu-id="ef0c6-105">Yeni ASP.NET Core uygulamalar .NET Core üzerinde oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-105">New ASP.NET Core apps should be built on .NET Core.</span></span> <span data-ttu-id="ef0c6-106">.NET Core 3,0 sürümünden itibaren, .NET Core 'un parçası olarak ASP.NET Core 3,0 ' yi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-106">Starting with the .NET Core 3.0 release, you can think of ASP.NET Core 3.0 as being part of .NET Core.</span></span>

<span data-ttu-id="ef0c6-107">.NET Framework ASP.NET Core kullanan müşteriler, [2,1 LTS sürümünü](https://www.microsoft.com/net/download/dotnet-core/2.1)kullanarak tam olarak desteklenen bir biçimde devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-107">Customers using ASP.NET Core with .NET Framework can continue in a fully supported fashion using the [2.1 LTS release](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span> <span data-ttu-id="ef0c6-108">2,1 için destek ve bakım, en az 21 Ağustos 2021 tarihine kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-108">Support and servicing for 2.1 continues until at least August 21, 2021.</span></span> <span data-ttu-id="ef0c6-109">Bu tarih, [.net destek ilkesi](https://www.microsoft.com/net/platform/support-policy)başına LTS sürümünün bildiriminden sonraki üç yıldır.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-109">This date is three years after declaration of the LTS release per the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy).</span></span> <span data-ttu-id="ef0c6-110">**.NET Framework üzerinde** ASP.NET Core 2,1 paketleri için destek, [diğer paket tabanlı ASP.net çerçeveleri için bakım ilkesine](https://dotnet.microsoft.com/platform/support/policy/aspnet)benzer şekilde süresiz olarak genişletilir.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-110">Support for ASP.NET Core 2.1 packages **on .NET Framework** will extend indefinitely, similar to the [servicing policy for other package-based ASP.NET frameworks](https://dotnet.microsoft.com/platform/support/policy/aspnet).</span></span>

<span data-ttu-id="ef0c6-111">.NET Framework .NET Core 'a taşıma hakkında daha fazla bilgi için bkz. [.NET Core 'A taşıma](~/docs/core/porting/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef0c6-111">For more information about porting from .NET Framework to .NET Core, see [Porting to .NET Core](~/docs/core/porting/index.md).</span></span>

<span data-ttu-id="ef0c6-112">`Microsoft.Extensions` paketler (günlüğe kaydetme, bağımlılık ekleme ve yapılandırma gibi) ve Entity Framework Core etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-112">`Microsoft.Extensions` packages (such as logging, dependency injection, and configuration) and Entity Framework Core aren't affected.</span></span> <span data-ttu-id="ef0c6-113">.NET Standard desteklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-113">They'll continue to support .NET Standard.</span></span>

<span data-ttu-id="ef0c6-114">Bu değişiklik için mosyon hakkında daha fazla bilgi için, [özgün blog gönderisine](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-114">For more information on the motivation for this change, see [the original blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ef0c6-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ef0c6-115">Version introduced</span></span>

<span data-ttu-id="ef0c6-116">3.0</span><span class="sxs-lookup"><span data-stu-id="ef0c6-116">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ef0c6-117">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="ef0c6-117">Old behavior</span></span>

<span data-ttu-id="ef0c6-118">ASP.NET Core uygulamalar .NET Core veya .NET Framework üzerinde çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-118">ASP.NET Core apps could run on either .NET Core or .NET Framework.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ef0c6-119">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="ef0c6-119">New behavior</span></span>

<span data-ttu-id="ef0c6-120">ASP.NET Core uygulamalar yalnızca .NET Core üzerinde çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-120">ASP.NET Core apps can only be run on .NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ef0c6-121">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ef0c6-121">Recommended action</span></span>

<span data-ttu-id="ef0c6-122">Aşağıdaki eylemlerden birini gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="ef0c6-122">Take one of the following actions:</span></span>

- <span data-ttu-id="ef0c6-123">Uygulamanızı ASP.NET Core 2,1 ' de saklayın.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-123">Keep your app on ASP.NET Core 2.1.</span></span>
- <span data-ttu-id="ef0c6-124">Uygulamanızı ve bağımlılıklarınızı .NET Core 'a geçirin.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-124">Migrate your app and dependencies to .NET Core.</span></span>

#### <a name="category"></a><span data-ttu-id="ef0c6-125">Kategori</span><span class="sxs-lookup"><span data-stu-id="ef0c6-125">Category</span></span>

<span data-ttu-id="ef0c6-126">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef0c6-126">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ef0c6-127">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ef0c6-127">Affected APIs</span></span>

<span data-ttu-id="ef0c6-128">Yok.</span><span class="sxs-lookup"><span data-stu-id="ef0c6-128">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
