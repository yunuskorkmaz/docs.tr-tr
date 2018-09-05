---
title: WIF oturum yönetimi
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 04c2f4bdfe2a6309fde0821db308ee2a83887323
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520558"
---
# <a name="wif-session-management"></a>WIF oturum yönetimi
Bir istemci ilk bir bağlı olan taraf tarafından barındırılan korunan bir kaynağa erişmeyi denediğinde, istemci öncelikle kendisi için bağlı olan taraf tarafından güvenilen bir güvenlik belirteci hizmeti (STS) doğrulaması gerekir. STS istemciye daha sonra bir güvenlik belirteci verir. İstemci bu belirteci ardından korumalı kaynağa istemci erişim veren bir bağlı olan tarafa sunar. Ancak, özellikle, hatta aynı bilgisayarda veya bağlı olan taraf aynı etki alanında olabileceğinden sts'ye her istek için yeniden kimlik doğrulaması sağlamak için istemci istemezsiniz. Bunun yerine, bağlı olan taraf oturumu, istemci oturum güvenlik belirteci kendisini tüm istekler için bağlı olan tarafa sonra ilk istek kimliğini doğrulamak için kullanır ve istemci Windows Identity Foundation (WIF) sahiptir. Bağlı olan taraf istemcinin yeniden oluşturmak için bir tanımlama bilgisi içinde depolanır, bu oturum güvenlik belirteci kullanabilirsiniz <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 STS, hangi kimlik doğrulaması istemci sağlamalıdır tanımlar. Ancak, istemcinin birden çok kimlik bilgileri ile kendisini STS'ye kimlik doğrulaması yapabilir olabilir. Örneğin, bir Windows Live, bir kullanıcı adı ve parola, sertifika ve bir smartkey belirtecine sahip olabilir. Bu durumda, STS verir istemci istemci sunan kimlik bilgilerini birine karşılık gelen her bir kimliği ile birçok kimlik. İstemci erişim düzeyini karar verdiğinde bağlı olan tarafa bir veya daha fazla bu kimlikleri kullanabilirsiniz.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> İstemcinin yeniden oluşturmak için kullanılan <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, tüm istemci kimliklerini içeren <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>. Her <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> koleksiyonda bu kimlikle ilişkili önyükleme belirteçleri içerir.  
  
 Özgün Oturum belirteci oturum kimliği ile yeni bir oturum belirteci verilirse <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> belirteç önbelleği Oturum belirteci güncelleştirmez. Her zaman benzersiz bir oturum kimliği ile oturum belirteci örneğini oluşturmanız gerekir  
  
> [!NOTE]
>  Session.SecurityTokenHandler.ReadToken oluşturur bir <xref:System.Xml.XmlException> geçersiz giriş; alırsa, özel durum Örneğin, oturum belirteci içeren bir tanımlama bilgisi bozuk. Bu özel durumu yakalar ve uygulamaya özgü davranış sağlar öneririz.  
  
 Korumalı bir Web sayfası korumalı etki alanında olan kaynaklar (örneğin, küçük grafik) çok sayıda içeriyorsa, istemci kendi bu kaynakların her biri indirmek için bağlı olan taraf için yeniden kimliğini doğrulaması gerekir. Oturum kimlik doğrulama belirteci kullanımını her istek için sts'ye kimlik doğrulama gereksinimini ortadan kaldırır, ancak çok sayıda tanımlama bilgisi üzerinden gönderildiğini hala anlamına gelir. Alt öğeleri korumasız bir etki alanında depolanan ve ana Web sayfasından bağlı kaynakları ve önemli verileri korumalı etki alanında depolanır, böylece Web page up ayarlamak isteyebilirsiniz. Ayrıca, yalnızca korumalı etki alanı başvurmak için tanımlama bilgisi yolunu ayarlayın.  
  
 İçin bir işleyici sağlayarak Microsoft önerir başvuru modunda çalışmaya <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> olayında **global.asax.cs** dosya ve ayarı **IsReferenceMode** geçirilen belirteç özelliği <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> özelliği. Bu güncelleştirmeler Oturum belirteci her istek için referans modunda çalışır ve yalnızca ayarlama üzerinden stadyumlarda sağlayacak <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> oturumu kimlik doğrulama modülü özelliği.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
 Oturum yönetimi mekanizması genişletebilirsiniz. Bunun bir nedeni, performansı artırmak için olacaktır. Örneğin, bir özel tanımlama bilgisi işleyici dönüştüren ya da belleğe durumuna ve tanımlama bilgisine unsurları arasında oturum güvenlik belirteci iyileştirir oluşturabilirsiniz. Bunu yapmak için yapılandırabileceğiniz <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> özelliği <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> türeyen bir özel tanımlama bilgisi işleyicisi kullanacak şekilde <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType> tanımlama bilgilerini Köprü Metni Aktarım Protokolü (HTTP) için izin verilen boyutunu aştığından varsayılan tanımlama bilgisi işleyicisidir; Bunun yerine özel bir tanımlama bilgisi işleyici kullanırsanız, parçalama uygulamalıdır.  
  
 Daha fazla bilgi için [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) örnek. Bu örnek, böylece büyük tanımlama bilgileri değişimi yerine başvuruya göre oturumları kullanabilirsiniz (aksine, bir tokenreplycache) bir grup hazır oturum önbelleği gösterir; Bu örnek, bir gruptaki tanımlama bilgilerini güvenliğini sağlamak için daha kolay bir yolu da gösterir. WCF tabanlı oturum önbelleğidir. Güvenli hale getirme oturumu ile ilgili örnek web.config dosyasında yalnızca uygun parçacığı yapıştırarak etkinleştirilebilir MachineKey, temel bir tanımlama bilgisi dönüşümün WIF 4.5 içinde yeni bir özellik gösterir. Örnek değil "katılabilmesi", ancak Grup kullanıma hazır uygulamanızı yapmak için ihtiyacınız olanlar gösterilmektedir.
