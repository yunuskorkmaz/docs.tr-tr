---
title: ASP.NET MVC ve ASP.NET Core denetleyicilerini karşılaştırın
description: ASP.NET Core MVC denetleyicileri, ASP.NET MVC 5 ve Web API 2 denetleyicilerine benzerdir, ancak önemli farklılıklar vardır. Bu bölümde, ASP.NET MVC ve Web API 2 ' den ASP.NET Core için uygulamaların bağlantı noktası için gereken farklar ve adımlar incelenir.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 2c2b7b848162a6ab9901ac9f7779787e2cc994ce
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106042"
---
# <a name="compare-controllers-in-aspnet-mvc-and-web-api-with-controllers-in-aspnet-core"></a>ASP.NET Core 'daki denetleyicilerle ASP.NET MVC ve Web API 'sinde denetleyicileri karşılaştırın

ASP.NET MVC 5 ve Web API 2 ' de, iki farklı `Controller` temel tür vardı. Şuradan devralınan MVC denetleyicileri `Controller` ; Web API denetleyicileri öğesinden devralındı `ApiController` . ASP.NET Core, bu nesne hiyerarşisi birleştirildi. ASP.NET Core ' deki API denetleyicilerinin ' den devralması `ControllerBase` ve özniteliği eklemesi önerilir `[ApiController]` . Standart Görünüm tabanlı MVC denetleyicileri öğesinden devralması gerekir `Controller` .

Her iki çerçeve için de denetleyiciler, eylem yöntemlerinin kümelerini düzenlemek için kullanılır. Filtreler ve rotalar, işlem düzeyine ek olarak bir denetleyici düzeyinde uygulanabilir. Bu kurallar, `Controller` varsayılan davranış ve öznitelikleri uygulanmış özel temel türler kullanılarak daha fazla genişletilebilir.

ASP.NET MVC 'de içerik anlaşması desteklenmez. ASP.NET Web API 2, ASP.NET Core olduğu gibi, içerik anlaşmasını destekler. [İçerik anlaşmasını](/aspnet/core/web-api/advanced/formatting)kullanarak, bir isteğe döndürülen içerik biçimi, istemcinin içeriğin alınması için tercih edilen bir şeklini belirten üst bilgiler tarafından belirlenebilir.

ASP.NET Web API denetleyicilerini ASP.NET Core geçirirken, varsa birkaç bileşenin değiştirilmesi gerekir. Bunlar `ApiController` temel sınıfa, `System.Web.Http` ad alanına ve arabirime başvuruları içerir `IHttpActionResult` . [Bu belirli farklılıkları geçirmeye ilişkin öneriler için belgelere](/aspnet/core/migration/webapi)bakın. ASP.NET Core içindeki API eylemleri için tercih edilen dönüş türünün olduğunu unutmayın `ActionResult<T>` .

Ayrıca, `[ChildActionOnly]` öznitelik ASP.NET Core desteklenmez. ASP.NET Core, benzer işlevler [görüntüleme bileşenleri](/aspnet/core/mvc/views/view-components)kullanılarak elde edilir.

ASP.NET Core iki yeni öznitelik içerir: [Tüketimesattribute](/dotnet/api/microsoft.aspnetcore.mvc.consumesattribute) ve [ProducesAttribute](/dotnet/api/microsoft.aspnetcore.mvc.producesattribute). Bunlar, bir işlemin kullandığı veya ürettiği türü belirtmek için kullanılır. Bu, API 'YI [Swagger/Openapı](/aspnet/core/tutorials/web-api-help-pages-using-swagger)gibi araçları kullanarak Yönlendirme ve belgeleme için yararlı olabilir.

## <a name="references"></a>Başvurular

- [ASP.NET Core Web API 'sindeki yanıt verilerini biçimlendirme](/aspnet/core/web-api/advanced/formatting)
- [ASP.NET Web API 'sinden ASP.NET Core 'e geçiş](/aspnet/core/migration/webapi)

>[!div class="step-by-step"]
>[Önceki](identity-differences.md) 
> [Sonraki](razor-differences.md)
