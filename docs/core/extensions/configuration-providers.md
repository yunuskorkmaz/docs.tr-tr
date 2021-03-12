---
title: .NET 'teki yapılandırma sağlayıcıları
description: .NET uygulamalarını yapılandırmak için yapılandırma sağlayıcısı API 'sinin nasıl kullanıldığını öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 03/08/2021
ms.openlocfilehash: 5f248c93de1773a8bbe8209f002806fb196bb260
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102605015"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="0d947-103">.NET 'teki yapılandırma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="0d947-103">Configuration providers in .NET</span></span>

<span data-ttu-id="0d947-104">Yapılandırma sağlayıcılarıyla .NET için yapılandırma mümkündür.</span><span class="sxs-lookup"><span data-stu-id="0d947-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="0d947-105">Çeşitli yapılandırma kaynaklarını kullanan çeşitli sağlayıcı türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="0d947-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="0d947-106">Bu makalede, tüm farklı yapılandırma sağlayıcılarının ve bunlara karşılık gelen kaynakların ayrıntıları yer alırlar.</span><span class="sxs-lookup"><span data-stu-id="0d947-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="0d947-107">Dosya yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="0d947-108">Ortam değişkeni yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="0d947-109">Komut satırı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="0d947-110">Dosya başına anahtar yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="0d947-111">Bellek yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="0d947-112">Dosya yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-112">File configuration provider</span></span>

<span data-ttu-id="0d947-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> , dosya sisteminden yapılandırma yüklemeye yönelik temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="0d947-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="0d947-114">Aşağıdaki yapılandırma sağlayıcıları öğesinden türetilir `FileConfigurationProvider` :</span><span class="sxs-lookup"><span data-stu-id="0d947-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="0d947-115">JSON yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="0d947-116">XML yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="0d947-117">INı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="0d947-118">JSON yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-118">JSON configuration provider</span></span>

<span data-ttu-id="0d947-119"><xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider>Sınıfı, BIR json dosyasından yapılandırma yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="0d947-120">[`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="0d947-121">Aşırı yüklemeler şunları belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="0d947-121">Overloads can specify:</span></span>

- <span data-ttu-id="0d947-122">Dosyanın isteğe bağlı olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="0d947-122">Whether the file is optional</span></span>
- <span data-ttu-id="0d947-123">Dosya değişirse yapılandırmanın yeniden yüklenip yüklenmediğini belirtir</span><span class="sxs-lookup"><span data-stu-id="0d947-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="0d947-124">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="0d947-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-39,43-44" highlight="23-29":::

<span data-ttu-id="0d947-125">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="0d947-125">The preceding code:</span></span>

- <span data-ttu-id="0d947-126">Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="0d947-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="0d947-127">On ve *appsettings* *appsettings.js* yüklemek için JSON yapılandırma sağlayıcısını `Environment` yapılandırır. aşağıdaki seçeneklere sahip *JSON* dosyaları:</span><span class="sxs-lookup"><span data-stu-id="0d947-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="0d947-128">`optional: true`: Dosya isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d947-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="0d947-129">`reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0d947-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="0d947-130">JSON ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="0d947-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="0d947-131">Çeşitli yapılandırma ayarları ile dosyada bir örnek *appsettings.js* aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d947-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="0d947-132"><xref:Microsoft.Extensions.Configuration.IConfigurationBuilder>Örnekten, yapılandırma sağlayıcıları eklendikten sonra <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> nesneyi almak için öğesini çağırabilirsiniz <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> .</span><span class="sxs-lookup"><span data-stu-id="0d947-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="0d947-133">Yapılandırma kökü bir yapılandırma hiyerarşisinin kökünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0d947-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="0d947-134">Yapılandırma bölümleri, .NET nesnelerinin örneklerine bağlanabilir ve daha sonra <xref:Microsoft.Extensions.Options.IOptions%601> bağımlılık ekleme yoluyla olarak sağlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="0d947-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="0d947-135">`TransientFaultHandlingOptions`Aşağıdaki şekilde tanımlanan sınıfı göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="0d947-135">Consider the `TransientFaultHandlingOptions` class defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="0d947-136">Aşağıdaki kod yapılandırma kökünü oluşturur, bir bölümü `TransientFaultHandlingOptions` sınıf türüne bağlar ve bağlı değerleri konsol penceresine yazdırır:</span><span class="sxs-lookup"><span data-stu-id="0d947-136">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` class type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="0d947-137">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="0d947-137">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="40-42":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="0d947-138">XML yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-138">XML configuration provider</span></span>

<span data-ttu-id="0d947-139"><xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider>Sınıfı, çalışma zamanında BIR XML dosyasındaki yapılandırmayı yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-139">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="0d947-140">[`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-140">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="0d947-141">Aşağıdaki kod XML yapılandırma sağlayıcısını kullanarak XML dosyalarının yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d947-141">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-34,52,58-59" highlight="23-34":::

<span data-ttu-id="0d947-142">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="0d947-142">The preceding code:</span></span>

- <span data-ttu-id="0d947-143">Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="0d947-143">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="0d947-144">, Aşağıdaki seçeneklerle *appsettings.xml* ve *repeating-example.xml* dosyalarını yükleyecek XML yapılandırma sağlayıcısını yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="0d947-144">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="0d947-145">`optional: true`: Dosya isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="0d947-145">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="0d947-146">`reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0d947-146">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="0d947-147">Ortam değişkenleri yapılandırma sağlayıcısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="0d947-147">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="0d947-148">Verilen bağımsız değişkenler içeriyorsa, komut satırı yapılandırma sağlayıcısını yapılandırır `args` .</span><span class="sxs-lookup"><span data-stu-id="0d947-148">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="0d947-149">XML ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="0d947-149">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="0d947-150">Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.xml* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d947-150">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="0d947-151">Aynı öğe adını kullanan yinelenen öğeler, `name` özniteliği öğeleri ayırt etmek için kullanılacaksa çalışır:</span><span class="sxs-lookup"><span data-stu-id="0d947-151">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="0d947-152">Aşağıdaki kod, önceki yapılandırma dosyasını okur ve anahtarları ve değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0d947-152">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="36-51":::

<span data-ttu-id="0d947-153">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="0d947-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="53-57":::

<span data-ttu-id="0d947-154">Öznitelikler, değerler sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="0d947-154">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="0d947-155">Önceki yapılandırma dosyası aşağıdaki anahtarları ile yükler `value` :</span><span class="sxs-lookup"><span data-stu-id="0d947-155">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="0d947-156">INı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-156">INI configuration provider</span></span>

<span data-ttu-id="0d947-157"><xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider>Sınıfı, çalışma zamanında BIR INI dosyasındaki yapılandırmayı yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-157">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="0d947-158">[`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="0d947-158">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="0d947-159">Aşağıdaki kod, tüm yapılandırma sağlayıcılarını temizler ve `IniConfigurationProvider` kaynak olarak ıkı INI dosyası ile ekler:</span><span class="sxs-lookup"><span data-stu-id="0d947-159">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-37,44-45" highlight="24-30":::

<span data-ttu-id="0d947-160">Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.ini* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0d947-160">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="0d947-161">Aşağıdaki kod, önceki yapılandırma ayarlarını konsol penceresine yazarak görüntüler:</span><span class="sxs-lookup"><span data-stu-id="0d947-161">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-36":::

<span data-ttu-id="0d947-162">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="0d947-162">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="38-43":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="0d947-163">Ortam değişkeni yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-163">Environment variable configuration provider</span></span>

<span data-ttu-id="0d947-164">Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> yapılandırma *appsettings.json*, appSettings sonrasında anahtar-değer çiftlerinde bulunan yapılandırmayı yükler *.* `Environment` *. JSON* ve gizli yönetici.</span><span class="sxs-lookup"><span data-stu-id="0d947-164">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="0d947-165">Bu nedenle, ortamdan okunan anahtar değerleri, *appsettings.json*, appSettings öğesinden okunan değerleri geçersiz kılar *.* `Environment` *. JSON* ve gizli yönetici.</span><span class="sxs-lookup"><span data-stu-id="0d947-165">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="0d947-166">`:`Ayırıcı, tüm platformlarda ortam değişkeni hiyerarşik anahtarlarla birlikte çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="0d947-166">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="0d947-167">Çift alt çizgi ( `__` ) otomatik olarak bir ile değiştirilmiştir `:` ve tüm platformlar tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0d947-167">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="0d947-168">Örneğin, `:` ayırıcı [Bash](https://linuxhint.com/bash-environment-variables)tarafından desteklenmez, ancak `__` .</span><span class="sxs-lookup"><span data-stu-id="0d947-168">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="0d947-169">Aşağıdaki `set` Komutlar:</span><span class="sxs-lookup"><span data-stu-id="0d947-169">The following `set` commands:</span></span>

- <span data-ttu-id="0d947-170">Windows üzerinde önceki örneğin ortam anahtarlarını ve değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0d947-170">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="0d947-171">Ayarları varsayılan değerlerinden değiştirerek test edin.</span><span class="sxs-lookup"><span data-stu-id="0d947-171">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="0d947-172">`dotnet run`Komutun proje dizininde çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d947-172">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="0d947-173">Önceki ortam ayarları:</span><span class="sxs-lookup"><span data-stu-id="0d947-173">The preceding environment settings:</span></span>

- <span data-ttu-id="0d947-174">Yalnızca ' de ayarlanan komut penceresinden başlatılan işlemlerde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0d947-174">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="0d947-175">Visual Studio ile başlatılan Web Apps tarafından okunmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0d947-175">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="0d947-176">Aşağıdaki [Setx](/windows-server/administration/windows-commands/setx) komutları Windows üzerinde ortam anahtarlarını ve değerlerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0d947-176">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="0d947-177">Farklı olarak `set` , `setx` ayarlar kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="0d947-177">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="0d947-178">`/M` değişkeni sistem ortamında ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0d947-178">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="0d947-179">`/M`Anahtar kullanılmazsa, bir kullanıcı ortam değişkeni ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0d947-179">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="0d947-180">Yukarıdaki komutların ve appSettings *appsettings.js* geçersiz kılmasını test etmek *.* `Environment` *. JSON*:</span><span class="sxs-lookup"><span data-stu-id="0d947-180">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="0d947-181">Visual Studio ile: Exit ve Visual Studio 'Yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0d947-181">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="0d947-182">CLı ile: yeni bir komut penceresi başlatın ve girin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="0d947-182">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="0d947-183"><xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A>Ortam değişkenlerinin önekini belirtmek için bir dizeyle çağırın:</span><span class="sxs-lookup"><span data-stu-id="0d947-183">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="21-22":::

<span data-ttu-id="0d947-184">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="0d947-184">In the preceding code:</span></span>

- <span data-ttu-id="0d947-185">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` Varsayılan yapılandırma sağlayıcılarından sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="0d947-185">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="0d947-186">Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="0d947-186">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="0d947-187">Önek ile ayarlanan ortam değişkenleri `CustomPrefix_` varsayılan yapılandırma sağlayıcılarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0d947-187">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="0d947-188">Bu, öneki olmayan ortam değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="0d947-188">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="0d947-189">Yapılandırma anahtar-değer çiftleri okunduktan sonra önek çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="0d947-189">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="0d947-190">Aşağıdaki komutlar özel öneki test et:</span><span class="sxs-lookup"><span data-stu-id="0d947-190">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix__TransientFaultHandlingOptions__Enabled=true
set CustomPrefix__TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="0d947-191">Varsayılan yapılandırma, ön eki olan ortam değişkenlerini ve komut satırı bağımsız değişkenlerini yükler `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="0d947-191">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="0d947-192">`DOTNET_`Ön ek, .NET tarafından [konak](generic-host.md#host-configuration) ve [uygulama yapılandırması](generic-host.md#app-configuration)için kullanılır, ancak kullanıcı yapılandırması için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="0d947-192">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="0d947-193">Konak ve uygulama yapılandırması hakkında daha fazla bilgi için bkz. [.NET genel ana bilgisayar](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="0d947-193">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="0d947-194">[Azure App Service](https://azure.microsoft.com/services/app-service), **Ayarlar > yapılandırma** sayfasında **Yeni uygulama ayarı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="0d947-194">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="0d947-195">Azure App Service uygulama ayarları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0d947-195">Azure App Service application settings are:</span></span>

- <span data-ttu-id="0d947-196">Rest 'de şifrelenir ve şifreli bir kanal üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="0d947-196">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="0d947-197">Ortam değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="0d947-197">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="0d947-198">Bağlantı dizesi önekleri</span><span class="sxs-lookup"><span data-stu-id="0d947-198">Connection string prefixes</span></span>

<span data-ttu-id="0d947-199">Yapılandırma API 'sinin dört bağlantı dizesi ortam değişkeni için özel işleme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="0d947-199">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="0d947-200">Bu bağlantı dizeleri, uygulama ortamı için Azure bağlantı dizelerini yapılandırmaya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="0d947-200">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="0d947-201">Tabloda gösterilen öneklerle ortam değişkenleri, varsayılan yapılandırmayla veya uygulamasına hiçbir önek sağlanmadığında uygulamaya yüklenir `AddEnvironmentVariables` .</span><span class="sxs-lookup"><span data-stu-id="0d947-201">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="0d947-202">Bağlantı dizesi öneki</span><span class="sxs-lookup"><span data-stu-id="0d947-202">Connection string prefix</span></span> | <span data-ttu-id="0d947-203">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="0d947-203">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="0d947-204">Özel sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="0d947-204">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="0d947-205">MySQL</span><span class="sxs-lookup"><span data-stu-id="0d947-205">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="0d947-206">Azure SQL Veritabanı</span><span class="sxs-lookup"><span data-stu-id="0d947-206">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="0d947-207">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0d947-207">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="0d947-208">Bir ortam değişkeni keşfedildiğinde ve tabloda gösterilen dört önekle yapılandırmaya yüklendiğinde:</span><span class="sxs-lookup"><span data-stu-id="0d947-208">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="0d947-209">Yapılandırma anahtarı, ortam değişkeni öneki kaldırılarak ve bir yapılandırma anahtarı bölümü () eklenerek oluşturulur `ConnectionStrings` .</span><span class="sxs-lookup"><span data-stu-id="0d947-209">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="0d947-210">Veritabanı bağlantı sağlayıcısını temsil eden yeni bir yapılandırma anahtar-değer çifti oluşturulur (için `CUSTOMCONNSTR_` , belirtilen sağlayıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="0d947-210">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="0d947-211">Ortam değişkeni anahtarı</span><span class="sxs-lookup"><span data-stu-id="0d947-211">Environment variable key</span></span> | <span data-ttu-id="0d947-212">Dönüştürülen yapılandırma anahtarı</span><span class="sxs-lookup"><span data-stu-id="0d947-212">Converted configuration key</span></span> | <span data-ttu-id="0d947-213">Sağlayıcı yapılandırma girişi</span><span class="sxs-lookup"><span data-stu-id="0d947-213">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="0d947-214">Yapılandırma girişi oluşturulmamış.</span><span class="sxs-lookup"><span data-stu-id="0d947-214">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="0d947-215">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="0d947-215">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="0d947-216">Değer: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="0d947-216">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="0d947-217">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="0d947-217">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="0d947-218">Değer: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="0d947-218">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="0d947-219">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="0d947-219">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="0d947-220">Değer: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="0d947-220">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="0d947-221">launchSettings.jsüzerinde ayarlanan ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0d947-221">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="0d947-222">*launchSettings.js* ' de ayarlanan ortam değişkenleri, Sistem ortamındaki kümeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0d947-222">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="0d947-223">Komut satırı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-223">Command-line configuration provider</span></span>

<span data-ttu-id="0d947-224">Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> aşağıdaki yapılandırma kaynaklarından sonra komut satırı bağımsız değişkeninden anahtar-değer çiftlerinden yapılandırma yükler:</span><span class="sxs-lookup"><span data-stu-id="0d947-224">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="0d947-225">Ve *appsettings* *appsettings.js* . `Environment` .. *JSON* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="0d947-225">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="0d947-226">Ortamdaki uygulama gizli dizileri (gizli yönetici) `Development` .</span><span class="sxs-lookup"><span data-stu-id="0d947-226">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="0d947-227">Ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="0d947-227">Environment variables.</span></span>

<span data-ttu-id="0d947-228">Varsayılan olarak, komut satırı üzerinde ayarlanan yapılandırma değerleri, diğer tüm yapılandırma sağlayıcılarıyla ayarlanan yapılandırma değerlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="0d947-228">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="0d947-229">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0d947-229">Command-line arguments</span></span>

<span data-ttu-id="0d947-230">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `=` :</span><span class="sxs-lookup"><span data-stu-id="0d947-230">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="0d947-231">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `/` :</span><span class="sxs-lookup"><span data-stu-id="0d947-231">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="0d947-232">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `--` :</span><span class="sxs-lookup"><span data-stu-id="0d947-232">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="0d947-233">Anahtar değeri:</span><span class="sxs-lookup"><span data-stu-id="0d947-233">The key value:</span></span>

- <span data-ttu-id="0d947-234">`=`' İ izlemelidir, ya da anahtarın bir `--` `/` boşluk izleyen değeri veya öneki olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0d947-234">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="0d947-235">Kullanılıyorsa gerekli değildir `=` .</span><span class="sxs-lookup"><span data-stu-id="0d947-235">Isn't required if `=` is used.</span></span> <span data-ttu-id="0d947-236">Örneğin, `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="0d947-236">For example, `SomeKey=`.</span></span>

<span data-ttu-id="0d947-237">Aynı komut içinde, `=` bir boşluk kullanan anahtar-değer çiftleri ile birlikte kullanılan komut satırı bağımsız değişkeni anahtar-değer çiftlerini karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="0d947-237">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="0d947-238">Dosya başına anahtar yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-238">Key-per-file configuration provider</span></span>

<span data-ttu-id="0d947-239">, <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> Dizin dosyalarını yapılandırma anahtar-değer çiftleri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d947-239">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="0d947-240">Anahtar, dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="0d947-240">The key is the file name.</span></span> <span data-ttu-id="0d947-241">Değer, dosyanın içeriğidir.</span><span class="sxs-lookup"><span data-stu-id="0d947-241">The value is the file's contents.</span></span> <span data-ttu-id="0d947-242">Dosya başına anahtar yapılandırma sağlayıcısı Docker barındırma senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d947-242">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="0d947-243">Dosya başına anahtar yapılandırmasını etkinleştirmek için, <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> bir örneğinde genişletme yöntemini çağırın <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> .</span><span class="sxs-lookup"><span data-stu-id="0d947-243">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="0d947-244">`directoryPath`Dosyaların mutlak bir yol olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d947-244">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="0d947-245">Aşırı yüklemeler belirtmeye izin ver:</span><span class="sxs-lookup"><span data-stu-id="0d947-245">Overloads permit specifying:</span></span>

- <span data-ttu-id="0d947-246">`Action<KeyPerFileConfigurationSource>`Kaynağı yapılandıran bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="0d947-246">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="0d947-247">Dizinin isteğe bağlı olup olmadığını ve dizinin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d947-247">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="0d947-248">Çift alt çizgi ( `__` ), dosya adlarında yapılandırma anahtarı sınırlayıcısı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0d947-248">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="0d947-249">Örneğin, dosya adı `Logging__LogLevel__System` yapılandırma anahtarını üretir `Logging:LogLevel:System` .</span><span class="sxs-lookup"><span data-stu-id="0d947-249">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="0d947-250">`ConfigureAppConfiguration`Uygulamanın yapılandırmasını belirtmek için Konağı oluştururken çağırın:</span><span class="sxs-lookup"><span data-stu-id="0d947-250">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="0d947-251">Bellek yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0d947-251">Memory configuration provider</span></span>

<span data-ttu-id="0d947-252">, <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> Yapılandırma anahtar-değer çiftleri olarak bellek içi koleksiyon kullanır.</span><span class="sxs-lookup"><span data-stu-id="0d947-252">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="0d947-253">Aşağıdaki kod, yapılandırma sistemine bir bellek koleksiyonu ekler:</span><span class="sxs-lookup"><span data-stu-id="0d947-253">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="22-29":::

<span data-ttu-id="0d947-254">Yukarıdaki kodda, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> varsayılan yapılandırma sağlayıcılarından sonra bellek sağlayıcıyı ekler.</span><span class="sxs-lookup"><span data-stu-id="0d947-254">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="0d947-255">Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="0d947-255">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="0d947-256">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d947-256">See also</span></span>

- [<span data-ttu-id="0d947-257">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="0d947-257">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="0d947-258">.NET genel ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="0d947-258">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="0d947-259">Özel yapılandırma sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="0d947-259">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
