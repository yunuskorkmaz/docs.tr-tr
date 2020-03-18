---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901609"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="31d96-101">Barındırma: Genel ana bilgisayar Başlangıç yapıcı enjeksiyonu kısıtlar</span><span class="sxs-lookup"><span data-stu-id="31d96-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="31d96-102">Genel ana bilgisayar tarafından `Startup` sınıf yapıcı enjeksiyonu `IWebHostEnvironment`için `IConfiguration`destekleyen tek tür , `IHostEnvironment`ve .</span><span class="sxs-lookup"><span data-stu-id="31d96-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="31d96-103">Kullanan `WebHost` uygulamalar etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="31d96-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="31d96-104">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="31d96-104">Change description</span></span>

<span data-ttu-id="31d96-105">Core 3.0ASP.NETönce, yapıcı enjeksiyon `Startup` sınıfın oluşturucusundaki rasgele tipler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31d96-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="31d96-106">Core 3.0ASP.NET, web yığını genel ana bilgisayar kitaplığı üzerine yeniden platformlandı.</span><span class="sxs-lookup"><span data-stu-id="31d96-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="31d96-107">Şablonların *Program.cs* dosyasındaki değişikliği görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="31d96-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="31d96-108">**ASP.NET Çekirdek 2.x:**</span><span class="sxs-lookup"><span data-stu-id="31d96-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="31d96-109">**ASP.NET Çekirdek 3.0:**</span><span class="sxs-lookup"><span data-stu-id="31d96-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="31d96-110">`Host`uygulamayı oluşturmak için bir bağımlılık enjeksiyonu (DI) kapsayıcıkullanır.</span><span class="sxs-lookup"><span data-stu-id="31d96-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="31d96-111">`WebHost`iki kapsayıcı kullanır: biri ana bilgisayar için, diğeri uygulama için.</span><span class="sxs-lookup"><span data-stu-id="31d96-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="31d96-112">Sonuç olarak, `Startup` oluşturucu artık özel hizmet enjeksiyondestekler.</span><span class="sxs-lookup"><span data-stu-id="31d96-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="31d96-113">Sadece `IHostEnvironment` `IWebHostEnvironment`, `IConfiguration` , ve enjekte edilebilir.</span><span class="sxs-lookup"><span data-stu-id="31d96-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="31d96-114">Bu değişiklik, tek ton hizmetinin yinelenen oluşturulması gibi DI sorunlarını önler.</span><span class="sxs-lookup"><span data-stu-id="31d96-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31d96-115">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="31d96-115">Version introduced</span></span>

<span data-ttu-id="31d96-116">3,0</span><span class="sxs-lookup"><span data-stu-id="31d96-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="31d96-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="31d96-117">Reason for change</span></span>

<span data-ttu-id="31d96-118">Bu değişiklik, web yığınını genel ana bilgisayar kitaplığı üzerine yeniden platformlandırmanın bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="31d96-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31d96-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="31d96-119">Recommended action</span></span>

<span data-ttu-id="31d96-120">Hizmetleri yöntem `Startup.Configure` imzasına enjekte edin.</span><span class="sxs-lookup"><span data-stu-id="31d96-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="31d96-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="31d96-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="31d96-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="31d96-122">Category</span></span>

<span data-ttu-id="31d96-123">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="31d96-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31d96-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="31d96-124">Affected APIs</span></span>

<span data-ttu-id="31d96-125">None</span><span class="sxs-lookup"><span data-stu-id="31d96-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
