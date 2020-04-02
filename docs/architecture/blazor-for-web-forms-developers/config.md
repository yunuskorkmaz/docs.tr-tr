---
title: Uygulama yapılandırması
description: ConfigurationManager'ı kullanmadan Blazor uygulamalarını nasıl yapılandırıştırmayı öğrenin.
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588243"
---
# <a name="app-configuration"></a><span data-ttu-id="ddea2-103">Uygulama yapılandırması</span><span class="sxs-lookup"><span data-stu-id="ddea2-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ddea2-104">Web Formlar'da uygulama yapılandırmasını yüklemenin birincil yolu,&mdash;sunucudaki *web.config* dosyasındaki girişler veya *web.config*tarafından başvurulan ilgili yapılandırma dosyasıdır. Uygulama ayarları, `ConfigurationManager` veri deposu bağlantı dizeleri ve uygulamaya eklenen diğer genişletilmiş yapılandırma sağlayıcılarıyla etkileşimde kalmak için statik nesneyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="ddea2-105">Aşağıdaki kodda görüldüğü gibi uygulama yapılandırmasıyla etkileşimleri görmek tipiktir:</span><span class="sxs-lookup"><span data-stu-id="ddea2-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="ddea2-106">ASP.NET Core ve sunucu tarafı Blazor ile, uygulamanız bir Windows IIS sunucusunda barındırılırsa *web.config* dosyası hazır olabilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="ddea2-107">Ancak, bu yapılandırma `ConfigurationManager` ile hiçbir etkileşim yoktur ve diğer kaynaklardan daha yapılandırılmış uygulama yapılandırması alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="ddea2-108">Yapılandırmanın nasıl toplandığına ve bir *web.config* dosyasından yapılandırma bilgilerine nasıl erişebileceğinize bir göz atalım.</span><span class="sxs-lookup"><span data-stu-id="ddea2-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="ddea2-109">Yapılandırma kaynakları</span><span class="sxs-lookup"><span data-stu-id="ddea2-109">Configuration sources</span></span>

<span data-ttu-id="ddea2-110">ASP.NET Core, uygulamanız için kullanmak isteyebileceğin birçok yapılandırma kaynağı olduğunu kabul eder.</span><span class="sxs-lookup"><span data-stu-id="ddea2-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="ddea2-111">Çerçeve varsayılan olarak bu özelliklerden en iyi şekilde sunmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="ddea2-112">Yapılandırma, ASP.NET Core tarafından bu çeşitli kaynaklardan okunur ve toplanır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="ddea2-113">Aynı yapılandırma anahtarı için daha sonra yüklenen değerler önceki değerlere göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="ddea2-114">ASP.NET Core, bulut bilincine duyarlı olacak ve uygulamaların yapılandırmasını hem operatörler hem de geliştiriciler için daha kolay hale getirmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="ddea2-115">ASP.NET Core çevreye duyarlıdır ve sizin veya `Production` `Development` çevrenizde olup olmadığını bilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="ddea2-116">Ortam göstergesi sistem ortamı `ASPNETCORE_ENVIRONMENT` değişkeninde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="ddea2-117">Hiçbir değer yapılandırılmamışsa, uygulama `Production` varsayılan olarak ortamda çalışmaya başlar.</span><span class="sxs-lookup"><span data-stu-id="ddea2-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="ddea2-118">Uygulamanız, ortamın adına bağlı olarak çeşitli kaynaklardan yapılandırma tetikleyebilir ve ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="ddea2-119">Varsayılan olarak, yapılandırma listelenen sırada aşağıdaki kaynaklardan yüklenir:</span><span class="sxs-lookup"><span data-stu-id="ddea2-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="ddea2-120">*varsa appsettings.json* dosyası</span><span class="sxs-lookup"><span data-stu-id="ddea2-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="ddea2-121">*ayarları. {ENVIRONMENT_NAME}.json* dosyası, varsa</span><span class="sxs-lookup"><span data-stu-id="ddea2-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="ddea2-122">Varsa diskteki kullanıcı sırları dosyası</span><span class="sxs-lookup"><span data-stu-id="ddea2-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="ddea2-123">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ddea2-123">Environment variables</span></span>
1. <span data-ttu-id="ddea2-124">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ddea2-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="ddea2-125">appsettings.json formatı ve erişim</span><span class="sxs-lookup"><span data-stu-id="ddea2-125">appsettings.json format and access</span></span>

<span data-ttu-id="ddea2-126">*Appsettings.json* dosyası aşağıdaki JSON gibi yapılandırılmış değerlerle hiyerarşik olabilir:</span><span class="sxs-lookup"><span data-stu-id="ddea2-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

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

<span data-ttu-id="ddea2-127">Önceki JSON ile sunulduğunda, yapılandırma sistemi alt değerleri düzleştirir ve tam nitelikli hiyerarşik yollarına başvurur.</span><span class="sxs-lookup"><span data-stu-id="ddea2-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="ddea2-128">Bir iki`:`nokta üst üste ( ) karakter hiyerarşideki her özelliği ayırır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="ddea2-129">Örneğin, yapılandırma anahtarı `section1:key0` nesneliteral `section1` `key0` değerine erişer.</span><span class="sxs-lookup"><span data-stu-id="ddea2-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="ddea2-130">Kullanıcı sırları</span><span class="sxs-lookup"><span data-stu-id="ddea2-130">User secrets</span></span>

<span data-ttu-id="ddea2-131">Kullanıcı sırları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ddea2-131">User secrets are:</span></span>

* <span data-ttu-id="ddea2-132">Uygulama geliştirme klasörünün dışında, geliştiricinin iş istasyonundaki bir JSON dosyasında depolanan yapılandırma değerleri.</span><span class="sxs-lookup"><span data-stu-id="ddea2-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="ddea2-133">Yalnızca `Development` çevrede çalışırken yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="ddea2-134">Belirli bir uygulamayla ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-134">Associated with a specific app.</span></span>
* <span data-ttu-id="ddea2-135">.NET Core CLI `user-secrets` komutu ile yönetilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="ddea2-136">`user-secrets` Komutu uygulayarak uygulamanızı sırların depolanması için yapılandırın:</span><span class="sxs-lookup"><span data-stu-id="ddea2-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="ddea2-137">Önceki komut proje `UserSecretsId` dosyasına bir öğe ekler.</span><span class="sxs-lookup"><span data-stu-id="ddea2-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="ddea2-138">Öğe, uygulama ile sırları ilişkilendirmek için kullanılan bir GUID içerir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="ddea2-139">Daha sonra `set` komutu ile bir sır tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="ddea2-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ddea2-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="ddea2-141">Önceki komut, yapılandırma `Parent:ApiKey` anahtarını bir geliştiricinin iş istasyonunda `12345`değeriyle birlikte kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="ddea2-142">Kullanıcı sırlarını oluşturma, depolama ve yönetme hakkında daha fazla bilgi [için, ASP.NET Core belgesinde uygulama sırlarınıgeliştirmede güvenli depolama](/aspnet/core/security/app-secrets) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ddea2-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="ddea2-143">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ddea2-143">Environment variables</span></span>

<span data-ttu-id="ddea2-144">Uygulama yapılandırmanıza yüklenen bir sonraki değerler kümesi, sistemin ortam değişkenleridir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="ddea2-145">Sisteminizin tüm ortam değişken ayarlarına artık yapılandırma API'si aracılığıyla erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="ddea2-146">Hiyerarşik değerler, uygulamanızın içinde okunduğunda düzleştirilmiş ve iki nokta üst üste karakterlerle ayrılır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="ddea2-147">Ancak, bazı işletim sistemleri iki nokta üst üste karakter ortamı değişken adlarını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ddea2-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="ddea2-148">ASP.NET Core, bu sınırlamayı, çift alt çizgiye`__`sahip değerleri erişildiğinde bir üst üste dönüştürerek gider.</span><span class="sxs-lookup"><span data-stu-id="ddea2-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="ddea2-149">Yukarıdaki `Parent:ApiKey` kullanıcı sırları bölümünden değer ortam değişkeni `Parent__ApiKey`ile geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="ddea2-150">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="ddea2-150">Command-line arguments</span></span>

<span data-ttu-id="ddea2-151">Yapılandırma, uygulamanız başlatıldığında komut satırı bağımsız değişkenleri olarak da sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="ddea2-152">Ayarlanacak yapılandırma değerinin`--`adını ve yapılandırılacak değeri belirtmek için çift çizgi () veya ileri çizgi ()`/`notunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="ddea2-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="ddea2-153">Sözdizimi aşağıdaki komutları benzer:</span><span class="sxs-lookup"><span data-stu-id="ddea2-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="ddea2-154">web.config dönüşü</span><span class="sxs-lookup"><span data-stu-id="ddea2-154">The return of web.config</span></span>

<span data-ttu-id="ddea2-155">Uygulamanızı IIS'de Windows'a dağıttıysanız, *web.config* dosyası uygulamanızı yönetmek için IIS'yi yapılandırmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="ddea2-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="ddea2-156">Varsayılan olarak, IIS ASP.NET Çekirdek Modülüne (ANCM) bir başvuru ekler.</span><span class="sxs-lookup"><span data-stu-id="ddea2-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="ddea2-157">ANCM, uygulamanızı Kestrel web sunucusu yerine barındıran yerel bir IIS modülüdür.</span><span class="sxs-lookup"><span data-stu-id="ddea2-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="ddea2-158">Bu *web.config* bölümü aşağıdaki XML biçimlendirmesini benzer:</span><span class="sxs-lookup"><span data-stu-id="ddea2-158">This *web.config* section resembles the following XML markup:</span></span>

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

<span data-ttu-id="ddea2-159">Uygulamaya özgü `environmentVariables` `aspNetCore` yapılandırma, öğedeki bir öğeyi iç içe alarak tanımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="ddea2-160">Bu bölümde tanımlanan değerler ASP.NET Core uygulamasına ortam değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="ddea2-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="ddea2-161">Ortam değişkenleri, uygulama nın başlangıç segmentinde uygun şekilde yüklenir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-161">The environment variables load appropriately during that segment of app startup.</span></span>

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

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="ddea2-162">Uygulamada yapılandırmayı okuma</span><span class="sxs-lookup"><span data-stu-id="ddea2-162">Read configuration in the app</span></span>

<span data-ttu-id="ddea2-163">ASP.NET Core arayüz üzerinden <xref:Microsoft.Extensions.Configuration.IConfiguration> uygulama yapılandırması sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddea2-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="ddea2-164">Bu yapılandırma arabirimi Blazor bileşenleriniz, Blazor sayfalarınız ve yapılandırmaya erişmesi gereken diğer ASP.NET Çekirdek yönetilen sınıf tarafından istenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="ddea2-165">ASP.NET Core çerçevesi bu arabirimi daha önce yapılandırılan çözümlenmiş yapılandırmayla otomatik olarak dolduracaktır.</span><span class="sxs-lookup"><span data-stu-id="ddea2-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="ddea2-166">Blazor sayfasında veya bir bileşenin Jilet biçimlendirmesinde, nesneye `IConfiguration` `@inject` *.jilet* dosyasının üst kısmındaki bir yönergeyi şu şekilde enjekte edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ddea2-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="ddea2-167">Bu önceki deyim, `IConfiguration` nesneyi `Configuration` Razor şablonunun geri kalanında değişken olarak kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="ddea2-168">Tek tek yapılandırma ayarları, dizinleyici parametresi olarak aranan yapılandırma ayar hiyerarşisi belirtilerek okunabilir:</span><span class="sxs-lookup"><span data-stu-id="ddea2-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="ddea2-169">Önceki örnekten bölüm1 yapılandırmasını almaya benzer <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> `GetSection("section1")` bir sözdizimi ile belirli bir konumda anahtar koleksiyonu almak için yöntemi kullanarak tüm yapılandırma bölümleri getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="ddea2-170">Güçlü bir şekilde yazılan yapılandırma</span><span class="sxs-lookup"><span data-stu-id="ddea2-170">Strongly typed configuration</span></span>

<span data-ttu-id="ddea2-171">Web Formları ile, <xref:System.Configuration.ConfigurationSection> tür ve ilişkili türlerden devralınan güçlü bir şekilde yazılan bir yapılandırma türü oluşturmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ddea2-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="ddea2-172">A, `ConfigurationSection` bu yapılandırma değerleri için bazı iş kurallarını ve işlemeyi yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddea2-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="ddea2-173">ASP.NET Çekirdek'te, yapılandırma değerlerini alacak bir sınıf hiyerarşisi belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="ddea2-174">Bu sınıflar:</span><span class="sxs-lookup"><span data-stu-id="ddea2-174">These classes:</span></span>

* <span data-ttu-id="ddea2-175">Bir üst sınıftan devralmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ddea2-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="ddea2-176">Yakalamak `public` istediğiniz yapılandırma yapısı için özellikleri ve tür başvuruları eşleşen özellikleri içermelidir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="ddea2-177">Önceki *appsettings.json* örneği için, değerleri yakalamak için aşağıdaki sınıfları tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ddea2-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

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

<span data-ttu-id="ddea2-178">Bu sınıf hiyerarşisi `Startup.ConfigureServices` yönteme aşağıdaki satırı ekleyerek doldurulabilir:</span><span class="sxs-lookup"><span data-stu-id="ddea2-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="ddea2-179">Uygulamanın geri kalanında, güçlü bir şekilde yazılan yapılandırma ayarlarını almak için sınıflara bir giriş parametresi veya jilet türü `@inject` `IOptions<MyConfig>` şablonlarında bir yönerge ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddea2-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="ddea2-180">Özellik, `IOptions<MyConfig>.Value` yapılandırma `MyConfig` ayarlarından doldurulan değeri verir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="ddea2-181">Seçenekler özelliği hakkında daha fazla [bilgi, ASP.NET Çekirdek belgesindeki Seçenekler deseninde](/aspnet/core/fundamentals/configuration/options#options-interfaces) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ddea2-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ddea2-182">[Önceki](middleware.md)
>[Sonraki](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="ddea2-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
