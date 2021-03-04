---
title: ASP.NET MVC ve ASP.NET Core arasındaki yapılandırma farklılıkları
description: Yapılandırma değerleri nasıl depolanır ve ASP.NET ile ASP.NET Core arasında önemli ölçüde değiştirilir. Bu bölüm, ayrıntıları ve ASP.NET 'den ASP.NET Core 'e nasıl geçiş yapılacağını inceler.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 1e8e4d4ac408862f0216a5744476047186222304
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106070"
---
# <a name="configuration-differences-between-aspnet-mvc-and-aspnet-core"></a><span data-ttu-id="02a56-104">ASP.NET MVC ve ASP.NET Core arasındaki yapılandırma farklılıkları</span><span class="sxs-lookup"><span data-stu-id="02a56-104">Configuration differences between ASP.NET MVC and ASP.NET Core</span></span>

<span data-ttu-id="02a56-105">Yapılandırma değerleri nasıl depolanır ve ASP.NET ile ASP.NET Core arasında önemli ölçüde değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-105">How configuration values are stored and read changed dramatically between ASP.NET and ASP.NET Core.</span></span>

## <a name="aspnet-mvc-configuration"></a><span data-ttu-id="02a56-106">ASP.NET MVC yapılandırması</span><span class="sxs-lookup"><span data-stu-id="02a56-106">ASP.NET MVC configuration</span></span>

<span data-ttu-id="02a56-107">ASP.NET uygulamalarında, yapılandırma yerleşik .NET yapılandırma dosyalarını kullanır, uygulama klasöründeki *web.config* ve sunucuda *machine.config* .</span><span class="sxs-lookup"><span data-stu-id="02a56-107">In ASP.NET apps, configuration uses the built-in .NET configuration files, *web.config* in the app folder and *machine.config* on the server.</span></span> <span data-ttu-id="02a56-108">Çoğu ASP.NET MVC ve Web API uygulaması, ayarlarını yapılandırma dosyası `appSettings` veya `connectionStrings` öğelerinde depolar.</span><span class="sxs-lookup"><span data-stu-id="02a56-108">Most ASP.NET MVC and Web API apps store their settings in the configuration file's `appSettings` or `connectionStrings` elements.</span></span> <span data-ttu-id="02a56-109">Bazıları, bir ayarlar sınıfına eşlenemeyen özel yapılandırma bölümleri de kullanır.</span><span class="sxs-lookup"><span data-stu-id="02a56-109">Some also use custom configuration sections that can be mapped to a settings class.</span></span>

<span data-ttu-id="02a56-110">Bir .NET Framework uygulamasındaki yapılandırmaya, sınıfı kullanılarak erişilir `System.Configuration.ConfigurationManager` .</span><span class="sxs-lookup"><span data-stu-id="02a56-110">Configuration in a .NET Framework app is accessed using the `System.Configuration.ConfigurationManager` class.</span></span> <span data-ttu-id="02a56-111">Ne yazık ki bu sınıf yapılandırma öğelerine statik erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="02a56-111">Unfortunately, this class provides static access to the configuration elements.</span></span> <span data-ttu-id="02a56-112">Sonuç olarak, çok az sayıda ASP.NET MVC uygulaması, yapılandırma ayarlarına soyut erişim veya gerektiğinde bunları ekleme eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="02a56-112">As a result, very few ASP.NET MVC apps tend to abstract access to their configuration settings or inject them where needed.</span></span> <span data-ttu-id="02a56-113">Bunun yerine, çoğu .NET Framework uygulama, uygulamanın bir ayarı kullanması için ihtiyaç duyacağı her yerde yapılandırma sistemine doğrudan erişim eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="02a56-113">Instead, most .NET Framework apps tend to directly access the configuration system anywhere the app needs to use a setting.</span></span>

<span data-ttu-id="02a56-114">Tipik ASP.NET MVC yapılandırma erişimi:</span><span class="sxs-lookup"><span data-stu-id="02a56-114">Typical ASP.NET MVC configuration access:</span></span>

```csharp
string connectionString =
    ConfigurationManager.ConnectionStrings["DefaultConnection"]
        .ConnectionString;
```

## <a name="aspnet-core-configuration"></a><span data-ttu-id="02a56-115">ASP.NET Core yapılandırması</span><span class="sxs-lookup"><span data-stu-id="02a56-115">ASP.NET Core configuration</span></span>

<span data-ttu-id="02a56-116">ASP.NET Core uygulamalarda, yapılandırma, yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-116">In ASP.NET Core apps, configuration is, itself, configurable.</span></span> <span data-ttu-id="02a56-117">Ancak, çoğu uygulama Standart proje şablonlarının bir parçası olarak bir dizi varsayılan kümesi kullanır ve bu `ConfigureWebHostDefaults` Yöntem içinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="02a56-117">However, most apps use a set of defaults provided as part of the standard project templates and the `ConfigureWebHostDefaults` method used in them.</span></span> <span data-ttu-id="02a56-118">Varsayılan ayarlar, *üzerindeappsettings.Development.js* gibi ortama özgü dosyalarla *appsettings.jstemel* ayarları geçersiz KıLABILME özelliği ile JSON biçimli dosyaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="02a56-118">The default settings use JSON formatted files, with the ability to override settings in the base *appsettings.json* file with environment-specific files like *appsettings.Development.json*.</span></span> <span data-ttu-id="02a56-119">Ayrıca, varsayılan yapılandırma sistemi, dosya tabanlı tüm ayarları aynı adlandırılmış ayar için mevcut olan herhangi bir ortam değişkeniyle daha da geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="02a56-119">Additionally, the default configuration system further overrides all file-based settings with any environment variable that exists for the same named setting.</span></span> <span data-ttu-id="02a56-120">Bu pek çok senaryoda faydalıdır ve özellikle barındırma ortamına dağıtım yaparken yararlıdır, çünkü yapılandırma dosyalarının dağıtımı, önemli üretim yapılandırma ayarlarının yanlışlıkla üzerine yazılıp yazılmayacağı konusunda endişelenmenize gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="02a56-120">This is useful in many scenarios and is especially useful when deploying to a hosting environment, since it eliminates the need to worry about whether deploying configuration files will accidentally overwrite important production configuration settings.</span></span> <span data-ttu-id="02a56-121">Yapılandırma değerleri, komut satırı bağımsız değişkenleri olarak da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-121">Configuration values can also be provided as command line arguments.</span></span>

<span data-ttu-id="02a56-122">Yapılandırma değerlerine erişim, .NET Core 'da birçok şekilde yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-122">Accessing configuration values can be done in many ways in .NET Core.</span></span> <span data-ttu-id="02a56-123">Bağımlılık ekleme, .NET Core 'da yerleşik olduğundan, yapılandırma değerlerine genellikle gereken sınıflara eklenen bir arabirim üzerinden erişilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-123">Because dependency injection is built into .NET Core, configuration values are generally accessed through an interface that is injected into classes that need them.</span></span> <span data-ttu-id="02a56-124">Bu, gibi bir arabirimi geçirmeyi gerektirebilir <xref:Microsoft.Extensions.Configuration.IConfiguration> , ancak genellikle [Seçenekler modelini](/aspnet/core/fundamentals/configuration/options)kullanarak sınıfın gerektirdiği ayarları geçirmek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="02a56-124">This can involve passing a interface like <xref:Microsoft.Extensions.Configuration.IConfiguration>, but usually it's better to pass just the settings required by the class using the [options pattern](/aspnet/core/fundamentals/configuration/options).</span></span>

<span data-ttu-id="02a56-125">Şekil 2-2 `IConfiguration` ' de bir Razor sayfasına geçme ve yapılandırma ayarlarına erişme işlemlerinin nasıl yapılacağı gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="02a56-125">Figure 2-2 shows how to pass `IConfiguration` into a Razor Page and access configuration settings from it:</span></span>

```csharp
using Microsoft.Extensions.Configuration;

public class TestModel : PageModel
{
    private readonly IConfiguration _configuration;

    public TestModel(IConfiguration configuration)
    {
        _configuration= configuration;
    }

    public ContentResult OnGet()
    {
        var myKeyValue = _configuration["MyKey"];

        // ...
    }
}
```

<span data-ttu-id="02a56-126">**Şekil 2-2.**</span><span class="sxs-lookup"><span data-stu-id="02a56-126">**Figure 2-2.**</span></span> <span data-ttu-id="02a56-127">İle yapılandırma değerlerine erişme `IConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="02a56-127">Accessing configuration values with `IConfiguration`.</span></span>

<span data-ttu-id="02a56-128">Seçenekler modelini kullanarak, ayarlar erişimi benzerdir, ancak, Şekil 2-3 gösterdiği gibi, tüketen sınıf tarafından gerek duyulan ayarlara kesin ve daha belirgin bir şekilde yazılır.</span><span class="sxs-lookup"><span data-stu-id="02a56-128">Using the options pattern, settings access is similar but is strongly typed and more specific to the setting(s) needed by the consuming class, as Figure 2-3 demonstrates.</span></span>

```csharp
public class PositionOptions
{
    public const string Position = nameof(Position);

    public string Title { get; set; }
    public string Name { get; set; }
}

public class Test2Model : PageModel
{
    private readonly PositionOptions _options;

    public Test2Model(IOptions<PositionOptions> options)
    {
        _options = options.Value;
    }

    public ContentResult OnGet()
    {
        return Content($"Title: {_options.Title}\nName: {_options.Name}");
    }
}
```

<span data-ttu-id="02a56-129">**Şekil 2-3.**</span><span class="sxs-lookup"><span data-stu-id="02a56-129">**Figure 2-3.**</span></span> <span data-ttu-id="02a56-130">ASP.NET Core ' de seçenekler deseninin kullanımı.</span><span class="sxs-lookup"><span data-stu-id="02a56-130">Using the options pattern in ASP.NET Core.</span></span>

<span data-ttu-id="02a56-131">Seçenekler deseninin çalışması için, uygulama başlatıldığında seçenekler türü ' de yapılandırılmalıdır `ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="02a56-131">For the options pattern to work, the options type must be configured in `ConfigureServices` when the app starts up:</span></span>

```csharp
// required in ConfigureServices
services.Configure<PositionOptions>(Configuration.GetSection(PositionOptions.Position));
```

## <a name="migrate-configuration"></a><span data-ttu-id="02a56-132">Yapılandırmayı geçir</span><span class="sxs-lookup"><span data-stu-id="02a56-132">Migrate configuration</span></span>

<span data-ttu-id="02a56-133">.NET Framework bir uygulamanın yapılandırma ayarlarının .NET Core 'a nasıl bağlantı noktası alınacağını düşünürken, ilk adım kullanılmakta olan tüm yapılandırma ayarlarını belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="02a56-133">When considering how to port an app's configuration settings from .NET Framework to .NET Core, the first step is to identify all of the configuration settings that are being used.</span></span> <span data-ttu-id="02a56-134">Bunların çoğu, uygulamanın kök klasöründeki *web.config* dosyasında olacaktır, ancak bazı uygulamalar ayarların paylaşılan *machine.config* dosyasında da bulunması beklenir.</span><span class="sxs-lookup"><span data-stu-id="02a56-134">Most of these will be in the *web.config* file in the app's root folder, but some apps expect settings to be found in the shared *machine.config* file as well.</span></span>

<span data-ttu-id="02a56-135">Yapılandırma dosyalarındaki tüm ayarlar kataloglandığında, bir sonraki adım, ayarların uygulamanın kendisinde nerede ve nasıl kullanıldığını belirlemek için olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="02a56-135">Once all settings in the config files have been cataloged, the next step should be to identify where and how the settings are used in the app itself.</span></span> <span data-ttu-id="02a56-136">Bazı ayarlar kullanılmıyorsa, bu büyük olasılıkla geçişten atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-136">If some settings aren't being used, these can probably be omitted from the migration.</span></span> <span data-ttu-id="02a56-137">Her ayar için, kodu geçirdiğinizde herhangi bir şey kaçırmadığınızdan emin olmak için, kullanılmakta olan tüm yerleri göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="02a56-137">For each setting, note all of the places it's being used so you can be sure you don't miss any when you migrate the code.</span></span>

<span data-ttu-id="02a56-138">ASP.NET uygulamasını hala koruyorsanız, statik başvuruların `ConfigurationManager` ve arabirimlerin üzerinden erişime karşı değiştirilmesini önlemeye yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="02a56-138">If you're still maintaining the ASP.NET app, it may be helpful to avoid static references to `ConfigurationManager` and replace them with access through interfaces.</span></span> <span data-ttu-id="02a56-139">Bu, ASP.NET Core yapılandırma sistemine geçişi kolaylaştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="02a56-139">This will ease the transition to ASP.NET Core's configuration system.</span></span> <span data-ttu-id="02a56-140">Genel olarak, dış kaynaklara statik erişim kodun test ve bakımını daha zor hale getirir. bu nedenle, uygulamanın bu kalıbı takip eden bir yerde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="02a56-140">In general, static access to external resources makes code harder to test and maintain, so be on the lookout for anywhere else the app may be following this pattern.</span></span>

## <a name="references"></a><span data-ttu-id="02a56-141">Başvurular</span><span class="sxs-lookup"><span data-stu-id="02a56-141">References</span></span>

- [<span data-ttu-id="02a56-142">ASP.NET Core yapılandırma</span><span class="sxs-lookup"><span data-stu-id="02a56-142">Configuration in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/)
- [<span data-ttu-id="02a56-143">ASP.NET Core'da seçenek deseni</span><span class="sxs-lookup"><span data-stu-id="02a56-143">Options pattern in ASP.NET Core</span></span>](/aspnet/core/fundamentals/configuration/options)
- [<span data-ttu-id="02a56-144">Yapılandırmayı ASP.NET Core geçir</span><span class="sxs-lookup"><span data-stu-id="02a56-144">Migrate configuration to ASP.NET Core</span></span>](/aspnet/core/migration/configuration)
- [<span data-ttu-id="02a56-145">Statik yapılandırma erişimini yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="02a56-145">Refactoring Static Config Access</span></span>](https://ardalis.com/refactoring-static-config-access/)

>[!div class="step-by-step"]
><span data-ttu-id="02a56-146">[Önceki](middleware-modules-handlers.md) 
> [Sonraki](routing-differences.md)</span><span class="sxs-lookup"><span data-stu-id="02a56-146">[Previous](middleware-modules-handlers.md)
[Next](routing-differences.md)</span></span>
