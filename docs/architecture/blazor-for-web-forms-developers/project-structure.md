---
title: Uygulamalar için proje yapısı Blazor
description: ASP.NET Web Forms ve projelerinin proje yapılarının nasıl Blazor karşılaştırılacağını öğrenin.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
- WebAssembly
ms.date: 11/20/2020
ms.openlocfilehash: d91430eb654ee16934408bf064803b34ca700640
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509812"
---
# <a name="project-structure-for-no-locblazor-apps"></a><span data-ttu-id="0f5d2-103">Uygulamalar için proje yapısı Blazor</span><span class="sxs-lookup"><span data-stu-id="0f5d2-103">Project structure for Blazor apps</span></span>

<span data-ttu-id="0f5d2-104">Önemli proje yapısı farklılıklarına rağmen, ASP.NET Web Forms ve Blazor birçok benzer kavramı paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-104">Despite their significant project structure differences, ASP.NET Web Forms and Blazor share many similar concepts.</span></span> <span data-ttu-id="0f5d2-105">Burada, bir projenin yapısına bakacağız Blazor ve bunu bir ASP.NET Web Forms projesiyle karşılaştıracağız.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-105">Here, we'll look at the structure of a Blazor project and compare it to an ASP.NET Web Forms project.</span></span>

<span data-ttu-id="0f5d2-106">İlk uygulamanızı oluşturmak için Blazor [ Blazor Başlarken adımlarında](/aspnet/core/blazor/get-started)bulunan yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-106">To create your first Blazor app, follow the instructions in the [Blazor getting started steps](/aspnet/core/blazor/get-started).</span></span> <span data-ttu-id="0f5d2-107">Bir Blazor sunucu uygulaması veya Blazor ASP.NET Core barındırılan bir uygulama oluşturmak için yönergeleri takip edebilirsiniz WebAssembly .</span><span class="sxs-lookup"><span data-stu-id="0f5d2-107">You can follow the instructions to create either a Blazor Server app or a Blazor WebAssembly app hosted in ASP.NET Core.</span></span> <span data-ttu-id="0f5d2-108">Barındırma modeline özgü mantık dışında, her iki projedeki kodun çoğu aynıdır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-108">Except for the hosting model-specific logic, most of the code in both projects is the same.</span></span>

## <a name="project-file"></a><span data-ttu-id="0f5d2-109">Proje dosyası</span><span class="sxs-lookup"><span data-stu-id="0f5d2-109">Project file</span></span>

<span data-ttu-id="0f5d2-110">Blazor Sunucu uygulamaları .NET projelerdir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-110">Blazor Server apps are .NET projects.</span></span> <span data-ttu-id="0f5d2-111">Sunucu uygulamasının proje dosyası, Blazor Şu kadar basit bir işlemdir:</span><span class="sxs-lookup"><span data-stu-id="0f5d2-111">The project file for the Blazor Server app is about as simple as it can get:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="0f5d2-112">Uygulamanın proje dosyası Blazor WebAssembly biraz daha fazla görünür (tam sürüm numaraları farklılık gösterebilir):</span><span class="sxs-lookup"><span data-stu-id="0f5d2-112">The project file for a Blazor WebAssembly app looks slightly more involved (exact version numbers may vary):</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">

  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly" Version="5.0.0" />
    <PackageReference Include="Microsoft.AspNetCore.Components.WebAssembly.DevServer" Version="5.0.0" PrivateAssets="all" />
    <PackageReference Include="System.Net.Http.Json" Version="5.0.0" />
  </ItemGroup>

</Project>
```

<span data-ttu-id="0f5d2-113">BlazorWebAssembly `Microsoft.NET.Sdk.BlazorWebAssembly` `Microsoft.NET.Sdk.Web` bir WebAssembly tabanlı .NET çalışma zamanında tarayıcıda çalıştırıldıklarından SDK yerine proje hedefleri.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-113">Blazor WebAssembly project targets `Microsoft.NET.Sdk.BlazorWebAssembly` instead of `Microsoft.NET.Sdk.Web` sdk because they run in the browser on a WebAssembly-based .NET runtime.</span></span> <span data-ttu-id="0f5d2-114">Bir sunucu veya geliştirici makinesinde kullanabileceğiniz gibi bir Web tarayıcısına .NET yükleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-114">You can't install .NET into a web browser like you can on a server or developer machine.</span></span> <span data-ttu-id="0f5d2-115">Sonuç olarak, proje Blazor tekil paket başvurularını kullanarak çerçeveye başvurur.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-115">Consequently, the project references the Blazor framework using individual package references.</span></span>

<span data-ttu-id="0f5d2-116">Karşılaştırmayla, varsayılan bir ASP.NET Web Forms projesi *. csproj* dosyasında neredeyse 300 satır xml içerir ve bu, çoğu, projedeki çeşitli kod ve içerik dosyalarını açıkça listeler.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-116">By comparison, a default ASP.NET Web Forms project includes almost 300 lines of XML in its *.csproj* file, most of which is explicitly listing the various code and content files in the project.</span></span> <span data-ttu-id="0f5d2-117">`.NET 5`Hem hem de uygulamasının sürümü `Blazor Server` ile `Blazor WebAssembly` birleştirilmiş bir çalışma zamanını kolayca paylaşabilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-117">With the release of `.NET 5` both `Blazor Server` and `Blazor WebAssembly` app can easily share one unified runtime.</span></span>

<span data-ttu-id="0f5d2-118">Desteklenseler de, bireysel derleme başvuruları .NET projelerinde daha az yaygındır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-118">Although they're supported, individual assembly references are less common in .NET projects.</span></span> <span data-ttu-id="0f5d2-119">Çoğu proje bağımlılığı, NuGet paket başvuruları olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-119">Most project dependencies are handled as NuGet package references.</span></span> <span data-ttu-id="0f5d2-120">Yalnızca .NET projelerinde en üst düzey paket bağımlılıklarına başvurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-120">You only need to reference top-level package dependencies in .NET projects.</span></span> <span data-ttu-id="0f5d2-121">Geçişli bağımlılıklar otomatik olarak eklenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-121">Transitive dependencies are included automatically.</span></span> <span data-ttu-id="0f5d2-122">ASP.NET Web Forms projelerinde yaygın olarak bulunan *packages.config* dosyayı kullanmak yerine, paket başvuruları öğesi kullanılarak proje dosyasına eklenir `<PackageReference>` .</span><span class="sxs-lookup"><span data-stu-id="0f5d2-122">Instead of using the *packages.config* file commonly found in ASP.NET Web Forms projects to reference packages, package references are added to the project file using the `<PackageReference>` element.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

## <a name="entry-point"></a><span data-ttu-id="0f5d2-123">Giriş noktası</span><span class="sxs-lookup"><span data-stu-id="0f5d2-123">Entry point</span></span>

<span data-ttu-id="0f5d2-124">BlazorSunucu uygulamasının giriş noktası, bir konsol uygulamasında gördüğünüz gibi *program.cs* dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-124">The Blazor Server app's entry point is defined in the *Program.cs* file, as you would see in a Console app.</span></span> <span data-ttu-id="0f5d2-125">Uygulama yürütüldüğünde Web uygulamalarına özgü varsayılan değerleri kullanarak bir Web ana bilgisayar örneği oluşturur ve çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-125">When the app executes, it creates and runs a web host instance using defaults specific to web apps.</span></span> <span data-ttu-id="0f5d2-126">Web ana bilgisayarı, Blazor sunucu uygulamasının yaşam döngüsünü yönetir ve konak düzeyi Hizmetleri ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-126">The web host manages the Blazor Server app's lifecycle and sets up host-level services.</span></span> <span data-ttu-id="0f5d2-127">Bu hizmetlere örnek olarak yapılandırma, günlüğe kaydetme, bağımlılık ekleme ve HTTP sunucusu verilebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-127">Examples of such services are configuration, logging, dependency injection, and the HTTP server.</span></span> <span data-ttu-id="0f5d2-128">Bu kod çoğunlukla ortak olduğundan, genellikle değişmeden kalır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-128">This code is mostly boilerplate and is often left unchanged.</span></span>

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

<span data-ttu-id="0f5d2-129">BlazorWebAssemblyuygulamalar ayrıca *program.cs* içinde bir giriş noktası tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-129">Blazor WebAssembly apps also define an entry point in *Program.cs*.</span></span> <span data-ttu-id="0f5d2-130">Kod biraz farklı görünüyor.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-130">The code looks slightly different.</span></span> <span data-ttu-id="0f5d2-131">Kod, uygulamaya aynı ana bilgisayar düzeyi hizmetleri sağlamak için uygulama ana bilgisayarı ayarlamada benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-131">The code is similar in that it's setting up the app host to provide the same host-level services to the app.</span></span> <span data-ttu-id="0f5d2-132">WebAssemblyAncak, uygulama ana bilgisayarı doğrudan tarayıcıda yürütüldüğü için BIR http sunucusu ayarlama yapmaz.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-132">The WebAssembly app host doesn't, however, set up an HTTP server because it executes directly in the browser.</span></span>

<span data-ttu-id="0f5d2-133">Blazor uygulamalar `Startup` , uygulama için başlangıç mantığını tanımlamak üzere *Global. asax* dosyası yerine bir sınıfa sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-133">Blazor apps have a `Startup` class instead of a *Global.asax* file to define the startup logic for the app.</span></span> <span data-ttu-id="0f5d2-134">`Startup`Sınıfı, uygulamayı ve uygulamaya özgü hizmetleri yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-134">The `Startup` class is used to configure the app and any app-specific services.</span></span> <span data-ttu-id="0f5d2-135">Sunucu uygulamasında Blazor `Startup` sınıfı, Blazor istemci tarayıcıları ve sunucu arasında kullanılan gerçek zamanlı bağlantı için uç noktayı ayarlamak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-135">In the Blazor Server app, the `Startup` class is used to set up the endpoint for the real-time connection used by Blazor between the client browsers and the server.</span></span> <span data-ttu-id="0f5d2-136">Blazor WebAssembly Uygulamada, `Startup` sınıfı uygulamanın kök bileşenlerini ve bunların oluşturulması gereken yerleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-136">In the Blazor WebAssembly app, the `Startup` class defines the root components for the app and where they should be rendered.</span></span> <span data-ttu-id="0f5d2-137">`Startup` [Uygulama başlatma](./app-startup.md) bölümündeki sınıfına daha ayrıntılı bir bakış ekleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-137">We'll take a deeper look at the `Startup` class in the [App startup](./app-startup.md) section.</span></span>

## <a name="static-files"></a><span data-ttu-id="0f5d2-138">Statik dosyalar</span><span class="sxs-lookup"><span data-stu-id="0f5d2-138">Static files</span></span>

<span data-ttu-id="0f5d2-139">ASP.NET Web Forms projelerinin aksine, projedeki tüm dosyalar Blazor statik dosya olarak istenemez.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-139">Unlike ASP.NET Web Forms projects, not all files in a Blazor project can be requested as static files.</span></span> <span data-ttu-id="0f5d2-140">Yalnızca *Wwwroot* klasöründeki dosyalar Web adreslenebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-140">Only the files in the *wwwroot* folder are web-addressable.</span></span> <span data-ttu-id="0f5d2-141">Bu klasöre uygulamanın "Web root" adı verilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-141">This folder is referred to the app's "web root".</span></span> <span data-ttu-id="0f5d2-142">Uygulamanın Web kökünün dışındaki herhangi bir şey, Web 'de adreslenebilir *değildir* .</span><span class="sxs-lookup"><span data-stu-id="0f5d2-142">Anything outside of the app's web root *isn't* web-addressable.</span></span> <span data-ttu-id="0f5d2-143">Bu kurulum, proje dosyalarını web üzerinden yanlışlıkla açığa çıkaran ek bir güvenlik düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-143">This setup provides an additional level of security that prevents accidental exposing of project files over the web.</span></span>

## <a name="configuration"></a><span data-ttu-id="0f5d2-144">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0f5d2-144">Configuration</span></span>

<span data-ttu-id="0f5d2-145">ASP.NET Web Forms uygulamalarında yapılandırma genellikle bir veya daha fazla *web.config* dosyası kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-145">Configuration in ASP.NET Web Forms apps is typically handled using one or more *web.config* files.</span></span> <span data-ttu-id="0f5d2-146">Blazor uygulamalar genellikle *web.config* dosyalarına sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-146">Blazor apps don't typically have *web.config* files.</span></span> <span data-ttu-id="0f5d2-147">Bu dosyalar yalnızca IIS 'de barındırılırken IIS 'e özgü ayarları yapılandırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-147">If they do, the file is only used to configure IIS-specific settings when hosted on IIS.</span></span> <span data-ttu-id="0f5d2-148">Bunun yerine, Blazor sunucu uygulamaları ASP.NET Core yapılandırma soyutlamalarını kullanır ( Blazor WebAssembly uygulamalar şu anda aynı yapılandırma soyutlamalarını desteklememektedir, ancak gelecekte eklenmiş bir özellik olabilir).</span><span class="sxs-lookup"><span data-stu-id="0f5d2-148">Instead, Blazor Server apps use the ASP.NET Core configuration abstractions (Blazor WebAssembly apps don't currently support the same configuration abstractions, but that may be a feature added in the future).</span></span> <span data-ttu-id="0f5d2-149">Örneğin, varsayılan Blazor sunucu uygulaması *appsettings.js*' de bazı ayarları depolar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-149">For example, the default Blazor Server app stores some settings in *appsettings.json*.</span></span>

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

<span data-ttu-id="0f5d2-150">[Yapılandırma bölümünde ASP.NET Core](./config.md) projelerde yapılandırma hakkında daha fazla bilgi edineceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-150">We'll learn more about configuration in ASP.NET Core projects in the [Configuration](./config.md) section.</span></span>

## <a name="razor-components"></a><span data-ttu-id="0f5d2-151">Razor bileşenleri</span><span class="sxs-lookup"><span data-stu-id="0f5d2-151">Razor components</span></span>

<span data-ttu-id="0f5d2-152">Projelerdeki çoğu dosya Blazor *. Razor* dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-152">Most files in Blazor projects are *.razor* files.</span></span> <span data-ttu-id="0f5d2-153">Razor, dinamik olarak Web Kullanıcı arabirimi oluşturmak için kullanılan HTML ve C# tabanlı bir şablon oluşturma dilidir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-153">Razor is a templating language based on HTML and C# that is used to dynamically generate web UI.</span></span> <span data-ttu-id="0f5d2-154">*. Razor* dosyaları uygulamanın kullanıcı arabirimini oluşturan bileşenleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-154">The *.razor* files define components that make up the UI of the app.</span></span> <span data-ttu-id="0f5d2-155">Çoğu bölümde, bileşenler hem Blazor sunucu hem de uygulamalar için aynıdır Blazor WebAssembly .</span><span class="sxs-lookup"><span data-stu-id="0f5d2-155">For the most part, the components are identical for both the Blazor Server and Blazor WebAssembly apps.</span></span> <span data-ttu-id="0f5d2-156">İçindeki bileşenler Blazor , ASP.NET Web Forms içindeki kullanıcı denetimlerine benzerdir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-156">Components in Blazor are analogous to user controls in ASP.NET Web Forms.</span></span>

<span data-ttu-id="0f5d2-157">Her Razor bileşeni dosyası, proje oluşturulduğunda bir .NET sınıfına derlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-157">Each Razor component file is compiled into a .NET class when the project is built.</span></span> <span data-ttu-id="0f5d2-158">Oluşturulan sınıf, bileşenin durumunu, işleme mantığını, yaşam döngüsü yöntemlerini, olay işleyicilerini ve diğer mantığı yakalar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-158">The generated class captures the component's state, rendering logic, lifecycle methods, event handlers, and other logic.</span></span> <span data-ttu-id="0f5d2-159">Yeniden [kullanılabilir kullanıcı arabirimi Blazor bileşenlerinde oluşturma](./components.md) bölümünde bileşen yazma bölümüne bakacağız.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-159">We'll look at authoring components in the [Building reusable UI components with Blazor](./components.md) section.</span></span>

<span data-ttu-id="0f5d2-160">*_Imports. Razor* dosyaları Razor bileşen dosyaları değildir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-160">The *_Imports.razor* files aren't Razor component files.</span></span> <span data-ttu-id="0f5d2-161">Bunun yerine, aynı klasörde ve alt klasörlerinde bulunan diğer *. Razor* dosyalarını içeri aktarmak Için bir Razor yönergeleri kümesi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-161">Instead, they define a set of Razor directives to import into other *.razor* files within the same folder and in its subfolders.</span></span> <span data-ttu-id="0f5d2-162">Örneğin, bir *_Imports. Razor* dosyası, `using` yaygın olarak kullanılan ad alanları için yönergeler eklemenin geleneksel bir yoludur:</span><span class="sxs-lookup"><span data-stu-id="0f5d2-162">For example, a *_Imports.razor* file is a conventional way to add `using` directives for commonly used namespaces:</span></span>

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

## <a name="pages"></a><span data-ttu-id="0f5d2-163">Sayfalar</span><span class="sxs-lookup"><span data-stu-id="0f5d2-163">Pages</span></span>

<span data-ttu-id="0f5d2-164">Uygulamalardaki Sayfalar nerede Blazor ?</span><span class="sxs-lookup"><span data-stu-id="0f5d2-164">Where are the pages in the Blazor apps?</span></span> <span data-ttu-id="0f5d2-165">Blazor , ASP.NET Web Forms uygulamalarındaki *. aspx* dosyaları gibi adreslenebilir sayfalar için ayrı bir dosya uzantısı tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-165">Blazor doesn't define a separate file extension for addressable pages, like the *.aspx* files in ASP.NET Web Forms apps.</span></span> <span data-ttu-id="0f5d2-166">Bunun yerine, sayfalar bileşenlere rotalar atanarak tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-166">Instead, pages are defined by assigning routes to components.</span></span> <span data-ttu-id="0f5d2-167">Bir yol, genellikle `@page` Razor yönergesi kullanılarak atanır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-167">A route is typically assigned using the `@page` Razor directive.</span></span> <span data-ttu-id="0f5d2-168">Örneğin, `Counter` *Pages/Counter. Razor* dosyasında yazılan bileşen aşağıdaki rotayı tanımlar:</span><span class="sxs-lookup"><span data-stu-id="0f5d2-168">For example, the `Counter` component authored in the *Pages/Counter.razor* file defines the following route:</span></span>

```razor
@page "/counter"
```

<span data-ttu-id="0f5d2-169">İçindeki yönlendirme, Blazor sunucuda değil, istemci tarafında işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-169">Routing in Blazor is handled client-side, not on the server.</span></span> <span data-ttu-id="0f5d2-170">Kullanıcı tarayıcıda Blazor gezinirken, gezintiyi durdurur ve ardından bileşeni eşleşen yol ile işler.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-170">As the user navigates in the browser, Blazor intercepts the navigation and then renders the component with the matching route.</span></span>

<span data-ttu-id="0f5d2-171">Bileşen yolları şu anda bileşenin dosya konumu tarafından, *. aspx* sayfalarıyla oldukları gibi çıkarsanamıyor.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-171">The component routes aren't currently inferred by the component's file location like they are with *.aspx* pages.</span></span> <span data-ttu-id="0f5d2-172">Bu özellik gelecekte eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-172">This feature may be added in the future.</span></span> <span data-ttu-id="0f5d2-173">Her yol, bileşen üzerinde açık olarak belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-173">Each route must be specified explicitly on the component.</span></span> <span data-ttu-id="0f5d2-174">Bir *Sayfalar* klasöründe yönlendirilebilir bileşenlerin depolanması özel bir anlamı yoktur ve yalnızca bir kuraldır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-174">Storing routable components in a *Pages* folder has no special meaning and is purely a convention.</span></span>

<span data-ttu-id="0f5d2-175">Blazor [Sayfalar, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde ' de yönlendirme sırasında daha ayrıntılı bir ayrıntıya bakacağız.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-175">We'll look in greater detail at routing in Blazor in the [Pages, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="layout"></a><span data-ttu-id="0f5d2-176">Düzen</span><span class="sxs-lookup"><span data-stu-id="0f5d2-176">Layout</span></span>

<span data-ttu-id="0f5d2-177">ASP.NET Web Forms uygulamalarda, ana sayfalar (*site. Master*) kullanılarak ortak bir sayfa düzeni işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-177">In ASP.NET Web Forms apps, a common page layout is handled using master pages (*Site.Master*).</span></span> <span data-ttu-id="0f5d2-178">BlazorUygulamalarda, sayfa düzeni Düzen bileşenleri (*paylaşılan/mainlayout. Razor*) kullanılarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-178">In Blazor apps, the page layout is handled using layout components (*Shared/MainLayout.razor*).</span></span> <span data-ttu-id="0f5d2-179">Düzen bileşenleri [sayfa, Yönlendirme ve düzenler](./pages-routing-layouts.md) bölümünde daha ayrıntılı bir şekilde ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-179">Layout components will be discussed in more detail in [Page, routing, and layouts](./pages-routing-layouts.md) section.</span></span>

## <a name="bootstrap-no-locblazor"></a><span data-ttu-id="0f5d2-180">Yükleyebilirsiniz Blazor</span><span class="sxs-lookup"><span data-stu-id="0f5d2-180">Bootstrap Blazor</span></span>

<span data-ttu-id="0f5d2-181">Önyükleme yapmak için Blazor uygulamanın şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0f5d2-181">To bootstrap Blazor, the app must:</span></span>

- <span data-ttu-id="0f5d2-182">Kök bileşenin (*app. Razor*) nerede işleneceğini belirtin.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-182">Specify where on the page the root component (*App.Razor*) should be rendered.</span></span>
- <span data-ttu-id="0f5d2-183">İlgili Blazor Framework betiğini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-183">Add the corresponding Blazor framework script.</span></span>

<span data-ttu-id="0f5d2-184">Sunucu uygulamasında Blazor , kök bileşenin ana bilgisayar sayfası *_Host. cshtml* dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-184">In the Blazor Server app, the root component's host page is defined in the *_Host.cshtml* file.</span></span> <span data-ttu-id="0f5d2-185">Bu dosya, bir bileşeni değil Razor sayfasını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-185">This file defines a Razor Page, not a component.</span></span> <span data-ttu-id="0f5d2-186">Razor Pages, bir *. aspx* sayfasına benzer şekilde sunucu adreslenebilir bir sayfa tanımlamak için Razor söz dizimi kullanın.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-186">Razor Pages use Razor syntax to define a server-addressable page, very much like an *.aspx* page.</span></span> <span data-ttu-id="0f5d2-187">`Html.RenderComponentAsync<TComponent>(RenderMode)`Yöntemi, kök düzeyinde bir bileşenin nerede işleneceğini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-187">The `Html.RenderComponentAsync<TComponent>(RenderMode)` method is used to define where a root-level component should be rendered.</span></span> <span data-ttu-id="0f5d2-188">`RenderMode`Seçeneği, bileşenin oluşturulması gereken şekli gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-188">The `RenderMode` option indicates the manner in which the component should be rendered.</span></span> <span data-ttu-id="0f5d2-189">Aşağıdaki tabloda desteklenen `RenderMode` Seçenekler özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-189">The following table outlines the supported `RenderMode` options.</span></span>

|<span data-ttu-id="0f5d2-190">Seçenek</span><span class="sxs-lookup"><span data-stu-id="0f5d2-190">Option</span></span>                        |<span data-ttu-id="0f5d2-191">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f5d2-191">Description</span></span>       |
|------------------------------|------------------|
|`RenderMode.Server`           |<span data-ttu-id="0f5d2-192">Tarayıcıyla bir bağlantı kurulduktan sonra etkileşimli olarak işlendi</span><span class="sxs-lookup"><span data-stu-id="0f5d2-192">Rendered interactively once a connection with the browser is established</span></span>|
|`RenderMode.ServerPrerendered`|<span data-ttu-id="0f5d2-193">Önce ön ve daha sonra etkileşimli olarak işlendi</span><span class="sxs-lookup"><span data-stu-id="0f5d2-193">First prerendered and then rendered interactively</span></span>|
|`RenderMode.Static`           |<span data-ttu-id="0f5d2-194">Statik içerik olarak işlendi</span><span class="sxs-lookup"><span data-stu-id="0f5d2-194">Rendered as static content</span></span>|

<span data-ttu-id="0f5d2-195">*_Framework/blazor.server.js* betik başvurusu, sunucuyla gerçek zamanlı bağlantı kurar ve ardından tüm kullanıcı etkileşimleri ve Kullanıcı arabirimi güncelleştirmeleriyle ilgilenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-195">The script reference to *_framework/blazor.server.js* establishes the real-time connection with the server and then deals with all user interactions and UI updates.</span></span>

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

<span data-ttu-id="0f5d2-196">Blazor WebAssembly Uygulamada, ana bilgisayar sayfası *Wwwroot/index.html* altında basit bir statik HTML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-196">In the Blazor WebAssembly app, the host page is a simple static HTML file under *wwwroot/index.html*.</span></span> <span data-ttu-id="0f5d2-197">`<div>`Adlandırılmış kimliği olan öğe, `app` kök bileşenin nerede işleneceğini belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-197">The `<div>` element with id named `app` is used to indicate where the root component should be rendered.</span></span>

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
    <title>BlazorApp2</title>
    <base href="/" />
    <link href="css/bootstrap/bootstrap.min.css" rel="stylesheet" />
    <link href="css/app.css" rel="stylesheet" />
    <link href="blazor-web.styles.css" rel="stylesheet" />
</head>

<body>
    <div id="app">Loading...</div>

    <div id="blazor-error-ui">
        An unhandled error has occurred.
        <a href="" class="reload">Reload</a>
        <a class="dismiss">🗙</a>
    </div>
    <script src="_framework/blazor.webassembly.js"></script>
</body>

</html>

```

<span data-ttu-id="0f5d2-198">İşlenecek kök bileşen uygulamanın `Program.Main` yönteminde, bağımlılık ekleme yoluyla farklı Hizmetleri kaydetme esnekliği ile yapılandırılır. [ Blazor İçindeki WebAssembly ](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly) bir uygulamaya hizmet ekleme konusuna bakabilirsiniz</span><span class="sxs-lookup"><span data-stu-id="0f5d2-198">The root component to render is configured in the app's `Program.Main` method with the flexibility to register different services through dependency injection.You can refer add services to an app in [Blazor WebAssembly](https://docs.microsoft.com/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-5.0#blazor-webassembly)</span></span>

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("#app");

        ....
        ....
    }
}
```

## <a name="build-output"></a><span data-ttu-id="0f5d2-199">Derleme çıkışı</span><span class="sxs-lookup"><span data-stu-id="0f5d2-199">Build output</span></span>

<span data-ttu-id="0f5d2-200">Bir Blazor Proje oluşturulduğunda, tüm Razor bileşeni ve kod dosyaları tek bir derlemede derlenir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-200">When a Blazor project is built, all Razor component and code files are compiled into a single assembly.</span></span> <span data-ttu-id="0f5d2-201">ASP.NET Web Forms projelerinin aksine, Blazor UI mantığının çalışma zamanı derlemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-201">Unlike ASP.NET Web Forms projects, Blazor doesn't support runtime compilation of the UI logic.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="0f5d2-202">Uygulamayı çalıştırma</span><span class="sxs-lookup"><span data-stu-id="0f5d2-202">Run the app</span></span>

<span data-ttu-id="0f5d2-203">BlazorSunucu uygulamasını çalıştırmak için, `F5` Visual Studio 'da ' ya basın.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-203">To run the Blazor Server app, press `F5` in Visual Studio.</span></span> <span data-ttu-id="0f5d2-204">Blazor uygulamalar çalışma zamanı derlemesini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-204">Blazor apps don't support runtime compilation.</span></span> <span data-ttu-id="0f5d2-205">Kod ve bileşen biçimlendirme değişikliklerinin sonuçlarını görmek için, uygulamayı yeniden derleyin ve hata ayıklayıcı ekli olarak yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-205">To see the results of code and component markup changes, rebuild and restart the app with the debugger attached.</span></span> <span data-ttu-id="0f5d2-206">Hata ayıklayıcı ekli () olmadan çalıştırırsanız `Ctrl+F5` , Visual Studio dosya değişikliklerini izler ve değişiklikler yapıldıktan sonra uygulamayı yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-206">If you run without the debugger attached (`Ctrl+F5`), Visual Studio watches for file changes and restarts the app as changes are made.</span></span> <span data-ttu-id="0f5d2-207">Değişiklik yapıldığında tarayıcıyı el ile yenilemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-207">You manually refresh the browser as changes are made.</span></span>

<span data-ttu-id="0f5d2-208">Uygulamayı çalıştırmak için Blazor WebAssembly aşağıdaki yaklaşımlardan birini seçin:</span><span class="sxs-lookup"><span data-stu-id="0f5d2-208">To run the Blazor WebAssembly app, choose one of the following approaches:</span></span>

- <span data-ttu-id="0f5d2-209">İstemci projesini doğrudan geliştirme sunucusunu kullanarak çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-209">Run the client project directly using the development server.</span></span>
- <span data-ttu-id="0f5d2-210">ASP.NET Core ile uygulamayı barındırırken sunucu projesini çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f5d2-210">Run the server project when hosting the app with ASP.NET Core.</span></span>

<span data-ttu-id="0f5d2-211">BlazorWebAssemblyuygulamaların her ikisi de tarayıcıda ve Visual Studio 'da hata ayıklaması yapılabilir. Ayrıntılar için bkz. [hata ayıklama ASP.NET Core Blazor WebAssembly ](/aspnet/core/blazor/debug) .</span><span class="sxs-lookup"><span data-stu-id="0f5d2-211">Blazor WebAssembly apps can be debugged in both browser and Visual Studio.See [Debug ASP.NET Core Blazor WebAssembly](/aspnet/core/blazor/debug) for details.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0f5d2-212">[Önceki](hosting-models.md) 
> [Sonraki](app-startup.md)</span><span class="sxs-lookup"><span data-stu-id="0f5d2-212">[Previous](hosting-models.md)
[Next](app-startup.md)</span></span>
