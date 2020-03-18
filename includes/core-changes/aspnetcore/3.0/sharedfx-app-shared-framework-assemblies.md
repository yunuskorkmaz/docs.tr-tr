---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937280"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a>Paylaşılan çerçeve: Microsoft.AspNetCore.App'ten kaldırılan derlemeler

Core 3.0ASP.NETdan başlayarak, ASP.NET`Microsoft.AspNetCore.App`Core paylaşılan çerçevesi ( ) yalnızca Microsoft tarafından tamamen geliştirilen, desteklenen ve hizmet verilen birinci taraf derlemeleri içerir.

#### <a name="change-description"></a>Açıklamayı değiştir

Değişimi ASP.NET Core "platformu" için sınırların yeniden tanımlanması olarak düşünün. Paylaşılan [çerçeve, GitHub üzerinden herkes tarafından kaynak oluşturabilen](https://github.com/dotnet/source-build) bir çerçeve olacak ve .NET Core paylaşılan çerçevelerinin mevcut avantajlarını uygulamalarınız için sunmaya devam edecektir. Bazı avantajlar daha küçük dağıtım boyutu, merkezi yama ve daha hızlı başlatma süresi içerir.

Değişikliğin bir parçası olarak, bazı önemli kırılma `Microsoft.AspNetCore.App`değişiklikleri tanıtıldı.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Proje dosyasındaki `Microsoft.AspNetCore.App` `<PackageReference>` bir öğe üzerinden başvurulan projeler.

Ayrıca, `Microsoft.AspNetCore.App` aşağıdaki alt bileşenleri içeriyordu:

- Json.NET`Newtonsoft.Json`( )
- Varlık Çerçeve Çekirdeği (montajlar `Microsoft.EntityFrameworkCore.`ile önceden belirlenmiş)
- Roslyn`Microsoft.CodeAnalysis`( )

#### <a name="new-behavior"></a>Yeni davranış

Artık başvuru, `Microsoft.AspNetCore.App` proje `<PackageReference>` dosyasında bir öğe gerektirmez. .NET Core `<FrameworkReference>`SDK, kullanımını değiştiren yeni bir öğeyi `<PackageReference>`destekler.

Daha fazla bilgi için [dotnet/aspnetcore#3612'ye](https://github.com/dotnet/aspnetcore/issues/3612)bakın.

NuGet paketleri olarak Entity Framework Core gemileri. Bu değişiklik, gönderi modelini .NET'teki diğer tüm veri erişim kitaplıklarıyla hizalar. Çeşitli .NET platformlarını desteklerken yenilik yapmaya devam etmek için en basit yolu Entity Framework Core sağlar. Entity Framework Core'un paylaşılan çerçevenin dışına taşınmasının, Microsoft tarafından geliştirilen, desteklenen ve hizmet verilen kitaplık olarak durumu üzerinde hiçbir etkisi yoktur. [.NET Core destek politikası](https://www.microsoft.com/net/platform/support-policy) bunu karşılamaya devam ediyor.

Json.NET ve Entity Framework Core ASP.NET Core ile çalışmaya devam ediyor. Ancak, ortak çerçeveye dahil edilmeyecekler.

Daha fazla bilgi için [.NET Core 3.0'daki JSON'un geleceği](https://github.com/dotnet/announcements/issues/90)bölümüne bakın. Ayrıca paylaşılan çerçeveden kaldırılan [ikililerin tam listesine](https://github.com/dotnet/aspnetcore/issues/3755) bakın.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, NuGet `Microsoft.AspNetCore.App` paketleri ve paylaşılan çerçeveler arasındaki yinelemenin tüketimini kolaylaştırır ve azaltır.

Bu değişiklik için motivasyon hakkında daha fazla bilgi için, [bu blog yazısı](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)bakın.

#### <a name="recommended-action"></a>Önerilen eylem

Projelerin, derlemeleri NuGet paketleri `Microsoft.AspNetCore.App` olarak tüketmesi gerekli olmayacaktır. ASP.NET Core paylaşılan çerçevesinin hedeflemesini ve kullanımını kolaylaştırmak için, Core 1.0'ASP.NET dan bu yana gönderilen birçok NuGet paketi artık üretilmemaktadır. Bu paketlerin sağladığı API'ler, bir `<FrameworkReference>` `Microsoft.AspNetCore.App`to kullanarak uygulamalar için hala kullanılabilir. Yaygın API örnekleri kerkenez, MVC ve Razor içerir.

Bu değişiklik, ASP.NET Core `Microsoft.AspNetCore.App` 2.x'te başvurulan tüm ikili dosyalar için geçerli değildir. Önemli istisnalar şunlardır:

- `Microsoft.Extensions`.NET Standard'ı hedeflemeye devam eden kitaplıklar https://github.com/dotnet/extensions)NuGet paketleri olarak kullanılabilir (bkz.
- Bir parçası olmayan ASP.NET Core ekibi tarafından `Microsoft.AspNetCore.App`üretilen API'ler. Örneğin, aşağıdaki bileşenler NuGet paketleri olarak kullanılabilir:
  - Entity Framework Core
  - Üçüncü taraf tümleştirmesağlayan API'ler
  - Deneysel özellikler
  - [Paylaşılan çerçevede olması gereken gereksinimleri yerine getiremeyen bağımlılıklara](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md) sahip API'ler
- Json.NET desteğini koruyan MVC uzantıları. Json.NET ve MVC'yi kullanarak desteklemek için NuGet paketi olarak bir API sağlanacaktır.
- SignalR .NET istemcisi .NET Standard'ı desteklemeye ve NuGet paketi olarak göndermeye devam edecektir. Xamarin ve UWP gibi birçok .NET çalışma zamanında kullanılmak üzere tasarlanmıştır.

Daha fazla bilgi için bkz: [3.0'daki paylaşılan çerçeve derlemeleri için paketleri üretmeyi durdurun.](https://github.com/dotnet/aspnetcore/issues/3756) Tartışma için [dotnet/aspnetcore#3757'ye](https://github.com/dotnet/aspnetcore/issues/3757)bakın.

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
