---
title: .NET 'teki yapılandırma sağlayıcıları
description: .NET uygulamalarını yapılandırmak için yapılandırma sağlayıcısı API 'sinin nasıl kullanıldığını öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.openlocfilehash: d5333e8e52feb7d28e2149a988dc7ce53a926a50
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874748"
---
# <a name="configuration-providers-in-net"></a><span data-ttu-id="40f66-103">.NET 'teki yapılandırma sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="40f66-103">Configuration providers in .NET</span></span>

<span data-ttu-id="40f66-104">Yapılandırma sağlayıcılarıyla .NET için yapılandırma mümkündür.</span><span class="sxs-lookup"><span data-stu-id="40f66-104">Configuration in .NET is possible with configuration providers.</span></span> <span data-ttu-id="40f66-105">Çeşitli yapılandırma kaynaklarını kullanan çeşitli sağlayıcı türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="40f66-105">There are several types of providers that rely on various configuration sources.</span></span> <span data-ttu-id="40f66-106">Bu makalede, tüm farklı yapılandırma sağlayıcılarının ve bunlara karşılık gelen kaynakların ayrıntıları yer alırlar.</span><span class="sxs-lookup"><span data-stu-id="40f66-106">This article details all of the different configuration providers and their corresponding sources.</span></span>

- [<span data-ttu-id="40f66-107">Dosya yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-107">File configuration provider</span></span>](#file-configuration-provider)
- [<span data-ttu-id="40f66-108">Ortam değişkeni yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-108">Environment variable configuration provider</span></span>](#environment-variable-configuration-provider)
- [<span data-ttu-id="40f66-109">Komut satırı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-109">Command-line configuration provider</span></span>](#command-line-configuration-provider)
- [<span data-ttu-id="40f66-110">Dosya başına anahtar yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-110">Key-per-file configuration provider</span></span>](#key-per-file-configuration-provider)
- [<span data-ttu-id="40f66-111">Bellek yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-111">Memory configuration provider</span></span>](#memory-configuration-provider)

## <a name="file-configuration-provider"></a><span data-ttu-id="40f66-112">Dosya yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-112">File configuration provider</span></span>

<span data-ttu-id="40f66-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> , dosya sisteminden yapılandırma yüklemeye yönelik temel sınıftır.</span><span class="sxs-lookup"><span data-stu-id="40f66-113"><xref:Microsoft.Extensions.Configuration.FileConfigurationProvider> is the base class for loading configuration from the file system.</span></span> <span data-ttu-id="40f66-114">Aşağıdaki yapılandırma sağlayıcıları öğesinden türetilir `FileConfigurationProvider` :</span><span class="sxs-lookup"><span data-stu-id="40f66-114">The following configuration providers derive from `FileConfigurationProvider`:</span></span>

- [<span data-ttu-id="40f66-115">JSON yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-115">JSON configuration provider</span></span>](#json-configuration-provider)
- [<span data-ttu-id="40f66-116">XML yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-116">XML configuration provider</span></span>](#xml-configuration-provider)
- [<span data-ttu-id="40f66-117">INı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-117">INI configuration provider</span></span>](#ini-configuration-provider)

### <a name="json-configuration-provider"></a><span data-ttu-id="40f66-118">JSON yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-118">JSON configuration provider</span></span>

<span data-ttu-id="40f66-119"><xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider>Sınıfı, BIR json dosyasından yapılandırma yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-119">The <xref:Microsoft.Extensions.Configuration.Json.JsonConfigurationProvider> class loads configuration from a JSON file.</span></span> <span data-ttu-id="40f66-120">[`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-120">Install the [`Microsoft.Extensions.Configuration.Json`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json) NuGet package.</span></span>

<span data-ttu-id="40f66-121">Aşırı yüklemeler şunları belirtebilir:</span><span class="sxs-lookup"><span data-stu-id="40f66-121">Overloads can specify:</span></span>

- <span data-ttu-id="40f66-122">Dosyanın isteğe bağlı olup olmadığı</span><span class="sxs-lookup"><span data-stu-id="40f66-122">Whether the file is optional</span></span>
- <span data-ttu-id="40f66-123">Dosya değişirse yapılandırmanın yeniden yüklenip yüklenmediğini belirtir</span><span class="sxs-lookup"><span data-stu-id="40f66-123">Whether the configuration is reloaded if the file changes</span></span>

<span data-ttu-id="40f66-124">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="40f66-124">Consider the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="1-33,37-38" highlight="17-23":::

<span data-ttu-id="40f66-125">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="40f66-125">The preceding code:</span></span>

- <span data-ttu-id="40f66-126">Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="40f66-126">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="40f66-127">On ve *appsettings* *appsettings.js* yüklemek için JSON yapılandırma sağlayıcısını `Environment` yapılandırır. aşağıdaki seçeneklere sahip *JSON* dosyaları:</span><span class="sxs-lookup"><span data-stu-id="40f66-127">Configures the JSON configuration provider to load the *appsettings.json* and  *appsettings*.`Environment`.*json* files with the following options:</span></span>
  - <span data-ttu-id="40f66-128">`optional: true`: Dosya isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40f66-128">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="40f66-129">`reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="40f66-129">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>

<span data-ttu-id="40f66-130">JSON ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="40f66-130">The JSON settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="40f66-131">Çeşitli yapılandırma ayarları ile dosyada bir örnek *appsettings.js* aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40f66-131">An example *appsettings.json* file with various configuration settings follows:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json":::

<span data-ttu-id="40f66-132"><xref:Microsoft.Extensions.Configuration.IConfigurationBuilder>Örnekten, yapılandırma sağlayıcıları eklendikten sonra <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> nesneyi almak için öğesini çağırabilirsiniz <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> .</span><span class="sxs-lookup"><span data-stu-id="40f66-132">From the <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance, after configuration providers have been added you can call <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder.Build?displayProperty=nameWithType> to get the <xref:Microsoft.Extensions.Configuration.IConfigurationRoot> object.</span></span> <span data-ttu-id="40f66-133">Yapılandırma kökü bir yapılandırma hiyerarşisinin kökünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="40f66-133">The configuration root represents the root of a configuration hierarchy.</span></span> <span data-ttu-id="40f66-134">Yapılandırma bölümleri, .NET nesnelerinin örneklerine bağlanabilir ve daha sonra <xref:Microsoft.Extensions.Options.IOptions%601> bağımlılık ekleme yoluyla olarak sağlanmış olur.</span><span class="sxs-lookup"><span data-stu-id="40f66-134">Sections from the configuration can be bound to instances of .NET objects, and later provided as <xref:Microsoft.Extensions.Options.IOptions%601> through dependency injection.</span></span>

<span data-ttu-id="40f66-135">`TransientFaultHandlingOptions`Aşağıdaki şekilde tanımlanan kayıt türünü göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="40f66-135">Consider the `TransientFaultHandlingOptions` record type defined as follows:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs":::

<span data-ttu-id="40f66-136">Kayıt türleri hakkında bilgi için bkz. [C# 9 ' da kayıt türleri](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="40f66-136">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="40f66-137">Aşağıdaki kod yapılandırma kökünü oluşturur, bir bölümü `TransientFaultHandlingOptions` kayıt türüne bağlar ve bağlı değerleri konsol penceresine yazdırır:</span><span class="sxs-lookup"><span data-stu-id="40f66-137">The following code builds the configuration root, binds a section to the `TransientFaultHandlingOptions` record type, and prints the bound values to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

<span data-ttu-id="40f66-138">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="40f66-138">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="34-36":::

### <a name="xml-configuration-provider"></a><span data-ttu-id="40f66-139">XML yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-139">XML configuration provider</span></span>

<span data-ttu-id="40f66-140"><xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider>Sınıfı, çalışma zamanında BIR XML dosyasındaki yapılandırmayı yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-140">The <xref:Microsoft.Extensions.Configuration.Xml.XmlConfigurationProvider> class loads configuration from an XML file at runtime.</span></span> <span data-ttu-id="40f66-141">[`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-141">Install the [`Microsoft.Extensions.Configuration.Xml`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Xml) NuGet package.</span></span>

<span data-ttu-id="40f66-142">Aşağıdaki kod XML yapılandırma sağlayıcısını kullanarak XML dosyalarının yapılandırmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40f66-142">The following code demonstrates configuration of XML files using the XML configuration provider.</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="1-28,46,52-53" highlight="17-28":::

<span data-ttu-id="40f66-143">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="40f66-143">The preceding code:</span></span>

- <span data-ttu-id="40f66-144">Yönteminde varsayılan olarak eklenmiş olan tüm mevcut yapılandırma sağlayıcılarını temizler <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> .</span><span class="sxs-lookup"><span data-stu-id="40f66-144">Clears all existing configuration providers that were added by default in the <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])> method.</span></span>
- <span data-ttu-id="40f66-145">, Aşağıdaki seçeneklerle *appsettings.xml* ve *repeating-example.xml* dosyalarını yükleyecek XML yapılandırma sağlayıcısını yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="40f66-145">Configures the XML configuration provider to load the *appsettings.xml* and *repeating-example.xml* files with the following options:</span></span>
  - <span data-ttu-id="40f66-146">`optional: true`: Dosya isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40f66-146">`optional: true`: The file is optional.</span></span>
  - <span data-ttu-id="40f66-147">`reloadOnChange: true` : Değişiklikler kaydedildiğinde dosya yeniden yüklenir.</span><span class="sxs-lookup"><span data-stu-id="40f66-147">`reloadOnChange: true` : The file is reloaded when changes are saved.</span></span>
- <span data-ttu-id="40f66-148">Ortam değişkenleri yapılandırma sağlayıcısını yapılandırır.</span><span class="sxs-lookup"><span data-stu-id="40f66-148">Configures the environment variables configuration provider.</span></span>
- <span data-ttu-id="40f66-149">Verilen bağımsız değişkenler içeriyorsa, komut satırı yapılandırma sağlayıcısını yapılandırır `args` .</span><span class="sxs-lookup"><span data-stu-id="40f66-149">Configures the command-line configuration provider if the given `args` contains arguments.</span></span>

<span data-ttu-id="40f66-150">XML ayarları, [ortam değişkenleri yapılandırma sağlayıcısı](#environment-variable-configuration-provider) ve [komut satırı yapılandırma sağlayıcısı](#command-line-configuration-provider)ayarları tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="40f66-150">The XML settings are overridden by settings in the [Environment variables configuration provider](#environment-variable-configuration-provider) and the [Command-line configuration provider](#command-line-configuration-provider).</span></span>

<span data-ttu-id="40f66-151">Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.xml* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40f66-151">An example *appsettings.xml* file with various configuration settings follows:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/appsettings.xml":::

<span data-ttu-id="40f66-152">Aynı öğe adını kullanan yinelenen öğeler, `name` özniteliği öğeleri ayırt etmek için kullanılacaksa çalışır:</span><span class="sxs-lookup"><span data-stu-id="40f66-152">Repeating elements that use the same element name work if the `name` attribute is used to distinguish the elements:</span></span>

:::code language="xml" source="snippets/configuration/console-xml/repeating-example.xml":::

<span data-ttu-id="40f66-153">Aşağıdaki kod, önceki yapılandırma dosyasını okur ve anahtarları ve değerleri görüntüler:</span><span class="sxs-lookup"><span data-stu-id="40f66-153">The following code reads the previous configuration file and displays the keys and values:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="30-45":::

<span data-ttu-id="40f66-154">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="40f66-154">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-xml/Program.cs" range="47-51":::

<span data-ttu-id="40f66-155">Öznitelikler, değerler sağlamak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="40f66-155">Attributes can be used to supply values:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <key attribute="value" />
  <section>
    <key attribute="value" />
  </section>
</configuration>
```

<span data-ttu-id="40f66-156">Önceki yapılandırma dosyası aşağıdaki anahtarları ile yükler `value` :</span><span class="sxs-lookup"><span data-stu-id="40f66-156">The previous configuration file loads the following keys with `value`:</span></span>

- `key:attribute`
- `section:key:attribute`

### <a name="ini-configuration-provider"></a><span data-ttu-id="40f66-157">INı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-157">INI configuration provider</span></span>

<span data-ttu-id="40f66-158"><xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider>Sınıfı, çalışma zamanında BIR INI dosyasındaki yapılandırmayı yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-158">The <xref:Microsoft.Extensions.Configuration.Ini.IniConfigurationProvider> class loads configuration from an INI file at runtime.</span></span> <span data-ttu-id="40f66-159">[`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)NuGet paketini yükler.</span><span class="sxs-lookup"><span data-stu-id="40f66-159">Install the [`Microsoft.Extensions.Configuration.Ini`](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Ini)  NuGet package.</span></span>

<span data-ttu-id="40f66-160">Aşağıdaki kod, tüm yapılandırma sağlayıcılarını temizler ve `IniConfigurationProvider` kaynak olarak ıkı INI dosyası ile ekler:</span><span class="sxs-lookup"><span data-stu-id="40f66-160">The following code clears all the configuration providers and adds the `IniConfigurationProvider` with two INI files as the source:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="1-31,38-39" highlight="18-24":::

<span data-ttu-id="40f66-161">Çeşitli yapılandırma ayarlarına sahip bir örnek *appsettings.ini* dosyası aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="40f66-161">An example *appsettings.ini* file with various configuration settings follows:</span></span>

:::code language="ini" source="snippets/configuration/console-ini/appsettings.ini":::

<span data-ttu-id="40f66-162">Aşağıdaki kod, önceki yapılandırma ayarlarını konsol penceresine yazarak görüntüler:</span><span class="sxs-lookup"><span data-stu-id="40f66-162">The following code displays the preceding configuration settings by writing them to the console window:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="26-30":::

<span data-ttu-id="40f66-163">Uygulama aşağıdaki örnek çıktıyı Yazar:</span><span class="sxs-lookup"><span data-stu-id="40f66-163">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/console-ini/Program.cs" range="32-37":::

## <a name="environment-variable-configuration-provider"></a><span data-ttu-id="40f66-164">Ortam değişkeni yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-164">Environment variable configuration provider</span></span>

<span data-ttu-id="40f66-165">Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> yapılandırma *appsettings.json*, appSettings sonrasında anahtar-değer çiftlerinde bulunan yapılandırmayı yükler *.* `Environment` *. JSON*ve gizli yönetici.</span><span class="sxs-lookup"><span data-stu-id="40f66-165">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.EnvironmentVariables.EnvironmentVariablesConfigurationProvider> loads configuration from environment variable key-value pairs after reading *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span> <span data-ttu-id="40f66-166">Bu nedenle, ortamdan okunan anahtar değerleri, *appsettings.json*, appSettings öğesinden okunan değerleri geçersiz kılar *.* `Environment` *. JSON*ve gizli yönetici.</span><span class="sxs-lookup"><span data-stu-id="40f66-166">Therefore, key values read from the environment override values read from *appsettings.json*, *appsettings.*`Environment`*.json*, and Secret manager.</span></span>

<span data-ttu-id="40f66-167">`:`Ayırıcı, tüm platformlarda ortam değişkeni hiyerarşik anahtarlarla birlikte çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="40f66-167">The `:` separator doesn't work with environment variable hierarchical keys on all platforms.</span></span> <span data-ttu-id="40f66-168">Çift alt çizgi ( `__` ) otomatik olarak bir ile değiştirilmiştir `:` ve tüm platformlar tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="40f66-168">The double underscore (`__`) is automatically replaced by a `:` and is supported by all platforms.</span></span> <span data-ttu-id="40f66-169">Örneğin, `:` ayırıcı [Bash](https://linuxhint.com/bash-environment-variables)tarafından desteklenmez, ancak `__` .</span><span class="sxs-lookup"><span data-stu-id="40f66-169">For example, the `:` separator is not supported by [Bash](https://linuxhint.com/bash-environment-variables), but `__` is.</span></span>

<span data-ttu-id="40f66-170">Aşağıdaki `set` Komutlar:</span><span class="sxs-lookup"><span data-stu-id="40f66-170">The following `set` commands:</span></span>

- <span data-ttu-id="40f66-171">Windows üzerinde önceki örneğin ortam anahtarlarını ve değerlerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="40f66-171">Set the environment keys and values of the preceding example on Windows.</span></span>
- <span data-ttu-id="40f66-172">Ayarları varsayılan değerlerinden değiştirerek test edin.</span><span class="sxs-lookup"><span data-stu-id="40f66-172">Test the settings by changing them from their default values.</span></span> <span data-ttu-id="40f66-173">`dotnet run`Komutun proje dizininde çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40f66-173">The `dotnet run` command must be run in the project directory.</span></span>

```dotnetcli
set SecretKey="Secret key from environment"
set TransientFaultHandlingOptions__Enabled="true"
set TransientFaultHandlingOptions__AutoRetryDelay="00:00:13"

dotnet run
```

<span data-ttu-id="40f66-174">Önceki ortam ayarları:</span><span class="sxs-lookup"><span data-stu-id="40f66-174">The preceding environment settings:</span></span>

- <span data-ttu-id="40f66-175">Yalnızca ' de ayarlanan komut penceresinden başlatılan işlemlerde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="40f66-175">Are only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="40f66-176">Visual Studio ile başlatılan Web Apps tarafından okunmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="40f66-176">Won't be read by web apps launched with Visual Studio.</span></span>

<span data-ttu-id="40f66-177">Aşağıdaki [Setx](/windows-server/administration/windows-commands/setx) komutları Windows üzerinde ortam anahtarlarını ve değerlerini ayarlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40f66-177">The following [setx](/windows-server/administration/windows-commands/setx) commands can be used to set the environment keys and values on Windows.</span></span> <span data-ttu-id="40f66-178">Farklı olarak `set` , `setx` ayarlar kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="40f66-178">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="40f66-179">`/M` değişkeni sistem ortamında ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40f66-179">`/M` sets the variable in the system environment.</span></span> <span data-ttu-id="40f66-180">`/M`Anahtar kullanılmazsa, bir kullanıcı ortam değişkeni ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="40f66-180">If the `/M` switch isn't used, a user environment variable is set.</span></span>

```dotnetcli
setx SecretKey "Secret key from setx environment" /M
setx TransientFaultHandlingOptions__Enabled "true" /M
setx TransientFaultHandlingOptions__AutoRetryDelay "00:00:05" /M

dotnet run
```

<span data-ttu-id="40f66-181">Yukarıdaki komutların ve appSettings *appsettings.js* geçersiz kılmasını test etmek *.* `Environment` *. JSON*:</span><span class="sxs-lookup"><span data-stu-id="40f66-181">To test that the preceding commands override *appsettings.json* and *appsettings.*`Environment`*.json*:</span></span>

- <span data-ttu-id="40f66-182">Visual Studio ile: Exit ve Visual Studio 'Yu yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="40f66-182">With Visual Studio: Exit and restart Visual Studio.</span></span>
- <span data-ttu-id="40f66-183">CLı ile: yeni bir komut penceresi başlatın ve girin `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="40f66-183">With the CLI: Start a new command window and enter `dotnet run`.</span></span>

<span data-ttu-id="40f66-184"><xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A>Ortam değişkenlerinin önekini belirtmek için bir dizeyle çağırın:</span><span class="sxs-lookup"><span data-stu-id="40f66-184">Call <xref:Microsoft.Extensions.Configuration.EnvironmentVariablesExtensions.AddEnvironmentVariables%2A> with a string to specify a prefix for environment variables:</span></span>

:::code language="csharp" source="snippets/configuration/console-env/Program.cs" highlight="15-16":::

<span data-ttu-id="40f66-185">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="40f66-185">In the preceding code:</span></span>

- <span data-ttu-id="40f66-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` Varsayılan yapılandırma sağlayıcılarından sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="40f66-186">`config.AddEnvironmentVariables(prefix: "CustomPrefix_")` is added after the default configuration providers.</span></span> <span data-ttu-id="40f66-187">Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="40f66-187">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>
- <span data-ttu-id="40f66-188">Önek ile ayarlanan ortam değişkenleri `CustomPrefix_` varsayılan yapılandırma sağlayıcılarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="40f66-188">Environment variables set with the `CustomPrefix_` prefix override the default configuration providers.</span></span> <span data-ttu-id="40f66-189">Bu, öneki olmayan ortam değişkenlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="40f66-189">This includes environment variables without the prefix.</span></span>

<span data-ttu-id="40f66-190">Yapılandırma anahtar-değer çiftleri okunduktan sonra önek çıkarılır.</span><span class="sxs-lookup"><span data-stu-id="40f66-190">The prefix is stripped off when the configuration key-value pairs are read.</span></span>

<span data-ttu-id="40f66-191">Aşağıdaki komutlar özel öneki test et:</span><span class="sxs-lookup"><span data-stu-id="40f66-191">The following commands test the custom prefix:</span></span>

```dotnetcli
set CustomPrefix__SecretKey="Secret key with CustomPrefix_ environment"
set CustomPrefix_TransientFaultHandlingOptions__Enabled=true
set CustomPrefix_TransientFaultHandlingOptions__AutoRetryDelay=00:00:21

dotnet run
```

<span data-ttu-id="40f66-192">Varsayılan yapılandırma, ön eki olan ortam değişkenlerini ve komut satırı bağımsız değişkenlerini yükler `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="40f66-192">The default configuration loads environment variables and command-line arguments prefixed with `DOTNET_`.</span></span> <span data-ttu-id="40f66-193">`DOTNET_`Ön ek, .NET tarafından [konak](generic-host.md#host-configuration) ve [uygulama yapılandırması](generic-host.md#app-configuration)için kullanılır, ancak kullanıcı yapılandırması için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="40f66-193">The `DOTNET_` prefix is used by .NET for [host](generic-host.md#host-configuration) and [app configuration](generic-host.md#app-configuration), but not for user configuration.</span></span>

<span data-ttu-id="40f66-194">Konak ve uygulama yapılandırması hakkında daha fazla bilgi için bkz. [.NET genel ana bilgisayar](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="40f66-194">For more information on host and app configuration, see [.NET Generic Host](generic-host.md).</span></span>

<span data-ttu-id="40f66-195">[Azure App Service](https://azure.microsoft.com/services/app-service), **Ayarlar > yapılandırma** sayfasında **Yeni uygulama ayarı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="40f66-195">On [Azure App Service](https://azure.microsoft.com/services/app-service), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="40f66-196">Azure App Service uygulama ayarları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="40f66-196">Azure App Service application settings are:</span></span>

- <span data-ttu-id="40f66-197">Rest 'de şifrelenir ve şifreli bir kanal üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="40f66-197">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="40f66-198">Ortam değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="40f66-198">Exposed as environment variables.</span></span>

### <a name="connection-string-prefixes"></a><span data-ttu-id="40f66-199">Bağlantı dizesi önekleri</span><span class="sxs-lookup"><span data-stu-id="40f66-199">Connection string prefixes</span></span>

<span data-ttu-id="40f66-200">Yapılandırma API 'sinin dört bağlantı dizesi ortam değişkeni için özel işleme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="40f66-200">The Configuration API has special processing rules for four connection string environment variables.</span></span> <span data-ttu-id="40f66-201">Bu bağlantı dizeleri, uygulama ortamı için Azure bağlantı dizelerini yapılandırmaya dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="40f66-201">These connection strings are involved in configuring Azure connection strings for the app environment.</span></span> <span data-ttu-id="40f66-202">Tabloda gösterilen öneklerle ortam değişkenleri, varsayılan yapılandırmayla veya uygulamasına hiçbir önek sağlanmadığında uygulamaya yüklenir `AddEnvironmentVariables` .</span><span class="sxs-lookup"><span data-stu-id="40f66-202">Environment variables with the prefixes shown in the table are loaded into the app with the default configuration or when no prefix is supplied to `AddEnvironmentVariables`.</span></span>

| <span data-ttu-id="40f66-203">Bağlantı dizesi öneki</span><span class="sxs-lookup"><span data-stu-id="40f66-203">Connection string prefix</span></span> | <span data-ttu-id="40f66-204">Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="40f66-204">Provider</span></span>                                                                |
|--------------------------|-------------------------------------------------------------------------|
| `CUSTOMCONNSTR_`         | <span data-ttu-id="40f66-205">Özel sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="40f66-205">Custom provider</span></span>                                                         |
| `MYSQLCONNSTR_`          | [<span data-ttu-id="40f66-206">MySQL</span><span class="sxs-lookup"><span data-stu-id="40f66-206">MySQL</span></span>](https://www.mysql.com)                                          |
| `SQLAZURECONNSTR_`       | [<span data-ttu-id="40f66-207">Azure SQL Veritabanı</span><span class="sxs-lookup"><span data-stu-id="40f66-207">Azure SQL Database</span></span>](https://azure.microsoft.com/services/sql-database) |
| `SQLCONNSTR_`            | [<span data-ttu-id="40f66-208">SQL Server</span><span class="sxs-lookup"><span data-stu-id="40f66-208">SQL Server</span></span>](https://www.microsoft.com/sql-server)                      |

<span data-ttu-id="40f66-209">Bir ortam değişkeni keşfedildiğinde ve tabloda gösterilen dört önekle yapılandırmaya yüklendiğinde:</span><span class="sxs-lookup"><span data-stu-id="40f66-209">When an environment variable is discovered and loaded into configuration with any of the four prefixes shown in the table:</span></span>

- <span data-ttu-id="40f66-210">Yapılandırma anahtarı, ortam değişkeni öneki kaldırılarak ve bir yapılandırma anahtarı bölümü () eklenerek oluşturulur `ConnectionStrings` .</span><span class="sxs-lookup"><span data-stu-id="40f66-210">The configuration key is created by removing the environment variable prefix and adding a configuration key section (`ConnectionStrings`).</span></span>
- <span data-ttu-id="40f66-211">Veritabanı bağlantı sağlayıcısını temsil eden yeni bir yapılandırma anahtar-değer çifti oluşturulur (için `CUSTOMCONNSTR_` , belirtilen sağlayıcı olmayan).</span><span class="sxs-lookup"><span data-stu-id="40f66-211">A new configuration key-value pair is created that represents the database connection provider (except for `CUSTOMCONNSTR_`, which has no stated provider).</span></span>

| <span data-ttu-id="40f66-212">Ortam değişkeni anahtarı</span><span class="sxs-lookup"><span data-stu-id="40f66-212">Environment variable key</span></span> | <span data-ttu-id="40f66-213">Dönüştürülen yapılandırma anahtarı</span><span class="sxs-lookup"><span data-stu-id="40f66-213">Converted configuration key</span></span> | <span data-ttu-id="40f66-214">Sağlayıcı yapılandırma girişi</span><span class="sxs-lookup"><span data-stu-id="40f66-214">Provider configuration entry</span></span>                                                    |
|--------------------------|-----------------------------|---------------------------------------------------------------------------------|
| `CUSTOMCONNSTR_{KEY}`    | `ConnectionStrings:{KEY}`   | <span data-ttu-id="40f66-215">Yapılandırma girişi oluşturulmamış.</span><span class="sxs-lookup"><span data-stu-id="40f66-215">Configuration entry not created.</span></span>                                                |
| `MYSQLCONNSTR_{KEY}`     | `ConnectionStrings:{KEY}`   | <span data-ttu-id="40f66-216">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="40f66-216">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="40f66-217">Değer: `MySql.Data.MySqlClient`</span><span class="sxs-lookup"><span data-stu-id="40f66-217">Value: `MySql.Data.MySqlClient`</span></span> |
| `SQLAZURECONNSTR_{KEY}`  | `ConnectionStrings:{KEY}`   | <span data-ttu-id="40f66-218">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="40f66-218">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="40f66-219">Değer: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="40f66-219">Value: `System.Data.SqlClient`</span></span>  |
| `SQLCONNSTR_{KEY}`       | `ConnectionStrings:{KEY}`   | <span data-ttu-id="40f66-220">Anahtar: `ConnectionStrings:{KEY}_ProviderName` :</span><span class="sxs-lookup"><span data-stu-id="40f66-220">Key: `ConnectionStrings:{KEY}_ProviderName`:</span></span><br><span data-ttu-id="40f66-221">Değer: `System.Data.SqlClient`</span><span class="sxs-lookup"><span data-stu-id="40f66-221">Value: `System.Data.SqlClient`</span></span>  |

### <a name="environment-variables-set-in-launchsettingsjson"></a><span data-ttu-id="40f66-222">launchSettings.jsüzerinde ayarlanan ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="40f66-222">Environment variables set in launchSettings.json</span></span>

<span data-ttu-id="40f66-223">*launchSettings.js* ' de ayarlanan ortam değişkenleri, Sistem ortamındaki kümeyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="40f66-223">Environment variables set in *launchSettings.json* override those set in the system environment.</span></span>

## <a name="command-line-configuration-provider"></a><span data-ttu-id="40f66-224">Komut satırı yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-224">Command-line configuration provider</span></span>

<span data-ttu-id="40f66-225">Varsayılan yapılandırmayı kullanarak, <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> aşağıdaki yapılandırma kaynaklarından sonra komut satırı bağımsız değişkeninden anahtar-değer çiftlerinden yapılandırma yükler:</span><span class="sxs-lookup"><span data-stu-id="40f66-225">Using the default configuration, the <xref:Microsoft.Extensions.Configuration.CommandLine.CommandLineConfigurationProvider> loads configuration from command-line argument key-value pairs after the following configuration sources:</span></span>

- <span data-ttu-id="40f66-226">Ve *appsettings* *appsettings.js* . `Environment` .. *JSON* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="40f66-226">*appsettings.json* and *appsettings*.`Environment`.*json* files.</span></span>
- <span data-ttu-id="40f66-227">Ortamdaki uygulama gizli dizileri (gizli yönetici) `Development` .</span><span class="sxs-lookup"><span data-stu-id="40f66-227">App secrets (Secret Manager) in the `Development` environment.</span></span>
- <span data-ttu-id="40f66-228">Ortam değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="40f66-228">Environment variables.</span></span>

<span data-ttu-id="40f66-229">Varsayılan olarak, komut satırı üzerinde ayarlanan yapılandırma değerleri, diğer tüm yapılandırma sağlayıcılarıyla ayarlanan yapılandırma değerlerini geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="40f66-229">By default, configuration values set on the command line override configuration values set with all the other configuration providers.</span></span>

### <a name="command-line-arguments"></a><span data-ttu-id="40f66-230">Komut satırı bağımsız değişkenleri</span><span class="sxs-lookup"><span data-stu-id="40f66-230">Command-line arguments</span></span>

<span data-ttu-id="40f66-231">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `=` :</span><span class="sxs-lookup"><span data-stu-id="40f66-231">The following command sets keys and values using `=`:</span></span>

```dotnetcli
dotnet run SecretKey="Secret key from command line"
```

<span data-ttu-id="40f66-232">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `/` :</span><span class="sxs-lookup"><span data-stu-id="40f66-232">The following command sets keys and values using `/`:</span></span>

```dotnetcli
dotnet run /SecretKey "Secret key set from forward slash"
```

<span data-ttu-id="40f66-233">Aşağıdaki komut kullanarak anahtarları ve değerleri ayarlar `--` :</span><span class="sxs-lookup"><span data-stu-id="40f66-233">The following command sets keys and values using `--`:</span></span>

```dotnetcli
dotnet run --SecretKey "Secret key set from double hyphen"
```

<span data-ttu-id="40f66-234">Anahtar değeri:</span><span class="sxs-lookup"><span data-stu-id="40f66-234">The key value:</span></span>

- <span data-ttu-id="40f66-235">`=`' İ izlemelidir, ya da anahtarın bir `--` `/` boşluk izleyen değeri veya öneki olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="40f66-235">Must follow `=`, or the key must have a prefix of `--` or `/` when the value follows a space.</span></span>
- <span data-ttu-id="40f66-236">Kullanılıyorsa gerekli değildir `=` .</span><span class="sxs-lookup"><span data-stu-id="40f66-236">Isn't required if `=` is used.</span></span> <span data-ttu-id="40f66-237">Örneğin, `SomeKey=`.</span><span class="sxs-lookup"><span data-stu-id="40f66-237">For example, `SomeKey=`.</span></span>

<span data-ttu-id="40f66-238">Aynı komut içinde, `=` bir boşluk kullanan anahtar-değer çiftleri ile birlikte kullanılan komut satırı bağımsız değişkeni anahtar-değer çiftlerini karıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="40f66-238">Within the same command, don't mix command-line argument key-value pairs that use `=` with key-value pairs that use a space.</span></span>

## <a name="key-per-file-configuration-provider"></a><span data-ttu-id="40f66-239">Dosya başına anahtar yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-239">Key-per-file configuration provider</span></span>

<span data-ttu-id="40f66-240">, <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> Dizin dosyalarını yapılandırma anahtar-değer çiftleri olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="40f66-240">The <xref:Microsoft.Extensions.Configuration.KeyPerFile.KeyPerFileConfigurationProvider> uses a directory's files as configuration key-value pairs.</span></span> <span data-ttu-id="40f66-241">Anahtar, dosya adıdır.</span><span class="sxs-lookup"><span data-stu-id="40f66-241">The key is the file name.</span></span> <span data-ttu-id="40f66-242">Değer, dosyanın içeriğidir.</span><span class="sxs-lookup"><span data-stu-id="40f66-242">The value is the file's contents.</span></span> <span data-ttu-id="40f66-243">Dosya başına anahtar yapılandırma sağlayıcısı Docker barındırma senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40f66-243">The Key-per-file configuration provider is used in Docker hosting scenarios.</span></span>

<span data-ttu-id="40f66-244">Dosya başına anahtar yapılandırmasını etkinleştirmek için, <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> bir örneğinde genişletme yöntemini çağırın <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder> .</span><span class="sxs-lookup"><span data-stu-id="40f66-244">To activate key-per-file configuration, call the <xref:Microsoft.Extensions.Configuration.KeyPerFileConfigurationBuilderExtensions.AddKeyPerFile%2A> extension method on an instance of <xref:Microsoft.Extensions.Configuration.ConfigurationBuilder>.</span></span> <span data-ttu-id="40f66-245">`directoryPath`Dosyaların mutlak bir yol olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40f66-245">The `directoryPath` to the files must be an absolute path.</span></span>

<span data-ttu-id="40f66-246">Aşırı yüklemeler belirtmeye izin ver:</span><span class="sxs-lookup"><span data-stu-id="40f66-246">Overloads permit specifying:</span></span>

- <span data-ttu-id="40f66-247">`Action<KeyPerFileConfigurationSource>`Kaynağı yapılandıran bir temsilci.</span><span class="sxs-lookup"><span data-stu-id="40f66-247">An `Action<KeyPerFileConfigurationSource>` delegate that configures the source.</span></span>
- <span data-ttu-id="40f66-248">Dizinin isteğe bağlı olup olmadığını ve dizinin yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="40f66-248">Whether the directory is optional and the path to the directory.</span></span>

<span data-ttu-id="40f66-249">Çift alt çizgi ( `__` ), dosya adlarında yapılandırma anahtarı sınırlayıcısı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="40f66-249">The double-underscore (`__`) is used as a configuration key delimiter in file names.</span></span> <span data-ttu-id="40f66-250">Örneğin, dosya adı `Logging__LogLevel__System` yapılandırma anahtarını üretir `Logging:LogLevel:System` .</span><span class="sxs-lookup"><span data-stu-id="40f66-250">For example, the file name `Logging__LogLevel__System` produces the configuration key `Logging:LogLevel:System`.</span></span>

<span data-ttu-id="40f66-251">`ConfigureAppConfiguration`Uygulamanın yapılandırmasını belirtmek için Konağı oluştururken çağırın:</span><span class="sxs-lookup"><span data-stu-id="40f66-251">Call `ConfigureAppConfiguration` when building the host to specify the app's configuration:</span></span>

```csharp
.ConfigureAppConfiguration((_, configuration) =>
{
    var path = Path.Combine(
        Directory.GetCurrentDirectory(), "path/to/files");

    configuration.AddKeyPerFile(directoryPath: path, optional: true);
})
```

## <a name="memory-configuration-provider"></a><span data-ttu-id="40f66-252">Bellek yapılandırma sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40f66-252">Memory configuration provider</span></span>

<span data-ttu-id="40f66-253">, <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> Yapılandırma anahtar-değer çiftleri olarak bellek içi koleksiyon kullanır.</span><span class="sxs-lookup"><span data-stu-id="40f66-253">The <xref:Microsoft.Extensions.Configuration.Memory.MemoryConfigurationProvider> uses an in-memory collection as configuration key-value pairs.</span></span>

<span data-ttu-id="40f66-254">Aşağıdaki kod, yapılandırma sistemine bir bellek koleksiyonu ekler:</span><span class="sxs-lookup"><span data-stu-id="40f66-254">The following code adds a memory collection to the configuration system:</span></span>

:::code language="csharp" source="snippets/configuration/console-memory/Program.cs" highlight="16-23":::

<span data-ttu-id="40f66-255">Yukarıdaki kodda, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> varsayılan yapılandırma sağlayıcılarından sonra bellek sağlayıcıyı ekler.</span><span class="sxs-lookup"><span data-stu-id="40f66-255">In the preceding code, <xref:Microsoft.Extensions.Configuration.MemoryConfigurationBuilderExtensions.AddInMemoryCollection(Microsoft.Extensions.Configuration.IConfigurationBuilder,System.Collections.Generic.IEnumerable{System.Collections.Generic.KeyValuePair{System.String,System.String}})?displayProperty=nameWithType> adds the memory provider after the default configuration providers.</span></span> <span data-ttu-id="40f66-256">Yapılandırma sağlayıcılarını sipariş eden bir örnek için bkz. [XML yapılandırma sağlayıcısı](#xml-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="40f66-256">For an example of ordering the configuration providers, see [XML configuration provider](#xml-configuration-provider).</span></span>

## <a name="see-also"></a><span data-ttu-id="40f66-257">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40f66-257">See also</span></span>

- [<span data-ttu-id="40f66-258">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="40f66-258">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="40f66-259">.NET genel ana bilgisayar</span><span class="sxs-lookup"><span data-stu-id="40f66-259">.NET Generic Host</span></span>](generic-host.md)
- [<span data-ttu-id="40f66-260">Özel yapılandırma sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="40f66-260">Implement a custom configuration provider</span></span>](custom-configuration-provider.md)
