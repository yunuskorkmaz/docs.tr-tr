---
title: Bağımlılık ekleme yönergeleri
description: .NET uygulama geliştirmesi için çeşitli bağımlılık ekleme kılavuzlarını ve en iyi uygulamaları öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 092fdc70bd5d6bae82c4c1da96db4d5ac08df452
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063169"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="75ef6-103">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="75ef6-103">Dependency injection guidelines</span></span>

<span data-ttu-id="75ef6-104">Bu makalede, .NET uygulamalarında bağımlılık ekleme işlemini uygulamaya yönelik genel yönergeler ve en iyi uygulamalar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="75ef6-105">Bağımlılık ekleme için tasarım hizmetleri</span><span class="sxs-lookup"><span data-stu-id="75ef6-105">Design services for dependency injection</span></span>

<span data-ttu-id="75ef6-106">Bağımlılık ekleme için Hizmetleri tasarlarken:</span><span class="sxs-lookup"><span data-stu-id="75ef6-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="75ef6-107">Durum bilgisi olan statik sınıflar ve Üyeler kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="75ef6-108">Bunun yerine Singleton hizmetlerini kullanmak için uygulama tasarlayarak genel durum oluşturmamaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="75ef6-109">Hizmetler içindeki bağımlı sınıfların doğrudan örneklenmesini önleyin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="75ef6-110">Doğrudan örnekleme kodu belirli bir uygulamaya bağar.</span><span class="sxs-lookup"><span data-stu-id="75ef6-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="75ef6-111">Hizmetleri küçük, iyi bir şekilde ve kolayca test edin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="75ef6-112">Bir sınıfta eklenen çok sayıda bağımlılık varsa, bu, sınıfta çok fazla sorumluluğun olduğu ve [tek sorumluluk ilkesini (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)ihlal eden bir işaret olabilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="75ef6-113">Bazı sorumlulukları yeni sınıflara taşıyarak sınıfı yeniden düzenleme girişimi.</span><span class="sxs-lookup"><span data-stu-id="75ef6-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="75ef6-114">Hizmetlerin elden çıkarılması</span><span class="sxs-lookup"><span data-stu-id="75ef6-114">Disposal of services</span></span>

<span data-ttu-id="75ef6-115">Kapsayıcı, oluşturduğu türlerin temizlenmesi ve örneklere çağrı yapmaktan sorumludur <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="75ef6-116">Kapsayıcıdan çözümlenen hizmetler hiçbir şekilde geliştirici tarafından atılamaz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="75ef6-117">Bir tür veya fabrika tek bir olarak kayıtlıysa, kapsayıcı kendiliğinden otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="75ef6-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="75ef6-118">Aşağıdaki örnekte, hizmetler hizmet kapsayıcısı tarafından oluşturulur ve otomatik olarak elden alınır:</span><span class="sxs-lookup"><span data-stu-id="75ef6-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

<span data-ttu-id="75ef6-119">Önceki atılabilir, geçici bir yaşam süresine sahip olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-119">The preceding disposable is intended to have a transient lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

<span data-ttu-id="75ef6-120">Önceki atılabilir, kapsamlı bir yaşam süresine sahip olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-120">The preceding disposable is intended to have a scoped lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

<span data-ttu-id="75ef6-121">Önceki atılabilir tek bir yaşam süresine sahip olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-121">The preceding disposable is intended to have a singleton lifetime.</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

<span data-ttu-id="75ef6-122">Hata ayıklama konsolu, çalıştırıldıktan sonra aşağıdaki örnek çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="75ef6-122">The debug console shows the following sample output after running:</span></span>

```console
Scope 1...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

Scope 2...
ScopedDisposable.Dispose()
TransientDisposable.Dispose()

info: Microsoft.Hosting.Lifetime[0]
      Application started.Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
     Hosting environment: Production
info: Microsoft.Hosting.Lifetime[0]
     Content root path: .\configuration\console-di-disposable\bin\Debug\net5.0
info: Microsoft.Hosting.Lifetime[0]
     Application is shutting down...
SingletonDisposable.Dispose()
```

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="75ef6-123">Hizmet kapsayıcısı tarafından oluşturulmayan hizmetler</span><span class="sxs-lookup"><span data-stu-id="75ef6-123">Services not created by the service container</span></span>

<span data-ttu-id="75ef6-124">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="75ef6-124">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="75ef6-125">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="75ef6-125">In the preceding code:</span></span>

- <span data-ttu-id="75ef6-126">`ExampleService`Örnek, hizmet **not** kapsayıcısı tarafından oluşturulmamış.</span><span class="sxs-lookup"><span data-stu-id="75ef6-126">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="75ef6-127">Framework Hizmetleri otomatik **olarak elden atmaz.**</span><span class="sxs-lookup"><span data-stu-id="75ef6-127">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="75ef6-128">Geliştirici, hizmetleri elden atan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="75ef6-128">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="75ef6-129">Geçici ve paylaşılan örnekler için IDisposable Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="75ef6-129">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="75ef6-130">Geçici, sınırlı ömür</span><span class="sxs-lookup"><span data-stu-id="75ef6-130">Transient, limited lifetime</span></span>

<span data-ttu-id="75ef6-131">**Senaryo**</span><span class="sxs-lookup"><span data-stu-id="75ef6-131">**Scenario**</span></span>

<span data-ttu-id="75ef6-132">Uygulama, <xref:System.IDisposable> aşağıdaki senaryolardan biri için geçici bir yaşam süresine sahip bir örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="75ef6-132">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="75ef6-133">Örnek, kök kapsamda (kök kapsayıcı) çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-133">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="75ef6-134">Kapsam bitmeden önce örnek atılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-134">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="75ef6-135">**Çözüm**</span><span class="sxs-lookup"><span data-stu-id="75ef6-135">**Solution**</span></span>

<span data-ttu-id="75ef6-136">Üst kapsamın dışında bir örnek oluşturmak için fabrika modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-136">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="75ef6-137">Bu durumda, uygulama genellikle `Create` son türün oluşturucusunu doğrudan çağıran bir yönteme sahip olur.</span><span class="sxs-lookup"><span data-stu-id="75ef6-137">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="75ef6-138">Son türün başka bağımlılıkları varsa, fabrika şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="75ef6-138">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="75ef6-139">Oluşturucusunda bir alın <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-139">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="75ef6-140"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType>Kapsayıcının bağımlılıkları için kapsayıcıyı kullanırken, örneği kapsayıcının dışında örneklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-140">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="75ef6-141">Paylaşılan örnek, sınırlı ömür</span><span class="sxs-lookup"><span data-stu-id="75ef6-141">Shared instance, limited lifetime</span></span>

<span data-ttu-id="75ef6-142">**Senaryo**</span><span class="sxs-lookup"><span data-stu-id="75ef6-142">**Scenario**</span></span>

<span data-ttu-id="75ef6-143">Uygulamanın <xref:System.IDisposable> birden çok hizmet arasında paylaşılan bir örnek olması gerekir, ancak <xref:System.IDisposable> örnek sınırlı bir yaşam süresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-143">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="75ef6-144">**Çözüm**</span><span class="sxs-lookup"><span data-stu-id="75ef6-144">**Solution**</span></span>

<span data-ttu-id="75ef6-145">Örneği kapsamlı bir ömür ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-145">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="75ef6-146"><xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType>Yeni bir oluşturmak için kullanın <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-146">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="75ef6-147"><xref:System.IServiceProvider>Gerekli hizmetleri almak için kapsam ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-147">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="75ef6-148">Artık gerekli olmadığında kapsamı atın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-148">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="75ef6-149">Genel `IDisposable` yönergeler</span><span class="sxs-lookup"><span data-stu-id="75ef6-149">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="75ef6-150"><xref:System.IDisposable>Örnekleri geçici bir yaşam süresine kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="75ef6-150">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="75ef6-151">Bunun yerine fabrika modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-151">Use the factory pattern instead.</span></span>
- <span data-ttu-id="75ef6-152"><xref:System.IDisposable>Kök kapsamda geçici veya kapsamlı bir yaşam süresine sahip örnekleri çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-152">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="75ef6-153">Bunun tek istisnası, uygulamanın oluşturma/yeniden oluşturma/yeniden oluşturma ve uygulama oluşturmasıdır <xref:System.IServiceProvider> , ancak bu ideal bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-153">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="75ef6-154">Bir <xref:System.IDisposable> bağımlılık alma yoluyla, alıcının kendisini uygulaması gerekmez <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-154">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="75ef6-155"><xref:System.IDisposable>Bağımlılığın alıcısı <xref:System.IDisposable.Dispose%2A> Bu bağımlılıkta çağrımamalıdır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-155">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="75ef6-156">Hizmetlerin ömrünü denetlemek için kapsamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-156">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="75ef6-157">Kapsamlar hiyerarşik değildir ve kapsamlar arasında özel bir bağlantı yoktur.</span><span class="sxs-lookup"><span data-stu-id="75ef6-157">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="75ef6-158">Kaynak temizleme hakkında daha fazla bilgi için bkz. [ `Dispose` yöntemi uygulama](../../standard/garbage-collection/implementing-dispose.md)veya [ `DisposeAsync` Yöntem uygulama](../../standard/garbage-collection/implementing-disposeasync.md).</span><span class="sxs-lookup"><span data-stu-id="75ef6-158">For more information on resource cleanup, see [Implement a `Dispose` method](../../standard/garbage-collection/implementing-dispose.md), or [Implement a `DisposeAsync` method](../../standard/garbage-collection/implementing-disposeasync.md).</span></span> <span data-ttu-id="75ef6-159">Ayrıca, kaynak Temizleme ile bağlantılı olarak [kapsayıcı senaryosu tarafından yakalanan atılabilir geçici Hizmetleri](#disposable-transient-services-captured-by-container) de göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="75ef6-159">Additionally, consider the [Disposable transient services captured by container](#disposable-transient-services-captured-by-container) scenario as it relates to resource cleanup.</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="75ef6-160">Varsayılan hizmet kapsayıcısı değiştirme</span><span class="sxs-lookup"><span data-stu-id="75ef6-160">Default service container replacement</span></span>

<span data-ttu-id="75ef6-161">Yerleşik hizmet kapsayıcısı, çerçeve ihtiyaçlarına ve çoğu tüketici uygulamasına hizmet vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-161">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="75ef6-162">Desteklemediği belirli bir özelliğe ihtiyacınız yoksa, yerleşik kapsayıcının kullanılması önerilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="75ef6-162">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="75ef6-163">Özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="75ef6-163">Property injection</span></span>
- <span data-ttu-id="75ef6-164">Ada göre ekleme</span><span class="sxs-lookup"><span data-stu-id="75ef6-164">Injection based on name</span></span>
- <span data-ttu-id="75ef6-165">Alt kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="75ef6-165">Child containers</span></span>
- <span data-ttu-id="75ef6-166">Özel ömür yönetimi</span><span class="sxs-lookup"><span data-stu-id="75ef6-166">Custom lifetime management</span></span>
- <span data-ttu-id="75ef6-167">`Func<T>` yavaş başlatma desteği</span><span class="sxs-lookup"><span data-stu-id="75ef6-167">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="75ef6-168">Kural tabanlı kayıt</span><span class="sxs-lookup"><span data-stu-id="75ef6-168">Convention-based registration</span></span>

<span data-ttu-id="75ef6-169">Aşağıdaki üçüncü taraf kapsayıcıları ASP.NET Core uygulamalarla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="75ef6-169">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="75ef6-170">Autofac</span><span class="sxs-lookup"><span data-stu-id="75ef6-170">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="75ef6-171">Drıioc</span><span class="sxs-lookup"><span data-stu-id="75ef6-171">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="75ef6-172">Yetkisiz kullanım</span><span class="sxs-lookup"><span data-stu-id="75ef6-172">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="75ef6-173">Açık Inject</span><span class="sxs-lookup"><span data-stu-id="75ef6-173">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="75ef6-174">E</span><span class="sxs-lookup"><span data-stu-id="75ef6-174">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="75ef6-175">Stakıbox</span><span class="sxs-lookup"><span data-stu-id="75ef6-175">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="75ef6-176">Unity</span><span class="sxs-lookup"><span data-stu-id="75ef6-176">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="75ef6-177">İş parçacığı güvenliği</span><span class="sxs-lookup"><span data-stu-id="75ef6-177">Thread safety</span></span>

<span data-ttu-id="75ef6-178">İş parçacığı güvenli Singleton Hizmetleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="75ef6-178">Create thread-safe singleton services.</span></span> <span data-ttu-id="75ef6-179">Tek bir hizmetin geçici bir hizmete bağımlılığı varsa, geçici hizmet aynı zamanda tek tarafından nasıl kullanıldığına bağlı olarak iş parçacığı güvenliği de gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-179">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="75ef6-180">Tek bir hizmetin fabrika yöntemi (örneğin, AddSingleton için ikinci bağımsız değişken [ \<TService> \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), iş parçacığı açısından güvenli olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="75ef6-180">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="75ef6-181">Bir Type ( `static` ) Oluşturucusu gibi, tek bir iş parçacığı tarafından yalnızca bir kez çağrılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-181">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="75ef6-182">Öneriler</span><span class="sxs-lookup"><span data-stu-id="75ef6-182">Recommendations</span></span>

- <span data-ttu-id="75ef6-183">`async/await` ve `Task` tabanlı hizmet çözümlemesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="75ef6-183">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="75ef6-184">C# zaman uyumsuz oluşturucuları desteklemediğinden, hizmeti zaman uyumlu olarak çözümledikten sonra zaman uyumsuz yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-184">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="75ef6-185">Veri ve yapılandırmayı doğrudan hizmet kapsayıcısında saklamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-185">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="75ef6-186">Örneğin, bir kullanıcının alışveriş sepeti genellikle hizmet kapsayıcısına eklenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-186">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="75ef6-187">Yapılandırma, Seçenekler modelini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-187">Configuration should use the options pattern.</span></span> <span data-ttu-id="75ef6-188">Benzer şekilde, yalnızca başka bir nesneye erişime izin vermek için mevcut olan "veri sahibi" nesnelerinden kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-188">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="75ef6-189">DI aracılığıyla gerçek öğe istemek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-189">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="75ef6-190">Hizmetlere statik erişimi önleyin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-190">Avoid static access to services.</span></span> <span data-ttu-id="75ef6-191">Örneğin, başka bir yerde kullanmak üzere [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) statik bir alan veya özellik olarak yakalanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-191">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="75ef6-192">[Dı fabrikalarını](#async-di-factories-can-cause-deadlocks) hızlı ve zaman uyumlu tutun.</span><span class="sxs-lookup"><span data-stu-id="75ef6-192">Keep [DI factories](#async-di-factories-can-cause-deadlocks) fast and synchronous.</span></span>
- <span data-ttu-id="75ef6-193">[*Hizmet bulucu deseninin*](#scoped-service-as-singleton)kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-193">Avoid using the [*service locator pattern*](#scoped-service-as-singleton).</span></span> <span data-ttu-id="75ef6-194">Örneğin, <xref:System.IServiceProvider.GetService%2A> yerine bir hizmet örneği elde etmek için Invoke kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="75ef6-194">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="75ef6-195">Önlemek için başka bir hizmet bulucu çeşitlemesi, çalışma zamanında bağımlılıkları çözümleyen bir ekleme.</span><span class="sxs-lookup"><span data-stu-id="75ef6-195">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="75ef6-196">Bu uygulamalardan her ikisi de [Denetim stratejilerini geçersiz kılar](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) .</span><span class="sxs-lookup"><span data-stu-id="75ef6-196">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="75ef6-197">İçindeki çağrılardan <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> kaçının `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-197">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="75ef6-198">Çağırma `BuildServiceProvider` genellikle geliştirici içindeki bir hizmeti çözmek istediğinde oluşur `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-198">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="75ef6-199">[Atılabilir geçici hizmetler](#disposable-transient-services-captured-by-container) , aktiften çıkarma için kapsayıcı tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-199">[Disposable transient services are captured](#disposable-transient-services-captured-by-container) by the container for disposal.</span></span> <span data-ttu-id="75ef6-200">Bu, üst düzey kapsayıcıdan çözümlenirse bir bellek sızıntısını açabilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-200">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="75ef6-201">Uygulamanın kapsamlı hizmetleri yakalayan tekton içermediğinden emin olmak için kapsam doğrulamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="75ef6-201">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="75ef6-202">Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="75ef6-202">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="75ef6-203">Tüm öneri kümeleri gibi, bir öneriyi yok saymayı yok saymış durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-203">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="75ef6-204">Özel durumlar nadiren, genellikle Framework içindeki özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-204">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="75ef6-205">Dı, statik/genel nesne erişim desenlerinin bir *alternatifidir* .</span><span class="sxs-lookup"><span data-stu-id="75ef6-205">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="75ef6-206">Statik nesne erişimi ile karıştırırsanız, dı 'nin avantajlarını fark edemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-206">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="example-anti-patterns"></a><span data-ttu-id="75ef6-207">Örnek Desenler</span><span class="sxs-lookup"><span data-stu-id="75ef6-207">Example anti-patterns</span></span>

<span data-ttu-id="75ef6-208">Bu makaledeki yönergelere ek olarak, *kaçınması **gereken*** birkaç kenar düzeyi vardır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-208">In addition to the guidelines in this article, there are several anti-patterns *you **should** avoid* .</span></span> <span data-ttu-id="75ef6-209">Bu koruma alışkanlarından bazıları, çalışma zamanlarının kendisini geliştirmekten dersleri.</span><span class="sxs-lookup"><span data-stu-id="75ef6-209">Some of these anti-patterns are learnings from developing the runtimes themselves.</span></span>

> [!WARNING]
> <span data-ttu-id="75ef6-210">Bunlar örnek desenler, *kodu kopyalamayın,* bu *desenleri kullanmayın ve* tüm maliyetlerde bu modellerden kaçının.</span><span class="sxs-lookup"><span data-stu-id="75ef6-210">These are example anti-patterns, *do not* copy the code, *do not* use these patterns, and avoid these patterns at all costs.</span></span>

### <a name="disposable-transient-services-captured-by-container"></a><span data-ttu-id="75ef6-211">Atılabilir kapsayıcı tarafından yakalanan geçici hizmetler</span><span class="sxs-lookup"><span data-stu-id="75ef6-211">Disposable transient services captured by container</span></span>

<span data-ttu-id="75ef6-212">Uygulayan *geçici* Hizmetleri kaydettiğinizde <xref:System.IDisposable> , varsayılan olarak dı kapsayıcısı bu başvurulara sahip olur ve uygulama durduruluncaya kadar bu referanslara göre değil <xref:System.IDisposable.Dispose> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-212">When you register *Transient* services that implement <xref:System.IDisposable>, by default the DI container will hold onto these references, and not <xref:System.IDisposable.Dispose> of them until the application stops.</span></span> <span data-ttu-id="75ef6-213">Bu, düzey kapsayıcısından çözümlenirse bir bellek sızıntısını açabilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-213">This can turn into a memory leak if resolved from the level container.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

<span data-ttu-id="75ef6-214">Önceki anti-düzeninde, 1.000 `ExampleDisposable` nesnelerinin örneği oluşturulur ve kökü atanır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-214">In the preceding anti-pattern, 1,000 `ExampleDisposable` objects are instantiated and rooted.</span></span> <span data-ttu-id="75ef6-215">Bunlar, `serviceProvider` örnek atılana kadar uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-215">They will not be disposed of until the `serviceProvider` instance is disposed.</span></span>

<span data-ttu-id="75ef6-216">Bellek sızıntılarını hata ayıklama hakkında daha fazla bilgi için bkz. [.net 'te Bellek sızıntısını hata ayıklama](../diagnostics/debug-memory-leak.md).</span><span class="sxs-lookup"><span data-stu-id="75ef6-216">For more information on debugging memory leaks, see [Debug a memory leak in .NET](../diagnostics/debug-memory-leak.md).</span></span>

### <a name="async-di-factories-can-cause-deadlocks"></a><span data-ttu-id="75ef6-217">Zaman uyumsuz dı fabrikası kilitlenmeleri neden olabilir</span><span class="sxs-lookup"><span data-stu-id="75ef6-217">Async DI factories can cause deadlocks</span></span>

<span data-ttu-id="75ef6-218">"Dı fabrikaları" terimi çağrılırken var olan aşırı yükleme yöntemlerine başvurur `Add{LIFETIME}` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-218">The term "DI factories" refers to the overload methods that exist when calling `Add{LIFETIME}`.</span></span> <span data-ttu-id="75ef6-219">Hizmetin kaydedildiği konumu kabul eden aşırı yüklemeler vardır `Func<IServiceProvider, T>` `T` ve parametresi adlandırılır `implementationFactory` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-219">There are overloads accepting a `Func<IServiceProvider, T>` where `T` is the service being registered, and the parameter is named `implementationFactory`.</span></span> <span data-ttu-id="75ef6-220">`implementationFactory`Bir lambda ifadesi, yerel işlev veya yöntem olarak belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-220">The `implementationFactory` can be provided as a lambda expression, local function, or method.</span></span> <span data-ttu-id="75ef6-221">Fabrika zaman uyumsuzdur ve kullanıyorsanız <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> , bu da kilitlenmeye neden olur.</span><span class="sxs-lookup"><span data-stu-id="75ef6-221">If the factory is asynchronous, and you use <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>, this will cause a deadlock.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

<span data-ttu-id="75ef6-222">Önceki kodda, `implementationFactory` gövde döndürülen bir yöntemde çağırdığı bir lambda ifadesi verilir <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> `Task<Bar>` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-222">In the preceding code, the `implementationFactory` is given a lambda expression where the body calls <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> on a `Task<Bar>` returning method.</span></span> <span data-ttu-id="75ef6-223">Bu, ***kilitlenmeye neden olur*** .</span><span class="sxs-lookup"><span data-stu-id="75ef6-223">This ***causes a deadlock*** .</span></span> <span data-ttu-id="75ef6-224">`GetBarAsync`Yöntemi, ile zaman uyumsuz bir iş işlemini taklit eder <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve ardından çağırır <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-224">The `GetBarAsync` method simply emulates an asynchronous work operation with <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType>, and then calls <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)>.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

<span data-ttu-id="75ef6-225">Zaman uyumsuz yönergeler hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama: önemli bilgi ve öneriler](../../csharp/async.md#important-info-and-advice).</span><span class="sxs-lookup"><span data-stu-id="75ef6-225">For more information on asynchronous guidance, see [Asynchronous programming: Important info and advice](../../csharp/async.md#important-info-and-advice).</span></span> <span data-ttu-id="75ef6-226">Hata ayıklama kilitlenmeleri hakkında daha fazla bilgi için bkz. [.net 'te kilitlenmeye hata ayıklama](../diagnostics/debug-deadlock.md).</span><span class="sxs-lookup"><span data-stu-id="75ef6-226">For more information debugging deadlocks, see [Debug a deadlock in .NET](../diagnostics/debug-deadlock.md).</span></span>

<span data-ttu-id="75ef6-227">Bu bir anti-model çalıştırırken ve kilitlenme gerçekleştiğinde, Visual Studio 'nun paralel yığınları penceresinde bekleyen iki iş parçacığını görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-227">When you're running this anti-pattern and the deadlock occurs, you can view the two threads waiting from Visual Studio's Parallel Stacks window.</span></span> <span data-ttu-id="75ef6-228">Daha fazla bilgi için bkz. [Paralel Yığınlar penceresinde iş parçacıklarını ve görevleri görüntüleme](/visualstudio/debugger/using-the-parallel-stacks-window).</span><span class="sxs-lookup"><span data-stu-id="75ef6-228">For more information, see [View threads and tasks in the Parallel Stacks window](/visualstudio/debugger/using-the-parallel-stacks-window).</span></span>

### <a name="captive-dependency"></a><span data-ttu-id="75ef6-229">Captive bağımlılığı</span><span class="sxs-lookup"><span data-stu-id="75ef6-229">Captive dependency</span></span>

<span data-ttu-id="75ef6-230">["Captive Dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) terimi, [Seeman 'ı işaret](https://blog.ploeh.dk/about)ederek ortaklaşa bulunur ve daha uzun süreli bir hizmetin daha kısa süreli bir hizmet başlığı taşıdığı hizmet yaşam sürelerinin yanlış yapılandırılması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-230">The term ["captive dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) was coined by [Mark Seeman](https://blog.ploeh.dk/about), and refers to the misconfiguration of service lifetimes, where a longer-lived service holds a shorter-lived service captive.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

<span data-ttu-id="75ef6-231">Yukarıdaki kodda, `Foo` tek bir olarak kaydedilir ve `Bar` yüzeyde bir kapsam geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="75ef6-231">In the preceding code, `Foo` is registered as a singleton and `Bar` is scoped - which on the surface seems valid.</span></span> <span data-ttu-id="75ef6-232">Ancak uygulamasını göz önünde bulundurun `Foo` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-232">However, consider the implementation of `Foo`.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

<span data-ttu-id="75ef6-233">`Foo`Nesnesi, bir nesnesi gerektirir ve bu bir tekil olduğundan `Bar` `Foo` ve `Bar` kapsamı belirlenmiş olduğundan, bu bir yanlış yapılandırma.</span><span class="sxs-lookup"><span data-stu-id="75ef6-233">The `Foo` object requires a `Bar` object, and since `Foo` is a singleton, and `Bar` is scoped - this is a misconfiguration.</span></span> <span data-ttu-id="75ef6-234">Olduğu gibi, `Foo` yalnızca bir kez örneklenebilir ve `Bar` kendi yaşam süresi boyunca, amaçlanan kapsamlı yaşam süresinden daha uzun sürer `Bar` .</span><span class="sxs-lookup"><span data-stu-id="75ef6-234">As is, `Foo` would only be instantiated once, and it would hold onto `Bar` for its lifetime, which is longer than the intended scoped lifetime of `Bar`.</span></span> <span data-ttu-id="75ef6-235">' A geçirerek kapsamları doğrulamayı düşünmelisiniz `validateScopes: true` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-235">You should consider validating scopes, by passing `validateScopes: true` to the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)>.</span></span> <span data-ttu-id="75ef6-236">Kapsamları doğruladığınızda, <xref:System.InvalidOperationException> "tek tek ' foo ' öğesinden" kapsamlı hizmet ' çubuğu ' kullanılmasına benzer bir ileti içeren bir ileti alırsınız.</span><span class="sxs-lookup"><span data-stu-id="75ef6-236">When you validate the scopes, you'd get an <xref:System.InvalidOperationException> with a message similar to "Cannot consume scoped service 'Bar' from singleton 'Foo'.".</span></span>

<span data-ttu-id="75ef6-237">Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="75ef6-237">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

### <a name="scoped-service-as-singleton"></a><span data-ttu-id="75ef6-238">Tek tek olarak kapsamlı hizmet</span><span class="sxs-lookup"><span data-stu-id="75ef6-238">Scoped service as singleton</span></span>

<span data-ttu-id="75ef6-239">Kapsamı belirlenmiş hizmetler kullanılırken, kapsam veya mevcut bir kapsamda bir kapsam oluşturuyorsanız, hizmet tek olur.</span><span class="sxs-lookup"><span data-stu-id="75ef6-239">When using scoped services, if you're not creating a scope or within an existing scope - the service becomes a singleton.</span></span>

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

<span data-ttu-id="75ef6-240">Yukarıdaki kodda, `Bar` doğru olan bir içinde alınır <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="75ef6-240">In the preceding code, `Bar` is retrieved within an <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>, which is correct.</span></span> <span data-ttu-id="75ef6-241">Kenar yumuşatma, `Bar` kapsam dışından alındır ve değişken, `avoid` hangi örnek almanın yanlış olduğunu göstermek için adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="75ef6-241">The anti-pattern is the retrieval of `Bar` outside of the scope, and the variable is named `avoid` to show which example retrieval is incorrect.</span></span>

## <a name="see-also"></a><span data-ttu-id="75ef6-242">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75ef6-242">See also</span></span>

- [<span data-ttu-id="75ef6-243">.NET 'e bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="75ef6-243">Dependency injection in .NET</span></span>](dependency-injection.md)
- [<span data-ttu-id="75ef6-244">Öğretici: .NET 'te bağımlılık ekleme kullanma</span><span class="sxs-lookup"><span data-stu-id="75ef6-244">Tutorial: Use dependency injection in .NET</span></span>](dependency-injection-usage.md)
