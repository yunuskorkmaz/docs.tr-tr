---
title: Ara yazılımı modüller ve işleyicilerle karşılaştırın
description: Bu bölüm, istek işleme ardışık düzenleri için ara yazılımı tanımlayan ASP.NET Core uygulamalarla işleyicileri ve modülleri kullanan ASP.NET uygulamaları için yapı farklarını ele alırlar.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 5852aa82e58010882bda5424021302c60ba62d83
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488961"
---
# <a name="compare-middleware-to-modules-and-handlers"></a>Ara yazılımı modüller ve işleyicilerle karşılaştırın

Mevcut ASP.NET MVC veya Web API uygulamanız OWıN/Katana kullanıyorsa, en büyük olasılıkla ara yazılım kavramı hakkında bilgi sahibi olduğunuz ASP.NET Core oldukça basittir. Ancak, çoğu ASP.NET uygulaması, ara yazılım yerine HTTP modüllerine ve HTTP işleyicileriyle yararlanır. Bunları ASP.NET Core geçirmek için ek çaba gerekir.

## <a name="aspnet-modules-and-handlers"></a>ASP.NET modülleri ve işleyicileri

[Http modülleri ve http işleyicileri](https://docs.microsoft.com/troubleshoot/aspnet/http-modules-handlers) , ASP.NET mimarisinin ayrılmaz bir parçasıdır. İstek işlenirken, her istek birden çok HTTP modülü tarafından işlenir (örneğin, kimlik doğrulama modülü ve oturum modülü) ve ardından tek bir HTTP işleyici tarafından işlenir. İşleyici isteği işledikten sonra, istek HTTP modülleri üzerinden geri akar.

Uygulamanız özel HTTP modülleri veya HTTP işleyicileri kullanıyorsa, bunları ASP.NET Core geçirme planına sahip olmanız gerekir. ASP.NET Core en olası değişikliği ara yazılımlar.

## <a name="aspnet-core-middleware"></a>ASP.NET Core ara yazılımı

ASP.NET Core her uygulamanın yönteminde bir istek işlem hattı tanımlar `Configure` . Bu istek ardışık düzeni, bir gelen isteğin uygulama tarafından nasıl işlendiğini tanımlar. işlem hattının her bir yöntemi, bir yöntem sonlanana kadar bir sonraki yöntemi çağırır ve *Ara yazılım* zinciri sonlandırıldığında ve yığın geri döndürüyor. Ara yazılım tüm istekleri hedefleyebilir veya yalnızca istenen yola veya diğer faktörlere bağlı olarak belirli isteklere eşlenecek şekilde yapılandırılabilir. `Configure`Uygulama yönteminde tamamen veya ayrı bir sınıfta uygulanan şekilde yapılandırılabilir.

HTTP modüllerini kullanan bir ASP.NET MVC uygulamasındaki davranış, büyük olasılıkla [özel ara yazılım](https://docs.microsoft.com/aspnet/core/fundamentals/middleware/?view=aspnetcore-3.1&preserve-view=true)için en uygun seçenektir. Özel HTTP işleyicileri, aynı yola yanıt veren özel rotalar veya uç noktalar ile değiştirilebilir.

## <a name="references"></a>Başvurular

- [ASP.NET HTTP modülleri ve HTTP işleyicileri](https://docs.microsoft.com/troubleshoot/aspnet/http-modules-handlers)
- [ASP.NET Core ara yazılımı](https://docs.microsoft.com/aspnet/core/fundamentals/middleware/?view=aspnetcore-3.1&preserve-view=true)

>[!div class="step-by-step"]
>[Önceki](dependency-injection-differences.md) 
> [Sonraki](configuration-differences.md)
