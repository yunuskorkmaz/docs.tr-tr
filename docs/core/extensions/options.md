---
title: .NET 'teki seçenek kalıbı
author: IEvangelist
description: .NET uygulamalarında ilgili ayarların gruplarını temsil etmek için seçenekler deseninin nasıl kullanılacağını öğrenin.
ms.author: dapine
ms.date: 02/18/2021
ms.openlocfilehash: df30928cdb1832e94f89abbdf8cc41e1304f8e2e
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206614"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="2def7-103">.NET 'teki seçenek kalıbı</span><span class="sxs-lookup"><span data-stu-id="2def7-103">Options pattern in .NET</span></span>

<span data-ttu-id="2def7-104">Seçenekler stili, ilişkili ayarlar gruplarına kesin olarak yazılmış erişim sağlamak için sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="2def7-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="2def7-105">[Yapılandırma ayarları](configuration.md) senaryo tarafından ayrı sınıflara ayrılmışsa, uygulama iki önemli yazılım mühendisliği ilkelerine uyar:</span><span class="sxs-lookup"><span data-stu-id="2def7-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="2def7-106">Yapılandırma ayarlarına bağlı olan [arabirim ayırma ilkesi (ISS) veya kapsülleme](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): senaryolar (sınıflar) yalnızca kullandıkları yapılandırma ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2def7-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="2def7-107">[Kaygıları ayrımı](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): uygulamanın farklı bölümlerinin ayarları birbirlerine bağımlı değil veya birbirine bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="2def7-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="2def7-108">Seçenekler Ayrıca yapılandırma verilerini doğrulamaya yönelik bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="2def7-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="2def7-109">Daha fazla bilgi için [Seçenekler doğrulama](#options-validation) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="2def7-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="2def7-110">Hiyerarşik yapılandırmayı bağlama</span><span class="sxs-lookup"><span data-stu-id="2def7-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="2def7-111">İlgili yapılandırma değerlerini okumak için tercih edilen yol, Seçenekler modelini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2def7-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="2def7-112">Seçenekler deseninin, <xref:Microsoft.Extensions.Options.IOptions%601> genel tür parametresinin kısıtlı olduğu arabirim aracılığıyla mümkündür `TOptions` `class` .</span><span class="sxs-lookup"><span data-stu-id="2def7-112">The options pattern is possible through the <xref:Microsoft.Extensions.Options.IOptions%601> interface, where the generic type parameter `TOptions` is constrained to `class`.</span></span> <span data-ttu-id="2def7-113">`IOptions<TOptions>`Daha sonra bağımlılık ekleme yoluyla sağlanabilebilirler.</span><span class="sxs-lookup"><span data-stu-id="2def7-113">The `IOptions<TOptions>` can later be provided through dependency injection.</span></span> <span data-ttu-id="2def7-114">Daha fazla bilgi için bkz. [.net 'e bağımlılık ekleme](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="2def7-114">For more information, see [Dependency injection in .NET](dependency-injection.md).</span></span>

<span data-ttu-id="2def7-115">Örneğin, aşağıdaki yapılandırma değerlerini okumak için:</span><span class="sxs-lookup"><span data-stu-id="2def7-115">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="2def7-116">Aşağıdaki sınıfı oluşturun `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="2def7-116">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-9":::

<span data-ttu-id="2def7-117"><span id="options-class"></span> Seçenekler deseninin kullanıldığı bir seçenek sınıfı:</span><span class="sxs-lookup"><span data-stu-id="2def7-117"><span id="options-class"></span> When using the options pattern, an options class:</span></span>

- <span data-ttu-id="2def7-118">Ortak parametresiz bir oluşturucuya sahip olmayan Özet olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="2def7-118">Must be non-abstract with a public parameterless constructor</span></span>
- <span data-ttu-id="2def7-119">Bağlanacak genel okuma-yazma özelliklerini içerir (alanlar bağlı ***değildir*** )</span><span class="sxs-lookup"><span data-stu-id="2def7-119">Contain public read-write properties to bind (fields are ***not*** bound)</span></span>

<span data-ttu-id="2def7-120">Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="2def7-120">The following code:</span></span>

* <span data-ttu-id="2def7-121">Sınıfı bölümüne bağlamak için [Configurationciltçi. Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) ' i çağırır `TransientFaultHandlingOptions` `"TransientFaultHandlingOptions"` .</span><span class="sxs-lookup"><span data-stu-id="2def7-121">Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="2def7-122">Yapılandırma verilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2def7-122">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="31-38":::

<span data-ttu-id="2def7-123">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="2def7-123">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="2def7-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) belirtilen türü bağlar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="2def7-124">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="2def7-125">`ConfigurationBinder.Get<T>` , kullanmaktan daha uygun olabilir `ConfigurationBinder.Bind` .</span><span class="sxs-lookup"><span data-stu-id="2def7-125">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="2def7-126">Aşağıdaki kod, sınıfıyla birlikte nasıl kullanılacağını gösterir `ConfigurationBinder.Get<T>` `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="2def7-126">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
                     .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="2def7-127">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="2def7-127">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2def7-128"><xref:Microsoft.Extensions.Configuration.ConfigurationBinder>Sınıfı, `.Bind(object instance)` ve gibi `.Get<T>()` Kısıtlanmış ***olmayan*** çeşitli API 'ler sunar `class` .</span><span class="sxs-lookup"><span data-stu-id="2def7-128">The <xref:Microsoft.Extensions.Configuration.ConfigurationBinder> class exposes several APIs, such as `.Bind(object instance)` and `.Get<T>()` that are ***not*** constrained to `class`.</span></span> <span data-ttu-id="2def7-129">[Seçenek arabirimlerinden](#options-interfaces)herhangi birini kullanırken, yukarıda bahsedilen [seçenek sınıfı kısıtlamalarına](#options-class)uymalısınız.</span><span class="sxs-lookup"><span data-stu-id="2def7-129">When using any of the [Options interfaces](#options-interfaces), you must adhere to aforementioned [options class constraints](#options-class).</span></span>

<span data-ttu-id="2def7-130">Seçenekler deseninin kullanılmasına yönelik alternatif bir yaklaşım, `"TransientFaultHandlingOptions"` bölümü bağlamak ve [bağımlılık ekleme hizmeti kapsayıcısına](dependency-injection.md)eklemektir.</span><span class="sxs-lookup"><span data-stu-id="2def7-130">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="2def7-131">Aşağıdaki kodda, `TransientFaultHandlingOptions` ile hizmet kapsayıcısına eklenir <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> ve yapılandırmaya bağlanır:</span><span class="sxs-lookup"><span data-stu-id="2def7-131">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="2def7-132">`key`Parametresi, arama yapılacak yapılandırma bölümünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="2def7-132">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="2def7-133">Bunu temsil eden türün adıyla *eşleşmesi gerekmez.*</span><span class="sxs-lookup"><span data-stu-id="2def7-133">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="2def7-134">Örneğin, adlı bir bölüm olabilir `"FaultHandling"` ve sınıfı tarafından temsil edilebilir `TransientFaultHandlingOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-134">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="2def7-135">Bu örnekte, `"FaultHandling"` <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> bunun yerine işlevine geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2def7-135">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="2def7-136">`nameof`İşleci, adlandırılmış bölüm öğesine karşılık gelen türle eşleşen bir kolaylık olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2def7-136">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="2def7-137">Önceki kodu kullanarak, aşağıdaki kod konum seçeneklerini okur:</span><span class="sxs-lookup"><span data-stu-id="2def7-137">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="2def7-138">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan ***değişiklikler okunamaz.***</span><span class="sxs-lookup"><span data-stu-id="2def7-138">In the preceding code, changes to the JSON configuration file after the app has started are ***not*** read.</span></span> <span data-ttu-id="2def7-139">Uygulama başladıktan sonra değişiklikleri okumak için [ıoptionssnapshot](#use-ioptionssnapshot-to-read-updated-data)kullanın.</span><span class="sxs-lookup"><span data-stu-id="2def7-139">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="2def7-140">Seçenekler arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2def7-140">Options interfaces</span></span>

<span data-ttu-id="2def7-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="2def7-141"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="2def7-142">Şunları ***desteklemez:***</span><span class="sxs-lookup"><span data-stu-id="2def7-142">Does ***not*** support:</span></span>
  - <span data-ttu-id="2def7-143">Uygulama başladıktan sonra yapılandırma verilerinin okunması.</span><span class="sxs-lookup"><span data-stu-id="2def7-143">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="2def7-144">Adlandırılmış seçenekler</span><span class="sxs-lookup"><span data-stu-id="2def7-144">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="2def7-145">[Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2def7-145">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="2def7-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="2def7-146"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="2def7-147">, [Kapsamlı veya geçici yaşam süreleri](dependency-injection.md#service-lifetimes)içinde her ekleme çözünürlüğünde seçeneklerin yeniden hesaplanması gereken senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2def7-147">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="2def7-148">Daha fazla bilgi için bkz. [güncelleştirilmiş verileri okumak Için ıoptionssnapshot kullanma](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="2def7-148">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="2def7-149">[Kapsamlı](dependency-injection.md#scoped) olarak kaydedilir ve bu nedenle tek bir hizmete eklenemez.</span><span class="sxs-lookup"><span data-stu-id="2def7-149">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="2def7-150">[Adlandırılmış seçenekleri](#named-options-support-using-iconfigurenamedoptions) destekler</span><span class="sxs-lookup"><span data-stu-id="2def7-150">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="2def7-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="2def7-151"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="2def7-152">, Seçenekleri almak ve örnekler için seçenek bildirimlerini yönetmek için kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-152">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="2def7-153">[Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="2def7-153">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="2def7-154">Desteklememektedir</span><span class="sxs-lookup"><span data-stu-id="2def7-154">Supports:</span></span>
  - <span data-ttu-id="2def7-155">Değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="2def7-155">Change notifications</span></span>
  - [<span data-ttu-id="2def7-156">Adlandırılmış seçenekler</span><span class="sxs-lookup"><span data-stu-id="2def7-156">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="2def7-157">Yeniden yüklenebilir yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2def7-157">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="2def7-158">Seçmeli seçenekler geçersiz kılma ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> )</span><span class="sxs-lookup"><span data-stu-id="2def7-158">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>

<span data-ttu-id="2def7-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> yeni seçenek örnekleri oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="2def7-159"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="2def7-160">Tek bir metodu vardır <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> .</span><span class="sxs-lookup"><span data-stu-id="2def7-160">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="2def7-161">Varsayılan uygulama tüm kayıtlı <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ve <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> sonrasında tüm yapılandırmaları çalıştırır ve sonrasında yapılandırma sonrası.</span><span class="sxs-lookup"><span data-stu-id="2def7-161">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="2def7-162">Ve arasında ayrım yapar ve <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yalnızca uygun arabirimi çağırır.</span><span class="sxs-lookup"><span data-stu-id="2def7-162">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="2def7-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> , <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> örnekleri önbelleğe almak için tarafından kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-163"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="2def7-164">, <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> Değer yeniden hesaplanabilmesi için izleyici içindeki seçenek örneklerini geçersiz kılar ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A> ).</span><span class="sxs-lookup"><span data-stu-id="2def7-164">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="2def7-165">Değerler ile el ile tanıtılamaz <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> .</span><span class="sxs-lookup"><span data-stu-id="2def7-165">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="2def7-166"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A>Yöntemi, tüm adlandırılmış örneklerin isteğe bağlı olarak yeniden oluşturulması gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2def7-166">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

### <a name="options-interfaces-benefits"></a><span data-ttu-id="2def7-167">Seçenekler arabirimleri avantajları</span><span class="sxs-lookup"><span data-stu-id="2def7-167">Options interfaces benefits</span></span>

<span data-ttu-id="2def7-168">Genel bir sarmalayıcı türü kullanmak, bu seçeneğin yaşam süresini dı kapsayıcısından ayırma yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="2def7-168">Using a generic wrapper type gives you the ability to decouple the lifetime of the option from the DI container.</span></span> <span data-ttu-id="2def7-169"><xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>Arabirim, seçenek türlerinizde genel kısıtlamalar da dahil olmak üzere bir soyutlama katmanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2def7-169">The <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> interface provides a layer of abstraction, including generic constraints, on your options type.</span></span> <span data-ttu-id="2def7-170">Bu, aşağıdaki avantajları sağlar:</span><span class="sxs-lookup"><span data-stu-id="2def7-170">This provides the following benefits:</span></span>

- <span data-ttu-id="2def7-171">Yapılandırma örneğinin değerlendirmesi, `T` eklendiğinde değil, erişimine ertelenir <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2def7-171">The evaluation of the `T` configuration instance is deferred to the accessing of <xref:Microsoft.Extensions.Options.IOptions%601.Value?displayProperty=nameWithType>, rather than when it is injected.</span></span> <span data-ttu-id="2def7-172">Bu, `T` seçeneği çeşitli yerlerden tüketebilmeniz ve ile ilgili herhangi bir şeyi değiştirmeden ömür semantiğini seçebilmeniz açısından önemlidir `T` .</span><span class="sxs-lookup"><span data-stu-id="2def7-172">This is important because you can consume the `T` option from various places and choose the lifetime semantics without changing anything about `T`.</span></span>
- <span data-ttu-id="2def7-173">Tür seçeneklerini kaydederken `T` , türü açıkça kaydetmeniz gerekmez `T` .</span><span class="sxs-lookup"><span data-stu-id="2def7-173">When registering options of type `T`, you do not need to explicitly register the `T` type.</span></span> <span data-ttu-id="2def7-174">Bu, basit varsayılanlara sahip [bir kitaplık yazarken](options-library-authors.md) ve çağıranın belirli bir yaşam süresine sahip olan ayarları dı kapsayıcısına kaydetmesini zorlamak istemediğinizde kolaylık sağlar.</span><span class="sxs-lookup"><span data-stu-id="2def7-174">This is a convenience when you're [authoring a library](options-library-authors.md) with simple defaults, and you don't want to force the caller to register options into the DI container with a specific lifetime.</span></span>
- <span data-ttu-id="2def7-175">API 'nin perspektifinden, tür üzerindeki kısıtlamalara `T` (Bu durumda, `T` bir başvuru türüyle sınırlı olarak) izin verir.</span><span class="sxs-lookup"><span data-stu-id="2def7-175">From the perspective of the API, it allows for constraints on the type `T` (in this case, `T` is constrained to a reference type).</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="2def7-176">Güncelleştirilmiş verileri okumak için ıoptionssnapshot kullanın</span><span class="sxs-lookup"><span data-stu-id="2def7-176">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="2def7-177">Kullandığınızda <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> Seçenekler erişildiğinde istek başına bir kez hesaplanır ve isteğin ömrü boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="2def7-177">When you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="2def7-178">Güncelleştirilmiş yapılandırma değerlerini okumayı destekleyen yapılandırma sağlayıcıları kullanılırken, yapılandırma değişiklikleri uygulama başladıktan sonra okundu.</span><span class="sxs-lookup"><span data-stu-id="2def7-178">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="2def7-179">Ve arasındaki fark `IOptionsMonitor` `IOptionsSnapshot` şudur:</span><span class="sxs-lookup"><span data-stu-id="2def7-179">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="2def7-180">`IOptionsMonitor` , özellikle tek bağımlılıklarda yararlı olan herhangi bir zamanda geçerli seçenek değerlerini alan bir [tek hizmettir](dependency-injection.md#singleton) .</span><span class="sxs-lookup"><span data-stu-id="2def7-180">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="2def7-181">`IOptionsSnapshot` kapsamlı bir [hizmettir](dependency-injection.md#scoped) ve nesnenin oluşturulduğu sırada seçeneklerin anlık görüntüsünü sağlar `IOptionsSnapshot<T>` .</span><span class="sxs-lookup"><span data-stu-id="2def7-181">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="2def7-182">Seçenekler anlık görüntüleri geçici ve kapsamlı bağımlılıklarla kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2def7-182">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="2def7-183">Aşağıdaki kod kullanır <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .</span><span class="sxs-lookup"><span data-stu-id="2def7-183">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="2def7-184">Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="2def7-184">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="2def7-185">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="2def7-185">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="2def7-186">Ioptionsmonitor</span><span class="sxs-lookup"><span data-stu-id="2def7-186">IOptionsMonitor</span></span>

<span data-ttu-id="2def7-187">Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-187">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="2def7-188">Aşağıdaki örnek şunu kullanır <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> :</span><span class="sxs-lookup"><span data-stu-id="2def7-188">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="2def7-189">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="2def7-189">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="2def7-190">IController Enamedooptıons kullanarak adlandırılmış seçenekler desteği</span><span class="sxs-lookup"><span data-stu-id="2def7-190">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="2def7-191">Adlandırılmış seçenekler:</span><span class="sxs-lookup"><span data-stu-id="2def7-191">Named options:</span></span>

- <span data-ttu-id="2def7-192">Aynı özelliklere birden çok yapılandırma bölümü bağlandığı zaman faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="2def7-192">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="2def7-193">Büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2def7-193">Are case-sensitive.</span></span>

<span data-ttu-id="2def7-194">Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2def7-194">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

<span data-ttu-id="2def7-195">Ve bağlamak için iki sınıf oluşturmak yerine `Features:Personalize` `Features:WeatherStation` , her bölüm için aşağıdaki sınıf kullanılır:</span><span class="sxs-lookup"><span data-stu-id="2def7-195">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="2def7-196">Aşağıdaki kod, adlandırılmış seçenekleri yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="2def7-196">The following code configures the named options:</span></span>

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

<span data-ttu-id="2def7-197">Aşağıdaki kod, adlandırılmış seçenekleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="2def7-197">The following code displays the named options:</span></span>

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

<span data-ttu-id="2def7-198">Tüm seçenekler adlandırılmış örneklerdir.</span><span class="sxs-lookup"><span data-stu-id="2def7-198">All options are named instances.</span></span> <span data-ttu-id="2def7-199"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> örnekler, örneği hedefleme olarak değerlendirilir `Options.DefaultName` `string.Empty` .</span><span class="sxs-lookup"><span data-stu-id="2def7-199"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="2def7-200"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> Ayrıca uygular <xref:Microsoft.Extensions.Options.IConfigureOptions%601> .</span><span class="sxs-lookup"><span data-stu-id="2def7-200"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="2def7-201">Varsayılan uygulamasının, her birini <xref:Microsoft.Extensions.Options.IOptionsFactory%601> uygun şekilde kullanma mantığı vardır.</span><span class="sxs-lookup"><span data-stu-id="2def7-201">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="2def7-202">`null`Adlandırılmış seçenek, belirli bir adlandırılmış örnek yerine tüm adlandırılmış örnekleri hedeflemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2def7-202">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="2def7-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> ve <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> Bu kuralı kullanın.</span><span class="sxs-lookup"><span data-stu-id="2def7-203"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="2def7-204">Seçenekno Oluşturucu API 'SI</span><span class="sxs-lookup"><span data-stu-id="2def7-204">OptionsBuilder API</span></span>

<span data-ttu-id="2def7-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> örnekleri yapılandırmak için kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-205"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="2def7-206">`OptionsBuilder` adlandırılmış seçenekleri, sonraki çağrıların tümünde olmak yerine ilk çağrının tek bir parametresi olacak şekilde oluşturmayı kolaylaştırır `AddOptions<TOptions>(string optionsName)` .</span><span class="sxs-lookup"><span data-stu-id="2def7-206">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="2def7-207">Seçenekler doğrulaması ve `ConfigureOptions` hizmet bağımlılıklarını kabul eden aşırı yüklemeler yalnızca aracılığıyla kullanılabilir `OptionsBuilder` .</span><span class="sxs-lookup"><span data-stu-id="2def7-207">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="2def7-208">`OptionsBuilder`[Seçenekler doğrulama](#options-validation) bölümünde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2def7-208">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="2def7-209">Ayarları yapılandırmak için dı hizmetlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="2def7-209">Use DI services to configure options</span></span>

<span data-ttu-id="2def7-210">Seçenekleri iki şekilde yapılandırırken, hizmetlere bağımlılık ekleme işleminden erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="2def7-210">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="2def7-211">[Options Builder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601)'da [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) için bir yapılandırma temsilcisi geçirin.</span><span class="sxs-lookup"><span data-stu-id="2def7-211">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="2def7-212">`OptionsBuilder<TOptions>` , seçenekleri yapılandırmak için en fazla beş hizmet kullanılmasına izin veren [yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) yüklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="2def7-212">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="2def7-213">Veya uygulayan bir tür oluşturun <xref:Microsoft.Extensions.Options.IConfigureOptions%601> <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> ve türü bir hizmet olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="2def7-213">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="2def7-214">Bir hizmetin oluşturulması daha karmaşık olduğundan, [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)için bir yapılandırma temsilcisinin geçirilmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="2def7-214">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="2def7-215">Bir tür oluşturmak,, [Yapılandır](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)çağrılırken çerçevenin yaptığı işe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="2def7-215">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="2def7-216">[Yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) çağrısı <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> , belirtilen genel hizmet türlerini kabul eden bir oluşturucuya sahip olan geçici bir genel kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="2def7-216">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="2def7-217">Seçenekler doğrulaması</span><span class="sxs-lookup"><span data-stu-id="2def7-217">Options validation</span></span>

<span data-ttu-id="2def7-218">Seçenekler doğrulaması seçenek değerlerinin doğrulanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2def7-218">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="2def7-219">Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2def7-219">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="2def7-220">Aşağıdaki sınıf `"Settings"` yapılandırma bölümüne bağlanır ve birkaç `DataAnnotations` kural uygular:</span><span class="sxs-lookup"><span data-stu-id="2def7-220">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="2def7-221">Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="2def7-221">The following code:</span></span>

- <span data-ttu-id="2def7-222"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A>Sınıfına bağlanan bir [seçenekoluşturucu Oluşturucu \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) almak için çağırır `SettingsOptions` .</span><span class="sxs-lookup"><span data-stu-id="2def7-222">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="2def7-223"><xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A>Kullanarak doğrulamayı etkinleştirmek için çağırır `DataAnnotations` .</span><span class="sxs-lookup"><span data-stu-id="2def7-223">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="2def7-224">`ValidateDataAnnotations`Genişletme yöntemi, [Microsoft. Extensions. Options. dataaçıklamalarda](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet paketinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2def7-224">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="2def7-225">Aşağıdaki kod yapılandırma değerlerini veya doğrulama hatalarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="2def7-225">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="2def7-226">Aşağıdaki kod, bir temsilci kullanarak daha karmaşık bir doğrulama kuralı uygular:</span><span class="sxs-lookup"><span data-stu-id="2def7-226">The following code applies a more complex validation rule using a delegate:</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="2def7-227">Karmaşık doğrulama için ıvalidateoptions</span><span class="sxs-lookup"><span data-stu-id="2def7-227">IValidateOptions for complex validation</span></span>

<span data-ttu-id="2def7-228">Aşağıdaki sınıf şunları uygular <xref:Microsoft.Extensions.Options.IValidateOptions%601> :</span><span class="sxs-lookup"><span data-stu-id="2def7-228">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="2def7-229">`IValidateOptions` doğrulama kodunu bir sınıfa taşımaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="2def7-229">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="2def7-230">Önceki kodu kullanarak, doğrulama ' de `ConfigureServices` aşağıdaki kodla etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="2def7-230">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="2def7-231">Yapılandırma sonrası seçenekler</span><span class="sxs-lookup"><span data-stu-id="2def7-231">Options post-configuration</span></span>

<span data-ttu-id="2def7-232">Yapılandırma sonrası ' i ayarlayın <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> .</span><span class="sxs-lookup"><span data-stu-id="2def7-232">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="2def7-233">Yapılandırma sonrası tüm <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yapılandırma oluştuktan sonra çalışır ve yapılandırmayı geçersiz kılmanız gerektiğinde senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="2def7-233">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="2def7-234"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> , adlandırılmış seçenekleri yapılandırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2def7-234"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="2def7-235"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A>Tüm yapılandırma örneklerini yapılandırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="2def7-235">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="2def7-236">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2def7-236">See also</span></span>

- [<span data-ttu-id="2def7-237">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2def7-237">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="2def7-238">.NET kitaplığı yazarları için seçenekler model Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2def7-238">Options pattern guidance for .NET library authors</span></span>](options-library-authors.md)
