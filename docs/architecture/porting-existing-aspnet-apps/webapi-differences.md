---
title: ASP.NET Web API 2 ve ASP.NET Core karşılaştırın
description: Web API 'Leri ASP.NET Web API 2 uygulamaları ve ASP.NET Core uygulamalar arasında farklılık gösterir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02e243591c0a6815cfe8371fbbc0b45a1cf22651
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488938"
---
# <a name="compare-aspnet-web-api-2-and-aspnet-core"></a>ASP.NET Web API 2 ve ASP.NET Core karşılaştırın

ASP.NET Core, ASP.NET Web API 2 ' ye yönelik yinelemeli geliştirmeler sunar, ancak Web API 2 kullanan geliştiricilere tanıdık gelmelidir. ASP.NET Web API 2 geliştirilmiştir ve ASP.NET MVC ile birlikte gönderilmiştir. Bu, iki yaklaşımdan öznitelik yönlendirme ve bağımlılık ekleme gibi şeylere benzer ancak farklı yaklaşımlar olduğunu belirtir. ASP.NET Core, artık MVC ve Web API 'Leri arasında ayrım yoktur. Yalnızca görüntüleme tabanlı senaryolar, API uç noktaları ve Razor Pages (ve sistem durumu denetimleri ve SignalR gibi diğer çeşitlemeler) için destek içeren yalnızca ASP.NET MVC vardır.

.NET Core 'da oluşturulan API 'Lerin yanı ASP.NET Core sıra, ASP.NET Web API 2 ' de yerleşik olanlardan daha kolay test olması gerekir. [Test farklılıklarını](testing-differences.md) bir süre içinde daha ayrıntılı olarak ele alacağız. ASP.NET Core uygulamaları barındırmak için yerleşik destek; bir test konağında, `HttpClient` uygulamaya bellek içi istekleri yapan bir test ana bilgisayarı otomatik teste geldiğinde büyük bir avantajdır.

ASP.NET Web API 2 ' den ASP.NET Core geçiş yaparken, geçiş basittir. Büyük, blok denetleyicileriniz varsa, bunları bölmek için göz önünde bulundurmanız gereken tek bir yaklaşım, [Ardalış. ApiEndpoints](https://www.nuget.org/packages/Ardalis.ApiEndpoints/) NuGet paketlerinin kullanımı olur. Bu paket, her bir uç noktayı ilişkili istek ve yanıt türleriyle ilgili belirli bir sınıfa ayırır. Bu yaklaşım [, görünüm tabanlı kod organizasyonu üzerinde Razor Pages teklifiyle aynı avantajların](comparing-razor-pages-aspnet-mvc.md)çoğunu verir.

## <a name="references"></a>Başvurular

- [ASP.NET Web API 'sinden ASP.NET Core 'e geçiş](https://docs.microsoft.com/aspnet/core/migration/webapi)
- [Ardalış. ApiEndpoints NuGet paketi](https://www.nuget.org/packages/Ardalis.ApiEndpoints/)

>[!div class="step-by-step"]
>[Önceki](comparing-razor-pages-aspnet-mvc.md) 
> [Sonraki](authentication-differences.md)
