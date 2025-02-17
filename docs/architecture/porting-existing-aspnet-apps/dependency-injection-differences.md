---
title: ASP.NET MVC ve ASP.NET Core arasındaki bağımlılık ekleme farkları
description: Bağımlılık ekleme 'nin ASP.NET MVC ve ASP.NET Core 'de nasıl çalıştığı, farklı oldukları ve ASP.NET MVC 'den ASP.NET Core nasıl geçirileceği hakkında bir bakış.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: aa1c7dd2f70e1a545352feb6560177bc6e2baa2d
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106028"
---
# <a name="dependency-injection-differences-between-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core arasındaki bağımlılık ekleme farkları

Bağımlılık ekleme (DI), ASP.NET MVC veya Web API 'sine derlenmese de, birçok uygulama, denetim (ıOC) kapsayıcısının bir NuGet paketini ekleyerek etkinleştirir. Bunlar bazen bağımlılık ekleme (veya Inversion) için dı kapsayıcıları olarak adlandırılır. ASP.NET MVC uygulamalarında kullanılan en popüler kapsayıcıların bazıları şunlardır:

- [Autofac](https://www.autofac.org/)
- [Unity](https://unitycontainer.github.io/)
- [Nekleme](http://www.ninject.org/)
- [StructureMap](http://structuremap.github.io/) *(kullanım dışı)*
- [Role Wınsörü](http://www.castleproject.org/projects/windsor/)

ASP.NET MVC uygulamanız DI kullanıyorsa, muhtemelen ASP.NET Core için yerleşik desteğini araştırmak isteyeceksiniz. Dı, uygulamanızda gevşek modülleri yükseltir ve [katı](https://www.weeklydevtips.com/episodes/047)gibi kurallara daha iyi test ve bağlılığı sağlar.

Uygulamanız DI kullanıyorsa, kullandığınız kapsayıcının ASP.NET Core destekleyip desteklemediğini en iyi şekilde yapmanız olasıdır. Bu durumda, bu dosyayı ve tür eşlemelerinizi ve yaşam sürelerini açıklayan özel yapılandırma kurallarınızı kullanmaya devam edebilirsiniz.

Her iki durumda da, uygulamanızın ihtiyaçlarını karşılayacağından, ASP.NET Core ile birlikte gelen dı için yerleşik desteği kullanmayı düşünmelisiniz.

## <a name="dependency-injection-in-aspnet-core"></a>ASP.NET Core bağımlılık ekleme

ASP.NET Core, uygulamaların DI 'yi kullanacağı varsayılır. Yalnızca çerçeveye yerleşik değildir, ancak ASP.NET Core uygulamalarınıza Framework özellikleri desteğini getirmek için gereklidir. Uygulama başlangıcında, `ConfigureServices` dı kapsayıcısının (hizmet koleksiyonu/hizmet sağlayıcısı) oluşturup uygulamada ekleyebileceği tüm türlerin kaydolmasından sorumlu olan bir çağrı yapılır. Entity Framework Core, kimlik ve hatta MVC gibi yerleşik ASP.NET Core özellikler, yöntemi içinde hizmet olarak yapılandırarak uygulamaya getirilir `ConfigureServices` .

Uygulamalar, varsayılan uygulamayı kullanmanın yanı sıra özel kapsayıcılar kullanmaya devam edebilir. [Belgeler, varsayılan hizmet kapsayıcısının nasıl değiştirileceğini anlatmaktadır](../../core/extensions/dependency-injection-guidelines.md#default-service-container-replacement).

DI ASP.NET Core için temel. Takımınız bu uygulamada zaten iyi değilse, uygulamanızı aktarmadan önce bunu anlamak isteyeceksiniz.

## <a name="references"></a>Başvurular

- [.NET 'e bağımlılık ekleme](../../core/extensions/dependency-injection.md)
- [ASP.NET Core'da Bağımlılık Ekleme](/aspnet/core/fundamentals/dependency-injection)

>[!div class="step-by-step"]
>[Önceki](serving-static-files.md) 
> [Sonraki](middleware-modules-handlers.md)
