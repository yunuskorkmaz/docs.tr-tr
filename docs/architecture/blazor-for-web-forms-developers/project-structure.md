---
title: Blazor uygulamaları için proje yapısı
description: web formları ve Blazor projelerinin proje yapılarının ASP.NET karşılaştırın.
author: danroth27
ms.author: daroth
ms.date: 09/11/2019
ms.openlocfilehash: 2c383e86ff22f5a3460476998992b66e9417cc11
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401580"
---
# <a name="project-structure-for-blazor-apps"></a><span data-ttu-id="4ecb1-103">Blazor uygulamaları için proje yapısı</span><span class="sxs-lookup"><span data-stu-id="4ecb1-103">Project structure for Blazor apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="4ecb1-104">Önemli proje yapısı farklılıklarına rağmen, ASP.NET Web Formları ve Blazor benzer birçok kavramı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="4ecb1-105">Burada, bir Blazor projesinin yapısına bakacağız ve bunu ASP.NET web formları projesiyle karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="4ecb1-106">İlk Blazor uygulamanızı oluşturmak için, [Blazor'un başlangıç adımlarını](/aspnet/core/blazor/get-started)takip edin.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="4ecb1-107">Bir Blazor Server uygulaması veya ASP.NET Core'da barındırılan bir Blazor WebAssembly uygulaması oluşturmak için yönergeleri izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="4ecb1-108">Barındırma modeline özgü mantık dışında, her iki projedeki kodun çoğu aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="4ecb1-109">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="4ecb1-109">Project file</span></span>

<span data-ttu-id="4ecb1-110">Blazor Server uygulamaları .NET Core projeleridir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-110">Blazor Server apps are .NET Core projects.</span></span> <span data-ttu-id="4ecb1-111">Blazor Server uygulaması nın proje dosyası alabildiği kadar basittir:</span><span class="sxs-lookup"><span data-stu-id="4ecb1-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="4ecb1-112">Blazor WebAssembly uygulaması için proje dosyası biraz daha ilgili görünüyor (tam sürüm numaraları değişebilir):</span><span class="sxs-lookup"><span data-stu-id="4ecb1-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <RazorLangVersion>3.0</RazorLangVersion>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Blazor" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.Build" Version="3.1.0" PrivateAssets="all" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.HttpClient" Version="3.1.0" />
    <PackageReference Include="Microsoft.AspNetCore.Blazor.DevServer" Version="3.1.0" PrivateAssets="all" />
  </ItemGroup>

  <ItemGroup>
    <ProjectReference Include="..\Shared\BlazorWebAssemblyApp1.Shared.csproj" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="4ecb1-113">Blazor WebAssembly projeleri ,NET Core yerine .NET Standard'ı hedefler, çünkü tarayıcıda WebAssembly tabanlı .NET çalışma zamanında çalışırlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-113">Blazor WebAssembly projects target .NET Standard instead of .NET Core because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="4ecb1-114">.NET'i bir sunucu veya geliştirici makinesinde yaptığınız gibi bir web tarayıcısına yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="4ecb1-115">Sonuç olarak, proje tek tek paket referansları kullanarak Blazor çerçevesine başvurur.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="4ecb1-116">Buna karşılık, varsayılan bir ASP.NET Web Forms *projesi,.csproj* dosyasında neredeyse 300 XML satırı içerir ve bunların çoğu projedeki çeşitli kod ve içerik dosyalarını açıkça listeler.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="4ecb1-117">.NET Core ve .NET Standart tabanlı projelerdeki basitleştirmelerin çoğu, genellikle yalnızca Web SDK `Microsoft.NET.Sdk.Web` olarak adlandırılan SDK'ya başvurarak içe aktarılan varsayılan hedefler ve özelliklerden gelir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-117">Many of the simplifications in the .NET Core- and .NET Standard-based projects come from the default targets and properties imported by referencing the `Microsoft.NET.Sdk.Web` SDK, often referred to as simply the Web SDK.</span></span> <span data-ttu-id="4ecb1-118">Web SDK, projeye kod ve içerik dosyalarının eklenmesini kolaylaştıran joker karakterler ve diğer kolaylıklar içerir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-118">The Web SDK includes wildcards and other conveniences that simplify inclusion of code and content files in the project.</span></span> <span data-ttu-id="4ecb1-119">Dosyaları açıkça listelamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-119">You don't need to list the files explicitly.</span></span> <span data-ttu-id="4ecb1-120">.NET Core'u hedef alırken, Web SDK hem .NET Core hem de ASP.NET Core paylaşılan çerçevelerine çerçeve referansları ekler.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-120">When targeting .NET Core, the Web SDK also adds framework references to both the .NET Core and ASP.NET Core shared frameworks.</span></span> <span data-ttu-id="4ecb1-121">**Çerçeveler, Çözüm Gezgini** penceresindeki **Bağımlılıklar** > **Çerçeveleri** düğümünden görülebilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-121">The frameworks are visible from the **Dependencies** > **Frameworks** node in the **Solution Explorer** window.</span></span> <span data-ttu-id="4ecb1-122">Paylaşılan çerçeveler, .NET Core'u yüklerken makineye yüklenen derlemekoleksiyonlarıdır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-122">The shared frameworks are collections of assemblies that were installed on the machine when installing .NET Core.</span></span>

<span data-ttu-id="4ecb1-123">Desteklenmelerine rağmen, tek tek derleme başvuruları .NET Core projelerinde daha az yaygındır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-123">Although they're supported, individual assembly references are less common in .NET Core projects.</span></span> <span data-ttu-id="4ecb1-124">Çoğu proje bağımlılığı NuGet paket başvuruları olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-124">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="4ecb1-125">Sadece .NET Core projelerinde üst düzey paket bağımlılıklarına başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-125">You only need to reference top-level package dependencies in .NET Core projects.</span></span> <span data-ttu-id="4ecb1-126">Geçişli bağımlılıklar otomatik olarak dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-126">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="4ecb1-127">Paketleri referans ASP.NET Web Formlar projelerinde yaygın olarak bulunan *packages.config* dosyasını kullanmak yerine, `<PackageReference>` paket başvuruları öğe kullanılarak proje dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-127">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="4ecb1-128">Giriş noktası</span><span class="sxs-lookup"><span data-stu-id="4ecb1-128">Entry point</span></span>

<span data-ttu-id="4ecb1-129">Blazor Server uygulamasının giriş noktası, konsol uygulamasında gördüğünüz gibi *Program.cs* dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-129">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="4ecb1-130">Uygulama yürütüldüğünde, web uygulamalarına özgü varsayılanları kullanarak bir web barındırma örneği oluşturur ve çalıştırZ.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-130">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="4ecb1-131">Web barındırma, Blazor Server uygulamasının yaşam döngüsünü yönetir ve ana bilgisayar düzeyinde hizmetler kurar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-131">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="4ecb1-132">Bu tür hizmetlere örnek olarak yapılandırma, günlüğe kaydetme, bağımlılık enjeksiyonu ve HTTP sunucusu verilebilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-132">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="4ecb1-133">Bu kod çoğunlukla ortak ve genellikle değişmeden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-133">This code is mostly boilerplate and is often left unchanged.</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureWebHostDefaults(webBuilder =>
            {
                webBuilder.UseStartup<Startup>();
            });
}
```

<span data-ttu-id="4ecb1-134">Blazor WebAssembly uygulamaları da *Program.cs*bir giriş noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-134">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="4ecb1-135">Kod biraz farklı görünüyor.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-135">The code looks slightly different.</span></span> <span data-ttu-id="4ecb1-136">Kod, uygulama nın ana bilgisayara aynı ana bilgisayar düzeyindeki hizmetleri sağlamak üzere uygulama ana bilgisayarını ayarlaması açısından benzer.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-136">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="4ecb1-137">Ancak, WebAssembly uygulama ana bilgisayarı doğrudan tarayıcıda yürütüldettiği için bir HTTP sunucusu ayarlamaz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-137">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="4ecb1-138">Blazor uygulamaları, `Startup` uygulamanın başlangıç mantığını tanımlamak için *Global.asax* dosyası yerine bir sınıfa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-138">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="4ecb1-139">Sınıf, `Startup` uygulamayı ve uygulamaya özel hizmetleri yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-139">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="4ecb1-140">Blazor Server uygulamasında sınıf, `Startup` Blazor'un istemci tarayıcılar ve sunucu arasında kullandığı gerçek zamanlı bağlantı için bitiş noktasını ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-140">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="4ecb1-141">Blazor WebAssembly uygulamasında, `Startup` sınıf uygulamanın kök bileşenlerini ve bunların nerede işlenmesi gerektiğini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-141">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="4ecb1-142">[App başlangıç](./app-startup.md) bölümündeki sınıfa `Startup` daha derinlemesine bakacağız.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-142">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="4ecb1-143">Statik dosyalar</span><span class="sxs-lookup"><span data-stu-id="4ecb1-143">Static files</span></span>

<span data-ttu-id="4ecb1-144">Web Formları ASP.NET projelerinaksine, Blazor projesindeki tüm dosyalar statik dosya olarak istenemez.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-144">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="4ecb1-145">Yalnızca *wwwroot* klasöründeki dosyalar web adresine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-145">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="4ecb1-146">Bu klasör, uygulamanın "web kökü" olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-146">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="4ecb1-147">Uygulamanın web kökünün dışındaki hiçbir şey web adresine bağlı *değildir.*</span><span class="sxs-lookup"><span data-stu-id="4ecb1-147">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="4ecb1-148">Bu kurulum, proje dosyalarının web üzerinde yanlışlıkla açığa çıkarılmasını engelleyen ek bir güvenlik düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-148">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="4ecb1-149">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="4ecb1-149">Configuration</span></span>

<span data-ttu-id="4ecb1-150">ASP.NET Web Formları uygulamalarındaki yapılandırma genellikle bir veya daha fazla *web.config* dosyası kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-150">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="4ecb1-151">Blazor uygulamaları genellikle *web.config* dosyaları yok.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-151">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="4ecb1-152">Bunu yaparlarsa, dosya yalnızca IIS'de barındırıldığında IIS'ye özgü ayarları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-152">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="4ecb1-153">Bunun yerine, Blazor Server uygulamaları ASP.NET Core yapılandırma soyutlamalarını kullanır (Blazor WebAssembly uygulamaları şu anda aynı yapılandırma soyutlamalarını desteklemez, ancak bu gelecekte eklenen bir özellik olabilir).</span><span class="sxs-lookup"><span data-stu-id="4ecb1-153">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="4ecb1-154">Örneğin, varsayılan Blazor Server uygulaması bazı ayarları *appsettings.json'da*depolar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-154">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="4ecb1-155">[Yapılandırma](./config.md) bölümünde ASP.NET Core projelerinde yapılandırma hakkında daha fazla bilgi edineceğiz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-155">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="4ecb1-156">Jilet bileşenleri</span><span class="sxs-lookup"><span data-stu-id="4ecb1-156">Razor components</span></span>

<span data-ttu-id="4ecb1-157">Blazor projelerindeki dosyaların çoğu *jiletli* dosyalardır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-157">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="4ecb1-158">Razor, html ve C# tabanlı, dinamik olarak web ui oluşturmak için kullanılan cazip bir dildir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-158">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="4ecb1-159">*.razor* dosyaları, uygulamanın ui'sini oluşturan bileşenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-159">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="4ecb1-160">Çoğunlukla, bileşenler hem Blazor Server hem de Blazor WebAssembly uygulamaları için aynıdır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-160">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="4ecb1-161">Blazor'daki bileşenler, ASP.NET Web Formlar'daki kullanıcı denetimlerine benzer.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-161">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="4ecb1-162">Her Razor bileşen dosyası, proje oluşturulurken bir .NET sınıfına derlenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-162">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="4ecb1-163">Oluşturulan sınıf bileşenin durumunu yakalar, oluşturma mantığı, yaşam döngüsü yöntemleri, olay işleyicileri ve diğer mantık.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-163">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="4ecb1-164">[Blazor bölümüyle yeniden kullanılabilir UI bileşenlerinin binadaki](./components.md) bileşenleri yazmaya bakacağız.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-164">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="4ecb1-165">*_Imports.jilet* dosyaları Razor bileşen dosyaları değildir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-165">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="4ecb1-166">Bunun yerine, aynı klasör içinde ve alt klasörlerinde diğer *.razor* dosyalarına içe aktarılan bir dizi Razor yönergeleri tanımlarlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-166">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="4ecb1-167">Örneğin, *_Imports.razor* dosyası, yaygın olarak `using` kullanılan ad alanları için deyim eklemenin geleneksel bir yoludur:</span><span class="sxs-lookup"><span data-stu-id="4ecb1-167">For example, a *_Imports.razor* file is a conventional way to add `using` statements for commonly used namespaces:</span></span>

```razor
@using System.Net.Http
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.Forms
@using Microsoft.AspNetCore.Components.Routing
@using Microsoft.AspNetCore.Components.Web
@using Microsoft.JSInterop
@using BlazorApp1
@using BlazorApp1.Shared
```

## <a name="pages"></a><span data-ttu-id="4ecb1-168">Sayfalar</span><span class="sxs-lookup"><span data-stu-id="4ecb1-168">Pages</span></span>

<span data-ttu-id="4ecb1-169">Blazor uygulamalarındaki sayfalar nerede?</span><span class="sxs-lookup"><span data-stu-id="4ecb1-169">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="4ecb1-170">Blazor, ASP.NET Web Forms uygulamalarındaki *.aspx* dosyaları gibi adreslenebilir sayfalar için ayrı bir dosya uzantısı tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-170">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="4ecb1-171">Bunun yerine, sayfalar bileşenlere rotalar atayarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-171">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="4ecb1-172">Rota genellikle Razor yönergesi `@page` kullanılarak atanır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-172">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="4ecb1-173">Örneğin, `Counter` *Pages/Counter.razor* dosyasında yazılan bileşen aşağıdaki yolu tanımlar:</span><span class="sxs-lookup"><span data-stu-id="4ecb1-173">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="4ecb1-174">Blazor'da yönlendirme istemci tarafından işlenir, sunucuda değil.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-174">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="4ecb1-175">Kullanıcı tarayıcıda gezinirken, Blazor gezinmeyi yakalar ve bileşeni eşleşen rotayla işler.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-175">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="4ecb1-176">Bileşen yolları şu anda bileşenin dosya konumu tarafından *.aspx* sayfalarında olduğu gibi çıkarılmaz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-176">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="4ecb1-177">Bu özellik gelecekte eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-177">This feature may be added in the future.</span></span> <span data-ttu-id="4ecb1-178">Her rota bileşenüzerinde açıkça belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-178">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="4ecb1-179">Routable bileşenlerinin *Sayfalar* klasöründe saklanması özel bir anlam ifade etmez ve tamamen bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-179">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="4ecb1-180">Blazor'da [Sayfalar, yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde yönlendirmeyi daha ayrıntılı olarak inceeceğiz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-180">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="4ecb1-181">Düzen</span><span class="sxs-lookup"><span data-stu-id="4ecb1-181">Layout</span></span>

<span data-ttu-id="4ecb1-182">ASP.NET Web Formları uygulamalarında, ortak sayfa düzeni ana sayfalar *(Site.Master)* kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-182">In ASP.NET Web Forms apps, common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="4ecb1-183">Blazor uygulamalarında, sayfa düzeni mizanpaj bileşenleri *(Shared/MainLayout.razor)* kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-183">In Blazor apps, page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="4ecb1-184">Düzen bileşenleri [Sayfa, yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde daha ayrıntılı olarak ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-184">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-blazor"></a><span data-ttu-id="4ecb1-185">Bootstrap Blazor</span><span class="sxs-lookup"><span data-stu-id="4ecb1-185">Bootstrap Blazor</span></span>

<span data-ttu-id="4ecb1-186">Blazor'u tuzağa düşürmek için uygulamanın şunları yapması gerekir:</span><span class="sxs-lookup"><span data-stu-id="4ecb1-186">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="4ecb1-187">Sayfada kök bileşenin *(App.Razor)* nerede işlenmesi gerektiğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-187">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="4ecb1-188">İlgili Blazor çerçeve komut dosyasını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-188">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="4ecb1-189">Blazor Server uygulamasında, kök bileşenin ana sayfası *_Host.cshtml* dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-189">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="4ecb1-190">Bu dosya bir bileşen değil, bir Razor Page tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-190">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="4ecb1-191">Razor Pages, sunucu adreslenebilir bir sayfa tanımlamak için Razor sözdizimini kullanır, tıpkı *.aspx* sayfasına çok benzer.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-191">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="4ecb1-192">Yöntem, `Html.RenderComponentAsync<TComponent>(RenderMode)` kök düzeyindebir bileşenin nerede işlenmesi gerektiğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-192">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="4ecb1-193">Seçenek, `RenderMode` bileşenin nasıl işlenmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-193">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="4ecb1-194">Aşağıdaki tabloda desteklenen `RenderMode` seçenekler sıralanır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-194">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="4ecb1-195">Seçenek</span><span class="sxs-lookup"><span data-stu-id="4ecb1-195">Option</span></span>                        |<span data-ttu-id="4ecb1-196">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ecb1-196">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="4ecb1-197">Tarayıcı ile bağlantı kurulduktan sonra etkileşimli olarak işlenir</span><span class="sxs-lookup"><span data-stu-id="4ecb1-197">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="4ecb1-198">Önce önceden işlenmiş ve daha sonra etkileşimli olarak işlenmiş</span><span class="sxs-lookup"><span data-stu-id="4ecb1-198">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="4ecb1-199">Statik içerik olarak işlenir</span><span class="sxs-lookup"><span data-stu-id="4ecb1-199">Rendered as static content</span></span>|

<span data-ttu-id="4ecb1-200">*_framework/blazor.server.js* komut dosyası başvurusu sunucuile gerçek zamanlı bağlantı kurar ve ardından tüm kullanıcı etkileşimleri ve Kullanıcı Arabirimi güncelleştirmeleri ile ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-200">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

```razor
@page "/"
@namespace BlazorApp1.Pages
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>BlazorApp1</title>
    <base href="~/" />
    <link rel="stylesheet" href="css/bootstrap/bootstrap.min.css" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>
        @(await Html.RenderComponentAsync<App>(RenderMode.ServerPrerendered))
    </app>

    <script src="_framework/blazor.server.js"></script>
</body>
</html>
```

<span data-ttu-id="4ecb1-201">Blazor WebAssembly uygulamasında, ana sayfa *wwwroot/index.html*altında basit bir statik HTML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-201">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="4ecb1-202">Öğe, `<app>` kök bileşenin nerede işlenmesi gerektiğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-202">The `<app>` element is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/site.css" rel="stylesheet" />
</head>
<body>
    <app>Loading...</app>

    <script src="_framework/blazor.webassembly.js"></script>
</body>
</html>
```

<span data-ttu-id="4ecb1-203">İşlenecek belirli bileşen, bileşenin nerede `Startup.Configure` işlenmesi gerektiğini belirten ilgili bir CSS seçiciyle uygulama yönteminde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-203">The specific component to render is configured in the app's `Startup.Configure` method with a corresponding CSS selector indicating where the component should be rendered.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
    }

    public void Configure(IComponentsApplicationBuilder app)
    {
        app.AddComponent<App>("app");
    }
}
```

## <a name="build-output"></a><span data-ttu-id="4ecb1-204">Üretim oluşturma</span><span class="sxs-lookup"><span data-stu-id="4ecb1-204">Build output</span></span>

<span data-ttu-id="4ecb1-205">Bir Blazor projesi inşa edildiğinde, tüm Razor bileşeni ve kod dosyaları tek bir derlemede derlenir.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-205">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="4ecb1-206">Web Formları projelerinin ASP.NET aksine Blazor, Web-oğlık mantığı mantığının çalışma zamanı derlemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-206">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="4ecb1-207">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="4ecb1-207">Run the app</span></span>

<span data-ttu-id="4ecb1-208">Blazor Server uygulamasını çalıştırmak `F5` için Visual Studio'ya basın.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-208">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="4ecb1-209">Blazor uygulamaları çalışma zamanı derlemeyi desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-209">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="4ecb1-210">Kod ve bileşen biçimlendirme değişikliklerinin sonuçlarını görmek için, hata ayıklayıcı ekli uygulamayı yeniden oluşturup yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-210">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="4ecb1-211">Hata ayıklama ekli olmadan çalıştırırsanız (`Ctrl+F5`), Visual Studio dosya değişiklikleri için saatler ve değişiklikler yapılırken uygulamayı yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-211">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="4ecb1-212">Değişiklikler yapıldıkça tarayıcıyı el ile yenilersiniz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-212">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="4ecb1-213">Blazor WebAssembly uygulamasını çalıştırmak için aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="4ecb1-213">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="4ecb1-214">İstemci projesini doğrudan geliştirme sunucusunu kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-214">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="4ecb1-215">uygulamayı ASP.NET Core ile barındırırken sunucu projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-215">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="4ecb1-216">Blazor WebAssembly uygulamaları Visual Studio kullanarak hata ayıklama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-216">Blazor WebAssembly apps don't support debugging using Visual Studio.</span></span> <span data-ttu-id="4ecb1-217">Uygulamayı çalıştırmak için, `Ctrl+F5` `F5`".</span><span class="sxs-lookup"><span data-stu-id="4ecb1-217">To run the app, use `Ctrl+F5` instead of `F5`.</span></span> <span data-ttu-id="4ecb1-218">Bunun yerine Blazor WebAssembly uygulamalarını doğrudan tarayıcıda hata ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-218">You can instead debug Blazor WebAssembly apps directly in the browser.</span></span> <span data-ttu-id="4ecb1-219">Ayrıntılar için [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4ecb1-219">See [Debug ASP.NET Core Blazor](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4ecb1-220">[Önceki](hosting-models.md)
>[Sonraki](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="4ecb1-220">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
