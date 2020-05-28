---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144984"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Paylaşılan çerçeve: Microsoft. AspNetCore. app öğesinden kaldırılan derlemeler

ASP.NET Core 3,0 ' den başlayarak, ASP.NET Core paylaşılan Framework ( `Microsoft.AspNetCore.App` ) yalnızca Microsoft tarafından tam olarak geliştirilen, desteklenen ve hizmet verebilir olan birinci taraf derlemeleri içerir.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core "Platform" için sınırları yeniden tanımlayarak değişikliği düşünün. Paylaşılan Framework, [GitHub aracılığıyla herkes tarafından kaynak tarafından](https://github.com/dotnet/source-build) oluşturulabilir ve .NET Core paylaşılan çerçevelerinin mevcut avantajlarını uygulamalarınıza sunmaya devam edecektir. Bazı avantajlar, daha küçük dağıtım boyutu, merkezi düzeltme eki uygulama ve daha hızlı başlangıç süresi içerir.

Değişikliğin bir parçası olarak, bazı önemli değişiklikler ' de kullanıma sunulmuştur `Microsoft.AspNetCore.App` .

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`Microsoft.AspNetCore.App`Proje dosyasındaki bir öğe aracılığıyla başvurulan projeler `<PackageReference>` .

Ayrıca, `Microsoft.AspNetCore.App` aşağıdaki alt bileşenleri de içerir:

- Json.NET ( `Newtonsoft.Json` )
- Entity Framework Core (ön eki olan derlemeler `Microsoft.EntityFrameworkCore.` )
- Roslyn ( `Microsoft.CodeAnalysis` )

#### <a name="new-behavior"></a>Yeni davranış

Bir başvuru `Microsoft.AspNetCore.App` artık `<PackageReference>` Proje dosyasında bir öğe gerektirmez. .NET Core SDK, öğesinin kullanımını değiştiren adlı yeni bir öğeyi destekler `<FrameworkReference>` `<PackageReference>` .

Daha fazla bilgi için bkz. [DotNet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612).

Entity Framework Core NuGet paketleri olarak gelir. Bu değişiklik, .NET 'teki diğer tüm veri erişim kitaplıklarıyla birlikte teslim modelini hizalar. Çeşitli .NET platformlarını destekleyerek sürmek devam etmek için en basit yolu Entity Framework Core sağlar. Entity Framework Core paylaşılan çerçevenin dışına taşınması, Microsoft tarafından geliştirilen, desteklenen ve hizmet verebilir kitaplığı olarak durumunu etkilemez. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) onu kapsamaya devam eder.

Json.NET ve Entity Framework Core ASP.NET Core ile çalışmaya devam eder. Ancak, paylaşılan çerçeveye dahil edilmezler.

Daha fazla bilgi için [.NET Core 3,0 ' de JSON 'nin geleceğe](https://github.com/dotnet/announcements/issues/90)bakın. Ayrıca, paylaşılan çerçeveden kaldırılan [ikili dosyaların tüm listesine](https://github.com/dotnet/aspnetcore/issues/3755) bakın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, tüketimini basitleştirir `Microsoft.AspNetCore.App` ve NuGet paketleri ile paylaşılan Çerçeveler arasındaki yinelemeyi azaltır.

Bu değişiklik için mosyon hakkında daha fazla bilgi için [Bu blog gönderisine](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.

#### <a name="recommended-action"></a>Önerilen eylem

Projelerin NuGet paketleri olarak içindeki derlemeleri kullanması gerekli değildir `Microsoft.AspNetCore.App` . ASP.NET Core paylaşılan Framework 'ün hedeflediği ve kullanımının basitleşmesini sağlamak için, ASP.NET Core 1,0 ' den itibaren sevk edilen birçok NuGet paketi artık üretilmez. Bu paketlerin sağladığı API 'Ler, ' a ' i kullanarak uygulamalar için hala kullanılabilir `<FrameworkReference>` `Microsoft.AspNetCore.App` . Ortak API örnekleri Kestrel, MVC ve Razor içerir.

Bu değişiklik `Microsoft.AspNetCore.App` , ASP.NET Core 2. x ile başvurulan tüm ikili dosyalar için geçerlidir. Önemli özel durumlar şunlardır:

- `Microsoft.Extensions`hedef .NET Standard devam eden kitaplıklar, NuGet paketleri olarak kullanılabilir (bkz <https://github.com/dotnet/extensions> .).
- ' Nin parçası olmayan ASP.NET Core ekibi tarafından oluşturulan API 'Ler `Microsoft.AspNetCore.App` . Örneğin, aşağıdaki bileşenler NuGet paketleri olarak kullanılabilir:
  - Entity Framework Core
  - Üçüncü taraf tümleştirme sağlayan API 'Ler
  - Deneysel özellikler
  - [Paylaşılan çerçevede olması gereken gereksinimleri yerine](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md) getiren bağımlılıklara sahip API 'ler
- Json.NET desteğini sağlayan MVC uzantıları. API, Json.NET ve MVC kullanımını desteklemek için bir NuGet paketi olarak sağlanacaktır.
- SignalR .NET istemcisi .NET Standard desteklemeye ve bir NuGet paketi olarak göndermeye devam edecektir. Xamarin ve UWP gibi birçok .NET çalışma zamanı için kullanılması amaçlanmıştır.

Daha fazla bilgi için bkz. [3,0 ' de paylaşılan çerçeve derlemeleri için paketleri oluşturmayı durdurma](https://github.com/dotnet/aspnetcore/issues/3756). Tartışma için bkz. [DotNet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
