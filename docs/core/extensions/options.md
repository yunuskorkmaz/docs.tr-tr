---
title: .NET 'teki seçenek kalıbı
author: IEvangelist
description: .NET uygulamalarında ilgili ayarların gruplarını temsil etmek için seçenekler deseninin nasıl kullanılacağını öğrenin.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: 5c59a14223ec7c35456e1ea84d3f976e236f45dd
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614752"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="93e5b-103">.NET 'teki seçenek kalıbı</span><span class="sxs-lookup"><span data-stu-id="93e5b-103">Options pattern in .NET</span></span>

<span data-ttu-id="93e5b-104">Seçenekler stili, ilişkili ayarlar gruplarına kesin olarak yazılmış erişim sağlamak için sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="93e5b-105">[Yapılandırma ayarları](configuration.md) senaryo tarafından ayrı sınıflara ayrılmışsa, uygulama iki önemli yazılım mühendisliği ilkelerine uyar:</span><span class="sxs-lookup"><span data-stu-id="93e5b-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="93e5b-106">Yapılandırma ayarlarına bağlı olan [arabirim ayırma ilkesi (ISS) veya kapsülleme](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): senaryolar (sınıflar) yalnızca kullandıkları yapılandırma ayarlarına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="93e5b-107">[Kaygıları ayrımı](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): uygulamanın farklı bölümlerinin ayarları birbirlerine bağımlı değil veya birbirine bağlı değil.</span><span class="sxs-lookup"><span data-stu-id="93e5b-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="93e5b-108">Seçenekler Ayrıca yapılandırma verilerini doğrulamaya yönelik bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e5b-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="93e5b-109">Daha fazla bilgi için [Seçenekler doğrulama](#options-validation) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="93e5b-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="93e5b-110">Hiyerarşik yapılandırmayı bağlama</span><span class="sxs-lookup"><span data-stu-id="93e5b-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="93e5b-111">İlgili yapılandırma değerlerini okumak için tercih edilen yol, Seçenekler modelini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="93e5b-112">Örneğin, aşağıdaki yapılandırma değerlerini okumak için:</span><span class="sxs-lookup"><span data-stu-id="93e5b-112">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="93e5b-113">Aşağıdaki sınıfı oluşturun `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="93e5b-113">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-6":::

<span data-ttu-id="93e5b-114">Seçenekler sınıfı:</span><span class="sxs-lookup"><span data-stu-id="93e5b-114">An options class:</span></span>

* <span data-ttu-id="93e5b-115">Ortak parametresiz bir oluşturucuya sahip olmayan Özet olmamalıdır</span><span class="sxs-lookup"><span data-stu-id="93e5b-115">Must be non-abstract with a public parameterless constructor</span></span>
* <span data-ttu-id="93e5b-116">Bağlanacak genel okuma-yazma özelliklerini içerir (alanlar bağlı ***değildir*** )</span><span class="sxs-lookup"><span data-stu-id="93e5b-116">Contain public read-write properties to bind (fields are ***not*** bound)</span></span>

<span data-ttu-id="93e5b-117">Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="93e5b-117">The following code:</span></span>

* <span data-ttu-id="93e5b-118">Sınıfı bölümüne bağlamak için [Configurationciltçi. Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) ' i çağırır `TransientFaultHandlingOptions` `"TransientFaultHandlingOptions"` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-118">Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="93e5b-119">Yapılandırma verilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="93e5b-119">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

<span data-ttu-id="93e5b-120">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="93e5b-120">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="93e5b-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) belirtilen türü bağlar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="93e5b-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="93e5b-122">`ConfigurationBinder.Get<T>` , kullanmaktan daha uygun olabilir `ConfigurationBinder.Bind` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-122">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="93e5b-123">Aşağıdaki kod, sınıfıyla birlikte nasıl kullanılacağını gösterir `ConfigurationBinder.Get<T>` `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="93e5b-123">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
        .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="93e5b-124">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="93e5b-124">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="93e5b-125">Seçenekler deseninin kullanılmasına yönelik alternatif bir yaklaşım, `"TransientFaultHandlingOptions"` bölümü bağlamak ve [bağımlılık ekleme hizmeti kapsayıcısına](dependency-injection.md)eklemektir.</span><span class="sxs-lookup"><span data-stu-id="93e5b-125">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="93e5b-126">Aşağıdaki kodda, `TransientFaultHandlingOptions` ile hizmet kapsayıcısına eklenir <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> ve yapılandırmaya bağlanır:</span><span class="sxs-lookup"><span data-stu-id="93e5b-126">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="93e5b-127">`key`Parametresi, arama yapılacak yapılandırma bölümünün adıdır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-127">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="93e5b-128">Bunu temsil eden türün adıyla *eşleşmesi gerekmez.*</span><span class="sxs-lookup"><span data-stu-id="93e5b-128">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="93e5b-129">Örneğin, adlı bir bölüm olabilir `"FaultHandling"` ve sınıfı tarafından temsil edilebilir `TransientFaultHandlingOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-129">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="93e5b-130">Bu örnekte, `"FaultHandling"` <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> bunun yerine işlevine geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="93e5b-130">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="93e5b-131">`nameof`İşleci, adlandırılmış bölüm öğesine karşılık gelen türle eşleşen bir kolaylık olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-131">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="93e5b-132">Önceki kodu kullanarak, aşağıdaki kod konum seçeneklerini okur:</span><span class="sxs-lookup"><span data-stu-id="93e5b-132">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="93e5b-133">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan ***değişiklikler okunamaz.***</span><span class="sxs-lookup"><span data-stu-id="93e5b-133">In the preceding code, changes to the JSON configuration file after the app has started are ***not*** read.</span></span> <span data-ttu-id="93e5b-134">Uygulama başladıktan sonra değişiklikleri okumak için [ıoptionssnapshot](#use-ioptionssnapshot-to-read-updated-data)kullanın.</span><span class="sxs-lookup"><span data-stu-id="93e5b-134">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="93e5b-135">Seçenekler arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93e5b-135">Options interfaces</span></span>

<span data-ttu-id="93e5b-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="93e5b-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="93e5b-137">Şunları ***desteklemez:***</span><span class="sxs-lookup"><span data-stu-id="93e5b-137">Does ***not*** support:</span></span>
  - <span data-ttu-id="93e5b-138">Uygulama başladıktan sonra yapılandırma verilerinin okunması.</span><span class="sxs-lookup"><span data-stu-id="93e5b-138">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="93e5b-139">Adlandırılmış seçenekler</span><span class="sxs-lookup"><span data-stu-id="93e5b-139">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="93e5b-140">[Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="93e5b-140">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="93e5b-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="93e5b-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="93e5b-142">, [Kapsamlı veya geçici yaşam süreleri](dependency-injection.md#service-lifetimes)içinde her ekleme çözünürlüğünde seçeneklerin yeniden hesaplanması gereken senaryolarda yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-142">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="93e5b-143">Daha fazla bilgi için bkz. [güncelleştirilmiş verileri okumak Için ıoptionssnapshot kullanma](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="93e5b-143">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="93e5b-144">[Kapsamlı](dependency-injection.md#scoped) olarak kaydedilir ve bu nedenle tek bir hizmete eklenemez.</span><span class="sxs-lookup"><span data-stu-id="93e5b-144">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="93e5b-145">[Adlandırılmış seçenekleri](#named-options-support-using-iconfigurenamedoptions) destekler</span><span class="sxs-lookup"><span data-stu-id="93e5b-145">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="93e5b-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="93e5b-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="93e5b-147">, Seçenekleri almak ve örnekler için seçenek bildirimlerini yönetmek için kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-147">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="93e5b-148">[Tek](dependency-injection.md#singleton) bir olarak kaydedilir ve herhangi bir [hizmet ömrüne](dependency-injection.md#service-lifetimes)eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="93e5b-148">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="93e5b-149">Desteklememektedir</span><span class="sxs-lookup"><span data-stu-id="93e5b-149">Supports:</span></span>
  - <span data-ttu-id="93e5b-150">Değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="93e5b-150">Change notifications</span></span>
  - [<span data-ttu-id="93e5b-151">Adlandırılmış seçenekler</span><span class="sxs-lookup"><span data-stu-id="93e5b-151">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="93e5b-152">Yeniden yüklenebilir yapılandırma</span><span class="sxs-lookup"><span data-stu-id="93e5b-152">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="93e5b-153">Seçmeli seçenekler geçersiz kılma ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> )</span><span class="sxs-lookup"><span data-stu-id="93e5b-153">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>
  
<span data-ttu-id="93e5b-154"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> yeni seçenek örnekleri oluşturmaktan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="93e5b-154"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="93e5b-155">Tek bir metodu vardır <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> .</span><span class="sxs-lookup"><span data-stu-id="93e5b-155">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="93e5b-156">Varsayılan uygulama tüm kayıtlı <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ve <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> sonrasında tüm yapılandırmaları çalıştırır ve sonrasında yapılandırma sonrası.</span><span class="sxs-lookup"><span data-stu-id="93e5b-156">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="93e5b-157">Ve arasında ayrım yapar ve <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yalnızca uygun arabirimi çağırır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-157">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="93e5b-158"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> , <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> örnekleri önbelleğe almak için tarafından kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-158"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="93e5b-159">, <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> Değer yeniden hesaplanabilmesi için izleyici içindeki seçenek örneklerini geçersiz kılar ( <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A> ).</span><span class="sxs-lookup"><span data-stu-id="93e5b-159">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="93e5b-160">Değerler ile el ile tanıtılamaz <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A> .</span><span class="sxs-lookup"><span data-stu-id="93e5b-160">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="93e5b-161"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A>Yöntemi, tüm adlandırılmış örneklerin isteğe bağlı olarak yeniden oluşturulması gerektiğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-161">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="93e5b-162">Güncelleştirilmiş verileri okumak için ıoptionssnapshot kullanın</span><span class="sxs-lookup"><span data-stu-id="93e5b-162">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="93e5b-163">kullandığınızda <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> Seçenekler erişildiğinde istek başına bir kez hesaplanır ve isteğin ömrü boyunca önbelleğe alınır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-163">when you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="93e5b-164">Güncelleştirilmiş yapılandırma değerlerini okumayı destekleyen yapılandırma sağlayıcıları kullanılırken, yapılandırma değişiklikleri uygulama başladıktan sonra okundu.</span><span class="sxs-lookup"><span data-stu-id="93e5b-164">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="93e5b-165">Ve arasındaki fark `IOptionsMonitor` `IOptionsSnapshot` şudur:</span><span class="sxs-lookup"><span data-stu-id="93e5b-165">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="93e5b-166">`IOptionsMonitor` , özellikle tek bağımlılıklarda yararlı olan herhangi bir zamanda geçerli seçenek değerlerini alan bir [tek hizmettir](dependency-injection.md#singleton) .</span><span class="sxs-lookup"><span data-stu-id="93e5b-166">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="93e5b-167">`IOptionsSnapshot` kapsamlı bir [hizmettir](dependency-injection.md#scoped) ve nesnenin oluşturulduğu sırada seçeneklerin anlık görüntüsünü sağlar `IOptionsSnapshot<T>` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-167">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="93e5b-168">Seçenekler anlık görüntüleri geçici ve kapsamlı bağımlılıklarla kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-168">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="93e5b-169">Aşağıdaki kod kullanır <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .</span><span class="sxs-lookup"><span data-stu-id="93e5b-169">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="93e5b-170">Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` :</span><span class="sxs-lookup"><span data-stu-id="93e5b-170">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="93e5b-171">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="93e5b-171">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="93e5b-172">Ioptionsmonitor</span><span class="sxs-lookup"><span data-stu-id="93e5b-172">IOptionsMonitor</span></span>

<span data-ttu-id="93e5b-173">Aşağıdaki kod, ' a bağlanan bir yapılandırma örneği kaydeder `TransientFaultHandlingOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-173">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="93e5b-174">Aşağıdaki örnek şunu kullanır <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> :</span><span class="sxs-lookup"><span data-stu-id="93e5b-174">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="93e5b-175">Yukarıdaki kodda, uygulama başladıktan sonra JSON yapılandırma dosyasında yapılan değişiklikler okundu.</span><span class="sxs-lookup"><span data-stu-id="93e5b-175">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="93e5b-176">IController Enamedooptıons kullanarak adlandırılmış seçenekler desteği</span><span class="sxs-lookup"><span data-stu-id="93e5b-176">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="93e5b-177">Adlandırılmış seçenekler:</span><span class="sxs-lookup"><span data-stu-id="93e5b-177">Named options:</span></span>

- <span data-ttu-id="93e5b-178">Aynı özelliklere birden çok yapılandırma bölümü bağlandığı zaman faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-178">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="93e5b-179">Büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-179">Are case-sensitive.</span></span>

<span data-ttu-id="93e5b-180">Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="93e5b-180">Consider the following *appsettings.json* file:</span></span>

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

<span data-ttu-id="93e5b-181">Ve bağlamak için iki sınıf oluşturmak yerine `Features:Personalize` `Features:WeatherStation` , her bölüm için aşağıdaki sınıf kullanılır:</span><span class="sxs-lookup"><span data-stu-id="93e5b-181">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="93e5b-182">Aşağıdaki kod, adlandırılmış seçenekleri yapılandırır:</span><span class="sxs-lookup"><span data-stu-id="93e5b-182">The following code configures the named options:</span></span>

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

<span data-ttu-id="93e5b-183">Aşağıdaki kod, adlandırılmış seçenekleri gösterir:</span><span class="sxs-lookup"><span data-stu-id="93e5b-183">The following code displays the named options:</span></span>

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

<span data-ttu-id="93e5b-184">Tüm seçenekler adlandırılmış örneklerdir.</span><span class="sxs-lookup"><span data-stu-id="93e5b-184">All options are named instances.</span></span> <span data-ttu-id="93e5b-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> örnekler, örneği hedefleme olarak değerlendirilir `Options.DefaultName` `string.Empty` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="93e5b-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> Ayrıca uygular <xref:Microsoft.Extensions.Options.IConfigureOptions%601> .</span><span class="sxs-lookup"><span data-stu-id="93e5b-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="93e5b-187">Varsayılan uygulamasının, her birini <xref:Microsoft.Extensions.Options.IOptionsFactory%601> uygun şekilde kullanma mantığı vardır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-187">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="93e5b-188">`null`Adlandırılmış seçenek, belirli bir adlandırılmış örnek yerine tüm adlandırılmış örnekleri hedeflemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-188">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="93e5b-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> ve <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> Bu kuralı kullanın.</span><span class="sxs-lookup"><span data-stu-id="93e5b-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="93e5b-190">Seçenekno Oluşturucu API 'SI</span><span class="sxs-lookup"><span data-stu-id="93e5b-190">OptionsBuilder API</span></span>

<span data-ttu-id="93e5b-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> örnekleri yapılandırmak için kullanılır `TOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="93e5b-192">`OptionsBuilder` adlandırılmış seçenekleri, sonraki çağrıların tümünde olmak yerine ilk çağrının tek bir parametresi olacak şekilde oluşturmayı kolaylaştırır `AddOptions<TOptions>(string optionsName)` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-192">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="93e5b-193">Seçenekler doğrulaması ve `ConfigureOptions` hizmet bağımlılıklarını kabul eden aşırı yüklemeler yalnızca aracılığıyla kullanılabilir `OptionsBuilder` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-193">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="93e5b-194">`OptionsBuilder`[Seçenekler doğrulama](#options-validation) bölümünde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-194">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="93e5b-195">Ayarları yapılandırmak için dı hizmetlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="93e5b-195">Use DI services to configure options</span></span>

<span data-ttu-id="93e5b-196">Seçenekleri iki şekilde yapılandırırken, hizmetlere bağımlılık ekleme işleminden erişilebilir:</span><span class="sxs-lookup"><span data-stu-id="93e5b-196">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="93e5b-197">[Options Builder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601)'da [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) için bir yapılandırma temsilcisi geçirin.</span><span class="sxs-lookup"><span data-stu-id="93e5b-197">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="93e5b-198">`OptionsBuilder<TOptions>` , seçenekleri yapılandırmak için en fazla beş hizmet kullanılmasına izin veren [yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) yüklerini sağlar:</span><span class="sxs-lookup"><span data-stu-id="93e5b-198">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="93e5b-199">Veya uygulayan bir tür oluşturun <xref:Microsoft.Extensions.Options.IConfigureOptions%601> <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> ve türü bir hizmet olarak kaydedin.</span><span class="sxs-lookup"><span data-stu-id="93e5b-199">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="93e5b-200">Bir hizmetin oluşturulması daha karmaşık olduğundan, [yapılandırmak](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)için bir yapılandırma temsilcisinin geçirilmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="93e5b-200">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="93e5b-201">Bir tür oluşturmak,, [Yapılandır](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A)çağrılırken çerçevenin yaptığı işe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="93e5b-201">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="93e5b-202">[Yapılandırma](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) çağrısı <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> , belirtilen genel hizmet türlerini kabul eden bir oluşturucuya sahip olan geçici bir genel kayıt kaydeder.</span><span class="sxs-lookup"><span data-stu-id="93e5b-202">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="93e5b-203">Seçenekler doğrulaması</span><span class="sxs-lookup"><span data-stu-id="93e5b-203">Options validation</span></span>

<span data-ttu-id="93e5b-204">Seçenekler doğrulaması seçenek değerlerinin doğrulanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="93e5b-204">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="93e5b-205">Dosyasında aşağıdaki *appsettings.js* göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="93e5b-205">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="93e5b-206">Aşağıdaki sınıf `"Settings"` yapılandırma bölümüne bağlanır ve birkaç `DataAnnotations` kural uygular:</span><span class="sxs-lookup"><span data-stu-id="93e5b-206">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="93e5b-207">Aşağıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="93e5b-207">The following code:</span></span>

- <span data-ttu-id="93e5b-208"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A>Sınıfına bağlanan bir [seçenekoluşturucu Oluşturucu \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) almak için çağırır `SettingsOptions` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-208">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="93e5b-209"><xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A>Kullanarak doğrulamayı etkinleştirmek için çağırır `DataAnnotations` .</span><span class="sxs-lookup"><span data-stu-id="93e5b-209">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="93e5b-210">`ValidateDataAnnotations`Genişletme yöntemi, [Microsoft. Extensions. Options. dataaçıklamalarda](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet paketinde tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="93e5b-210">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="93e5b-211">Aşağıdaki kod yapılandırma değerlerini veya doğrulama hatalarını görüntüler:</span><span class="sxs-lookup"><span data-stu-id="93e5b-211">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="93e5b-212">Aşağıdaki kod, bir temsilci kullanarak daha karmaşık bir doğrulama kuralı uygular:</span><span class="sxs-lookup"><span data-stu-id="93e5b-212">The following code applies a more complex validation rule using a delegate:</span></span>

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

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="93e5b-213">Karmaşık doğrulama için ıvalidateoptions</span><span class="sxs-lookup"><span data-stu-id="93e5b-213">IValidateOptions for complex validation</span></span>

<span data-ttu-id="93e5b-214">Aşağıdaki sınıf şunları uygular <xref:Microsoft.Extensions.Options.IValidateOptions%601> :</span><span class="sxs-lookup"><span data-stu-id="93e5b-214">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="93e5b-215">`IValidateOptions` doğrulama kodunu bir sınıfa taşımaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="93e5b-215">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="93e5b-216">Önceki kodu kullanarak, doğrulama ' de `ConfigureServices` aşağıdaki kodla etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="93e5b-216">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="93e5b-217">Yapılandırma sonrası seçenekler</span><span class="sxs-lookup"><span data-stu-id="93e5b-217">Options post-configuration</span></span>

<span data-ttu-id="93e5b-218">Yapılandırma sonrası ' i ayarlayın <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> .</span><span class="sxs-lookup"><span data-stu-id="93e5b-218">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="93e5b-219">Yapılandırma sonrası tüm <xref:Microsoft.Extensions.Options.IConfigureOptions%601> yapılandırma oluştuktan sonra çalışır ve yapılandırmayı geçersiz kılmanız gerektiğinde senaryolarda yararlı olabilir:</span><span class="sxs-lookup"><span data-stu-id="93e5b-219">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="93e5b-220"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> , adlandırılmış seçenekleri yapılandırmak için kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="93e5b-220"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="93e5b-221"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A>Tüm yapılandırma örneklerini yapılandırmak için kullanın:</span><span class="sxs-lookup"><span data-stu-id="93e5b-221">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="93e5b-222">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93e5b-222">See also</span></span>

- [<span data-ttu-id="93e5b-223">.NET 'teki yapılandırma</span><span class="sxs-lookup"><span data-stu-id="93e5b-223">Configuration in .NET</span></span>](configuration.md)
