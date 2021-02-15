---
title: ASP.NET Identity ve ASP.NET Core kimliğini karşılaştırın
description: Bu bölümde ASP.NET Identity ve ASP.NET Core kimliği arasındaki farklar incelanıyor. Bu, .NET Framework ' den .NET Core 'a geçiş planlarken özellikle önemlidir.
author: ardalis
ms.date: 11/13/2020
ms.openlocfilehash: bf915c7343b0c8060ef8192387a3cec33a1f0eea
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100488887"
---
# <a name="compare-aspnet-identity-and-aspnet-core-identity"></a>ASP.NET Identity ve ASP.NET Core kimliğini karşılaştırın

ASP.NET MVC 'de, kimlik özellikleri genellikle *App_Start* klasöründe *IdentityConfig.cs* ' de yapılandırılır. Bunun mevcut uygulamada nasıl yapılandırıldığını gözden geçirin ve *Startup.cs* Içinde [ASP.NET Core kimliği için gereken yapılandırmayla](https://docs.microsoft.com/aspnet/core/security/authentication/identity-configuration) karşılaştırın.

ASP.NET Identity, Kullanıcı arabirimi oturum açma işlevselliğini destekleyen ve kullanıcıları, parolaları, profil verilerini, rolleri, talepleri, belirteçleri, e-posta onaylarını ve daha fazlasını yöneten bir API 'dir. Facebook, Google, Microsoft ve Twitter gibi dış oturum açma sağlayıcılarını destekler.

ASP.NET MVC uygulamanız ASP.NET üyeliğini kullanıyorsa, [ASP.NET üyelik kimlik doğrulamasından ASP.NET Core 2,0 kimliğine geçiş](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)kılavuzunu bulacaksınız. Bu temel olarak, geçirilen Kullanıcı kayıtlarıyla ASP.NET Core kimliğini kullanabilmeniz için bir veri geçiş alýþtýrmadır.

ASP.NET Identity kullanıcılarınızı ASP.NET Core kimliğe geçirirseniz, parola karmalarını güncelleştirmeniz veya yeni ASP.NET Core kimlik yaklaşımına veya eski ASP.NET Identity yaklaşımıyla hangi parolaların karma olduğunu izlemeniz gerekebilir. [Stack Overflow açıklanan bu yaklaşım](https://stackoverflow.com/a/57074910/13729) , Kullanıcı parolası karmalarının tek seferde değil, zaman içinde geçirilmesi için bazı seçenekler sağlar.

ASP.NET Identity karşılaştırılan ASP.NET Core kimliği için verilen en büyük farklardan biri, projenize dahil etmeniz gereken küçük kod. ASP.NET Core kimlik artık Razor sınıf kitaplığı olarak gelir, yani Kullanıcı arabirimi ve Logic bir NuGet paketinden kullanılabilir. [ASP.NET Core kimlik dosyalarını](https://docs.microsoft.com/aspnet/core/security/authentication/scaffold-identity) düzenleyerek mevcut kullanıcı arabirimini ve mantığı geçersiz kılabilirsiniz, ancak bu durumda, yalnızca değiştirmek istediğiniz sayfaları, var olan her birini değil yalnızca yapı birimi için de kullanabilirsiniz.

## <a name="migrate-from-owin--katana"></a>OWıN/Katana 'dan geçiş

Aşağıdaki kaynaklar OWıN/Katana 'dan geçiş için bazı rehberlik sunar:

- [Geçiş](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/#globalasax-file-replacement)
- [Bir katana, ASPNET 5](https://devblogs.microsoft.com/aspnet/katana-asp-net-5-and-bridging-the-gap/)

## <a name="references"></a>Başvurular

- [Kimlik doğrulaması ve kimliği ASP.NET Core geçir](https://docs.microsoft.com/aspnet/core/migration/identity)
- [ASP.NET Core kimliğe giriş](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)
- [ASP.NET Core kimliğini yapılandırma](https://docs.microsoft.com/aspnet/core/security/authentication/identity-configuration)
- [ASP.NET Core projelerinde yapı iskelesi kimliği](https://docs.microsoft.com/aspnet/core/security/authentication/scaffold-identity)

>[!div class="step-by-step"]
>[Önceki](authentication-differences.md) 
> [Sonraki](controller-differences.md)
