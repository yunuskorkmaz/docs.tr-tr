---
title: Uygulama yapılandırması
description: BlazorConfigurationManager kullanılmadan uygulamaları yapılandırmayı öğrenin.
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173321"
---
# <a name="app-configuration"></a><span data-ttu-id="f2126-103">Uygulama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="f2126-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="f2126-104">Web Forms ' de uygulama yapılandırmasını yüklemeye yönelik birincil yol, *web.config* &mdash; sunucuda veya *web.config*tarafından başvurulan ilgili bir yapılandırma dosyasında bulunanweb.configdosyasında yer alan girişlerdir. Statik nesneyi, uygulama `ConfigurationManager` ayarları, veri deposu bağlantı dizeleri ve uygulamaya eklenen diğer genişletilmiş yapılandırma sağlayıcıları ile etkileşim kurmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2126-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="f2126-105">Aşağıdaki kodda görüldüğü gibi, uygulama yapılandırması ile etkileşimleri görmek normaldir:</span><span class="sxs-lookup"><span data-stu-id="f2126-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="f2126-106">ASP.NET Core ve sunucu tarafında Blazor , uygulamanız bir WINDOWS IIS sunucusunda barındırılıyorsa, *web.config* dosyası mevcut olabilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="f2126-107">Bununla birlikte, `ConfigurationManager` Bu yapılandırmayla etkileşim yoktur ve diğer kaynaklardan daha fazla yapılandırılmış uygulama yapılandırması da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2126-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="f2126-108">Yapılandırmanın nasıl toplandığını ve bir *web.config* dosyasından yapılandırma bilgilerine nasıl erişekullanabileceğinizi göz atalım.</span><span class="sxs-lookup"><span data-stu-id="f2126-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="f2126-109">Yapılandırma kaynakları</span><span class="sxs-lookup"><span data-stu-id="f2126-109">Configuration sources</span></span>

<span data-ttu-id="f2126-110">ASP.NET Core, uygulamanız için kullanmak isteyebileceğiniz birçok yapılandırma kaynağını tanır.</span><span class="sxs-lookup"><span data-stu-id="f2126-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="f2126-111">Framework, varsayılan olarak bu özelliklerden en iyi şekilde bu özellikleri sunmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="f2126-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="f2126-112">Yapılandırma ASP.NET Core tarafından bu çeşitli kaynaklardan okunurdur ve toplanır.</span><span class="sxs-lookup"><span data-stu-id="f2126-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="f2126-113">Aynı yapılandırma anahtarı için daha sonra yüklenen değerler önceki değerlerden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="f2126-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="f2126-114">ASP.NET Core, bulut açısından uyumlu olacak şekilde tasarlanmıştır ve uygulamaların yapılandırılmasını hem operatörler hem de geliştiriciler için daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f2126-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="f2126-115">ASP.NET Core, ortama duyarlı ve veya ortamınızda çalışıp çalışmadığını biliyor `Production` `Development` .</span><span class="sxs-lookup"><span data-stu-id="f2126-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="f2126-116">Ortam göstergesi, `ASPNETCORE_ENVIRONMENT` Sistem ortamı değişkeninde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="f2126-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="f2126-117">Hiçbir değer yapılandırılmamışsa, uygulamanın ortamda çalışması varsayılan olur `Production` .</span><span class="sxs-lookup"><span data-stu-id="f2126-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="f2126-118">Uygulamanız, ortam adına göre çeşitli kaynaklardan yapılandırma tetikleyip ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="f2126-119">Varsayılan olarak, yapılandırma aşağıdaki kaynaklardan listelenen sırayla yüklenir:</span><span class="sxs-lookup"><span data-stu-id="f2126-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="f2126-120">Varsa dosyada *appsettings.js*</span><span class="sxs-lookup"><span data-stu-id="f2126-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="f2126-121">*appSettings. {ENVIRONMENT_NAME}. JSON* dosyası varsa</span><span class="sxs-lookup"><span data-stu-id="f2126-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="f2126-122">Varsa, diskte Kullanıcı gizli dizileri dosyası</span><span class="sxs-lookup"><span data-stu-id="f2126-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="f2126-123">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f2126-123">Environment variables</span></span>
1. <span data-ttu-id="f2126-124">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f2126-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="f2126-125">Biçim ve erişim üzerinde appsettings.js</span><span class="sxs-lookup"><span data-stu-id="f2126-125">appsettings.json format and access</span></span>

<span data-ttu-id="f2126-126">Dosyadaki *appsettings.js* , aşağıdaki JSON gibi yapılandırılmış değerlerle hiyerarşik olabilir:</span><span class="sxs-lookup"><span data-stu-id="f2126-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

<span data-ttu-id="f2126-127">Önceki JSON ile sunulursa, yapılandırma sistemi alt değerleri düzleştirir ve tam hiyerarşik yollara başvurur.</span><span class="sxs-lookup"><span data-stu-id="f2126-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="f2126-128">İki nokta ( `:` ) karakteri hiyerarşideki her özelliği ayırır.</span><span class="sxs-lookup"><span data-stu-id="f2126-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="f2126-129">Örneğin, yapılandırma anahtarı `section1:key0` `section1` nesne değişmez `key0` değerine erişir.</span><span class="sxs-lookup"><span data-stu-id="f2126-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="f2126-130">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="f2126-130">User secrets</span></span>

<span data-ttu-id="f2126-131">Kullanıcı gizli dizileri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f2126-131">User secrets are:</span></span>

* <span data-ttu-id="f2126-132">Geliştirici iş istasyonundaki bir JSON dosyasında depolanan yapılandırma değerleri, uygulama geliştirme klasörü dışında.</span><span class="sxs-lookup"><span data-stu-id="f2126-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="f2126-133">Yalnızca ortamda çalışırken yüklenir `Development` .</span><span class="sxs-lookup"><span data-stu-id="f2126-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="f2126-134">Belirli bir uygulamayla ilişkili.</span><span class="sxs-lookup"><span data-stu-id="f2126-134">Associated with a specific app.</span></span>
* <span data-ttu-id="f2126-135">.NET Core CLI `user-secrets` komutuyla yönetiliyor.</span><span class="sxs-lookup"><span data-stu-id="f2126-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="f2126-136">Komutu yürüterek uygulamanızı gizli dizi depolaması için yapılandırın `user-secrets` :</span><span class="sxs-lookup"><span data-stu-id="f2126-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="f2126-137">Yukarıdaki komut, `UserSecretsId` proje dosyasına bir öğesi ekler.</span><span class="sxs-lookup"><span data-stu-id="f2126-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="f2126-138">Öğesi, gizli dizileri uygulamayla ilişkilendirmek için kullanılan bir GUID içerir.</span><span class="sxs-lookup"><span data-stu-id="f2126-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="f2126-139">Daha sonra komutuyla bir gizli dizi tanımlayabilirsiniz `set` .</span><span class="sxs-lookup"><span data-stu-id="f2126-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="f2126-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="f2126-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="f2126-141">Yukarıdaki komut, `Parent:ApiKey` yapılandırma anahtarını bir geliştiricinin iş istasyonunda değeri ile kullanılabilir hale getirir `12345` .</span><span class="sxs-lookup"><span data-stu-id="f2126-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="f2126-142">Kullanıcı parolaları oluşturma, depolama ve yönetme hakkında daha fazla bilgi için, ASP.NET Core belgesinde [geliştirme sırasında uygulama gizli dizileri 'Nin güvenli depolama](/aspnet/core/security/app-secrets) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f2126-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="f2126-143">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f2126-143">Environment variables</span></span>

<span data-ttu-id="f2126-144">Uygulama yapılandırmanıza yüklenen sonraki değer kümesi, sistemin ortam değişkenleridir.</span><span class="sxs-lookup"><span data-stu-id="f2126-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="f2126-145">Tüm sisteminizin ortam değişkeni ayarlarına artık Yapılandırma API 'SI aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="f2126-146">Hiyerarşik değerler, uygulamanızın içinde okuma sırasında düz ve iki nokta üst üste karakteriyle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="f2126-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="f2126-147">Ancak bazı işletim sistemleri, iki nokta üst üste karakter ortamı değişken adlarına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="f2126-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="f2126-148">ASP.NET Core Çift alt çizgi () içeren değerleri `__` erişildiğinde iki nokta üst üste dönüştürerek bu sınırlamaya yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="f2126-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="f2126-149">`Parent:ApiKey`Yukarıdaki Kullanıcı gizli dizileri bölümünün değeri, ortam değişkeniyle geçersiz kılınabilir `Parent__ApiKey` .</span><span class="sxs-lookup"><span data-stu-id="f2126-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="f2126-150">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="f2126-150">Command-line arguments</span></span>

<span data-ttu-id="f2126-151">Yapılandırma ayrıca uygulamanız başlatıldığında komut satırı bağımsız değişkenleri olarak da bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="f2126-152">`--` `/` Ayarlanacak yapılandırma değerinin adını ve yapılandırılacak değeri belirtmek için çift Dash () veya Forward-eğik çizgi () gösterimini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f2126-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="f2126-153">Söz dizimi aşağıdaki komutlara benzer:</span><span class="sxs-lookup"><span data-stu-id="f2126-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="f2126-154">web.config dönüşü</span><span class="sxs-lookup"><span data-stu-id="f2126-154">The return of web.config</span></span>

<span data-ttu-id="f2126-155">Uygulamanızı IIS 'de Windows 'a dağıttıysanız, *web.config* dosyası uygulamanızı yönetmek için yıne de IIS 'yi yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="f2126-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="f2126-156">IIS, varsayılan olarak ASP.NET Core modülüne (ANCM) bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="f2126-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="f2126-157">ANCM, Kestrel Web sunucusu yerine uygulamanızı barındıran yerel bir IIS modülüdür.</span><span class="sxs-lookup"><span data-stu-id="f2126-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="f2126-158">Bu *web.config* bölümü aşağıdaki XML biçimlendirmesine benzer:</span><span class="sxs-lookup"><span data-stu-id="f2126-158">This *web.config* section resembles the following XML markup:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

<span data-ttu-id="f2126-159">Uygulamaya özel yapılandırma, öğesinde bir öğe yuvalanarak tanımlanabilir `environmentVariables` `aspNetCore` .</span><span class="sxs-lookup"><span data-stu-id="f2126-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="f2126-160">Bu bölümde tanımlanan değerler, ASP.NET Core uygulamasına ortam değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="f2126-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="f2126-161">Ortam değişkenleri, bu uygulama başlatma segmenti için uygun şekilde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f2126-161">The environment variables load appropriately during that segment of app startup.</span></span>

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="f2126-162">Uygulamada yapılandırmayı okuma</span><span class="sxs-lookup"><span data-stu-id="f2126-162">Read configuration in the app</span></span>

<span data-ttu-id="f2126-163">ASP.NET Core arabirim aracılığıyla uygulama yapılandırması sağlar <xref:Microsoft.Extensions.Configuration.IConfiguration> .</span><span class="sxs-lookup"><span data-stu-id="f2126-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="f2126-164">Bu yapılandırma arabirimi, Blazor bileşenlerinizde, Blazor sayfalarınızda ve yapılandırmaya erişmesi gereken diğer ASP.NET Core yönetilen bir sınıftan istenir.</span><span class="sxs-lookup"><span data-stu-id="f2126-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="f2126-165">ASP.NET Core Framework, bu arabirimi daha önce yapılandırılan çözümlenmiş yapılandırmayla otomatik olarak doldurur.</span><span class="sxs-lookup"><span data-stu-id="f2126-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="f2126-166">Bir Blazor sayfada veya bileşenin Razor biçimlendirmesinde, `IConfiguration` nesneyi `@inject` *. Razor* dosyasının en üstünde yer alan bir yönergeyle bu şekilde ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2126-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="f2126-167">Bu önceki ifade, `IConfiguration` nesneyi `Configuration` Razor şablonunun geri kalanı boyunca değişken olarak kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="f2126-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="f2126-168">Bir dizin oluşturucu parametresi olarak aranan yapılandırma ayarı hiyerarşisi belirtilerek ayrı yapılandırma ayarları okunabilir:</span><span class="sxs-lookup"><span data-stu-id="f2126-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="f2126-169">Tüm yapılandırma bölümlerini, <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> `GetSection("section1")` önceki örnekteki Section1 yapılandırmasını almak için öğesine benzer bir sözdizimi ile, belirli bir konumdaki anahtarların bir koleksiyonunu almak için yöntemini kullanarak getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2126-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="f2126-170">Türü kesin belirlenmiş yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f2126-170">Strongly typed configuration</span></span>

<span data-ttu-id="f2126-171">Web Forms, <xref:System.Configuration.ConfigurationSection> türü ve ilişkili türlerden devralınan kesin türü belirtilmiş bir yapılandırma türü oluşturmak mümkün.</span><span class="sxs-lookup"><span data-stu-id="f2126-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="f2126-172">`ConfigurationSection`Bu yapılandırma değerleri için bazı iş kurallarını ve işlemeyi yapılandırmanıza izin verilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="f2126-173">ASP.NET Core, yapılandırma değerlerini alacak bir sınıf hiyerarşisi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2126-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="f2126-174">Bu sınıflar:</span><span class="sxs-lookup"><span data-stu-id="f2126-174">These classes:</span></span>

* <span data-ttu-id="f2126-175">Üst sınıftan devralması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="f2126-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="f2126-176">`public`, Yakalamak istediğiniz yapılandırma yapısına yönelik özellikler ve tür başvurularıyla eşleşen özellikleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="f2126-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="f2126-177">Örnek yukarıdaki *appsettings.js* , değerleri yakalamak için aşağıdaki sınıfları tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="f2126-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

<span data-ttu-id="f2126-178">Aşağıdaki satırı yöntemine ekleyerek bu sınıf hiyerarşisi doldurulabilir `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="f2126-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="f2126-179">Uygulamanın geri kalanında, `@inject` `IOptions<MyConfig>` kesin olarak belirlenmiş yapılandırma ayarlarını almak için sınıflardaki bir giriş parametresini veya Razor şablonlarındaki bir yönergeyi ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2126-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="f2126-180">`IOptions<MyConfig>.Value`Özelliği, `MyConfig` yapılandırma ayarlarından doldurulmuş değeri verir.</span><span class="sxs-lookup"><span data-stu-id="f2126-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="f2126-181">Seçenekler özelliği hakkında daha fazla bilgi [ASP.NET Core belge ' deki Seçenekler modelinde](/aspnet/core/fundamentals/configuration/options#options-interfaces) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="f2126-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f2126-182">[Önceki](middleware.md) 
> [Sonraki](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="f2126-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
