---
title: ASP.NET MVC ve ASP.NET Core içindeki statik dosyaları sunma
description: IIS 'de ASP.NET MVC ile karşılaştırıldığında ASP.NET Core statik dosyalar sunma desteğini yapılandırma yenilikleri nelerdir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 02f84a6985835502c24db8cc68db24c8de086b18
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105820"
---
# <a name="serve-static-files-in-aspnet-mvc-and-aspnet-core"></a>ASP.NET MVC ve ASP.NET Core içindeki statik dosyaları sunma

Çoğu Web uygulaması, olduğu gibi istemciye gönderilmesi gereken sunucu tarafı mantığı ve statik dosyaların bir birleşimini içerir. ASP.NET MVC 'den ASP.NET Core tanıtıcısı statik dosyalara hizmet vermeye nasıl yapılır?

## <a name="host-static-files-in-aspnet-mvc"></a>ASP.NET MVC 'de statik dosyaları barındırma

IIS tarafından barındırılan ASP.NET MVC uygulamaları, genellikle statik dosyaları doğrudan uygulamadan barındırır. ASP.NET MVC, statik dosyaların sunucuda özel tutulması gereken dosyalarla yan yana yerleştirilmesini destekler. IIS ve ASP.NET, belirli dosyaların veya dosya uzantılarının ASP.NET uygulamasının barındırıldığı klasörden sunulmasını açıkça kısıtlamayı gerektirir.

Birçok statik dosya için bir içerik teslim ağı (CDN) kullanmak iyi bir uygulamadır. [Statik içerik barındırma](/azure/architecture/patterns/static-content-hosting) , uygulama sunucularından yükü ve bant genişliğini azaltırken daha iyi performans sağlar.

## <a name="host-static-files-in-aspnet-core"></a>Statik dosyaları ASP.NET Core içinde barının

Bu, şaşırtıcı olabilir, ancak ASP.NET Core statik dosyalar için yerleşik desteğe sahip değildir. IIS tarafından etkinleştirilen, ASP.NET 'in bir parçası olarak her zaman var olan bu özellik, ASP.NET Core veya Kestrel Web sunucusuna içsel değildir. ASP.NET Core bir uygulamadan statik dosyalara hizmeti sağlamak için [statik dosyalar ara yazılımı](/aspnet/core/fundamentals/static-files)' nı yapılandırmanız gerekir.

Statik dosya ara yazılımı yapılandırıldığında, ASP.NET Core bir uygulama belirli bir klasörde bulunan tüm dosyaları (genellikle */Wwwroot*) sunar. Uygulama veya proje klasöründeki başka hiçbir dosya, yanlışlıkla sunucu tarafından açığa çıkmakta risk altında değil. IIS 'de olduğu gibi, dosya adlarına veya uzantılara dayalı özel kısıtlamalar yapılandırılması gerekmez. Bunun yerine, geliştiriciler dosyaları *Wwwroot* klasörüne yerleştirdiklerinde herkese açık bir şekilde sunmayı seçer. Varsayılan olarak, bu klasörün dışındaki dosyalar paylaşılmaz.

Statik dosyalar için destek ara yazılım kullandığından, diğer tüm ara yazılımlar aynı istek ardışık düzeninin bir parçası olarak uygulanabilir. Ara yazılım örnekleri arasında kimlik doğrulaması, önbelleğe alma ve sıkıştırma sayılabilir.

Tabii ki, CDNs, ASP.NET MVC uygulamalarında kullandıkları her nedenden dolayı ASP.NET Core uygulamalar için iyi bir seçimdir. .NET Core 'a geçişe hazırlanma kapsamında, uygulamanızın bir CDN 'yi kullandığındaki avantajlar varsa, .NET Core 'a geçmeden önce statik dosyaları bir CDN 'ye taşımak iyi olacaktır. Bunun yapılması, statik varlıkların geçiş çabalarının genel kapsamını azaltır.

## <a name="references"></a>Başvurular

- [Statik içerik barındırma](/azure/architecture/patterns/static-content-hosting)
- [ASP.NET Core statik dosyalar](/aspnet/core/fundamentals/static-files)

>[!div class="step-by-step"]
>[Önceki](hosting-differences.md) 
> [Sonraki](dependency-injection-differences.md)
