---
ms.openlocfilehash: 8344fdedcff34f102b73f977b688abc15563bd4c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198597"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Paylaşılan çerçeve: Microsoft. AspNetCore. app öğesinden kaldırılan derlemeler

ASP.NET Core 3,0 ' den başlayarak, ASP.NET Core paylaşılan çerçeve (`Microsoft.AspNetCore.App`) yalnızca Microsoft tarafından tam olarak geliştirilen, desteklenen ve hizmet veren birinci taraf derlemeleri içerir.

#### <a name="change-description"></a>Açıklamayı Değiştir

ASP.NET Core "Platform" için sınırları yeniden tanımlayarak değişikliği düşünün. Paylaşılan Framework, [GitHub aracılığıyla herkes tarafından kaynak tarafından](https://github.com/dotnet/source-build) oluşturulabilir ve .NET Core paylaşılan çerçevelerinin mevcut avantajlarını uygulamalarınıza sunmaya devam edecektir. Bazı avantajlar, daha küçük dağıtım boyutu, merkezi düzeltme eki uygulama ve daha hızlı başlangıç süresi içerir.

Değişikliğin bir parçası olarak, bazı önemli değişiklikler `Microsoft.AspNetCore.App` ' da tanıtılmıştır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Proje dosyasındaki `<PackageReference>` öğesi aracılığıyla `Microsoft.AspNetCore.App` başvurulan projeler.

Ayrıca, `Microsoft.AspNetCore.App` aşağıdaki alt bileşenleri içeriyordu:

- Json.NET (`Newtonsoft.Json`)
- Entity Framework Core (`Microsoft.EntityFrameworkCore.` ' dan ön ekli derlemeler)
- Roslyn (`Microsoft.CodeAnalysis`)

#### <a name="new-behavior"></a>Yeni davranış

`Microsoft.AspNetCore.App` bir başvuru artık proje dosyasında bir `<PackageReference>` öğesi gerektiriyor. .NET Core SDK, `<PackageReference>` kullanımını değiştiren `<FrameworkReference>` adlı yeni bir öğeyi destekler.

Daha fazla bilgi için bkz. [ASPNET/AspNetCore # 3612](https://github.com/aspnet/AspNetCore/issues/3612).

Entity Framework Core NuGet paketleri olarak gelir. Bu değişiklik, .NET 'teki diğer tüm veri erişim kitaplıklarıyla birlikte teslim modelini hizalar. Çeşitli .NET platformlarını destekleyerek sürmek devam etmek için en basit yolu Entity Framework Core sağlar. Entity Framework Core paylaşılan çerçevenin dışına taşınması, Microsoft tarafından geliştirilen, desteklenen ve hizmet verebilir kitaplığı olarak durumunu etkilemez. [.NET Core destek ilkesi](https://www.microsoft.com/net/platform/support-policy) onu kapsamaya devam eder.

Json.NET ve Entity Framework Core ASP.NET Core ile çalışmaya devam eder. Ancak, paylaşılan çerçeveye dahil edilmezler.

Daha fazla bilgi için [.NET Core 3,0 ' de JSON 'nin geleceğe](https://github.com/dotnet/announcements/issues/90)bakın. Ayrıca, paylaşılan çerçeveden kaldırılan [ikili dosyaların tüm listesine](https://github.com/aspnet/AspNetCore/issues/3755) bakın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, `Microsoft.AspNetCore.App` ' ın tüketimini basitleştirir ve NuGet paketleri ile paylaşılan Çerçeveler arasındaki yinelemeyi azaltır.

Bu değişiklik için mosyon hakkında daha fazla bilgi için [Bu blog gönderisine](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0)bakın.

#### <a name="recommended-action"></a>Önerilen eylem

Projelerin NuGet paketleri olarak `Microsoft.AspNetCore.App` ' daki derlemeleri tüketmesi gerekmez. ASP.NET Core paylaşılan Framework 'ün hedeflediği ve kullanımının basitleşmesini sağlamak için, ASP.NET Core 1,0 ' den itibaren sevk edilen birçok NuGet paketi artık üretilmez. Bu paketlerin sağladığı API 'Ler, `Microsoft.AspNetCore.App` ile `<FrameworkReference>` kullanarak uygulamalar için hala kullanılabilir. Ortak API örnekleri Kestrel, MVC ve Razor içerir.

Bu değişiklik, ASP.NET Core 2. x içinde `Microsoft.AspNetCore.App` ile başvurulan tüm ikili dosyalar için geçerlidir. Önemli özel durumlar şunlardır:

- hedef .NET Standard devam eden `Microsoft.Extensions` kitaplıkları, NuGet paketleri olarak kullanılabilir (bkz. https://github.com/aspnet/Extensions).
- `Microsoft.AspNetCore.App`parçası olmayan ASP.NET Core ekibi tarafından oluşturulan API 'Ler. Örneğin, aşağıdaki bileşenler NuGet paketleri olarak kullanılabilir:
  - Entity Framework Core
  - Üçüncü taraf tümleştirme sağlayan API 'Ler
  - Deneysel özellikler
  - [Paylaşılan çerçevede olması gereken gereksinimleri yerine](https://github.com/aspnet/AspNetCore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md) getiren bağımlılıklara sahip API 'ler
- Json.NET desteğini sağlayan MVC uzantıları. API, Json.NET ve MVC kullanımını desteklemek için bir NuGet paketi olarak sağlanacaktır.
- SignalR .NET istemcisi .NET Standard desteklemeye ve bir NuGet paketi olarak göndermeye devam edecektir. Xamarin ve UWP gibi birçok .NET çalışma zamanı için kullanılması amaçlanmıştır.

Daha fazla bilgi için bkz. [3,0 ' de paylaşılan çerçeve derlemeleri için paketleri oluşturmayı durdurma](https://github.com/aspnet/AspNetCore/issues/3756). Tartışma için bkz. [ASPNET/AspNetCore # 3757](https://github.com/aspnet/AspNetCore/issues/3757).

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
