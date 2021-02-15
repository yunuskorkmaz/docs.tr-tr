---
title: ASP.NET Web Forms uygulamalarını geçirme stratejileri
description: Ekipler, ASP.NET Web Forms uygulamalarını .NET Core 'a geçirmek için hangi stratejileri kullanabilir?
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: 0b37a37f047de50c347313be14a2228838da6995
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488954"
---
# <a name="strategies-for-migrating-aspnet-web-forms-apps"></a>ASP.NET Web Forms uygulamalarını geçirme stratejileri

Bu kitapta, büyük ASP.NET MVC ve Web API uygulamalarının .NET Core 'a geçirilmesi için rehberlik sunulmaktadır. Bu ASP.NET uygulamalarından bazıları, değinilmesi gereken Web Forms (*. aspx*) sayfalarını da içerebilir. ASP.NET Web Forms .NET Core (veya ASP.NET Web Pages) sürümünde desteklenmez. Genellikle, bu sayfaların işlevselliği ASP.NET Core 'ye taşıma sırasında yeniden yazılması gerekir. Bununla birlikte, gereken genel çabayı azaltmaya yardımcı olmak için, bu geçiş sırasında veya sırasında uygulayabileceğiniz bazı stratejiler vardır.

Web Forms, oldukça bir süre içinde desteklenmeye devam edecektir. Bir seçenek, bu işlevselliği bir ASP.NET 4. x uygulamasında tutmak olabilir.

## <a name="separate-business-logic-and-other-concerns"></a>İş mantığını ve diğer kaygıları ayırın

ASP.NET Web Forms sayfalarınızda daha az kod, daha iyidir. Mümkün olduğunda, iş mantığını ve farklı sınıflarda veri erişimi gibi diğer kaygıları ayrı sınıf kitaplıklarında idealdir. Bu sınıf kitaplıkları .NET Standard ve herhangi bir ASP.NET Core uygulaması tarafından tüketilebilir.

## <a name="implement-client-behavior-and-web-apis"></a>İstemci davranışı ve Web API 'Leri uygulama

API çağrılarının yardımıyla Web Forms veya tarayıcıda uygulama gerçekleştirme arasındaki seçimi göz önünde bulundurun. İkincisini tercih edin. API 'Leri ASP.NET Core 'ye geçirme desteklenir. İstemci tarafı davranışı, uygulamanızın kullandığı sunucu tarafı yığınından bağımsız olmalıdır. Bu yaklaşımın kullanılması, daha hızlı bir kullanıcı deneyimi sağlamaya yönelik ek avantaja sahiptir.

## <a name="consider-blazor"></a>Blazor değerlendirin

Blazor JavaScript yerine C# ile etkileşimli Web uda oluşturmanıza olanak sağlar. Bu, sunucu üzerinde veya WebAssembly kullanarak tarayıcıda çalışabilir. ASP.NET Web Forms uygulamalar, sayfa tarafından Blazor uygulamalarına kadar sayfadan oluşabilir. Web Forms uygulamaları Blazor 'e taşıma hakkında daha fazla bilgi için bkz. [Blazor for ASP.NET Web Forms Developers](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/). Ayrıca, bir açık kaynaklı topluluk projesi, [Blazor Web Forms bileşenleri](https://fritzandfriends.github.io/BlazorWebFormsComponents/)kapsamında birçok Web Forms denetimi Blazor. Bu bileşenlerle, yerleşik Web Forms denetimlerini kullansalar bile, Web Forms sayfaları daha kolay bir şekilde bağlantı noktası oluşturabilirsiniz.

## <a name="summary"></a>Özet

Doğrudan ASP.NET Web Forms 'den ASP.NET Core geçiş desteklenmez. Ancak, ASP.NET Core daha kolay bir şekilde geçmeyi sağlamak için stratejiler vardır. Web Forms işlevlerinden şu şekilde ASP.NET Core başarıyla geçiş yapabilirsiniz:

* Web dışı işlevselliği projelerinizden koruma.
* Mümkün olan yerlerde Web API 'Leri kullanma.
* Daha modern bir kullanıcı arabirimi için Blazor seçeneği olarak değerlendiriliyor.

## <a name="references"></a>Başvurular

- [Ücretsiz e-kitap: ASP.NET Web Forms geliştiricileri için Blazor](https://devblogs.microsoft.com/aspnet/blazor-aspnet-webforms-ebook/)
- [Blazor Web Forms bileşenleri (topluluk projesi)](https://fritzandfriends.github.io/BlazorWebFormsComponents/)

>[!div class="step-by-step"]
>[Önceki](incremental-migration-strategies.md) 
> [Sonraki](deployment-strategies.md)
