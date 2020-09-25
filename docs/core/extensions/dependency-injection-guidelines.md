---
title: Bağımlılık ekleme yönergeleri
description: .NET uygulama geliştirmesi için çeşitli bağımlılık ekleme kılavuzlarını ve en iyi uygulamaları öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: guide
ms.openlocfilehash: a8d52642b9217c7340db69494624d8ab85ea6c92
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247911"
---
# <a name="dependency-injection-guidelines"></a><span data-ttu-id="94717-103">Bağımlılık ekleme yönergeleri</span><span class="sxs-lookup"><span data-stu-id="94717-103">Dependency injection guidelines</span></span>

<span data-ttu-id="94717-104">Bu makalede, .NET uygulamalarında bağımlılık ekleme işlemini uygulamaya yönelik genel yönergeler ve en iyi uygulamalar sağlanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94717-104">This article provides general guidelines and best practices for implementing dependency injection in .NET applications.</span></span>

## <a name="design-services-for-dependency-injection"></a><span data-ttu-id="94717-105">Bağımlılık ekleme için tasarım hizmetleri</span><span class="sxs-lookup"><span data-stu-id="94717-105">Design services for dependency injection</span></span>

<span data-ttu-id="94717-106">Bağımlılık ekleme için Hizmetleri tasarlarken:</span><span class="sxs-lookup"><span data-stu-id="94717-106">When designing services for dependency injection:</span></span>

- <span data-ttu-id="94717-107">Durum bilgisi olan statik sınıflar ve Üyeler kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="94717-107">Avoid stateful, static classes and members.</span></span> <span data-ttu-id="94717-108">Bunun yerine Singleton hizmetlerini kullanmak için uygulama tasarlayarak genel durum oluşturmamaya özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="94717-108">Avoid creating global state by designing apps to use singleton services instead.</span></span>
- <span data-ttu-id="94717-109">Hizmetler içindeki bağımlı sınıfların doğrudan örneklenmesini önleyin.</span><span class="sxs-lookup"><span data-stu-id="94717-109">Avoid direct instantiation of dependent classes within services.</span></span> <span data-ttu-id="94717-110">Doğrudan örnekleme kodu belirli bir uygulamaya bağar.</span><span class="sxs-lookup"><span data-stu-id="94717-110">Direct instantiation couples the code to a particular implementation.</span></span>
- <span data-ttu-id="94717-111">Hizmetleri küçük, iyi bir şekilde ve kolayca test edin.</span><span class="sxs-lookup"><span data-stu-id="94717-111">Make services small, well-factored, and easily tested.</span></span>

<span data-ttu-id="94717-112">Bir sınıfta eklenen çok sayıda bağımlılık varsa, bu, sınıfta çok fazla sorumluluğun olduğu ve [tek sorumluluk ilkesini (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)ihlal eden bir işaret olabilir.</span><span class="sxs-lookup"><span data-stu-id="94717-112">If a class has many injected dependencies, it might be a sign that the class has too many responsibilities and violates the [Single Responsibility Principle (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility).</span></span> <span data-ttu-id="94717-113">Bazı sorumlulukları yeni sınıflara taşıyarak sınıfı yeniden düzenleme girişimi.</span><span class="sxs-lookup"><span data-stu-id="94717-113">Attempt to refactor the class by moving some of its responsibilities into new classes.</span></span>

### <a name="disposal-of-services"></a><span data-ttu-id="94717-114">Hizmetlerin elden çıkarılması</span><span class="sxs-lookup"><span data-stu-id="94717-114">Disposal of services</span></span>

<span data-ttu-id="94717-115">Kapsayıcı, oluşturduğu türlerin temizlenmesi ve örneklere çağrı yapmaktan sorumludur <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="94717-115">The container is responsible for cleanup of types it creates, and calls <xref:System.IDisposable.Dispose%2A> on <xref:System.IDisposable> instances.</span></span> <span data-ttu-id="94717-116">Kapsayıcıdan çözümlenen hizmetler hiçbir şekilde geliştirici tarafından atılamaz.</span><span class="sxs-lookup"><span data-stu-id="94717-116">Services resolved from the container should never be disposed by the developer.</span></span> <span data-ttu-id="94717-117">Bir tür veya fabrika tek bir olarak kayıtlıysa, kapsayıcı kendiliğinden otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="94717-117">If a type or factory is registered as a singleton, the container disposes the singleton automatically.</span></span>

<span data-ttu-id="94717-118">Aşağıdaki örnekte, hizmetler hizmet kapsayıcısı tarafından oluşturulur ve otomatik olarak elden alınır:</span><span class="sxs-lookup"><span data-stu-id="94717-118">In the following example, the services are created by the service container and disposed automatically:</span></span>

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

<span data-ttu-id="94717-119">Hata ayıklama konsolu, çalıştırıldıktan sonra aşağıdaki örnek çıktıyı gösterir:</span><span class="sxs-lookup"><span data-stu-id="94717-119">The debug console shows the following sample output after running:</span></span>

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

### <a name="services-not-created-by-the-service-container"></a><span data-ttu-id="94717-120">Hizmet kapsayıcısı tarafından oluşturulmayan hizmetler</span><span class="sxs-lookup"><span data-stu-id="94717-120">Services not created by the service container</span></span>

<span data-ttu-id="94717-121">Aşağıdaki kodu inceleyin:</span><span class="sxs-lookup"><span data-stu-id="94717-121">Consider the following code:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

<span data-ttu-id="94717-122">Yukarıdaki kodda:</span><span class="sxs-lookup"><span data-stu-id="94717-122">In the preceding code:</span></span>

- <span data-ttu-id="94717-123">`ExampleService`Örnek, hizmet **not** kapsayıcısı tarafından oluşturulmamış.</span><span class="sxs-lookup"><span data-stu-id="94717-123">The `ExampleService` instance is **not** created by the service container.</span></span>
- <span data-ttu-id="94717-124">Framework Hizmetleri otomatik **olarak elden atmaz.**</span><span class="sxs-lookup"><span data-stu-id="94717-124">The framework does **not** dispose of the services automatically.</span></span>
- <span data-ttu-id="94717-125">Geliştirici, hizmetleri elden atan sorumludur.</span><span class="sxs-lookup"><span data-stu-id="94717-125">The developer is responsible for disposing the services.</span></span>

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a><span data-ttu-id="94717-126">Geçici ve paylaşılan örnekler için IDisposable Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="94717-126">IDisposable guidance for Transient and shared instances</span></span>

#### <a name="transient-limited-lifetime"></a><span data-ttu-id="94717-127">Geçici, sınırlı ömür</span><span class="sxs-lookup"><span data-stu-id="94717-127">Transient, limited lifetime</span></span>

<span data-ttu-id="94717-128">**Senaryo**</span><span class="sxs-lookup"><span data-stu-id="94717-128">**Scenario**</span></span>

<span data-ttu-id="94717-129">Uygulama, <xref:System.IDisposable> aşağıdaki senaryolardan biri için geçici bir yaşam süresine sahip bir örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="94717-129">The app requires an <xref:System.IDisposable> instance with a transient lifetime for either of the following scenarios:</span></span>

- <span data-ttu-id="94717-130">Örnek, kök kapsamda (kök kapsayıcı) çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="94717-130">The instance is resolved in the root scope (root container).</span></span>
- <span data-ttu-id="94717-131">Kapsam bitmeden önce örnek atılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94717-131">The instance should be disposed before the scope ends.</span></span>

<span data-ttu-id="94717-132">**Çözüm**</span><span class="sxs-lookup"><span data-stu-id="94717-132">**Solution**</span></span>

<span data-ttu-id="94717-133">Üst kapsamın dışında bir örnek oluşturmak için fabrika modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-133">Use the factory pattern to create an instance outside of the parent scope.</span></span> <span data-ttu-id="94717-134">Bu durumda, uygulama genellikle `Create` son türün oluşturucusunu doğrudan çağıran bir yönteme sahip olur.</span><span class="sxs-lookup"><span data-stu-id="94717-134">In this situation, the app would generally have a `Create` method that calls the final type's constructor directly.</span></span> <span data-ttu-id="94717-135">Son türün başka bağımlılıkları varsa, fabrika şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="94717-135">If the final type has other dependencies, the factory can:</span></span>

- <span data-ttu-id="94717-136">Oluşturucusunda bir alın <xref:System.IServiceProvider> .</span><span class="sxs-lookup"><span data-stu-id="94717-136">Receive an <xref:System.IServiceProvider> in its constructor.</span></span>
- <span data-ttu-id="94717-137"><xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType>Kapsayıcının bağımlılıkları için kapsayıcıyı kullanırken, örneği kapsayıcının dışında örneklemek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-137">Use <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType> to instantiate the instance outside of the container, while using the container for its dependencies.</span></span>

#### <a name="shared-instance-limited-lifetime"></a><span data-ttu-id="94717-138">Paylaşılan örnek, sınırlı ömür</span><span class="sxs-lookup"><span data-stu-id="94717-138">Shared instance, limited lifetime</span></span>

<span data-ttu-id="94717-139">**Senaryo**</span><span class="sxs-lookup"><span data-stu-id="94717-139">**Scenario**</span></span>

<span data-ttu-id="94717-140">Uygulamanın <xref:System.IDisposable> birden çok hizmet arasında paylaşılan bir örnek olması gerekir, ancak <xref:System.IDisposable> örnek sınırlı bir yaşam süresine sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94717-140">The app requires a shared <xref:System.IDisposable> instance across multiple services, but the <xref:System.IDisposable> instance should have a limited lifetime.</span></span>

<span data-ttu-id="94717-141">**Çözüm**</span><span class="sxs-lookup"><span data-stu-id="94717-141">**Solution**</span></span>

<span data-ttu-id="94717-142">Örneği kapsamlı bir ömür ile kaydedin.</span><span class="sxs-lookup"><span data-stu-id="94717-142">Register the instance with a scoped lifetime.</span></span> <span data-ttu-id="94717-143"><xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType>Yeni bir oluşturmak için kullanın <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> .</span><span class="sxs-lookup"><span data-stu-id="94717-143">Use <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType> to create a new <xref:Microsoft.Extensions.DependencyInjection.IServiceScope>.</span></span> <span data-ttu-id="94717-144"><xref:System.IServiceProvider>Gerekli hizmetleri almak için kapsam ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-144">Use the scope's <xref:System.IServiceProvider> to get required services.</span></span> <span data-ttu-id="94717-145">Artık gerekli olmadığında kapsamı atın.</span><span class="sxs-lookup"><span data-stu-id="94717-145">Dispose the scope when it's no longer needed.</span></span>

#### <a name="general-idisposable-guidelines"></a><span data-ttu-id="94717-146">Genel `IDisposable` yönergeler</span><span class="sxs-lookup"><span data-stu-id="94717-146">General `IDisposable` guidelines</span></span>

- <span data-ttu-id="94717-147"><xref:System.IDisposable>Örnekleri geçici bir yaşam süresine kaydetmez.</span><span class="sxs-lookup"><span data-stu-id="94717-147">Don't register <xref:System.IDisposable> instances with a transient lifetime.</span></span> <span data-ttu-id="94717-148">Bunun yerine fabrika modelini kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-148">Use the factory pattern instead.</span></span>
- <span data-ttu-id="94717-149"><xref:System.IDisposable>Kök kapsamda geçici veya kapsamlı bir yaşam süresine sahip örnekleri çözümleyin.</span><span class="sxs-lookup"><span data-stu-id="94717-149">Don't resolve <xref:System.IDisposable> instances with a transient or scoped lifetime in the root scope.</span></span> <span data-ttu-id="94717-150">Bunun tek istisnası, uygulamanın oluşturma/yeniden oluşturma/yeniden oluşturma ve uygulama oluşturmasıdır <xref:System.IServiceProvider> , ancak bu ideal bir modeldir.</span><span class="sxs-lookup"><span data-stu-id="94717-150">The only exception to this is if the app creates/recreates and disposes <xref:System.IServiceProvider>, but this isn't an ideal pattern.</span></span>
- <span data-ttu-id="94717-151">Bir <xref:System.IDisposable> bağımlılık alma yoluyla, alıcının kendisini uygulaması gerekmez <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="94717-151">Receiving an <xref:System.IDisposable> dependency via DI doesn't require that the receiver implement <xref:System.IDisposable> itself.</span></span> <span data-ttu-id="94717-152"><xref:System.IDisposable>Bağımlılığın alıcısı <xref:System.IDisposable.Dispose%2A> Bu bağımlılıkta çağrımamalıdır.</span><span class="sxs-lookup"><span data-stu-id="94717-152">The receiver of the <xref:System.IDisposable> dependency shouldn't call <xref:System.IDisposable.Dispose%2A> on that dependency.</span></span>
- <span data-ttu-id="94717-153">Hizmetlerin ömrünü denetlemek için kapsamları kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-153">Use scopes to control the lifetimes of services.</span></span> <span data-ttu-id="94717-154">Kapsamlar hiyerarşik değildir ve kapsamlar arasında özel bir bağlantı yoktur.</span><span class="sxs-lookup"><span data-stu-id="94717-154">Scopes aren't hierarchical, and there's no special connection among scopes.</span></span>

<span data-ttu-id="94717-155">Kaynak temizleme hakkında daha fazla bilgi için bkz. [Dispose yöntemi uygulama](../../standard/garbage-collection/implementing-dispose.md)</span><span class="sxs-lookup"><span data-stu-id="94717-155">For more information on resource cleanup, see [Implement a Dispose method](../../standard/garbage-collection/implementing-dispose.md)</span></span>

## <a name="default-service-container-replacement"></a><span data-ttu-id="94717-156">Varsayılan hizmet kapsayıcısı değiştirme</span><span class="sxs-lookup"><span data-stu-id="94717-156">Default service container replacement</span></span>

<span data-ttu-id="94717-157">Yerleşik hizmet kapsayıcısı, çerçeve ihtiyaçlarına ve çoğu tüketici uygulamasına hizmet vermek için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="94717-157">The built-in service container is designed to serve the needs of the framework and most consumer apps.</span></span> <span data-ttu-id="94717-158">Desteklemediği belirli bir özelliğe ihtiyacınız yoksa, yerleşik kapsayıcının kullanılması önerilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="94717-158">We recommend using the built-in container unless you need a specific feature that it doesn't support, such as:</span></span>

- <span data-ttu-id="94717-159">Özellik ekleme</span><span class="sxs-lookup"><span data-stu-id="94717-159">Property injection</span></span>
- <span data-ttu-id="94717-160">Ada göre ekleme</span><span class="sxs-lookup"><span data-stu-id="94717-160">Injection based on name</span></span>
- <span data-ttu-id="94717-161">Alt kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="94717-161">Child containers</span></span>
- <span data-ttu-id="94717-162">Özel ömür yönetimi</span><span class="sxs-lookup"><span data-stu-id="94717-162">Custom lifetime management</span></span>
- <span data-ttu-id="94717-163">`Func<T>` yavaş başlatma desteği</span><span class="sxs-lookup"><span data-stu-id="94717-163">`Func<T>` support for lazy initialization</span></span>
- <span data-ttu-id="94717-164">Kural tabanlı kayıt</span><span class="sxs-lookup"><span data-stu-id="94717-164">Convention-based registration</span></span>

<span data-ttu-id="94717-165">Aşağıdaki üçüncü taraf kapsayıcıları ASP.NET Core uygulamalarla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="94717-165">The following third-party containers can be used with ASP.NET Core apps:</span></span>

- [<span data-ttu-id="94717-166">Autofac</span><span class="sxs-lookup"><span data-stu-id="94717-166">Autofac</span></span>](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [<span data-ttu-id="94717-167">Drıioc</span><span class="sxs-lookup"><span data-stu-id="94717-167">DryIoc</span></span>](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [<span data-ttu-id="94717-168">Yetkisiz kullanım</span><span class="sxs-lookup"><span data-stu-id="94717-168">Grace</span></span>](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [<span data-ttu-id="94717-169">Açık Inject</span><span class="sxs-lookup"><span data-stu-id="94717-169">LightInject</span></span>](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [<span data-ttu-id="94717-170">E</span><span class="sxs-lookup"><span data-stu-id="94717-170">Lamar</span></span>](https://jasperfx.github.io/lamar/)
- [<span data-ttu-id="94717-171">Stakıbox</span><span class="sxs-lookup"><span data-stu-id="94717-171">Stashbox</span></span>](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [<span data-ttu-id="94717-172">Unity</span><span class="sxs-lookup"><span data-stu-id="94717-172">Unity</span></span>](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a><span data-ttu-id="94717-173">İş parçacığı güvenliği</span><span class="sxs-lookup"><span data-stu-id="94717-173">Thread safety</span></span>

<span data-ttu-id="94717-174">İş parçacığı güvenli Singleton Hizmetleri oluşturun.</span><span class="sxs-lookup"><span data-stu-id="94717-174">Create thread-safe singleton services.</span></span> <span data-ttu-id="94717-175">Tek bir hizmetin geçici bir hizmete bağımlılığı varsa, geçici hizmet aynı zamanda tek tarafından nasıl kullanıldığına bağlı olarak iş parçacığı güvenliği de gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="94717-175">If a singleton service has a dependency on a transient service, the transient service may also require thread safety depending on how it's used by the singleton.</span></span>

<span data-ttu-id="94717-176">Tek bir hizmetin fabrika yöntemi (örneğin, AddSingleton için ikinci bağımsız değişken [ \<TService> \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), iş parçacığı açısından güvenli olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="94717-176">The factory method of single service, such as the second argument to [AddSingleton\<TService>(IServiceCollection, Func\<IServiceProvider,TService>)](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), doesn't need to be thread-safe.</span></span> <span data-ttu-id="94717-177">Bir Type ( `static` ) Oluşturucusu gibi, tek bir iş parçacığı tarafından yalnızca bir kez çağrılması garanti edilir.</span><span class="sxs-lookup"><span data-stu-id="94717-177">Like a type (`static`) constructor, it's guaranteed to be called only once by a single thread.</span></span>

## <a name="recommendations"></a><span data-ttu-id="94717-178">Öneriler</span><span class="sxs-lookup"><span data-stu-id="94717-178">Recommendations</span></span>

- <span data-ttu-id="94717-179">`async/await` ve `Task` tabanlı hizmet çözümlemesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="94717-179">`async/await` and `Task` based service resolution isn't supported.</span></span> <span data-ttu-id="94717-180">C# zaman uyumsuz oluşturucuları desteklemediğinden, hizmeti zaman uyumlu olarak çözümledikten sonra zaman uyumsuz yöntemler kullanın.</span><span class="sxs-lookup"><span data-stu-id="94717-180">Because C# doesn't support asynchronous constructors, use asynchronous methods after synchronously resolving the service.</span></span>
- <span data-ttu-id="94717-181">Veri ve yapılandırmayı doğrudan hizmet kapsayıcısında saklamaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="94717-181">Avoid storing data and configuration directly in the service container.</span></span> <span data-ttu-id="94717-182">Örneğin, bir kullanıcının alışveriş sepeti genellikle hizmet kapsayıcısına eklenmemelidir.</span><span class="sxs-lookup"><span data-stu-id="94717-182">For example, a user's shopping cart shouldn't typically be added to the service container.</span></span> <span data-ttu-id="94717-183">Yapılandırma, Seçenekler modelini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="94717-183">Configuration should use the options pattern.</span></span> <span data-ttu-id="94717-184">Benzer şekilde, yalnızca başka bir nesneye erişime izin vermek için mevcut olan "veri sahibi" nesnelerinden kaçının.</span><span class="sxs-lookup"><span data-stu-id="94717-184">Similarly, avoid "data holder" objects that only exist to allow access to another object.</span></span> <span data-ttu-id="94717-185">DI aracılığıyla gerçek öğe istemek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="94717-185">It's better to request the actual item via DI.</span></span>
- <span data-ttu-id="94717-186">Hizmetlere statik erişimi önleyin.</span><span class="sxs-lookup"><span data-stu-id="94717-186">Avoid static access to services.</span></span> <span data-ttu-id="94717-187">Örneğin, başka bir yerde kullanmak üzere [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) statik bir alan veya özellik olarak yakalanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="94717-187">For example, avoid capturing [IApplicationBuilder.ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) as a static field or property for use elsewhere.</span></span>
- <span data-ttu-id="94717-188">Dı fabrikalarını hızlı ve zaman uyumlu tutun.</span><span class="sxs-lookup"><span data-stu-id="94717-188">Keep DI factories fast and synchronous.</span></span>
- <span data-ttu-id="94717-189">*Hizmet bulucu deseninin*kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="94717-189">Avoid using the *service locator pattern*.</span></span> <span data-ttu-id="94717-190">Örneğin, <xref:System.IServiceProvider.GetService%2A> yerine bir hizmet örneği elde etmek için Invoke kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="94717-190">For example, don't invoke <xref:System.IServiceProvider.GetService%2A> to obtain a service instance when you can use DI instead.</span></span>
- <span data-ttu-id="94717-191">Önlemek için başka bir hizmet bulucu çeşitlemesi, çalışma zamanında bağımlılıkları çözümleyen bir ekleme.</span><span class="sxs-lookup"><span data-stu-id="94717-191">Another service locator variation to avoid is injecting a factory that resolves dependencies at runtime.</span></span> <span data-ttu-id="94717-192">Bu uygulamalardan her ikisi de [Denetim stratejilerini geçersiz kılar](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) .</span><span class="sxs-lookup"><span data-stu-id="94717-192">Both of these practices mix [Inversion of Control](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) strategies.</span></span>
- <span data-ttu-id="94717-193">İçindeki çağrılardan <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> kaçının `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="94717-193">Avoid calls to <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> in `ConfigureServices`.</span></span> <span data-ttu-id="94717-194">Çağırma `BuildServiceProvider` genellikle geliştirici içindeki bir hizmeti çözmek istediğinde oluşur `ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="94717-194">Calling `BuildServiceProvider` typically happens when the developer wants to resolve a service in `ConfigureServices`.</span></span>
- <span data-ttu-id="94717-195">Atılabilir geçici hizmetler, aktiften çıkarma için kapsayıcı tarafından yakalanır.</span><span class="sxs-lookup"><span data-stu-id="94717-195">Disposable transient services are captured by the container for disposal.</span></span> <span data-ttu-id="94717-196">Bu, üst düzey kapsayıcıdan çözümlenirse bir bellek sızıntısını açabilir.</span><span class="sxs-lookup"><span data-stu-id="94717-196">This can turn into a memory leak if resolved from the top-level container.</span></span>
- <span data-ttu-id="94717-197">Uygulamanın kapsamlı hizmetleri yakalayan tekton içermediğinden emin olmak için kapsam doğrulamayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="94717-197">Enable scope validation to make sure the app doesn't have singletons that capture scoped services.</span></span> <span data-ttu-id="94717-198">Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).</span><span class="sxs-lookup"><span data-stu-id="94717-198">For more information, see [Scope validation](dependency-injection.md#scope-validation).</span></span>

<span data-ttu-id="94717-199">Tüm öneri kümeleri gibi, bir öneriyi yok saymayı yok saymış durumlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94717-199">Like all sets of recommendations, you may encounter situations where ignoring a recommendation is required.</span></span> <span data-ttu-id="94717-200">Özel durumlar nadiren, genellikle Framework içindeki özel durumlardır.</span><span class="sxs-lookup"><span data-stu-id="94717-200">Exceptions are rare, mostly special cases within the framework itself.</span></span>

<span data-ttu-id="94717-201">Dı, statik/genel nesne erişim desenlerinin bir *alternatifidir* .</span><span class="sxs-lookup"><span data-stu-id="94717-201">DI is an *alternative* to static/global object access patterns.</span></span> <span data-ttu-id="94717-202">Statik nesne erişimi ile karıştırırsanız, dı 'nin avantajlarını fark edemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94717-202">You may not be able to realize the benefits of DI if you mix it with static object access.</span></span>

## <a name="see-also"></a><span data-ttu-id="94717-203">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94717-203">See also</span></span>

- [<span data-ttu-id="94717-204">.NET 'e bağımlılık ekleme</span><span class="sxs-lookup"><span data-stu-id="94717-204">Dependency injection in .NET</span></span>](dependency-injection.md)
