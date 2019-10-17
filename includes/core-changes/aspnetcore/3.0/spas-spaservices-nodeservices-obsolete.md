---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394074"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>Maça 'Lar: gereksiz olarak işaretlenen SpaServices ve NodeServices

ASP.NET Core 2,1 ' den bu yana aşağıdaki NuGet paketlerinin içeriği gereksizdir. Sonuç olarak, aşağıdaki paketler artık kullanılmıyor olarak işaretlenir:

- [Microsoft. AspNetCore. SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft. AspNetCore. NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Aynı nedenden dolayı, aşağıdaki NPM modülleri kullanım dışı olarak işaretlenmekte:

- [ASPNET-angular](https://www.npmjs.com/package/aspnet-angular)
- [ASPNET-prerendering](https://www.npmjs.com/package/aspnet-prerendering)
- [ASPNET-WebPack](https://www.npmjs.com/package/aspnet-webpack)
- [ASPNET-WebPack-tepki verme](https://www.npmjs.com/package/aspnet-webpack-react)
- [etki alanı-görev](https://www.npmjs.com/package/domain-task)

Önceki paketler ve NPM modülleri daha sonra .NET 5 ' te kaldırılacaktır.

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

Kullanım dışı bırakılan paketler ve NPM modülleri, ASP.NET Core tek sayfalı uygulama (SPA) çerçeveleri ile tümleştirme amacını taşımaktadır. Bu tür çerçeveler, Redux ile angular, tepki verme ve tepki verme içerir.

#### <a name="new-behavior"></a>Yeni davranış

[Microsoft. AspNetCore. SpaServices. Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet paketinde yeni bir tümleştirme mekanizması bulunur. Paket, ASP.NET Core 2,1 ' den itibaren angular ve tepki verme projesi şablonlarına göre kalır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core, angular, tepki verme ve Redux ile tepki verme gibi çeşitli tek sayfalı uygulama (SPA) çerçeveleri ile tümleştirmeyi destekler. Başlangıçta bu çerçevelerle tümleştirme, sunucu tarafı prerendering ve WebPack ile tümleştirme gibi senaryolar işlenen ASP.NET Core özel bileşenlerle oluşturulmuştur. Saat itibarıyla, sektör standartları değişmiştir. SPA çerçevelerinin her biri kendi standart komut satırı arabirimlerini serbest bıraktı. Örneğin, angular CLı ve oluşturma-tepki-uygulama.

ASP.NET Core 2,1 Mayıs 2018 ' de yayınlanmışsa, takım standartlara göre değişikliğe cevap verdi. SPA çerçevelerinin kendi araç zincirleriyle tümleştirmenin daha yeni ve kolay bir yolu sağlandı. Yeni tümleştirme mekanizması `Microsoft.AspNetCore.SpaServices.Extensions` ' da bulunur ve ASP.NET Core 2,1 ' den itibaren angular ve tepki verme projesi şablonlarına göre kalır.

Eski ASP.NET Core özgü bileşenlerin ilgisiz olduğunu ve önerilmediğini netleştirmek için:

- 2,1 öncesi tümleştirme mekanizması eski olarak işaretlenir.
- Destekleyici NPM paketleri kullanım dışı olarak işaretlenir.

#### <a name="recommended-action"></a>Önerilen eylem

Bu paketleri kullanıyorsanız, işlevleri kullanmak için uygulamalarınızı güncelleştirin:

- @No__t-0 paketinde.
- Kullanmakta olduğunuz SPA çerçeveleri tarafından sağlanıyor

Sunucu tarafı prerendering ve sık erişimli modül yeniden yükleme gibi özellikleri etkinleştirmek için ilgili SPA çerçevesine yönelik belgelere bakın. @No__t-0 ' daki *işlevler kullanılmıyor ve* desteklenmeye devam edecek.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->
