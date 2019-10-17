---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394306"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="6737c-101">Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar</span><span class="sxs-lookup"><span data-stu-id="6737c-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="6737c-102">Genel ana bilgisayarın `Startup` sınıf oluşturucu ekleme için desteklediği tek türler `IHostEnvironment`, `IWebHostEnvironment` ve `IConfiguration` ' tür.</span><span class="sxs-lookup"><span data-stu-id="6737c-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="6737c-103">@No__t-0 kullanan uygulamalar etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="6737c-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6737c-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6737c-104">Change description</span></span>

<span data-ttu-id="6737c-105">ASP.NET Core 3,0 ' dan önce, Oluşturucu Ekleme `Startup` sınıfının oluşturucusunda rastgele türler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6737c-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="6737c-106">ASP.NET Core 3,0 ' de, Web yığını genel ana bilgisayar kitaplığı üzerine oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="6737c-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="6737c-107">Şablonların *program.cs* dosyasında değişikliği görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="6737c-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="6737c-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="6737c-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="6737c-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="6737c-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="6737c-110">`Host`, uygulamayı derlemek için bir bağımlılık ekleme (dı) kapsayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6737c-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="6737c-111">`WebHost` iki kapsayıcı kullanır: biri konak ve uygulama için bir tane.</span><span class="sxs-lookup"><span data-stu-id="6737c-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="6737c-112">Sonuç olarak, `Startup` Oluşturucusu artık özel hizmet ekleme işlemini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="6737c-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="6737c-113">Yalnızca `IHostEnvironment`, `IWebHostEnvironment` ve `IConfiguration` eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="6737c-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="6737c-114">Bu değişiklik, tek bir hizmetin yinelenen olarak oluşturulması gibi diğer sorunları önler.</span><span class="sxs-lookup"><span data-stu-id="6737c-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6737c-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6737c-115">Version introduced</span></span>

<span data-ttu-id="6737c-116">3.0</span><span class="sxs-lookup"><span data-stu-id="6737c-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6737c-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="6737c-117">Reason for change</span></span>

<span data-ttu-id="6737c-118">Bu değişiklik, Web yığınını genel ana bilgisayar kitaplığı üzerinde oluşturan bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="6737c-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6737c-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6737c-119">Recommended action</span></span>

<span data-ttu-id="6737c-120">@No__t-0 Yöntem imzasına hizmet ekleme.</span><span class="sxs-lookup"><span data-stu-id="6737c-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="6737c-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6737c-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="6737c-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="6737c-122">Category</span></span>

<span data-ttu-id="6737c-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6737c-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6737c-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6737c-124">Affected APIs</span></span>

<span data-ttu-id="6737c-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="6737c-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
