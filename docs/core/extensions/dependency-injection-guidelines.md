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

:::code language="csharp" source="snippets/configuration/console-di-disposable/ScopedDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/SingletonDisposable.cs":::

:::code language="csharp" source="snippets/configuration/console-di-disposable/Program.cs" range="1-21,41-60":::

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

- `ExampleService`Örnek, hizmet **not** kapsayıcısı tarafından oluşturulmamış.
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

Kaynak temizleme hakkında daha fazla bilgi için bkz. [Dispose yöntemi uygulama](../../standard/garbage-collection/implementing-dispose.md)

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

Tek bir hizmetin fabrika yöntemi (örneğin, AddSingleton için ikinci bağımsız değişken [ \<TService> \<IServiceProvider,TService> )](xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionServiceExtensions.AddSingleton%2A), iş parçacığı açısından güvenli olması gerekmez. Bir Type ( `static` ) Oluşturucusu gibi, tek bir iş parçacığı tarafından yalnızca bir kez çağrılması garanti edilir.

## <a name="recommendations"></a>Öneriler

- `async/await` ve `Task` tabanlı hizmet çözümlemesi desteklenmez. C# zaman uyumsuz oluşturucuları desteklemediğinden, hizmeti zaman uyumlu olarak çözümledikten sonra zaman uyumsuz yöntemler kullanın.
- Veri ve yapılandırmayı doğrudan hizmet kapsayıcısında saklamaktan kaçının. Örneğin, bir kullanıcının alışveriş sepeti genellikle hizmet kapsayıcısına eklenmemelidir. Yapılandırma, Seçenekler modelini kullanmalıdır. Benzer şekilde, yalnızca başka bir nesneye erişime izin vermek için mevcut olan "veri sahibi" nesnelerinden kaçının. DI aracılığıyla gerçek öğe istemek daha iyidir.
- Hizmetlere statik erişimi önleyin. Örneğin, başka bir yerde kullanmak üzere [IApplicationBuilder. ApplicationServices](xref:Microsoft.AspNetCore.Builder.IApplicationBuilder.ApplicationServices) statik bir alan veya özellik olarak yakalanmaktan kaçının.
- Dı fabrikalarını hızlı ve zaman uyumlu tutun.
- *Hizmet bulucu deseninin*kullanmaktan kaçının. Örneğin, <xref:System.IServiceProvider.GetService%2A> yerine bir hizmet örneği elde etmek için Invoke kullanmayın.
- Önlemek için başka bir hizmet bulucu çeşitlemesi, çalışma zamanında bağımlılıkları çözümleyen bir ekleme. Bu uygulamalardan her ikisi de [Denetim stratejilerini geçersiz kılar](/dotnet/standard/modern-web-apps-azure-architecture/architectural-principles#dependency-inversion) .
- İçindeki çağrılardan <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionContainerBuilderExtensions.BuildServiceProvider%2A> kaçının `ConfigureServices` . Çağırma `BuildServiceProvider` genellikle geliştirici içindeki bir hizmeti çözmek istediğinde oluşur `ConfigureServices` .
- Atılabilir geçici hizmetler, aktiften çıkarma için kapsayıcı tarafından yakalanır. Bu, üst düzey kapsayıcıdan çözümlenirse bir bellek sızıntısını açabilir.
- Uygulamanın kapsamlı hizmetleri yakalayan tekton içermediğinden emin olmak için kapsam doğrulamayı etkinleştirin. Daha fazla bilgi için bkz. [kapsam doğrulaması](dependency-injection.md#scope-validation).

Tüm öneri kümeleri gibi, bir öneriyi yok saymayı yok saymış durumlarla karşılaşabilirsiniz. Özel durumlar nadiren, genellikle Framework içindeki özel durumlardır.

Dı, statik/genel nesne erişim desenlerinin bir *alternatifidir* . Statik nesne erişimi ile karıştırırsanız, dı 'nin avantajlarını fark edemeyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'e bağımlılık ekleme](dependency-injection.md)
