---
title: Bağımlılık ekleme yönergeleri
description: .NET uygulama geliştirmesi için çeşitli bağımlılık ekleme kılavuzlarını ve en iyi uygulamaları öğrenin.
author: IEvangelist
ms.author: dapine
ms.date: 10/29/2020
ms.topic: guide
ms.openlocfilehash: 105536df873829dc79dcca1b86d080360e71303f
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505406"
---
# <a name="dependency-injection-guidelines"></a>Bağımlılık ekleme yönergeleri

Bu makalede, .NET uygulamalarında bağımlılık ekleme işlemini uygulamaya yönelik genel yönergeler ve en iyi uygulamalar sağlanmaktadır.

## <a name="design-services-for-dependency-injection"></a>Bağımlılık ekleme için tasarım hizmetleri

Bağımlılık ekleme için Hizmetleri tasarlarken:

- Durum bilgisi olan statik sınıflar ve Üyeler kullanmaktan kaçının. Bunun yerine Singleton hizmetlerini kullanmak için uygulama tasarlayarak genel durum oluşturmamaya özen gösterin.
- Hizmetler içindeki bağımlı sınıfların doğrudan örneklenmesini önleyin. Doğrudan örnekleme kodu belirli bir uygulamaya bağar.
- Hizmetleri küçük, iyi bir şekilde ve kolayca test edin.

Bir sınıfta eklenen çok sayıda bağımlılık varsa, bu, sınıfta çok fazla sorumluluğun olduğu ve [tek sorumluluk ilkesini (SRP)](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#single-responsibility)ihlal eden bir işaret olabilir. Bazı sorumlulukları yeni sınıflara taşıyarak sınıfı yeniden düzenleme girişimi.

### <a name="disposal-of-services"></a>Hizmetlerin elden çıkarılması

Kapsayıcı, oluşturduğu türlerin temizlenmesi ve örneklere çağrı yapmaktan sorumludur <xref:System.IDisposable.Dispose%2A> <xref:System.IDisposable> . Kapsayıcıdan çözümlenen hizmetler hiçbir şekilde geliştirici tarafından atılamaz. Bir tür veya fabrika tek bir olarak kayıtlıysa, kapsayıcı kendiliğinden otomatik olarak atar.

Aşağıdaki örnekte, hizmetler hizmet kapsayıcısı tarafından oluşturulur ve otomatik olarak elden alınır:

:::code language="csharp" source="snippets/configuration/console-di-disposable/TransientDisposable.cs":::

Önceki atılabilir, geçici bir yaşam süresine sahip olmak için tasarlanmıştır.

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

Önceki atılabilir, kapsamlı bir yaşam süresine sahip olmak için tasarlanmıştır.

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

Önceki atılabilir tek bir yaşam süresine sahip olmak için tasarlanmıştır.

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60" highlight="":::

Hata ayıklama konsolu, çalıştırıldıktan sonra aşağıdaki örnek çıktıyı gösterir:

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

### <a name="services-not-created-by-the-service-container"></a>Hizmet kapsayıcısı tarafından oluşturulmayan hizmetler

Aşağıdaki kodu inceleyin:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddSingleton(new ExampleService());

    // ...
}
```

Yukarıdaki kodda:

- `ExampleService`Örnek, hizmet  kapsayıcısı tarafından oluşturulmamış.
- Framework Hizmetleri otomatik **olarak elden atmaz.**
- Geliştirici, hizmetleri elden atan sorumludur.

### <a name="idisposable-guidance-for-transient-and-shared-instances"></a>Geçici ve paylaşılan örnekler için IDisposable Kılavuzu

#### <a name="transient-limited-lifetime"></a>Geçici, sınırlı ömür

**Senaryo**

Uygulama, <xref:System.IDisposable> aşağıdaki senaryolardan biri için geçici bir yaşam süresine sahip bir örnek gerektirir:

- Örnek, kök kapsamda (kök kapsayıcı) çözümlenir.
- Kapsam bitmeden önce örnek atılmalıdır.

**Çözüm**

Üst kapsamın dışında bir örnek oluşturmak için fabrika modelini kullanın. Bu durumda, uygulama genellikle `Create` son türün oluşturucusunu doğrudan çağıran bir yönteme sahip olur. Son türün başka bağımlılıkları varsa, fabrika şunları yapabilir:

- Oluşturucusunda bir alın <xref:System.IServiceProvider> .
- <xref:Microsoft.Extensions.DependencyInjection.ActivatorUtilities.CreateInstance%2A?displayProperty=nameWithType>Kapsayıcının bağımlılıkları için kapsayıcıyı kullanırken, örneği kapsayıcının dışında örneklemek için kullanın.

#### <a name="shared-instance-limited-lifetime"></a>Paylaşılan örnek, sınırlı ömür

**Senaryo**

Uygulamanın <xref:System.IDisposable> birden çok hizmet arasında paylaşılan bir örnek olması gerekir, ancak <xref:System.IDisposable> örnek sınırlı bir yaşam süresine sahip olmalıdır.

**Çözüm**

Örneği kapsamlı bir ömür ile kaydedin. <xref:Microsoft.Extensions.DependencyInjection.IServiceScopeFactory.CreateScope%2A?displayProperty=nameWithType>Yeni bir oluşturmak için kullanın <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> . <xref:System.IServiceProvider>Gerekli hizmetleri almak için kapsam ' i kullanın. Artık gerekli olmadığında kapsamı atın.

#### <a name="general-idisposable-guidelines"></a>Genel `IDisposable` yönergeler

- <xref:System.IDisposable>Örnekleri geçici bir yaşam süresine kaydetmez. Bunun yerine fabrika modelini kullanın.
- <xref:System.IDisposable>Kök kapsamda geçici veya kapsamlı bir yaşam süresine sahip örnekleri çözümleyin. Bunun tek istisnası, uygulamanın oluşturma/yeniden oluşturma/yeniden oluşturma ve uygulama oluşturmasıdır <xref:System.IServiceProvider> , ancak bu ideal bir modeldir.
- Bir <xref:System.IDisposable> bağımlılık alma yoluyla, alıcının kendisini uygulaması gerekmez <xref:System.IDisposable> . <xref:System.IDisposable>Bağımlılığın alıcısı <xref:System.IDisposable.Dispose%2A> Bu bağımlılıkta çağrımamalıdır.
- Hizmetlerin ömrünü denetlemek için kapsamları kullanın. Kapsamlar hiyerarşik değildir ve kapsamlar arasında özel bir bağlantı yoktur.

Kaynak temizleme hakkında daha fazla bilgi için bkz. [ `Dispose` yöntemi uygulama](../../standard/garbage-collection/implementing-dispose.md)veya [ `DisposeAsync` Yöntem uygulama](../../standard/garbage-collection/implementing-disposeasync.md). Ayrıca, kaynak Temizleme ile bağlantılı olarak [kapsayıcı senaryosu tarafından yakalanan atılabilir geçici Hizmetleri](#disposable-transient-services-captured-by-container) de göz önünde bulundurun.

## <a name="default-service-container-replacement"></a>Varsayılan hizmet kapsayıcısı değiştirme

Yerleşik hizmet kapsayıcısı, çerçeve ihtiyaçlarına ve çoğu tüketici uygulamasına hizmet vermek için tasarlanmıştır. Desteklemediği belirli bir özelliğe ihtiyacınız yoksa, yerleşik kapsayıcının kullanılması önerilir, örneğin:

- Özellik ekleme
- Ada göre ekleme
- Alt kapsayıcılar
- Özel ömür yönetimi
- `Func<T>` yavaş başlatma desteği
- Kural tabanlı kayıt

Aşağıdaki üçüncü taraf kapsayıcıları ASP.NET Core uygulamalarla kullanılabilir:

- [Autofac](https://autofac.readthedocs.io/en/latest/integration/aspnetcore.html)
- [Drıioc](https://www.nuget.org/packages/DryIoc.Microsoft.DependencyInjection)
- [Yetkisiz kullanım](https://www.nuget.org/packages/Grace.DependencyInjection.Extensions)
- [Açık Inject](https://github.com/seesharper/LightInject.Microsoft.DependencyInjection)
- [E](https://jasperfx.github.io/lamar/)
- [Stakıbox](https://github.com/z4kn4fein/stashbox-extensions-dependencyinjection)
- [Unity](https://www.nuget.org/packages/Unity.Microsoft.DependencyInjection)

## <a name="thread-safety"></a>İş parçacığı güvenliği

İş parçacığı güvenli Singleton Hizmetleri oluşturun. Tek bir hizmetin geçici bir hizmete bağımlılığı varsa, geçici hizmet aynı zamanda tek tarafından nasıl kullanıldığına bağlı olarak iş parçacığı güvenliği de gerektirebilir.

Tek bir hizmetin Factory yöntemi (örneğin, AddSingleton için ikinci bağımsız değişken [ \<TService> \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), iş parçacığı açısından güvenli olması gerekmez. Bir Type ( `static` ) Oluşturucusu gibi, tek bir iş parçacığı tarafından yalnızca bir kez çağrılması garanti edilir.

## <a name="recommendations"></a>Öneriler

- `async/await` ve `Task` tabanlı hizmet çözümlemesi desteklenmez. C# zaman uyumsuz oluşturucuları desteklemediğinden, hizmeti zaman uyumlu olarak çözümledikten sonra zaman uyumsuz yöntemler kullanın.
- Veri ve yapılandırmayı doğrudan hizmet kapsayıcısında saklamaktan kaçının. Örneğin, bir kullanıcının alışveriş sepeti genellikle hizmet kapsayıcısına eklenmemelidir. Yapılandırma, Seçenekler modelini kullanmalıdır. Benzer şekilde, yalnızca başka bir nesneye erişime izin vermek için mevcut olan "veri sahibi" nesnelerinden kaçının. DI aracılığıyla gerçek öğe istemek daha iyidir.
- Hizmetlere statik erişimi önleyin. Örneğin, başka bir yerde kullanmak üzere [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) statik bir alan veya özellik olarak yakalanmaktan kaçının.
- [Dı fabrikalarını](#async-di-factories-can-cause-deadlocks) hızlı ve zaman uyumlu tutun.
- [*Hizmet bulucu deseninin*](#scoped-service-as-singleton)kullanmaktan kaçının. Örneğin, <xref:System.IServiceProvider.GetService%2A> yerine bir hizmet örneği elde etmek için Invoke kullanmayın.
- Önlemek için başka bir hizmet bulucu çeşitlemesi, çalışma zamanında bağımlılıkları çözümleyen bir ekleme. Bu uygulamalardan her ikisi de [Denetim stratejilerini geçersiz kılar](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) .
- İçindeki çağrılardan <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> kaçının `ConfigureServices` . Çağırma `BuildServiceProvider` genellikle geliştirici içindeki bir hizmeti çözmek istediğinde oluşur `ConfigureServices` .
- [Atılabilir geçici hizmetler](#disposable-transient-services-captured-by-container) , aktiften çıkarma için kapsayıcı tarafından yakalanır. Bu, üst düzey kapsayıcıdan çözümlenirse bir bellek sızıntısını açabilir.
- Uygulamanın kapsamlı hizmetleri yakalayan tekton içermediğinden emin olmak için kapsam doğrulamayı etkinleştirin. Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).

Tüm öneri kümeleri gibi, bir öneriyi yok saymayı yok saymış durumlarla karşılaşabilirsiniz. Özel durumlar nadiren, genellikle Framework içindeki özel durumlardır.

Dı, statik/genel nesne erişim desenlerinin bir *alternatifidir* . Statik nesne erişimi ile karıştırırsanız, dı 'nin avantajlarını fark edemeyebilirsiniz.

## <a name="example-anti-patterns"></a>Örnek Desenler

Bu makaledeki yönergelere ek olarak, *kaçınması **gereken*** birkaç kenar düzeyi vardır. Bu koruma alışkanlarından bazıları, çalışma zamanlarının kendisini geliştirmekten dersleri.

> [!WARNING]
> Bunlar örnek desenler, *kodu kopyalamayın,* bu *desenleri kullanmayın ve* tüm maliyetlerde bu modellerden kaçının.

### <a name="disposable-transient-services-captured-by-container"></a>Atılabilir kapsayıcı tarafından yakalanan geçici hizmetler

' I uygulayan *geçici* Hizmetleri kaydettiğinizde, <xref:System.IDisposable> Varsayılan olarak dı kapsayıcısı bu referanslara sahip olur ve uygulama, kapsayıcıdan çözümlenmişse <xref:System.IDisposable.Dispose> veya kapsam bir kapsamdan çözümlendiklerinde atılana kadar bu başvuruları bırakır. Bu, kapsayıcı düzeyinden çözümlenirse bir bellek sızıntısını açabilir.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="18-30":::

Önceki anti-düzeninde, 1.000 `ExampleDisposable` nesnelerinin örneği oluşturulur ve kökü atanır. Bunlar, `serviceProvider` örnek atılana kadar uygulanmaz.

Bellek sızıntılarını hata ayıklama hakkında daha fazla bilgi için bkz. [.net 'te Bellek sızıntısını hata ayıklama](../diagnostics/debug-memory-leak.md).

### <a name="async-di-factories-can-cause-deadlocks"></a>Zaman uyumsuz dı fabrikası kilitlenmeleri neden olabilir

"Dı fabrikaları" terimi çağrılırken var olan aşırı yükleme yöntemlerine başvurur `Add{LIFETIME}` . Hizmetin kaydedildiği konumu kabul eden aşırı yüklemeler vardır `Func<IServiceProvider, T>` `T` ve parametresi adlandırılır `implementationFactory` . `implementationFactory`Bir lambda ifadesi, yerel işlev veya yöntem olarak belirtilebilir. Fabrika zaman uyumsuzdur ve kullanıyorsanız <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> , bu da kilitlenmeye neden olur.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="32-45" highlight="4-8":::

Önceki kodda, `implementationFactory` gövde döndürülen bir yöntemde çağırdığı bir lambda ifadesi verilir <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> `Task<Bar>` . Bu, ***kilitlenmeye neden olur***. `GetBarAsync`Yöntemi, ile zaman uyumsuz bir iş işlemini taklit eder <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> ve ardından çağırır <xref:Microsoft.Extensions.DependencyInjection.ServiceProviderServiceExtensions.GetRequiredService%60%601(System.IServiceProvider)> .

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="47-53":::

Zaman uyumsuz yönergeler hakkında daha fazla bilgi için bkz. [zaman uyumsuz programlama: önemli bilgi ve öneriler](../../csharp/async.md#important-info-and-advice). Hata ayıklama kilitlenmeleri hakkında daha fazla bilgi için bkz. [.net 'te kilitlenmeye hata ayıklama](../diagnostics/debug-deadlock.md).

Bu bir anti-model çalıştırırken ve kilitlenme gerçekleştiğinde, Visual Studio 'nun paralel yığınları penceresinde bekleyen iki iş parçacığını görüntüleyebilirsiniz. Daha fazla bilgi için bkz. [Paralel Yığınlar penceresinde iş parçacıklarını ve görevleri görüntüleme](/visualstudio/debugger/using-the-parallel-stacks-window).

### <a name="captive-dependency"></a>Captive bağımlılığı

["Captive Dependency"](https://blog.ploeh.dk/2014/06/02/captive-dependency) terimi, [Seeman 'ı işaret](https://blog.ploeh.dk/about)ederek ortaklaşa bulunur ve daha uzun süreli bir hizmetin daha kısa süreli bir hizmet başlığı taşıdığı hizmet yaşam sürelerinin yanlış yapılandırılması anlamına gelir.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="55-65":::

Yukarıdaki kodda, `Foo` tek bir olarak kaydedilir ve `Bar` yüzeyde bir kapsam geçerlidir. Ancak uygulamasını göz önünde bulundurun `Foo` .

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Foo.cs" highlight="5":::

`Foo`Nesnesi, bir nesnesi gerektirir ve bu bir tekil olduğundan `Bar` `Foo` ve `Bar` kapsamı belirlenmiş olduğundan, bu bir yanlış yapılandırma. Olduğu gibi, `Foo` yalnızca bir kez örneklenebilir ve `Bar` kendi yaşam süresi boyunca, amaçlanan kapsamlı yaşam süresinden daha uzun sürer `Bar` . ' A geçirerek kapsamları doğrulamayı düşünmelisiniz `validateScopes: true` <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Boolean)> . Kapsamları doğruladığınızda, <xref:System.InvalidOperationException> "tek tek ' foo ' öğesinden" kapsamlı hizmet ' çubuğu ' kullanılmasına benzer bir ileti içeren bir ileti alırsınız.

Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).

### <a name="scoped-service-as-singleton"></a>Tek tek olarak kapsamlı hizmet

Kapsamı belirlenmiş hizmetler kullanılırken, kapsam veya mevcut bir kapsamda bir kapsam oluşturuyorsanız, hizmet tek olur.

:::code language="csharp" source="snippets/configuration/di-anti-patterns/Program.cs" range="68-82" highlight="13-14":::

Yukarıdaki kodda, `Bar` doğru olan bir içinde alınır <xref:Microsoft.Extensions.DependencyInjection.IServiceScope> . Kenar yumuşatma, `Bar` kapsam dışından alındır ve değişken, `avoid` hangi örnek almanın yanlış olduğunu göstermek için adlandırılır.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'e bağımlılık ekleme](dependency-injection.md)
- [Öğretici: .NET 'te bağımlılık ekleme kullanma](dependency-injection-usage.md)
