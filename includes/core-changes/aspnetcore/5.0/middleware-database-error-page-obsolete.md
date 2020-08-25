---
ms.openlocfilehash: f1129500c9b779256b2650fe6fa855152cb3ae80
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811293"
---
### <a name="middleware-database-error-page-marked-as-obsolete"></a><span data-ttu-id="3780d-101">Ara yazılım: veritabanı hatası sayfası eski olarak işaretlendi</span><span class="sxs-lookup"><span data-stu-id="3780d-101">Middleware: Database error page marked as obsolete</span></span>

<span data-ttu-id="3780d-102">[Databaseerrorpageara yazılımı](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) ve ilişkili uzantı yöntemleri ASP.NET Core 5,0 ' de kullanılmıyor olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="3780d-102">The [DatabaseErrorPageMiddleware](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0) and its associated extension methods were marked as obsolete in ASP.NET Core 5.0.</span></span> <span data-ttu-id="3780d-103">Ara yazılım ve uzantı yöntemleri ASP.NET Core 6,0 ' de kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="3780d-103">The middleware and extension methods will be removed in ASP.NET Core 6.0.</span></span> <span data-ttu-id="3780d-104">Bu işlevsellik, `DatabaseDeveloperPageExceptionFilter` ve uzantı yöntemleri tarafından sağlanacak.</span><span class="sxs-lookup"><span data-stu-id="3780d-104">The functionality will instead be provided by `DatabaseDeveloperPageExceptionFilter` and its extension methods.</span></span>

<span data-ttu-id="3780d-105">Tartışma için, [DotNet/aspnetcore # 24987](https://github.com/dotnet/aspnetcore/issues/24987)konumundaki GitHub sorununa bakın.</span><span class="sxs-lookup"><span data-stu-id="3780d-105">For discussion, see the GitHub issue at [dotnet/aspnetcore#24987](https://github.com/dotnet/aspnetcore/issues/24987).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3780d-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3780d-106">Version introduced</span></span>

<span data-ttu-id="3780d-107">5,0 RC 1</span><span class="sxs-lookup"><span data-stu-id="3780d-107">5.0 RC 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3780d-108">Eski davranış</span><span class="sxs-lookup"><span data-stu-id="3780d-108">Old behavior</span></span>

<span data-ttu-id="3780d-109">`DatabaseErrorPageMiddleware` ve ilişkili uzantı yöntemleri artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3780d-109">`DatabaseErrorPageMiddleware` and its associated extension methods weren't obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3780d-110">Yeni davranış</span><span class="sxs-lookup"><span data-stu-id="3780d-110">New behavior</span></span>

<span data-ttu-id="3780d-111">`DatabaseErrorPageMiddleware` ve ilişkili genişletme yöntemleri artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3780d-111">`DatabaseErrorPageMiddleware` and its associated extension methods are obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3780d-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3780d-112">Reason for change</span></span>

<span data-ttu-id="3780d-113">`DatabaseErrorPageMiddleware`[Geliştirici özel durum sayfası](/aspnet/core/fundamentals/error-handling#developer-exception-page)için GENIŞLETILEBILIR bir API 'ye geçirildi.</span><span class="sxs-lookup"><span data-stu-id="3780d-113">`DatabaseErrorPageMiddleware` was migrated to an extensible API for the [developer exception page](/aspnet/core/fundamentals/error-handling#developer-exception-page).</span></span> <span data-ttu-id="3780d-114">Genişletilebilir API hakkında daha fazla bilgi için bkz. GitHub sorunu [DotNet/aspnetcore # 8536](https://github.com/dotnet/aspnetcore/issues/8536).</span><span class="sxs-lookup"><span data-stu-id="3780d-114">For more information on the extensible API, see GitHub issue [dotnet/aspnetcore#8536](https://github.com/dotnet/aspnetcore/issues/8536).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3780d-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3780d-115">Recommended action</span></span>

<span data-ttu-id="3780d-116">Aşağıdaki adımları tamamlayın:</span><span class="sxs-lookup"><span data-stu-id="3780d-116">Complete the following steps:</span></span>

1. <span data-ttu-id="3780d-117">Projenizde kullanmayı durdurun `DatabaseErrorPageMiddleware` .</span><span class="sxs-lookup"><span data-stu-id="3780d-117">Stop using `DatabaseErrorPageMiddleware` in your project.</span></span> <span data-ttu-id="3780d-118">Örneğin, `UseDatabaseErrorPage` öğesinden yöntem çağrısını kaldırın `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="3780d-118">For example, remove the `UseDatabaseErrorPage` method call from `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDatabaseErrorPage();
        }
    }
    ```

1. <span data-ttu-id="3780d-119">Geliştirici özel durum sayfasını projenize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3780d-119">Add the developer exception page to your project.</span></span> <span data-ttu-id="3780d-120">Örneğin, <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> içinde yöntemini çağırın `Startup.Configure` :</span><span class="sxs-lookup"><span data-stu-id="3780d-120">For example, call the <xref:Microsoft.AspNetCore.Builder.DeveloperExceptionPageExtensions.UseDeveloperExceptionPage%2A> method in `Startup.Configure`:</span></span>

    ```csharp
    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        if (env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
    }
    ```

1. <span data-ttu-id="3780d-121">Veritabanı Geliştirici sayfası özel durum filtresini hizmetler koleksiyonuna ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3780d-121">Add the database developer page exception filter to the services collection.</span></span> <span data-ttu-id="3780d-122">Örneğin, `AddDatabaseDeveloperPageExceptionFilter` içinde yöntemini çağırın `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="3780d-122">For example, call the `AddDatabaseDeveloperPageExceptionFilter` method in `Startup.ConfigureServices`:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddDatabaseDeveloperPageExceptionFilter();
    }
    ```

#### <a name="category"></a><span data-ttu-id="3780d-123">Kategori</span><span class="sxs-lookup"><span data-stu-id="3780d-123">Category</span></span>

<span data-ttu-id="3780d-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3780d-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3780d-125">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3780d-125">Affected APIs</span></span>

- [<span data-ttu-id="3780d-126">Microsoft. AspNetCore. Builder. DatabaseErrorPageExtensions. UseDatabaseErrorPage</span><span class="sxs-lookup"><span data-stu-id="3780d-126">Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage</span></span>](/dotnet/api/microsoft.aspnetcore.builder.databaseerrorpageextensions.usedatabaseerrorpage?view=aspnetcore-3.0)
- [<span data-ttu-id="3780d-127">Microsoft. AspNetCore. Diagnostics. EntityFrameworkCore. Databaseerrorpageara yazılımı</span><span class="sxs-lookup"><span data-stu-id="3780d-127">Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware</span></span>](/dotnet/api/microsoft.aspnetcore.diagnostics.entityframeworkcore.databaseerrorpagemiddleware?view=aspnetcore-3.0)

<!-- 

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.DatabaseErrorPageExtensions.UseDatabaseErrorPage`
- `T:Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore.DatabaseErrorPageMiddleware`

-->
