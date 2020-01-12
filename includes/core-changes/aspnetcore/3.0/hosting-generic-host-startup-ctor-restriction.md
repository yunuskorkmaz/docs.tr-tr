---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901609"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="f520e-101">Barındırma: genel ana bilgisayar, başlangıç Oluşturucu ekleme işlemini kısıtlar</span><span class="sxs-lookup"><span data-stu-id="f520e-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="f520e-102">Genel ana bilgisayarın `Startup` sınıf oluşturucu ekleme için desteklediği tek tür `IHostEnvironment`, `IWebHostEnvironment`ve `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f520e-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="f520e-103">`WebHost` kullanan uygulamalar etkilenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="f520e-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f520e-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f520e-104">Change description</span></span>

<span data-ttu-id="f520e-105">ASP.NET Core 3,0 ' dan önce, Oluşturucu Ekleme `Startup` sınıfının oluşturucusunda rastgele türler için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f520e-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="f520e-106">ASP.NET Core 3,0 ' de, Web yığını genel ana bilgisayar kitaplığı üzerine oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="f520e-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="f520e-107">Şablonların *program.cs* dosyasında değişikliği görebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f520e-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="f520e-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="f520e-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="f520e-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="f520e-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="f520e-110">`Host`, uygulamayı derlemek için bir bağımlılık ekleme (dı) kapsayıcısı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f520e-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="f520e-111">`WebHost` iki kapsayıcı kullanır: biri konak ve uygulama için bir tane.</span><span class="sxs-lookup"><span data-stu-id="f520e-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="f520e-112">Sonuç olarak, `Startup` Oluşturucusu artık özel hizmet ekleme işlemini desteklememektedir.</span><span class="sxs-lookup"><span data-stu-id="f520e-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="f520e-113">Yalnızca `IHostEnvironment`, `IWebHostEnvironment`ve `IConfiguration` eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f520e-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="f520e-114">Bu değişiklik, tek bir hizmetin yinelenen olarak oluşturulması gibi diğer sorunları önler.</span><span class="sxs-lookup"><span data-stu-id="f520e-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f520e-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f520e-115">Version introduced</span></span>

<span data-ttu-id="f520e-116">3.0</span><span class="sxs-lookup"><span data-stu-id="f520e-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f520e-117">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f520e-117">Reason for change</span></span>

<span data-ttu-id="f520e-118">Bu değişiklik, Web yığınını genel ana bilgisayar kitaplığı üzerinde oluşturan bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="f520e-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f520e-119">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f520e-119">Recommended action</span></span>

<span data-ttu-id="f520e-120">`Startup.Configure` yöntemi imzasına hizmet ekleme.</span><span class="sxs-lookup"><span data-stu-id="f520e-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="f520e-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="f520e-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="f520e-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="f520e-122">Category</span></span>

<span data-ttu-id="f520e-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f520e-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f520e-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f520e-124">Affected APIs</span></span>

<span data-ttu-id="f520e-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="f520e-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
