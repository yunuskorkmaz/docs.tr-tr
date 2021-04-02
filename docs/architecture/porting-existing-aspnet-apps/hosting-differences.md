---
title: ASP.NET MVC ve ASP.NET Core arasındaki barındırma farklılıkları
description: ASP.NET MVC uygulamalarının ASP.NET Core uygulamalara karşı nasıl barındırıldığı ile arasındaki farklılıklara genel bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 9881a40403f8109fa63e25167b753ed4ce8ade17
ms.sourcegitcommit: b5d2290673e1c91260c9205202dd8b95fbab1a0b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2021
ms.locfileid: "106122904"
---
# <a name="hosting-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki barındırma farklılıkları

ASP.NET MVC uygulamaları IIS 'de barındırılır ve davranışları için IIS yapılandırmasına bağlı olabilir. Bu genellikle [IIS modüllerini](/iis/get-started/introduction-to-iis/iis-modules-overview)içerir. ASP.NET MVC 'den ASP.NET Core 'e bağlantı noktasına hazırlanmaya yönelik bir uygulama gözden geçirilme kapsamında, takımlar, varsa, sunucusunda yüklü olan IIS modülleri listesinden hangi modüllerin kullandığını tanımlarlar.

[ASP.NET Core uygulamalar birçok farklı sunucu üzerinde çalışabilir](/aspnet/core/fundamentals/servers/). Varsayılan Kestrel platformlar arası sunucu, iyi bir varsayılan seçenektir. Kestrel ' de çalışan uygulamalar IIS tarafından barındırılabilir ve ayrı bir işlemde çalıştırılabilir. Windows 'da, uygulamalar IIS 'de veya HTTP.sys kullanarak da çalışır. Kestrel genellikle en iyi performans için önerilir. HTTP.sys, uygulamanın Internet 'e sunulabileceği senaryolarda ve gerekli yetenekler, HTTP.sys tarafından desteklenmediği durumlarda kullanılabilir.

Kestrel, IIS modülleriyle eşdeğer değildir (ancak IIS 'de barındırılan uygulamalar IIS modüllerinden yine de faydalanabilir). Eşdeğer davranış elde etmek için, ASP.NET Core uygulamada yapılandırılan [Ara yazılım](/aspnet/core/fundamentals/middleware/) genellikle kullanılır.

## <a name="references"></a>Başvurular

- [IIS Modülleri](/iis/get-started/introduction-to-iis/iis-modules-overview)
- [ASP.NET Core ara yazılımı](/aspnet/core/fundamentals/middleware/)
- [ASP.NET Core sunucuları](/aspnet/core/fundamentals/servers/)

>[!div class="step-by-step"]
>[Önceki](app-startup-differences.md) 
> [Sonraki](serving-static-files.md)
