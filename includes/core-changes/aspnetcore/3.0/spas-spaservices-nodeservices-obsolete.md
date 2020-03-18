---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394074"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a>STA'lar: SpaServices ve NodeServices eski işaretlenmiş

Aşağıdaki NuGet paketlerinin içeriği Core 2.1'ASP.NET beri gereksizdir. Sonuç olarak, aşağıdaki paketler eski olarak işaretlenmektedir:

- [Microsoft.AspNetCore.SpaServices](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [Microsoft.AspNetCore.NodeServices](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

Aynı nedenle, aşağıdaki npm modülleri amortismana npm olarak işaretlenmektedir:

- [aspnet-açısal](https://www.npmjs.com/package/aspnet-angular)
- [aspnet önoluşturma](https://www.npmjs.com/package/aspnet-prerendering)
- [aspnet-webpack](https://www.npmjs.com/package/aspnet-webpack)
- [aspnet-webpack-tepki](https://www.npmjs.com/package/aspnet-webpack-react)
- [etki alanı görevi](https://www.npmjs.com/package/domain-task)

Önceki paketler ve npm modülleri daha sonra .NET 5'te kaldırılır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

Amortismana tabi paketler ve npm modülleri ASP.NET Core'u çeşitli Tek Sayfalı Uygulama (SPA) çerçeveleriyle entegre etmeyi amaçlıyordu. Bu tür çerçeveler Açısal içerir, React, ve Redux ile React.

#### <a name="new-behavior"></a>Yeni davranış

[Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet paketinde yeni bir tümleştirme mekanizması bulunmaktadır. Paket, Core 2.1'ASP.NET bu yana Açısal ve Tepki proje şablonlarının temelini oluşturur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

ASP.NET Core, Açısal, React ve React with Redux gibi çeşitli Tek Sayfalı Uygulama (SPA) çerçeveleriyle tümleştirmeyi destekler. Başlangıçta, bu çerçevelerle tümleştirme, sunucu tarafı ön oluşturma ve Webpack ile tümleştirme gibi senaryoları işleyen ASP.NET Core'a özgü bileşenlerle gerçekleştirilmiştir. Zaman geçtikçe, endüstri standartları değişti. SPA çerçevelerinin her biri kendi standart komut satırı arayüzlerini yayımladı. Örneğin, Açısal CLI ve create-react-app.

ASP.NET Core 2.1 Mayıs 2018'de piyasaya sürüldüğünde, ekip standartlardaki değişikliğe yanıt verdi. SPA çerçevelerinin kendi araç zincirleriyle entegre olmak için daha yeni ve daha basit bir yol sağlanmıştır. Yeni tümleştirme mekanizması pakette `Microsoft.AspNetCore.SpaServices.Extensions` bulunur ve Core 2.1'den ASP.NET bu yana Açısal ve Tepki proje şablonlarının temelini oluşturur.

Eski ASP.NET Core'a özgü bileşenlerin alakasız olduğunu ve önerilmediğini açıklığa kavuşturmak için:

- Pre-2.1 tümleştirme mekanizması eski olarak işaretlenmiştir.
- Destekleyen npm paketleri amortismana lı olarak işaretlenir.

#### <a name="recommended-action"></a>Önerilen eylem

Bu paketleri kullanıyorsanız, işlevselliği kullanmak için uygulamalarınızı güncelleyin:

- Pakette. `Microsoft.AspNetCore.SpaServices.Extensions`
- Kullandığınız SPA çerçeveleri tarafından sağlanan

Sunucu tarafı önoluşturma ve sıcak modül yeniden yüklemesi gibi özellikleri etkinleştirmek için ilgili SPA çerçevesi için belgelere bakın. İşlevsellik eski `Microsoft.AspNetCore.SpaServices.Extensions` *değildir* ve desteklenmeye devam edecektir.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

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
