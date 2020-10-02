---
title: .NET oturumu açma
author: IEvangelist
description: Microsoft. Extensions. Logging NuGet paketi tarafından sunulan günlüğe kaydetme çerçevesini nasıl kullanacağınızı öğrenin.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: 2e6d8710015d8e998a9710f2cdeb86d925236196
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654835"
---
# <a name="logging-in-net"></a><span data-ttu-id="3e4eb-103">.NET oturumu açma</span><span class="sxs-lookup"><span data-stu-id="3e4eb-103">Logging in .NET</span></span>

<span data-ttu-id="3e4eb-104">.NET, çeşitli yerleşik ve üçüncü taraf oturum açma sağlayıcılarıyla birlikte çalışarak bir günlüğe kaydetme API 'sini destekler.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-104">.NET supports a logging API that works with a variety of built-in and third-party logging providers.</span></span> <span data-ttu-id="3e4eb-105">Bu makalede, yerleşik sağlayıcılarla günlüğe kaydetme API 'sinin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-105">This article shows how to use the logging API with built-in providers.</span></span> <span data-ttu-id="3e4eb-106">Bu makalede gösterilen kod örneklerinin çoğu, [genel ana bilgisayarı](generic-host.md)kullanan tüm .NET uygulamaları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-106">Most of the code examples shown in this article apply to any .NET app that uses the [Generic Host](generic-host.md).</span></span> <span data-ttu-id="3e4eb-107">Genel ana bilgisayarı kullanmayan uygulamalar için bkz. [konak konsol olmayan uygulama](#non-host-console-app).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-107">For apps that don't use the Generic Host, see [Non-host console app](#non-host-console-app).</span></span>

## <a name="create-logs"></a><span data-ttu-id="3e4eb-108">Günlükleri oluştur</span><span class="sxs-lookup"><span data-stu-id="3e4eb-108">Create logs</span></span>

<span data-ttu-id="3e4eb-109">Günlükler oluşturmak için <xref:Microsoft.Extensions.Logging.ILogger%601> [bağımlılık ekleme (dı)](dependency-injection.md)öğesinden bir nesne kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-109">To create logs, use an <xref:Microsoft.Extensions.Logging.ILogger%601> object from [dependency injection (DI)](dependency-injection.md).</span></span>

<span data-ttu-id="3e4eb-110">Aşağıdaki örnek:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-110">The following example:</span></span>

- <span data-ttu-id="3e4eb-111">`ILogger<Worker>`Türün tam adı olan bir günlük *kategorisini* kullanan bir günlükçü oluşturur `Worker` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-111">Creates a logger, `ILogger<Worker>`, which uses a log *category* of the fully qualified name of the type `Worker`.</span></span> <span data-ttu-id="3e4eb-112">Günlük kategorisi, her günlük ile ilişkili bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-112">The log category is a string that is associated with each log.</span></span>
- <span data-ttu-id="3e4eb-113">Bu <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> düzeyde günlüğe kaydedilecek çağrılar `Information` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-113">Calls <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> to log at the `Information` level.</span></span> <span data-ttu-id="3e4eb-114">Günlük *düzeyi* günlüğe kaydedilen etkinliğin önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-114">The Log *level* indicates the severity of the logged event.</span></span>

:::code language="csharp" source="snippets/configuration/worker-service/Worker.cs" range="9-24" highlight="12":::

<span data-ttu-id="3e4eb-115">[Düzeyler](#log-level) ve [Kategoriler](#log-category) Bu makalenin ilerleyen kısımlarında daha ayrıntılı olarak açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-115">[Levels](#log-level) and [categories](#log-category) are explained in more detail later in this article.</span></span>

## <a name="configure-logging"></a><span data-ttu-id="3e4eb-116">Günlüğe kaydetmeyi yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3e4eb-116">Configure logging</span></span>

<span data-ttu-id="3e4eb-117">Günlüğe kaydetme yapılandırması genellikle `Logging` *appSettings*'in bölümü tarafından sağlanır. `{Environment}` *. JSON* dosyaları.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-117">Logging configuration is commonly provided by the `Logging` section of *appsettings*.`{Environment}`*.json* files.</span></span> <span data-ttu-id="3e4eb-118">Aşağıdaki *appsettings.Development.js* dosyadaki .net Worker hizmet şablonları tarafından oluşturulmuştur:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-118">The following *appsettings.Development.json* file is generated by the .NET Worker service templates:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Development.json":::

<span data-ttu-id="3e4eb-119">Önceki JSON 'da:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-119">In the preceding JSON:</span></span>

- <span data-ttu-id="3e4eb-120">`"Default"`, `"Microsoft"` Ve `"Microsoft.Hosting.Lifetime"` kategorileri belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-120">The `"Default"`, `"Microsoft"`, and `"Microsoft.Hosting.Lifetime"` categories are specified.</span></span>
- <span data-ttu-id="3e4eb-121">`"Microsoft"`Kategori, ile başlayan tüm kategoriler için geçerlidir `"Microsoft"` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-121">The `"Microsoft"` category applies to all categories that start with `"Microsoft"`.</span></span>
- <span data-ttu-id="3e4eb-122">`"Microsoft"`Günlük düzeyindeki `Warning` ve daha yüksek kategori günlükleri.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-122">The `"Microsoft"` category logs at log level `Warning` and higher.</span></span>
- <span data-ttu-id="3e4eb-123">Kategori kategorisinden `"Microsoft.Hosting.Lifetime"` daha özeldir `"Microsoft"` , bu nedenle `"Microsoft.Hosting.Lifetime"` Kategori "Information" ve üzeri günlük düzeyinde günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-123">The `"Microsoft.Hosting.Lifetime"` category is more specific than the `"Microsoft"` category, so the `"Microsoft.Hosting.Lifetime"` category logs at log level "Information" and higher.</span></span>
- <span data-ttu-id="3e4eb-124">Belirli bir günlük sağlayıcısı belirtilmedi, bu nedenle `LogLevel` [Windows olay](logging-providers.md#windows-eventlog)günlüğü hariç tüm etkin günlük sağlayıcıları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-124">A specific log provider is not specified, so `LogLevel` applies to all the enabled logging providers except for the [Windows EventLog](logging-providers.md#windows-eventlog).</span></span>

<span data-ttu-id="3e4eb-125">`Logging`Özelliği <xref:Microsoft.Extensions.Logging.LogLevel> ve günlük sağlayıcısı özelliklerine sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-125">The `Logging` property can have <xref:Microsoft.Extensions.Logging.LogLevel> and log provider properties.</span></span> <span data-ttu-id="3e4eb-126">`LogLevel`Seçili kategoriler için günlüğe kaydedilecek en düşük [düzeyi](#log-level) belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-126">The `LogLevel` specifies the minimum [level](#log-level) to log for selected categories.</span></span> <span data-ttu-id="3e4eb-127">Önceki JSON 'da `Information` ve `Warning` günlük düzeyleri belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-127">In the preceding JSON, `Information` and `Warning` log levels are specified.</span></span> <span data-ttu-id="3e4eb-128">`LogLevel` Günlüğün önem derecesini ve 0 ile 6 arasındaki aralıkları belirtir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-128">`LogLevel` indicates the severity of the log and ranges from 0 to 6:</span></span>

<span data-ttu-id="3e4eb-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5 ve `None` = 6.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-129">`Trace` = 0, `Debug` = 1, `Information` = 2, `Warning` = 3, `Error` = 4, `Critical` = 5, and `None` = 6.</span></span>

<span data-ttu-id="3e4eb-130">Bir `LogLevel` belirtildiğinde, belirtilen düzeydeki ve daha yüksek iletiler için günlüğe kaydetme etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-130">When a `LogLevel` is specified, logging is enabled for messages at the specified level and higher.</span></span> <span data-ttu-id="3e4eb-131">Önceki JSON 'da `Default` Kategori, ve üzeri için günlüğe kaydedilir `Information` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-131">In the preceding JSON, the `Default` category is logged for `Information` and higher.</span></span> <span data-ttu-id="3e4eb-132">Örneğin,, `Information` , `Warning` `Error` ve `Critical` iletileri günlüğe kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-132">For example, `Information`, `Warning`, `Error`, and `Critical` messages are logged.</span></span> <span data-ttu-id="3e4eb-133">Hayır `LogLevel` belirtilmemişse, günlüğe kaydetme varsayılan olarak `Information` düzeydir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-133">If no `LogLevel` is specified, logging defaults to the `Information` level.</span></span> <span data-ttu-id="3e4eb-134">Daha fazla bilgi için bkz. [günlük düzeyleri](#log-level).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-134">For more information, see [Log levels](#log-level).</span></span>

<span data-ttu-id="3e4eb-135">Sağlayıcı özelliği, bir özelliği belirtebilir `LogLevel` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-135">A provider property can specify a `LogLevel` property.</span></span> <span data-ttu-id="3e4eb-136">`LogLevel` sağlayıcı altında, bu sağlayıcının günlüğe kaydedilecek düzeyleri belirtir ve sağlayıcı olmayan günlük ayarlarını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-136">`LogLevel` under a provider specifies levels to log for that provider, and overrides the non-provider log settings.</span></span> <span data-ttu-id="3e4eb-137">Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-137">Consider the following *appsettings.json* file:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Staging.json":::

<span data-ttu-id="3e4eb-138">`Logging.{ProviderName}.LogLevel`' Deki geçersiz kılma ayarlarındaki ayarlar `Logging.LogLevel` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-138">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="3e4eb-139">Önceki JSON 'da, `Debug` sağlayıcının varsayılan günlük düzeyi şu şekilde ayarlanır `Information` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-139">In the preceding JSON, the `Debug` provider's default log level is set to `Information`:</span></span>

`Logging:Debug:LogLevel:Default:Information`

<span data-ttu-id="3e4eb-140">Yukarıdaki ayar, `Information` hariç her kategori için günlük düzeyini belirtir `Logging:Debug:` `Microsoft.Hosting` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-140">The preceding setting specifies the `Information` log level for every `Logging:Debug:` category except `Microsoft.Hosting`.</span></span> <span data-ttu-id="3e4eb-141">Belirli bir kategori listelendiğinde, belirtilen kategori varsayılan kategoriyi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-141">When a specific category is listed, the specific category overrides the default category.</span></span> <span data-ttu-id="3e4eb-142">Önceki JSON 'da `Logging:Debug:LogLevel` Kategoriler `"Microsoft.Hosting"` ve `"Default"` içindeki ayarları geçersiz kılın `Logging:LogLevel`</span><span class="sxs-lookup"><span data-stu-id="3e4eb-142">In the preceding JSON, the `Logging:Debug:LogLevel` categories `"Microsoft.Hosting"` and `"Default"` override the settings in `Logging:LogLevel`</span></span>

<span data-ttu-id="3e4eb-143">En düşük günlük düzeyi şu şekilde belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-143">The minimum log level can be specified for any of:</span></span>

- <span data-ttu-id="3e4eb-144">Belirli sağlayıcılar: Örneğin, `Logging:EventSource:LogLevel:Default:Information`</span><span class="sxs-lookup"><span data-stu-id="3e4eb-144">Specific providers:  For example, `Logging:EventSource:LogLevel:Default:Information`</span></span>
- <span data-ttu-id="3e4eb-145">Belirli Kategoriler: Örneğin, `Logging:LogLevel:Microsoft:Warning`</span><span class="sxs-lookup"><span data-stu-id="3e4eb-145">Specific categories: For example, `Logging:LogLevel:Microsoft:Warning`</span></span>
- <span data-ttu-id="3e4eb-146">Tüm sağlayıcılar ve tüm Kategoriler: `Logging:LogLevel:Default:Warning`</span><span class="sxs-lookup"><span data-stu-id="3e4eb-146">All providers and all categories: `Logging:LogLevel:Default:Warning`</span></span>

<span data-ttu-id="3e4eb-147">Minimum düzeyin altındaki tüm Günlükler şu ***değildir***:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-147">Any logs below the minimum level are ***not***:</span></span>

- <span data-ttu-id="3e4eb-148">Sağlayıcıya geçirildi.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-148">Passed to the provider.</span></span>
- <span data-ttu-id="3e4eb-149">Günlüğe kaydedilir veya gösterilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-149">Logged or displayed.</span></span>

<span data-ttu-id="3e4eb-150">Tüm günlükleri gizlemek için [LogLevel. None](xref:Microsoft.Extensions.Logging.LogLevel)belirtin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-150">To suppress all logs, specify [LogLevel.None](xref:Microsoft.Extensions.Logging.LogLevel).</span></span> <span data-ttu-id="3e4eb-151">`LogLevel.None` 6 değerine sahiptir `LogLevel.Critical` (5).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-151">`LogLevel.None` has a value of 6, which is higher than `LogLevel.Critical` (5).</span></span>

<span data-ttu-id="3e4eb-152">Bir sağlayıcı, [günlük kapsamlarını](#log-scopes)destekliyorsa, etkinleştirilip etkinleştirilmeyeceğini `IncludeScopes` belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-152">If a provider supports [log scopes](#log-scopes), `IncludeScopes` indicates whether they're enabled.</span></span> <span data-ttu-id="3e4eb-153">Daha fazla bilgi için bkz. [günlük kapsamları](#log-scopes)</span><span class="sxs-lookup"><span data-stu-id="3e4eb-153">For more information, see [log scopes](#log-scopes)</span></span>

<span data-ttu-id="3e4eb-154">Aşağıdaki *appsettings.js* dosyadaki tüm yerleşik sağlayıcıların ayarlarını içerir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-154">The following *appsettings.json* file contains settings for all of the built-in providers:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.Production.json":::

<span data-ttu-id="3e4eb-155">Yukarıdaki örnekte:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-155">In the preceding sample:</span></span>

- <span data-ttu-id="3e4eb-156">Kategoriler ve düzeyler önerilen değerler değildir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-156">The categories and levels are not suggested values.</span></span> <span data-ttu-id="3e4eb-157">Varsayılan tüm sağlayıcıları göstermek için örnek sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-157">The sample is provided to show all the default providers.</span></span>
- <span data-ttu-id="3e4eb-158">`Logging.{ProviderName}.LogLevel`' Deki geçersiz kılma ayarlarındaki ayarlar `Logging.LogLevel` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-158">Settings in `Logging.{ProviderName}.LogLevel` override settings in `Logging.LogLevel`.</span></span> <span data-ttu-id="3e4eb-159">Örneğin, içindeki düzeyi `Debug.LogLevel.Default` içindeki düzeyi geçersiz kılar `LogLevel.Default` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-159">For example, the level in `Debug.LogLevel.Default` overrides the level in `LogLevel.Default`.</span></span>
- <span data-ttu-id="3e4eb-160">Her sağlayıcının *diğer adı* kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-160">Each provider's *alias* is used.</span></span> <span data-ttu-id="3e4eb-161">Her sağlayıcı, tam nitelikli tür adı yerine yapılandırmada kullanılabilecek bir *diğer ad* tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-161">Each provider defines an *alias* that can be used in configuration in place of the fully qualified type name.</span></span> <span data-ttu-id="3e4eb-162">Yerleşik sağlayıcıların diğer adları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-162">The built-in providers' aliases are:</span></span>
  - <span data-ttu-id="3e4eb-163">Konsol</span><span class="sxs-lookup"><span data-stu-id="3e4eb-163">Console</span></span>
  - <span data-ttu-id="3e4eb-164">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3e4eb-164">Debug</span></span>
  - <span data-ttu-id="3e4eb-165">EventSource</span><span class="sxs-lookup"><span data-stu-id="3e4eb-165">EventSource</span></span>
  - <span data-ttu-id="3e4eb-166">EventLog</span><span class="sxs-lookup"><span data-stu-id="3e4eb-166">EventLog</span></span>
  - <span data-ttu-id="3e4eb-167">AzureAppServicesFile</span><span class="sxs-lookup"><span data-stu-id="3e4eb-167">AzureAppServicesFile</span></span>
  - <span data-ttu-id="3e4eb-168">AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="3e4eb-168">AzureAppServicesBlob</span></span>
  - <span data-ttu-id="3e4eb-169">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="3e4eb-169">ApplicationInsights</span></span>

### <a name="set-log-level-by-command-line-environment-variables-and-other-configuration"></a><span data-ttu-id="3e4eb-170">Günlük düzeyini komut satırı, ortam değişkenleri ve diğer yapılandırma ile ayarlama</span><span class="sxs-lookup"><span data-stu-id="3e4eb-170">Set log level by command line, environment variables, and other configuration</span></span>

<span data-ttu-id="3e4eb-171">Günlük düzeyi herhangi bir [yapılandırma sağlayıcısından](configuration-providers.md)ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-171">Log level can be set by any of the [configuration providers](configuration-providers.md).</span></span>

<span data-ttu-id="3e4eb-172">Aşağıdaki komutlar:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-172">The following commands:</span></span>

- <span data-ttu-id="3e4eb-173">Ortam anahtarını `Logging:LogLevel:Microsoft` Windows üzerinde bir değeri olarak ayarlayın `Information` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-173">Set the environment key `Logging:LogLevel:Microsoft` to a value of `Information` on Windows.</span></span>
- <span data-ttu-id="3e4eb-174">.NET Worker hizmeti şablonlarıyla oluşturulan bir uygulamayı kullanırken ayarları test edin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-174">Test the settings when using an app created with the .NET Worker service templates.</span></span> <span data-ttu-id="3e4eb-175">`dotnet run`Komutun kullanıldıktan sonra proje dizininde çalıştırılması gerekir `set` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-175">The `dotnet run` command must be run in the project directory after using `set`.</span></span>

```cmd
set Logging__LogLevel__Microsoft=Information
dotnet run
```

<span data-ttu-id="3e4eb-176">Önceki ortam ayarı:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-176">The preceding environment setting:</span></span>

- <span data-ttu-id="3e4eb-177">Yalnızca ' de ayarlanan komut penceresinden başlatılan işlemlerde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-177">Is only set in processes launched from the command window they were set in.</span></span>
- <span data-ttu-id="3e4eb-178">Visual Studio ile başlatılan uygulamalar tarafından okunamaz.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-178">Isn't read by apps launched with Visual Studio.</span></span>

<span data-ttu-id="3e4eb-179">Aşağıdaki [Setx](/windows-server/administration/windows-commands/setx) komutu, Windows 'daki ortam anahtarını ve değerini de ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-179">The following [setx](/windows-server/administration/windows-commands/setx) command also sets the environment key and value on Windows.</span></span> <span data-ttu-id="3e4eb-180">Farklı olarak `set` , `setx` ayarlar kalıcı hale getirilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-180">Unlike `set`, `setx` settings are persisted.</span></span> <span data-ttu-id="3e4eb-181">`/M`Anahtar, değişkeni sistem ortamında ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-181">The `/M` switch sets the variable in the system environment.</span></span> <span data-ttu-id="3e4eb-182">`/M`Kullanılmazsa, bir kullanıcı ortam değişkeni ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-182">If `/M` isn't used, a user environment variable is set.</span></span>

```cmd
setx Logging__LogLevel__Microsoft=Information /M
```

<span data-ttu-id="3e4eb-183">[Azure App Service](https://azure.microsoft.com/services/app-service/), **Ayarlar > yapılandırma** sayfasında **Yeni uygulama ayarı** ' nı seçin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-183">On [Azure App Service](https://azure.microsoft.com/services/app-service/), select **New application setting** on the **Settings > Configuration** page.</span></span> <span data-ttu-id="3e4eb-184">Azure App Service uygulama ayarları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-184">Azure App Service application settings are:</span></span>

- <span data-ttu-id="3e4eb-185">Rest 'de şifrelenir ve şifreli bir kanal üzerinden iletilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-185">Encrypted at rest and transmitted over an encrypted channel.</span></span>
- <span data-ttu-id="3e4eb-186">Ortam değişkenleri olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-186">Exposed as environment variables.</span></span>

<span data-ttu-id="3e4eb-187">Ortam değişkenlerini kullanarak .NET yapılandırma değerlerini ayarlama hakkında daha fazla bilgi için bkz. [ortam değişkenleri](configuration-providers.md#environment-variable-configuration-provider).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-187">For more information on setting .NET configuration values using environment variables, see [environment variables](configuration-providers.md#environment-variable-configuration-provider).</span></span>

## <a name="how-filtering-rules-are-applied"></a><span data-ttu-id="3e4eb-188">Filtreleme kuralları nasıl uygulanır</span><span class="sxs-lookup"><span data-stu-id="3e4eb-188">How filtering rules are applied</span></span>

<span data-ttu-id="3e4eb-189">Bir <xref:Microsoft.Extensions.Logging.ILogger%601> nesne oluşturulduğunda, <xref:Microsoft.Extensions.Logging.ILoggerFactory> nesne bu günlükçü için uygulanacak her sağlayıcı için tek bir kural seçer.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-189">When an <xref:Microsoft.Extensions.Logging.ILogger%601> object is created, the <xref:Microsoft.Extensions.Logging.ILoggerFactory> object selects a single rule per provider to apply to that logger.</span></span> <span data-ttu-id="3e4eb-190">Bir örnek tarafından yazılan tüm iletiler `ILogger` , seçilen kurallara göre filtrelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-190">All messages written by an `ILogger` instance are filtered based on the selected rules.</span></span> <span data-ttu-id="3e4eb-191">Her sağlayıcı ve kategori çifti için en özel kural, kullanılabilir kurallardan seçilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-191">The most specific rule for each provider and category pair is selected from the available rules.</span></span>

<span data-ttu-id="3e4eb-192">Belirli bir kategori için oluşturulan her sağlayıcı için aşağıdaki algoritma kullanılır `ILogger` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-192">The following algorithm is used for each provider when an `ILogger` is created for a given category:</span></span>

- <span data-ttu-id="3e4eb-193">Sağlayıcı veya diğer adıyla eşleşen tüm kuralları seçin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-193">Select all rules that match the provider or its alias.</span></span> <span data-ttu-id="3e4eb-194">Hiçbir eşleşme bulunmazsa, boş bir sağlayıcıya sahip tüm kurallar ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-194">If no match is found, select all rules with an empty provider.</span></span>
- <span data-ttu-id="3e4eb-195">Önceki adımın sonucunda, en uzun eşleşen kategori ön ekine sahip kurallar ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-195">From the result of the preceding step, select rules with longest matching category prefix.</span></span> <span data-ttu-id="3e4eb-196">Eşleşme bulunmazsa, kategori belirtmeyen tüm kuralları seçin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-196">If no match is found, select all rules that don't specify a category.</span></span>
- <span data-ttu-id="3e4eb-197">Birden çok kural seçilirse, **son** olanı götürün.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-197">If multiple rules are selected, take the **last** one.</span></span>
- <span data-ttu-id="3e4eb-198">Hiçbir kural seçilmemişse, <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> En düşük günlük düzeyini belirtmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-198">If no rules are selected, use <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.SetMinimumLevel(Microsoft.Extensions.Logging.ILoggingBuilder,Microsoft.Extensions.Logging.LogLevel)?displayProperty=nameWithType> to specify the minimum logging level.</span></span>

## <a name="log-category"></a><span data-ttu-id="3e4eb-199">Günlük kategorisi</span><span class="sxs-lookup"><span data-stu-id="3e4eb-199">Log category</span></span>

<span data-ttu-id="3e4eb-200">Bir `ILogger` nesne oluşturulduğunda, bir *Kategori* belirtilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-200">When an `ILogger` object is created, a *category* is specified.</span></span> <span data-ttu-id="3e4eb-201">Bu kategori, bu örneği tarafından oluşturulan her günlük iletisine dahildir `ILogger` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-201">That category is included with each log message created by that instance of `ILogger`.</span></span> <span data-ttu-id="3e4eb-202">Kategori dizesi rastgele, ancak kural sınıf adını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-202">The category string is arbitrary, but the convention is to use the class name.</span></span> <span data-ttu-id="3e4eb-203">Örneğin, bir hizmet içeren bir uygulamada aşağıdaki nesne gibi bir, kategori şöyle olabilir `"Example.DefaultService"` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-203">For example, in an application with a service define like the following object, the category might be `"Example.DefaultService"`:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger<DefaultService> _logger;

        public DefaultService(ILogger<DefaultService> logger) =>
            _logger = logger;

        // ...
    }
}
```

<span data-ttu-id="3e4eb-204">Kategoriyi açıkça belirtmek için şunu çağırın <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-204">To explicitly specify the category, call <xref:Microsoft.Extensions.Logging.LoggerFactory.CreateLogger%2A?displayProperty=nameWithType>:</span></span>

```csharp
namespace Example
{
    public class DefaultService : IService
    {
        private readonly ILogger _logger;

        public DefaultService(ILoggerFactory loggerFactory) =>
            _logger = logger.CreateLogger("CustomCategory");

        // ...
    }
}
```

<span data-ttu-id="3e4eb-205">`CreateLogger`Sabit bir adla çağırmak, olayların kategoriye göre düzenlenebilmesi için birden çok yöntemde kullanıldığında faydalı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-205">Calling `CreateLogger` with a fixed name can be useful when used in multiple methods so the events can be organized by category.</span></span>

<span data-ttu-id="3e4eb-206">`ILogger<T>` , `CreateLogger` tam nitelikli tür adı ile çağırma ile eşdeğerdir `T` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-206">`ILogger<T>` is equivalent to calling `CreateLogger` with the fully qualified type name of `T`.</span></span>

## <a name="log-level"></a><span data-ttu-id="3e4eb-207">Günlük düzeyi</span><span class="sxs-lookup"><span data-stu-id="3e4eb-207">Log level</span></span>

<span data-ttu-id="3e4eb-208">Aşağıdaki tabloda <xref:Microsoft.Extensions.Logging.LogLevel> değerler, kolaylık `Log{LogLevel}` genişletme yöntemi ve önerilen kullanım listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-208">The following table lists the <xref:Microsoft.Extensions.Logging.LogLevel> values, the convenience `Log{LogLevel}` extension method, and the suggested usage:</span></span>

| <span data-ttu-id="3e4eb-209">LogLevel</span><span class="sxs-lookup"><span data-stu-id="3e4eb-209">LogLevel</span></span> | <span data-ttu-id="3e4eb-210">Değer</span><span class="sxs-lookup"><span data-stu-id="3e4eb-210">Value</span></span> | <span data-ttu-id="3e4eb-211">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3e4eb-211">Method</span></span> | <span data-ttu-id="3e4eb-212">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e4eb-212">Description</span></span> |
|--|--|--|--|
| [<span data-ttu-id="3e4eb-213">İzleme</span><span class="sxs-lookup"><span data-stu-id="3e4eb-213">Trace</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-214">0</span><span class="sxs-lookup"><span data-stu-id="3e4eb-214">0</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogTrace%2A> | <span data-ttu-id="3e4eb-215">En ayrıntılı iletileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-215">Contain the most detailed messages.</span></span> <span data-ttu-id="3e4eb-216">Bu iletilerde hassas uygulama verileri bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-216">These messages may contain sensitive app data.</span></span> <span data-ttu-id="3e4eb-217">Bu iletiler varsayılan olarak devre dışıdır ve üretimde ***etkinleştirilmemelidir.***</span><span class="sxs-lookup"><span data-stu-id="3e4eb-217">These messages are disabled by default and should ***not*** be enabled in production.</span></span> |
| [<span data-ttu-id="3e4eb-218">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3e4eb-218">Debug</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-219">1</span><span class="sxs-lookup"><span data-stu-id="3e4eb-219">1</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> | <span data-ttu-id="3e4eb-220">Hata ayıklama ve geliştirme için.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-220">For debugging and development.</span></span> <span data-ttu-id="3e4eb-221">Yüksek hacimden dolayı üretimde dikkatli olarak kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-221">Use with caution in production due to the high volume.</span></span> |
| [<span data-ttu-id="3e4eb-222">Bilgi</span><span class="sxs-lookup"><span data-stu-id="3e4eb-222">Information</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-223">2</span><span class="sxs-lookup"><span data-stu-id="3e4eb-223">2</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> | <span data-ttu-id="3e4eb-224">Uygulamanın genel akışını izler.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-224">Tracks the general flow of the app.</span></span> <span data-ttu-id="3e4eb-225">Uzun süreli bir değere sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-225">May have long-term value.</span></span> |
| [<span data-ttu-id="3e4eb-226">Uyarı</span><span class="sxs-lookup"><span data-stu-id="3e4eb-226">Warning</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-227">3</span><span class="sxs-lookup"><span data-stu-id="3e4eb-227">3</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogWarning%2A> | <span data-ttu-id="3e4eb-228">Olağandışı veya beklenmeyen olaylar için.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-228">For abnormal or unexpected events.</span></span> <span data-ttu-id="3e4eb-229">Genellikle, uygulamanın başarısız olmasına neden olmayan hataları veya koşulları içerir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-229">Typically includes errors or conditions that don't cause the app to fail.</span></span> |
| [<span data-ttu-id="3e4eb-230">Hata</span><span class="sxs-lookup"><span data-stu-id="3e4eb-230">Error</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-231">4</span><span class="sxs-lookup"><span data-stu-id="3e4eb-231">4</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogError%2A> | <span data-ttu-id="3e4eb-232">İşlenemeyen hatalar ve özel durumlar için.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-232">For errors and exceptions that cannot be handled.</span></span> <span data-ttu-id="3e4eb-233">Bu iletiler, uygulama genelinde bir hata değil, geçerli işlemde veya istekte bir hata olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-233">These messages indicate a failure in the current operation or request, not an app-wide failure.</span></span> |
| [<span data-ttu-id="3e4eb-234">Kritik</span><span class="sxs-lookup"><span data-stu-id="3e4eb-234">Critical</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-235">5</span><span class="sxs-lookup"><span data-stu-id="3e4eb-235">5</span></span> | <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogCritical%2A> | <span data-ttu-id="3e4eb-236">Anında ilgilenilmesi gereken hatalarda.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-236">For failures that require immediate attention.</span></span> <span data-ttu-id="3e4eb-237">Örnekler: veri kaybı senaryoları, disk alanı yetersiz.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-237">Examples: data loss scenarios, out of disk space.</span></span> |
| [<span data-ttu-id="3e4eb-238">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="3e4eb-238">None</span></span>](xref:Microsoft.Extensions.Logging.LogLevel) | <span data-ttu-id="3e4eb-239">6</span><span class="sxs-lookup"><span data-stu-id="3e4eb-239">6</span></span> |  | <span data-ttu-id="3e4eb-240">Hiçbir ileti yazılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-240">Specifies that no messages should be written.</span></span> |

<span data-ttu-id="3e4eb-241">Önceki tabloda, `LogLevel` En düşük önem derecesine göre listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-241">In the previous table, the `LogLevel` is listed from lowest to highest severity.</span></span>

<span data-ttu-id="3e4eb-242">[Günlük](xref:Microsoft.Extensions.Logging.LoggerExtensions) yönteminin ilk parametresi, <xref:Microsoft.Extensions.Logging.LogLevel> Günlüğün önem derecesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-242">The [Log](xref:Microsoft.Extensions.Logging.LoggerExtensions) method's first parameter, <xref:Microsoft.Extensions.Logging.LogLevel>, indicates the severity of the log.</span></span> <span data-ttu-id="3e4eb-243">Çağırmak yerine `Log(LogLevel, ...)` , çoğu Geliştirici [günlük {LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) uzantı yöntemlerini çağırır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-243">Rather than calling `Log(LogLevel, ...)`, most developers call the [Log{LogLevel}](xref:Microsoft.Extensions.Logging.LoggerExtensions) extension methods.</span></span> <span data-ttu-id="3e4eb-244">`Log{LogLevel}`Uzantı yöntemleri [günlük yöntemini çağırır ve LogLevel değerini belirtir](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-244">The `Log{LogLevel}` extension methods [call the Log method and specify the LogLevel](https://github.com/dotnet/extensions/blob/release/3.1/src/Logging/Logging.Abstractions/src/LoggerExtensions.cs).</span></span> <span data-ttu-id="3e4eb-245">Örneğin, aşağıdaki iki günlük çağrısı işlevsel olarak eşdeğerdir ve aynı günlüğü üretir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-245">For example, the following two logging calls are functionally equivalent and produce the same log:</span></span>

```csharp
public void LogDetails()
{
    var logMessage = "Details for log.";

    _logger.Log(LogLevel.Information, AppLogEvents.Details, logMessage);
    _logger.LogInformation(AppLogEvents.Details, logMessage);
}
```

<span data-ttu-id="3e4eb-246">`AppLogEvents.Details` olay KIMLIĞIDIR ve örtülü olarak sabit bir değerle temsil edilir <xref:System.Int32> .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-246">`AppLogEvents.Details` is the event ID, and is implicitly represented by a constant <xref:System.Int32> value.</span></span> <span data-ttu-id="3e4eb-247">`AppLogEvents` , çeşitli adlandırılmış tanımlayıcı sabitleri kullanıma sunan ve [günlük olay kimliği](#log-event-id) bölümünde görüntülenen bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-247">`AppLogEvents` is a class that exposes various named identifier constants and is displayed in the [Log event ID](#log-event-id) section.</span></span>

<span data-ttu-id="3e4eb-248">Aşağıdaki kod oluşturur `Information` ve `Warning` günlükleri:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-248">The following code creates `Information` and `Warning` logs:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    _logger.LogInformation(AppLogEvents.Read, "Reading value for {Id}", id);

    var result = await _repository.GetAsync(id);
    if (result is null)
    {
        _logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
    }

    return result;
}
```

<span data-ttu-id="3e4eb-249">Yukarıdaki kodda, ilk `Log{LogLevel}` parametresi `AppLogEvents.Read` [günlük olay kimliğidir](#log-event-id).</span><span class="sxs-lookup"><span data-stu-id="3e4eb-249">In the preceding code, the first `Log{LogLevel}` parameter,`AppLogEvents.Read`, is the [Log event ID](#log-event-id).</span></span> <span data-ttu-id="3e4eb-250">İkinci parametre, kalan Yöntem parametreleri tarafından belirtilen bağımsız değişken değerleri için yer tutucuları olan bir ileti şablonudur.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-250">The second parameter is a message template with placeholders for argument values provided by the remaining method parameters.</span></span> <span data-ttu-id="3e4eb-251">Yöntem parametreleri bu makalenin ilerleyen kısımlarında bulunan [ileti şablonu](#log-message-template) bölümünde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-251">The method parameters are explained in the [message template](#log-message-template) section later in this article.</span></span>

<span data-ttu-id="3e4eb-252">Uygun günlük düzeyini yapılandırın ve `Log{LogLevel}` belirli bir depolama ortamına ne kadar günlük çıkışının yazıldığını denetlemek için doğru yöntemleri çağırın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-252">Configure the the appropriate log level and call the correct `Log{LogLevel}` methods to control how much log output is written to a particular storage medium.</span></span> <span data-ttu-id="3e4eb-253">Örnek:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-253">For example:</span></span>

- <span data-ttu-id="3e4eb-254">Üretimde:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-254">In production:</span></span>
  - <span data-ttu-id="3e4eb-255">Veya düzeylerinde günlüğe kaydetme, `Trace` `Information` yüksek hacimli ayrıntılı günlük iletileri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-255">Logging at the `Trace` or `Information` levels produces a high-volume of detailed log messages.</span></span> <span data-ttu-id="3e4eb-256">Maliyetleri denetlemek ve veri depolama sınırlarını aşmamak için, `Trace` `Information` iletileri yüksek hacimli ve düşük maliyetli bir veri deposuna günlüğe kaydedin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-256">To control costs and not exceed data storage limits, log `Trace` and `Information` level messages to a high-volume, low-cost data store.</span></span> <span data-ttu-id="3e4eb-257">`Trace`Belirli kategorileri ve sınırlamayı değerlendirin `Information` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-257">Consider limiting `Trace` and `Information` to specific categories.</span></span>
  - <span data-ttu-id="3e4eb-258">Düzeylerde oturum açma, `Warning` `Critical` birkaç günlük iletisi üretmelidir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-258">Logging at `Warning` through `Critical` levels should produce few log messages.</span></span>
    - <span data-ttu-id="3e4eb-259">Maliyetler ve depolama sınırları genellikle bir sorun değildir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-259">Costs and storage limits usually aren't a concern.</span></span>
    - <span data-ttu-id="3e4eb-260">Birkaç günlük veri deposu seçimlerine daha fazla esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-260">Few logs allow more flexibility in data store choices.</span></span>
- <span data-ttu-id="3e4eb-261">Geliştirme aşamasında:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-261">In development:</span></span>
  - <span data-ttu-id="3e4eb-262">`Warning` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-262">Set to `Warning`.</span></span>
  - <span data-ttu-id="3e4eb-263">`Trace` `Information` Sorun giderirken veya ileti ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-263">Add `Trace` or `Information` messages when troubleshooting.</span></span> <span data-ttu-id="3e4eb-264">Çıktıyı sınırlandırmak için, `Trace` `Information` yalnızca araştırma bölümündeki Kategoriler için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-264">To limit output, set `Trace` or `Information` only for the categories under investigation.</span></span>

<span data-ttu-id="3e4eb-265">Aşağıdaki JSON kümeleri `Logging:Console:LogLevel:Microsoft:Information` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-265">The following JSON sets `Logging:Console:LogLevel:Microsoft:Information`:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.MSFT.json":::

## <a name="log-event-id"></a><span data-ttu-id="3e4eb-266">Günlüğe olay KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="3e4eb-266">Log event ID</span></span>

<span data-ttu-id="3e4eb-267">Her günlük bir *olay tanımlayıcı*belirtebilir, <xref:Microsoft.Extensions.Logging.EventId> `Id` ve isteğe bağlı ReadOnly özellikleri olan bir yapıdır `Name` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-267">Each log can specify an *event identifer*, the <xref:Microsoft.Extensions.Logging.EventId> is a structure with an `Id` and optional `Name` readonly properties.</span></span> <span data-ttu-id="3e4eb-268">Örnek kaynak kodu, `AppLogEvents` olay kimliklerini tanımlamak için sınıfını kullanır:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-268">The sample source code uses the `AppLogEvents` class to define event IDs:</span></span>

```csharp
internal static class AppLogEvents
{
    internal const int Create = 1000;
    internal const int Read = 1001;
    internal const int Update = 1002;
    internal const int Delete = 1003;

    internal const int Details = 3000;
    internal const int Error = 3001;

    internal const int ReadNotFound = 4000;
    internal const int UpdateNotFound = 4001;

    // ...
}
```

<span data-ttu-id="3e4eb-269">Olay KIMLIĞI bir olay kümesini ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-269">An event ID associates a set of events.</span></span> <span data-ttu-id="3e4eb-270">Örneğin, bir depodan değer okuma ile ilgili tüm Günlükler olabilir `1001` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-270">For example, all logs related to reading values from a repository might be `1001`.</span></span>

<span data-ttu-id="3e4eb-271">Günlüğe kaydetme sağlayıcısı, olay KIMLIĞINI günlüğe kaydetme iletisindeki bir KIMLIK alanında veya hiç değil, günlüğe alabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-271">The logging provider may log the event ID in an ID field, in the logging message, or not at all.</span></span> <span data-ttu-id="3e4eb-272">Hata ayıklama sağlayıcısı olay kimliklerini göstermiyor.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-272">The Debug provider doesn't show event IDs.</span></span> <span data-ttu-id="3e4eb-273">Konsol sağlayıcısı, etkinlik kimliklerini kategoriden sonra parantez içinde gösterir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-273">The console provider shows event IDs in brackets after the category:</span></span>

```console
info: Example.DefaultService.GetAsync[1001]
      Reading value for a1b2c3
warn: Example.DefaultService.GetAsync[4000]
      GetAsync(a1b2c3) not found
```

<span data-ttu-id="3e4eb-274">Bazı günlük sağlayıcıları olay KIMLIĞINI bir alanda depolar, bu da KIMLIĞE filtrelemeye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-274">Some logging providers store the event ID in a field, which allows for filtering on the ID.</span></span>

## <a name="log-message-template"></a><span data-ttu-id="3e4eb-275">Günlük iletisi şablonu</span><span class="sxs-lookup"><span data-stu-id="3e4eb-275">Log message template</span></span>

<span data-ttu-id="3e4eb-276">Her günlük API 'SI bir ileti şablonu kullanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-276">Each log API uses a message template.</span></span> <span data-ttu-id="3e4eb-277">İleti şablonu, bağımsız değişkenlerin sağlandığı yer tutucuları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-277">The message template can contain placeholders for which arguments are provided.</span></span> <span data-ttu-id="3e4eb-278">Sayılar değil, yer tutucular için adları kullanın.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-278">Use names for the placeholders, not numbers.</span></span> <span data-ttu-id="3e4eb-279">Adlarının, değerlerinin sağlanması için hangi parametrelerin kullanılacağını belirleyen yer tutucular sırası.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-279">The order of placeholders, not their names, determines which parameters are used to provide their values.</span></span> <span data-ttu-id="3e4eb-280">Aşağıdaki kodda, parametre adları ileti şablonunda sıra dışında:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-280">In the following code, the parameter names are out of sequence in the message template:</span></span>

```csharp
string p1 = "param1";
string p2 = "param2";
_logger.LogInformation("Parameter values: {p2}, {p1}", p1, p2);
```

<span data-ttu-id="3e4eb-281">Yukarıdaki kod, sırasıyla parametre değerleriyle bir günlük iletisi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-281">The preceding code creates a log message with the parameter values in sequence:</span></span>

```text
Parameter values: param1, param2
```

<span data-ttu-id="3e4eb-282">Bu yaklaşım, günlük sağlayıcılarının [anlam veya yapılandırılmış günlük kaydı](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging)uygulamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-282">This approach allows logging providers to implement [semantic or structured logging](https://github.com/NLog/NLog/wiki/How-to-use-structured-logging).</span></span> <span data-ttu-id="3e4eb-283">Bağımsız değişkenler yalnızca biçimli ileti şablonuna değil, günlük sistemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-283">The arguments themselves are passed to the logging system, not just the formatted message template.</span></span> <span data-ttu-id="3e4eb-284">Bu, günlük sağlayıcılarının parametre değerlerini alan olarak depolamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-284">This enables logging providers to store the parameter values as fields.</span></span> <span data-ttu-id="3e4eb-285">Aşağıdaki günlükçü yöntemini göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-285">Consider the following logger method:</span></span>

```csharp
_logger.LogInformation("Getting item {Id} at {RunTime}", id, DateTime.Now);
```

<span data-ttu-id="3e4eb-286">Örneğin, Azure Tablo depolama alanına oturum açarken:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-286">For example, when logging to Azure Table Storage:</span></span>

- <span data-ttu-id="3e4eb-287">Her Azure Tablo varlığı `ID` ve özellikleri olabilir `RunTime` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-287">Each Azure Table entity can have `ID` and `RunTime` properties.</span></span>
- <span data-ttu-id="3e4eb-288">Özellikleri olan tablolar günlüğe kaydedilen verilerde sorguları basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-288">Tables with properties simplify queries on logged data.</span></span> <span data-ttu-id="3e4eb-289">Örneğin, bir sorgu belirli bir aralıktaki tüm günlükleri, `RunTime` kısa mesajdaki zaman aşımını ayrıştırmadan bulabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-289">For example, a query can find all logs within a particular `RunTime` range without having to parse the time out of the text message.</span></span>

## <a name="log-exceptions"></a><span data-ttu-id="3e4eb-290">Günlük özel durumları</span><span class="sxs-lookup"><span data-stu-id="3e4eb-290">Log exceptions</span></span>

<span data-ttu-id="3e4eb-291">Günlükçü yöntemlerinde bir özel durum parametresi alan aşırı yüklemeleri var:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-291">The logger methods have overloads that take an exception parameter:</span></span>

```csharp
public void Test(string id)
{
    try
    {
        if (id == "none")
        {
            throw new Exception("Default Id detected.");
        }
    }
    catch (Exception ex)
    {
        _logger.LogWarning(
            AppLogEvents.Error, ex,
            "Failed to process iteration: {Id}", id)
    }
}
```

<span data-ttu-id="3e4eb-292">Özel durum günlüğe kaydetme, sağlayıcıya özgüdür.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-292">Exception logging is provider-specific.</span></span>

### <a name="default-log-level"></a><span data-ttu-id="3e4eb-293">Varsayılan günlük düzeyi</span><span class="sxs-lookup"><span data-stu-id="3e4eb-293">Default log level</span></span>

<span data-ttu-id="3e4eb-294">Varsayılan günlük düzeyi ayarlanmamışsa varsayılan günlük düzeyi değeri olur `Information` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-294">If the default log level is not set, the default log level value is `Information`.</span></span>

<span data-ttu-id="3e4eb-295">Örneğin, aşağıdaki çalışan hizmeti uygulamasını göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-295">For example, consider the following worker service app:</span></span>

- <span data-ttu-id="3e4eb-296">.NET Worker şablonlarıyla oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-296">Created with the .NET Worker templates.</span></span>
- <span data-ttu-id="3e4eb-297">*appsettings.js* ve *appsettings.Development.js* silinmiş ya da yeniden adlandırıldı.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-297">*appsettings.json* and *appsettings.Development.json* deleted or renamed.</span></span>

<span data-ttu-id="3e4eb-298">Önceki kurulumla, gizlilik veya giriş sayfasına gidildiğinde `Trace` `Debug` Kategori adında birçok, ve `Information`  ile ileti üretilir `Microsoft` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-298">With the preceding setup, navigating to the privacy or home page produces many `Trace`, `Debug`, and `Information`  messages with `Microsoft` in the category name.</span></span>

<span data-ttu-id="3e4eb-299">Aşağıdaki kod, varsayılan günlük düzeyi yapılandırmada ayarlanmamışsa varsayılan günlük düzeyini ayarlar:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-299">The following code sets the default log level when the default log level is not set in configuration:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging => logging.SetMinimumLevel(LogLevel.Warning));
}
```

### <a name="filter-function"></a><span data-ttu-id="3e4eb-300">Filter işlevi</span><span class="sxs-lookup"><span data-stu-id="3e4eb-300">Filter function</span></span>

<span data-ttu-id="3e4eb-301">Configuration veya Code tarafından kendisine atanmış kuralları olmayan tüm sağlayıcılar ve kategoriler için bir filtre işlevi çağrılır:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-301">A filter function is invoked for all providers and categories that don't have rules assigned to them by configuration or code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddFilter((provider, category, logLevel) =>
                {
                    return provider.Contains("ConsoleLoggerProvider")
                        && (category.Contains("Example") || category.Contains("Microsoft"))
                        && logLevel >= LogLevel.Information;
                }));
}
```

<span data-ttu-id="3e4eb-302">Önceki kod, kategori içerdiğinde `Example` veya `Microsoft` ve günlük düzeyi `Information` veya daha yüksek olduğunda konsol günlüklerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-302">The preceding code displays console logs when the category contains `Example` or `Microsoft` and the log level is `Information` or higher.</span></span>

## <a name="log-scopes"></a><span data-ttu-id="3e4eb-303">Günlük kapsamları</span><span class="sxs-lookup"><span data-stu-id="3e4eb-303">Log scopes</span></span>

 <span data-ttu-id="3e4eb-304">*Kapsam* bir mantıksal işlemler kümesini gruplandırabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-304">A *scope* can group a set of logical operations.</span></span> <span data-ttu-id="3e4eb-305">Bu gruplandırma, kümenin bir parçası olarak oluşturulan her günlüğe aynı verileri eklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-305">This grouping can be used to attach the same data to each log that's created as part of a set.</span></span> <span data-ttu-id="3e4eb-306">Örneğin, bir işlemin işlenmesi kapsamında oluşturulan her günlük işlem KIMLIĞI içerebilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-306">For example, every log created as part of processing a transaction can include the transaction ID.</span></span>

<span data-ttu-id="3e4eb-307">Kapsam:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-307">A scope:</span></span>

- <span data-ttu-id="3e4eb-308"><xref:System.IDisposable>, Yöntemi tarafından döndürülen türdür <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-308">Is an <xref:System.IDisposable> type that's returned by the <xref:Microsoft.Extensions.Logging.ILogger.BeginScope%2A> method.</span></span>
- <span data-ttu-id="3e4eb-309">Atılana kadar sürer.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-309">Lasts until it's disposed.</span></span>

<span data-ttu-id="3e4eb-310">Aşağıdaki sağlayıcılar kapsamları destekler:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-310">The following providers support scopes:</span></span>

- `Console`
- [<span data-ttu-id="3e4eb-311">AzureAppServicesFile ve AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="3e4eb-311">AzureAppServicesFile and AzureAppServicesBlob</span></span>](xref:Microsoft.Extensions.Logging.AzureAppServices.BatchingLoggerOptions.IncludeScopes)

<span data-ttu-id="3e4eb-312">Bir blok içinde günlükçü çağrılarını sarmalayarak kapsam kullanın `using` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-312">Use a scope by wrapping logger calls in a `using` block:</span></span>

```csharp
public async Task<T> GetAsync<T>(string id)
{
    T result;

    using (_logger.BeginScope("using block message"))
    {
        _logger.LogInformation(
            AppLogEvents.Read, "Reading value for {Id}", id);

        var result = await _repository.GetAsync(id);
        if (result is null)
        {
            _logger.LogWarning(
                AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
        }
    }

    return result;
}
```

<span data-ttu-id="3e4eb-313">Aşağıdaki JSON konsol sağlayıcısı için kapsamları etkinleştirdi:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-313">The following JSON enables scopes for the console provider:</span></span>

:::code language="json" source="snippets/configuration/worker-service/appsettings.IncludeScopes.json" highlight="9":::

<span data-ttu-id="3e4eb-314">Aşağıdaki kod konsol sağlayıcısı için kapsamları etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-314">The following code enables scopes for the console provider:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging((_, logging) =>
                logging.ClearProviders()
                    .AddConsole(options => options.IncludeScopes = true));
}
```

## <a name="non-host-console-app"></a><span data-ttu-id="3e4eb-315">Konak olmayan konsol uygulaması</span><span class="sxs-lookup"><span data-stu-id="3e4eb-315">Non-host console app</span></span>

<span data-ttu-id="3e4eb-316">[Genel ana bilgisayarı](generic-host.md) olmayan uygulamalar için günlük kaydı kodu, [sağlayıcıların Eklenme](logging-providers.md#built-in-logging-providers) ve [günlükçülerin oluşturulduğu](#create-logs)yönteme göre farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-316">Logging code for apps without a [Generic Host](generic-host.md) differs in the way [providers are added](logging-providers.md#built-in-logging-providers) and [loggers are created](#create-logs).</span></span> <span data-ttu-id="3e4eb-317">Konak olmayan bir konsol uygulamasında, `Add{provider name}` oluşturma sırasında sağlayıcının uzantı yöntemini çağırın `LoggerFactory` :</span><span class="sxs-lookup"><span data-stu-id="3e4eb-317">In a non-host console app, call the provider's `Add{provider name}` extension method while creating a `LoggerFactory`:</span></span>

```csharp
class Program
{
    static void Main(string[] args)
    {
        using var loggerFactory = LoggerFactory.Create(builder =>
        {
            builder
                .AddFilter("Microsoft", LogLevel.Warning)
                .AddFilter("System", LogLevel.Warning)
                .AddFilter("LoggingConsoleApp.Program", LogLevel.Debug)
                .AddConsole();
        });

        ILogger logger = loggerFactory.CreateLogger<Program>();
        logger.LogInformation("Example log message");
    }
}
```

<span data-ttu-id="3e4eb-318">`loggerFactory`Nesne bir örnek oluşturmak için kullanılır <xref:Microsoft.Extensions.Logging.ILogger> .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-318">The `loggerFactory` object is used to create an <xref:Microsoft.Extensions.Logging.ILogger> instance.</span></span>

## <a name="create-logs-in-main"></a><span data-ttu-id="3e4eb-319">Ana oturum oluşturma</span><span class="sxs-lookup"><span data-stu-id="3e4eb-319">Create logs in Main</span></span>

<span data-ttu-id="3e4eb-320">Aşağıdaki kod, `Main` `ILogger` konak oluşturulduktan sonra bir örneğinden bir örnek alarak oturum açar:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-320">The following code logs in `Main` by getting an `ILogger` instance from DI after building the host:</span></span>

```csharp
using System;
using System.Threading.Tasks;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

class Program
{
    static Task Main(string[] args)
    {
        IHost host = Host.CreateDefaultBuilder(args).Build();

        var logger = host.Services.GetRequiredService<ILogger<Program>>();
        logger.LogInformation("Host created.");

        return host.RunAsync();
    }
}
```

### <a name="no-asynchronous-logger-methods"></a><span data-ttu-id="3e4eb-321">Zaman uyumsuz günlükçü yöntemi yok</span><span class="sxs-lookup"><span data-stu-id="3e4eb-321">No asynchronous logger methods</span></span>

<span data-ttu-id="3e4eb-322">Günlüğe kaydetme, zaman uyumsuz kodun performans maliyetine değer olmaması kadar hızlı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-322">Logging should be so fast that it isn't worth the performance cost of asynchronous code.</span></span> <span data-ttu-id="3e4eb-323">Günlüğe kaydetme veri deposu yavaşsa doğrudan yazma.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-323">If a logging data store is slow, don't write to it directly.</span></span> <span data-ttu-id="3e4eb-324">Günlük iletilerini başlangıçta hızlı bir mağazaya yazmayı ve sonra bunları yavaş depoya daha sonra taşımayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-324">Consider writing the log messages to a fast store initially, then moving them to the slow store later.</span></span> <span data-ttu-id="3e4eb-325">Örneğin, SQL Server oturum açarken `Log` Yöntemler zaman uyumlu olduğundan doğrudan bir yöntemde yapmayın `Log` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-325">For example, when logging to SQL Server, don't do so directly in a `Log` method, since the `Log` methods are synchronous.</span></span> <span data-ttu-id="3e4eb-326">Bunun yerine, günlük iletilerini bir bellek içi kuyruğa eşzamanlı olarak ekleyin ve bir arka plan çalışanı, SQL Server veri gönderme zaman uyumsuz çalışmasını sağlamak için iletileri kuyruktan çekin.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-326">Instead, synchronously add log messages to an in-memory queue and have a background worker pull the messages out of the queue to do the asynchronous work of pushing data to SQL Server.</span></span>

## <a name="change-log-levels-in-a-running-app"></a><span data-ttu-id="3e4eb-327">Çalışan bir uygulamadaki günlük düzeylerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="3e4eb-327">Change log levels in a running app</span></span>

<span data-ttu-id="3e4eb-328">Günlüğe kaydetme API 'SI, bir uygulama çalışırken günlük düzeylerini değiştirme senaryosu içermez.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-328">The Logging API doesn't include a scenario to change log levels while an app is running.</span></span> <span data-ttu-id="3e4eb-329">Ancak, bazı yapılandırma sağlayıcıları yapılandırmayı yeniden yükleme yeteneğine sahiptir ve bu, günlüğe kaydetme yapılandırması üzerinde etkili bir şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-329">However, some configuration providers are capable of reloading configuration, which takes immediate effect on logging configuration.</span></span> <span data-ttu-id="3e4eb-330">Örneğin, [dosya yapılandırma sağlayıcısı](configuration-providers.md#file-configuration-provider) günlük yapılandırmasını varsayılan olarak yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-330">For example, the [File Configuration Provider](configuration-providers.md#file-configuration-provider) reloads logging configuration by default.</span></span> <span data-ttu-id="3e4eb-331">Uygulama çalışırken kodda yapılandırma değiştirilirse uygulama, uygulamanın günlük yapılandırmasını güncelleştirmek için [IController. Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) ' i çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-331">If configuration is changed in code while an app is running, the app can call [IConfigurationRoot.Reload](xref:Microsoft.Extensions.Configuration.IConfigurationRoot.Reload%2A) to update the app's logging configuration.</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="3e4eb-332">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="3e4eb-332">NuGet packages</span></span>

<span data-ttu-id="3e4eb-333"><xref:Microsoft.Extensions.Logging.ILogger%601>Ve <xref:Microsoft.Extensions.Logging.ILoggerFactory> arabirimleri ve uygulamaları .NET Core SDK dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-333">The <xref:Microsoft.Extensions.Logging.ILogger%601> and <xref:Microsoft.Extensions.Logging.ILoggerFactory> interfaces and implementations are included in the .NET Core SDK.</span></span> <span data-ttu-id="3e4eb-334">Bunlar ayrıca aşağıdaki NuGet paketlerinde de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-334">They are also available in the following NuGet packages:</span></span>

- <span data-ttu-id="3e4eb-335">Arabirimler [Microsoft. Extensions. Logging. soyutlamalar](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions)içinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-335">The interfaces are in [Microsoft.Extensions.Logging.Abstractions](https://www.nuget.org/packages/Microsoft.Extensions.Logging.Abstractions).</span></span>
- <span data-ttu-id="3e4eb-336">Varsayılan uygulamalar [Microsoft. Extensions. Logging](https://www.nuget.org/packages/microsoft.extensions.logging)' dir.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-336">The default implementations are in [Microsoft.Extensions.Logging](https://www.nuget.org/packages/microsoft.extensions.logging).</span></span>

## <a name="apply-log-filter-rules-in-code"></a><span data-ttu-id="3e4eb-337">Koddaki günlük filtresi kurallarını Uygula</span><span class="sxs-lookup"><span data-stu-id="3e4eb-337">Apply log filter rules in code</span></span>

<span data-ttu-id="3e4eb-338">Günlük filtresi kurallarını ayarlamak için tercih edilen yaklaşım [yapılandırma](configuration.md)kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-338">The preferred approach for setting log filter rules is by using [Configuration](configuration.md).</span></span>

<span data-ttu-id="3e4eb-339">Aşağıdaki örnek, koddaki filtre kurallarının nasıl kaydedileceği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="3e4eb-339">The following example shows how to register filter rules in code:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
               logging.AddFilter("System", LogLevel.Debug)
                  .AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)
                  .AddFilter<ConsoleLoggerProvider>("Microsoft", LogLevel.Trace));
}
```

<span data-ttu-id="3e4eb-340">`logging.AddFilter("System", LogLevel.Debug)``System`Kategori ve günlük düzeyini belirtir `Debug` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-340">`logging.AddFilter("System", LogLevel.Debug)` specifies the `System` category and log level `Debug`.</span></span> <span data-ttu-id="3e4eb-341">Belirli bir sağlayıcı yapılandırılmadığı için filtre tüm sağlayıcılara uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-341">The filter is applied to all providers because a specific provider was not configured.</span></span>

<span data-ttu-id="3e4eb-342">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` belirtir</span><span class="sxs-lookup"><span data-stu-id="3e4eb-342">`AddFilter<DebugLoggerProvider>("Microsoft", LogLevel.Information)` specifies:</span></span>

- <span data-ttu-id="3e4eb-343">`Debug`Günlüğe kaydetme sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-343">The `Debug` logging provider.</span></span>
- <span data-ttu-id="3e4eb-344">Günlük düzeyi `Information` ve üzeri.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-344">Log level `Information` and higher.</span></span>
- <span data-ttu-id="3e4eb-345">İle başlayan tüm kategoriler `"Microsoft"` .</span><span class="sxs-lookup"><span data-stu-id="3e4eb-345">All categories starting with `"Microsoft"`.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e4eb-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3e4eb-346">See also</span></span>

- [<span data-ttu-id="3e4eb-347">.NET 'te günlüğe kaydetme sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="3e4eb-347">Logging providers in .NET</span></span>](logging-providers.md)
- [<span data-ttu-id="3e4eb-348">.NET ' te özel bir günlüğe kaydetme sağlayıcısı uygulama</span><span class="sxs-lookup"><span data-stu-id="3e4eb-348">Implement a custom logging provider in .NET</span></span>](custom-logging-provider.md)
- [<span data-ttu-id="3e4eb-349">.NET 'te yüksek performanslı günlüğe kaydetme</span><span class="sxs-lookup"><span data-stu-id="3e4eb-349">High-performance logging in .NET</span></span>](high-performance-logging.md)
- <span data-ttu-id="3e4eb-350">[GitHub.com/DotNet/Extensions](https://github.com/dotnet/extensions/issues) deposu 'nda günlüğe kaydetme hataları oluşturulmalıdır</span><span class="sxs-lookup"><span data-stu-id="3e4eb-350">Logging bugs should be created in the [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) repo</span></span>
